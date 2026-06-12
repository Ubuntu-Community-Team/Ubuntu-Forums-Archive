---
title: "dependancy problem going to intrepid ibex?"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by pletso on 2008-11-13
Hi all this is my first post
So I upgraded to intrepid ibex
I find some problems trying to install wlassitant
at first I used synaptic and obtained:

   Could not mark package for installation or upgrade

   The following packages have unresolved dependancies.
   Make sure that all required repositories are added and
   enabled in the preferences.

   wlassistant:

   Package wlassistant has no available version, but exists in
   the database.
   This typically means that the package was mentioned in a 
   dependency and never uploaded, has been obsoleted or is 
   not available with the contents of sources.list

I don't know if i had to add an aditional repository for installing 
wlassistant.

I keep trying now with the konsole:

>sudo apt-get install wlassistant
 Reading package lists... Done
 Building dependency tree
 Reading state information... Done
 Package wlassistant is not available, but is referred to by another
 package.
 This may mean that the package is missing, has been obsoleted, or
 is only available from another source
 E: Package wlassistant has no installation candidate

then as my repositories seemed like the ones of previous release:

>sudo aptitude update

so now my repositories look like the correct ones of intrepid ibex
after the update repeated the command before and same thing happens

also tried with:

>sudo aptitude install wlassistant

 .
 ..
 ...
 No candidate version found for wlassistant           
 No candidate version found for wlassistant           
 No packages will be installed, upgraded, or removed. 
 0 packages upgraded, 0 newly installed, 0 to remove and 59 not upgraded.
 Need to get 0B of archives. After unpacking 0B will be used. 

any help?



...
.
.

---

### Post by cariboo on 2008-11-13
Have you got all the repositories selected in System-->Administration-->Software Sources? Also you have to spell it right **wlassistant** :). I did a little more looking after not finding the package in the Intrepid repositories. You can get it here:

[http://packages.ubuntu.com/hardy/wlassistant](http://packages.ubuntu.com/hardy/wlassistant)

It is the Hardy package, but it should work in Intrepid.

Jim

---

