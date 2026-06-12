---
title: "Trying to install 6.10"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by LilRayRay on 2007-01-06
Hi all, I am trying to install Edgy, but am having little luck.  When running the live CD (normal and safe-graphics), xserver returns the error "No Screens Found".  I Then installed it under text mode (alternate cd) only to receive the same "No screens found" error.  In safe mode in the new installation, I tryed to manually configure xserver with "sudo dpkg-reconfigure xserver-xorg".  After this long process, I rebooted, and after the ubuntu logo and loading bar finished, I was welcomed with a black screen.  I rebooted into failsafe and typed "startx".  The screen turned black and then spat me back to the command line with the error "No screens found".  Does anyone have any idea on how I might get xserver to run?  I would continue with dapper (runs fine), but I have not had any luck getting my video card to run under dapper.

any help is much appreciated

system specs:
Dell XPS 400
2 gb 667 mhz ram
2x2.8ghz PD
Nvidia GeForce 8800 GTS

---

### Post by Striker9 on 2007-01-06
I'm having the same problem on pretty much the same computer, but with an x300. Any help would be appreciated.

---

### Post by coltrane on 2007-01-07
I have the same problem with an ASUS A8N-SLI motherboard with 2x6600 gt's. But after lots of experiments and head scratching, I don't think it's a problem with the xorg server.
I can boot into recovery mode and xorg works just fine, but I'm always as root.
I installed a command line system from the alternate CD and it works fine (without GUI), but when I install ubuntu-desktop all hell breaks loose. By the end of the installation I have a screen full of error messages with long hexadecimal numbers IRQ's and strings and then it freezes, my system then becomes unbootable.

I am wondering if it's something to do with the D-bus program as it never seems to be functioning and only does when you reinstall from apt-get but then disappears again on reboot.:confused: :confused: 
 
I've tried everything I can think of but I just cannot get a fully functioning 64 bit ubuntu or for that matter a 32bit one on a 64bit PC, looking at other threads nor can a lot of people.](*,) 
This also happens with dapper!

The only 64bit distribution I could get to work was Gentoo, but you need a lifespan of about 500 years as every new piece of software has to be compiled, not practical for me.:( 

I also tried Suse 10.2, Fedora core 6 these can't seem to work either.

Funny but Knoppix works wonderfully well, wish there was a 64bit version of this.

---

### Post by phubai on 2007-01-07
> **coltrane said:**
> 

Funny but Knoppix works wonderfully well, wish there was a 64bit version of this.


Have you tried Sabayon?

[http://www.sabayonlinux.org/index.php?option=com_content&task=view&id=16&Itemid=27]("http://www.sabayonlinux.org/index.php?option=com_content&task=view&id=16&Itemid=27")

If you haven't it may be worth a (large) download of the liveDVD. Mini x86-64 (CD) is out, altho I don't think it's the latest which is 3.25 (soon to be 3.26). I like the distro cuz' it's Gentoo based without all of the work (time).

---

### Post by coltrane on 2007-01-07
> **phubai said:**
> Have you tried Sabayon?

[http://www.sabayonlinux.org/index.php?option=com_content&task=view&id=16&Itemid=27]("http://www.sabayonlinux.org/index.php?option=com_content&task=view&id=16&Itemid=27")

If you haven't it may be worth a (large) download of the liveDVD. Mini x86-64 (CD) is out, altho I don't think it's the latest which is 3.25 (soon to be 3.26). I like the distro cuz' it's Gentoo based without all of the work (time).

Thanks i'll have a look at this.:)

---

### Post by LilRayRay on 2007-01-07
Dapper worked just great for me, and I would still use it if I could get my video card to work (8800).  Is it possible to replace the edgy xorg.conf with the dapper xorg.conf?

---

### Post by clownius on 2007-01-07
Short answer yes i did a partial upgrade to edgy to get my onboard Intel video card to work.
Long answer it makes a real mess of your dependencies which led to me finishing the upgrade when i kept breaking packages.
I really do not recomend this.  Either go for one or the other

---

### Post by gandalf027 on 2007-01-07
> **LilRayRay said:**
> Dapper worked just great for me, and I would still use it if I could get my video card to work (8800).  Is it possible to replace the edgy xorg.conf with the dapper xorg.conf?


When you say worked great for you (i have a 8800gtx) does this means it works with nvidia driver?

Thanks

---

### Post by LilRayRay on 2007-01-07
no, it means I could boot into the live cd and install it (1024X768 resolution).  I am going to try to install the drivers in a bit (need to find the kernel sources).  

Anyway, I tryed SUSE 10.2, feisty fawn (live cd), and Fedora 6 (live cd).  Suse and Fedora both booted nicely, but neither of them supported much of my hardware as ubuntu does.  Feisty fawn booted identical to that of edgy in that it gave me the error "no screens found".

Should I send in a bug report?

---

### Post by gandalf027 on 2007-01-07
I think you should .. why not?

I am currently working on kubuntu with the vesa driver on my 8800. For now it's the only way.
I tried also to install the nvidia driver and got an error thar the kernel sources couldn't be found. You can check in another thread i posted with a few photos.

---

### Post by LilRayRay on 2007-01-07
can you apt-get the kernel sources?  If not, where do you get them?

---

### Post by coltrane on 2007-01-08
I tried Sabayon but it also does not work.
I think many Distributions still don't support the Nforce 4 chipset.

these certainly don't as far as I can tell

Kanotix 64, Suse 10.2 (64), Fedora Core 6 (64), Ubuntu 6.10 (64&32), & Ubuntu 6.06 (64).

cannot install any of the above, all seem to use Nforce 2 drivers which don't work.](*,) 

Has anyone got a 64 bit distibution to work on a ASUS A8N-SLI board?:confused: 

I can only get Gentoo to work, but I don't like this distribution at all.

---

