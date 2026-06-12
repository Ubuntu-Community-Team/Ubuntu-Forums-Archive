---
title: "Always asking for configuring Flash when installing"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by fmunkey on 2007-03-02
I tried to install flash player using ```
sudo apt-get install -y flashplugin-nonfree
``` I got that from [here]("http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html")  
So that didnt work, so i just installed it from the adobe website, but now when I try to install something for example, wine ([http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)) i get

```
anthony@anthony-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~edgy1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I at one point got ```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

``` So i ran that and nothing was fixed, I got the same error.  If anyone could help me, that would be great.  I'm sorry if this is in the wrong place, I'm new here.

Edit: Fixed the problem, i removed flash and got it to work.

---

### Post by D3ATH ROW3 on 2007-03-03
Thanks, I was having the same problem after using the same guide. I also removed flash and was able to get other packages to install.

I'll figure out how to properly install flash later. Any tips?

---

### Post by fmunkey on 2007-03-03
go to adobe's website.  Then go to downloads, and it works from there.

---

