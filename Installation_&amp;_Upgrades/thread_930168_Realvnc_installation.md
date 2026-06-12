---
title: "Realvnc installation"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by xtracool_protik on 2008-09-25
Hi guys,
 Here is how I installed realvnc on my ubuntu - well I needed realvnc only because the vnc server in my college is set using it so that if i don't give terminal number then I'm automatically directed to lowest loaded plus
if I give <hostname>:4 that means I want screen resolution number 4 - suitable for widescreen laptop.

 Well vncviewers in ubuntu worked well but i couldn't get proper resolution and i need to give terminal number

 Anyway if u want to install vncviewer - here is the way I did it:

 Download VNC Free Edition for Linux (x86) (gzip) from [http://www.realvnc.com/products/download.html](http://www.realvnc.com/products/download.html)
 After extracting
 $sudo ./vncinstall /usr/local/bin    (to use without <path>)

 then get libstdc++2.10-2.96-0.83mdk.i586.rpm form 
[http://fr.rpmfind.net/linux/rpm2html/search.php?query=libstdc%2B%2B-libc6.2-2.so.3](http://fr.rpmfind.net/linux/rpm2html/search.php?query=libstdc%2B%2B-libc6.2-2.so.3)
and convert it to debian(through alien) I guess we can use compact version also but I haven't tried 
 
 I've the debian version but don't know how to upload or even I'm allowed or no.

 Moderators help me here - if I'm wrong or misguiding, this is my first post to put some solution.

 Thank you

---

