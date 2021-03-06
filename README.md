
![glossz logo](https://github.com/toaster99/GlossZ/raw/master/repo_images/glossz_logo.png)

[glossz.whotofollow.co](glossz.whotofollow.co)

A PHP, MySQL, Twig miniature translations glossary.
![glossz screenshot](https://github.com/toaster99/GlossZ/raw/master/repo_images/glossz_screenshot.png)
GlossZ allows the creation of miniature term glossaries. Authenticated users can create glossaries with 3-5 terms inside them and contribute term translations to their glossary or glossaries created by other users.
### Functionality
---

![glossz screenshot](https://github.com/toaster99/GlossZ/raw/master/repo_images/glossz_screenshot2.png)

##### Glossaries
Authenticated and public users are able to browse and search glossaries. Searching glossaries does partial matches on the author's username and the title of the glossary.

Authenticated users have the ability to create a glossary. Created glossaries must have 3-5 terms in them. 
##### Translations
An authenticated user has the ability to contribute a translation in any supported language to a term in a glossary they have created or that was created by another user. The list of supported languages was taken from the "Native Language" selection box on the ProZ user profile edit screen.

### Technology
---
##### Backend
For the server, GlossZ is built on PHP with the [Slim Framework](https://www.slimframework.com) and MySQL. The Slim Framework was chosen to make creating new routes faster, to provide a basic organization to the project, and to allow the usage of authentication and validation middleware. Whereas many frameworks dictate all aspects of your project, Slim gives you the basic features and suggestions for organization while leaving a majority of the decisions to the developer.

MySQL was chosen as it provides a robust database system that is widely supported on third-party hosting solutions.
##### Frontend
GlossZ's frontend was developed using [Twig Templates](http://twig.sensiolabs.org), [Bootstrap 4](http://v4-alpha.getbootstrap.com), [jQuery](http://jquery.com), [FontAwesome](http://fontawesome.io),  [Google Fonts](https://fonts.google.com) and [Stylus](http://stylus-lang.com).

Twig was chosen for this project due to its modular nature and ability to be rendered from PHP with variables passed from a controller. This allows for the implementation of routes within the PHP application that generate dynamic HTML templates rendered from Twig files.

Bootstrap was used to speed up frontend implementation while maintaining a responsive, modern design. Customizations to the Bootstrap theme were done through CSS generated from compiled Stylus files. The usage of Stylus gives flexibility in the design by breaking it down into components and by setting fonts/colors through easily changed variables.

jQuery was leveraged to provide AJAX driven components that can load without a post-back.

Google Fonts and FontAwesome were used to make the design more aesthetically pleasing and to draw attention to certain interface elements.
##### Hosting
GlossZ is deployed on a VPS from [Cloudways](http://cloudways.com). GlossZ implements GIT deployment from this repository to the server. Composer is used to mangage dependincies for the project, and [Phinx](http://phinx.org) is used to handle database migrations/seeding. The site uses SSL provided by [Let's Encrypt](https://letsencrypt.org).

### Authentication
---
When a user creates an account on GlossZ, their username, email, and password are stored in the database. The password is hashed using the `password_hash` method. User states are stored in the PHP session. Certain areas or actions on the application are protected by a custom Slim middleware component that verifies a user is authenticated.

GlossZ  also implements the ProZ sign-on API. Using this method, a user's account is created as normal on login but the user is authenticated through the O-Auth API.

### SEO
---
GlossZ was developed with SEO in mind. All pages include standard meta-tags for Open graph and Twitter. GlossZ was designed so that content is visible without relying on Javascript. CSS and Javascript files have been minified to improve page loading. The site is fully responsive and has appropriate meta tags for mobile devices. 

![sitemap](https://github.com/toaster99/GlossZ/raw/master/repo_images/sitemap.png)

A dynamic sitemap.xml file is present for indexing. The sitemap file is generated based on the glossaries and users present on the site.

![twitter meta](https://github.com/toaster99/GlossZ/raw/master/repo_images/twittercardscreenshot.png)

![facebook meta](https://github.com/toaster99/GlossZ/raw/master/repo_images/facebookmetatag.png)

Images have been created and assigned as Meta tags for Facebook, Twitter, etc.

### Integration with ProZ services
---
The ProZ service 'KudoZ' is a perfect companion to GlossZ. KudoZ allows users to contribute translations to a term/sentence/paragraph. The functionality present in GlossZ would allow users to create collections of content centered around a single theme. Users would then be able to provide translations to the content within these collections. An example of this could be as follows: A user wants to gather translations for various greetings across numerous languages. The user creates a collection titled 'Greetings' and adds various English greetings to the collection ('Hello, how are you doing today?', 'Good morning!', etc.). The collection resembles a glossary from the GlossZ application. Users can now contribute translations with associated confidence score to the content within the collection. This would resemble the KudoZ functionality.

### GlossZ API
---
GlossZ was developed so that it could easily be used in other first-party or third-party services. Through the usage of Slim and routes, the application has an exposed REST API. This could be consumed by a mobile application or used to integrate GlossZ content into other web applications.

The following routes are currently present for the API:
- /api/terms                   GET     List of all terms            => json ModelResponse
- /api/term/tid                GET     Term by id                   => json ModelResponse
- /api/term/tid/translations   GET     Translations by term         => json ModelResponse
- /api/glossaries              GET     List of all glossaries       => json ModelResponse
- /api/glossary/gid            GET     Glossary by id               => json ModelResponse
- /api/glossary/gid/terms      GET     Terms by glossary of id      => json ModelResponse
- /api/languages               GET     List of all languages        => json ModelResponse
- /api/users                   GET     List of all users            => json ModelResponse

### Future Features
---
Given more time on this project, I would love to further enhance the user experience and value that the site can offer. More fine-tuned search would allow users to narrow down their search by translation or languages. A voting system would allow better translations to rise above those of lesser quality. A commenting system would allow users to collobrate and make suggestions on a glossary's content (this would also go well with the ability to share ownership of a glossary). Categorization of glossaries would be beneficiual to SEO and allow users to find glossaries faster.

If the restriction of 3-5 terms was removed and the scope of this application was slightly expanded it could be used as a collaborative translation list platform. If users were able to upload documents, media, sentences, terms that center around a shared topic, other users could provide translations and discussion. For example, a list about "Visiting Taiwan" could have pictures of bus instructions, train announcements, bike rental instructions and phrases for ordering food all translated to various languages for future travellers. These lists would be content rich and target many different niches in numerous languages. Google would love that.

