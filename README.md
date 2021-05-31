# umbraco-demoproject
This repository gives information about demo project of Umbraco where you can change content dynamically as per your requirement.

# create-Master page
Here @RenderBody() is required to chnage the body content. Whatever we change in home page that will be reflect here.
    
    @inherits Umbraco.Web.Mvc.UmbracoViewPage
    @{
	      Layout = null;
     }
    @* the fun starts here *@

    @RenderBody()

# create-home page
Here by adding of @Model.Value("title") you can change the content of textstring.
    
    @inherits Umbraco.Web.Mvc.UmbracoViewPage
    @{
	      Layout = "Master.cshtml";
     }
    @* the fun starts here *@

    @Model.Value("title")
    
 # Model Bulder For home page
 This is the Model builder file for home page, where there is one Home class and that class contains properties for home document.
 
    using System;
    using System.Collections.Generic;
    using System.Linq.Expressions;
    using System.Web;
    using Umbraco.Core.Models;
    using Umbraco.Core.Models.PublishedContent;
    using Umbraco.Web;
    using Umbraco.ModelsBuilder.Embedded;
    
    [assembly:ModelsBuilderAssembly(PureLive = true, SourceHash = "ea40d2ebeaca3ebd")]
    [assembly:System.Reflection.AssemblyVersion("0.0.0.1")]
    
    namespace Umbraco.Web.PublishedModels
    {
    	  /// <summary>Home</summary>
    	  [PublishedModel("home")]
    	  public partial class Home : PublishedContentModel
    	  {
    		    // helpers
            #pragma warning disable 0109 // new is redundant
    		    [global::System.CodeDom.Compiler.GeneratedCodeAttribute("Umbraco.ModelsBuilder.Embedded", "8.13.0")]
    		    public new const string ModelTypeAlias = "home";
    		    [global::System.CodeDom.Compiler.GeneratedCodeAttribute("Umbraco.ModelsBuilder.Embedded", "8.13.0")]
    		    public new const PublishedItemType ModelItemType = PublishedItemType.Content;
    		    [global::System.CodeDom.Compiler.GeneratedCodeAttribute("Umbraco.ModelsBuilder.Embedded", "8.13.0")]
    		    public new static IPublishedContentType GetModelContentType()
    		    	=> PublishedModelUtility.GetModelContentType(ModelItemType, ModelTypeAlias);
    		    [global::System.CodeDom.Compiler.GeneratedCodeAttribute("Umbraco.ModelsBuilder.Embedded", "8.13.0")]
    		    public static IPublishedPropertyType GetModelPropertyType<TValue>(Expression<Func<Home, TValue>> selector)
			      => PublishedModelUtility.GetModelPropertyType(GetModelContentType(), selector);
            #pragma warning restore 0109
          
          		// ctor
          		public Home(IPublishedContent content)
          			: base(content)
          		{ }
          
          		// properties
          
          		///<summary>
          		/// Title
          		///</summary>
          		[global::System.CodeDom.Compiler.GeneratedCodeAttribute("Umbraco.ModelsBuilder.Embedded", "8.13.0")]
          		[ImplementPropertyType("title")]
          		public virtual string Title => this.Value<string>("title");
        }
    }
