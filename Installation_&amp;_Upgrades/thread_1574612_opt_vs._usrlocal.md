---
title: "/opt vs. /usr/local"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2010-09-14
Hi all,


 /opt & /usr/local seem to have a similar purpose: a place to put sw that is not the part of the standard system 

** Can any one give me exact hard and fast rules for when to use /opt and when to use /usr/local directories , when installing 3rd party sw?**

The following points are taken from the [COLOR="Red"]Linux magazine march edition  article /opt vs. /usr/local by kyle rankin & Bill childers[/COLOR]

I**s there any other point that I have missed ?**


**/opt**

 third party sw installed by the package manager  is in this location

On a development system, or a sandbox, having an /opt directory where you can just toss things and see if they work makes a whole lot of sense. I know I’m not going to go through the effort of packaging things myself to try them out. If the app doesn’t work out, you can simply rm the /opt/mytestapp directory and that application is history. Packaging may make these things are packaged by the software maintainer or sense when you’re running a large deployment (there are that I want to go through with making packages.  when I do package apps), but lots of times, it’s nice to toss stuff in /opt


**/usr/local**:-

 third party sw installed by the admin is in this location

the traditional (and ancient) approach to install software before proper package managers came on the scene versus the modern way to deploy software on a server.

installing in this location is an extra step when you are deploying software to your servers, but it’s a step that makes sure you can automatically handle dependencies and can use standard tools and not tar, cp and rm to add and remove packages.

Ex:- If I wanted a custom apache, I’m going to have to compile it, right? All I have to do is use the --prefix option to change where it is installed from /usr to /usr/local. In my opinion, that’s easier than the /opt approach.

---

### Post by psusi on 2010-09-14
The use of /opt has never been widespread with Linux distros.  IIRC, it was used by AT&T Unix to install third party binary programs.  /usr/local is where things install to when you compile them.  

> **sulekha said:**
> Ex:- If I wanted a custom apache, I’m going to have to compile it, right? All I have to do is use the --prefix option to change where it is installed from /usr to /usr/local. In my opinion, that’s easier than the /opt approach.

The default is /usr/local, so you won't have to change anything.  When Ubuntu builds a binary package for you to install, the --prefix argument is used to move it out of local.

---

