---
title: "New to Ubuntu. How do I install software?"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by cdhauzie on 2010-12-17
Ok, bare with me everyone. I'm new to Ubuntu and I am coming over from the Windows world.
 
I was able to install the Gourmet Recipe application via the software center in Ubuntu but there is some kind of error in it so it won't load after the initial splash screen.
 
I found some posts online that said it's a known problem with 10.10 right out of the box so I should uninstall and then install the version from SourceForge.net. So I got a version from SourceForge.net and downloaded a .deb file. Now what?
 
Also, how do I get Skype onto my machine? I couldn't find it in the software center.
 
Thanks!!!

---

### Post by LSEactuary on 2010-12-17
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
Im new too - its exactly the same question i asked on G2G! lol

---

### Post by beew on 2010-12-17
Don't know about the program you talk about. But if it is true that the repo version is broken you should first uninstall it using Synaptic (find it, mark it for complete removal, to be thorough there is probably a configuration file in your home directory, go to the directory under your user name, on the left panel choose "show hidden files", then find the folder with name like .program_name and delete it, program_name is the name of your program, or if you can't find it there then open the .config folder and you may find a configuration file for said program,  if you do delete it)

To install the .deb file simly right click it and Software Center would offer to install it, click yes and that is it (so it works like Windows' .exe intaller) Alternatively you can install a package called gdebi from Synaptic and it will install .deb files by right clicking, I prefer it to the Software Center.

To get Skype you have to enable the "Canonical Partners" repository in Software Center.

---

