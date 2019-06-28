IWMW 2019 - Putting all your eggs in one basket
===============================================

_Peter Edwards_ University of Leeds

Short talk delivered at the IWMW conference 2019

Slide Notes
-----------

### Introduction

Hi, I've been working at the University of Leeds since 2009 as an Application Developer, first in two of the Faculties at the University, and later as part of a central team. My background is in Libraries and the Arts Sector, and I've been a developer now for over 20 years.

This talk is about the impracticality of diversification when it comes to choosing a content management platform, and the benefits you can gain when you settle on one solution and use it for everything. Although focusing on a single solution isn't such a good idea when you are running a portfolio of investments and you need to spread risk, in this case putting all your eggs in one basket serves to mitigate risk.

I spent a good hour looking up this phrase - apparently it is from a "Franco-Cockney" translation which infused the original text with flippancy and facetiousness, and has been described as "worse than worthless" by other translators of the text.

### The UNIX Hosting service at Leeds

When I first came to the University of Leeds, the CMS landscape was very diverse. The University operated a UNIX web hosting service much like a commercial hosting service, where staff could request web space and do whatever they wished with it once they got it. This resulted in a profusion of different CMS systems, static sites and custom applications.

The systems depicted on this slide were all represented there, along with some I couldn't find logos for any more.

In December 2016, all the sites in the UNIX hosting service were compromised and malicious code was inserted into each site. Any files which were writable by the webserver user were targets, and malicious JavaScript and PHP code was inserted into many of the files. Specific systems had their own attack vectors, such as the theme files in WordPress, the site cache in MODx, or the database in drupal, mediawiki and others.

All sites needed to be examined for signs of the compromise, and it quickly became apparent that the initial attack vector would have been impossible to determine, as there were so many possibilities to choose from.

### The WordPress hosting service at Leeds

Initially, the service consisted of a single WordPress multisite installation containing 160+ sites which had been created in 2011 for the two Faculties in which I had been working. This installation had outgrown its hosting (in a Virtual Machine on campus) and the service needed to be formalised and expanded to include other Faculties.

The purpose of the service was to provide hosting for small to medium sized websites for research projects, conferences and research groups in a managed environment. However, half way through the pilot, the service was almost filled to capacity with sites moving from the compromised UNIX hosting service

About half of WordPress sites were moved using an automated tool written by developers at WP Engine, but they had to be cleared of any infected files beforehand. Most of the remaining WordPress sites could be migrated using built-in import/export tools in WordPress.

Sites in other systems needed to be migrated to WordPress, so some migrations were carried out using the source system to generate a WordPress import file or CSV/JSON data which could then be imported into WordPress using custom scripts or plugins - this was only carried out for larger sites. The majority were migrated manually by copying and pasting content.

Since 2017, a large number of sites have been migrated to WordPress from Faculties whose when the main site was moved to the corporate CMS (Jadu). In 2018, over 120 sites were created in the service.

### Using WordPress at scale

The main disadvantage in using WordPress for multiple sites is the frequency this system, and its supporting plugins and themes, are updated. When you reach over 20 sites in separate installations, the need for an automated updating system becomes important. ManageWP is probably the best of these (which remains free of charge) at present, but there are alternatives.

For those of you not familiar with WordPress multisite, it enables you to set up multiple WordPress sites which utilise the same codebase and database. Users, Plugins and Themes are managed at a "Network" level, which makes it easy to control what software is available to users on sites within the Network.

We currently use WordPress multisite to host over 600 websites at the University of Leeds. These are spread across a few separate WordPress installations, so sites utilising the University's branded theme are all grouped together in an installation which only has this theme installed and the plugins which are known to work with it. Non-branded sites are placed in a different installation with a single theme (GeneratePress) installed along the plugins which are known to work with that theme. One installation is used to dump older WordPress sites developed by third parties and sites which require esoteric plugins, in order to separate them from the more simple sites.

Domain mapping allows you to assign different domain names to each of the sites in a multisite Network. All websites in the service at Leeds use their own domain names, and administrators and editors of these sites have the same experience as they would on a standalone installation of WordPress, with the exception that they cannot change the Theme, install Plugins or add users.

WP Engine provides caching and optimisation on their platform, but this can be set up quite easily using caching plugins and a little bit of server configuration. 

WordPress is not an optimal system for websites, and all pages should ideally be cached as HTML files by an appropriate plugin. WP Engine go a few steps further than this, including loading databases into RAM, which has caused problems for us with the multisite installations.

The disadvantages in using WordPress like this can also be turned around to be advantages (as you will see on the next slide).

The main disadvantage is that having a service which aids the proliferation of websites requires governance and monitoring, and contribution from Communications and Marketing to ensure that information is not being unnecessarily duplicated and maintains a high level of quality.

The ability to create sites in a standard design which follows the University brand is something which was sorely needed at the University of Leeds. There are still examples of websites hosted on campus which use the University logo from the 1980s and distinctly mid-1990s designs. Any new sites which utilise the leeds.ac.uk domain are now forced to apply the University branding.

The tools WP Engine provide on their platform to update code we produce are very powerful, and I can update the themes and plugins created by the Development team on multiple installations in a matter of minutes. We are hoping to automate this process further using Azure DevOps.

As all sites are within the same system, we also have access to data for them such as last updated dates, page and post counts, and the combined size of any uploaded files. We also use google analytics on all sites to monitor traffic and inform archiving strategies. 


