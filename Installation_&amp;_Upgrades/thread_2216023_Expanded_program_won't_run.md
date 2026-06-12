---
title: "Expanded program won't run"
date: 2014-04-09
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2014-04-09
I expanded a .7z file then checked "Allow executing file as program" in its Permissions tab from its Properties window, then double-clicked and nothing happens! 
What could be reason/s?
The file in question is: a specific Blender build at GraphicAll.org [http://www.graphicall.org/1111](http://www.graphicall.org/1111)
Comparatively I downloaded this other [build]("http://builder.blender.org/download/blender-2.70-d8c4763-linux-glibc211-x86_64.tar.bz2"), from Builder Blender, the difference is this one did work. All I did was expanded it, and double-click! Didn't even have to checkmark it to be used as a program.

JDL

---

### Post by Kirboosy on 2014-04-10
Do you have the 7zip package installed? Also from what I have read you need to use the 7zip tool from the terminal

```
sudo apt-get install p7zip-full
```

I was able to extract exact file you are working with the following command. (If you aren't familiar with the terminal please look at this guide. [Using the Terminal]("https://help.ubuntu.com/community/UsingTheTerminal"))

```
7z x 11044_cycles-bake_9dfe40c.7z
```

7zip is a strange beast in Ubuntu. As far as I know there aren't any applications for it that have a GUI front end to use.

Hope that helps!
~Caboose

---

