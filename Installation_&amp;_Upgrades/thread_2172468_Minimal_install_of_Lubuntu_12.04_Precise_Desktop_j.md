---
title: "Minimal install of Lubuntu 12.04 Precise Desktop jam for unknown reason"
date: 2013-09-05
forum: Installation &amp; Upgrades
---

### Post by Barbe_Rouge on 2013-09-05
Hello,

I am trying to get my old laptop up and running again. Windows XP is actually installed on it and I would like to try Lubuntu to see first if the laptop is more responsive and second to dicover Lubuntu.

What I tried:
- Tried to install the latest Lubuntu but didn't work because of non-PAE kernel
- Tried the 12.04 graphical and alternate versions but didn't work because of non-PAE kernel
- Now trying to install 12.04 minimal install version

I made a bootable USB and modified BIOS boot properties.
Installation starts normally. I choose Command Line Install as advised [HERE]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")
Got as far as choosing the archive mirror for downloading but then after validating mirror nothing happens.
It seems to access internet for a while and then neither the modem nor the USB key seem to be active.
Purple screen with a line at the bottom where i can type something but nothing seems to help.

Does it sound familiar to anybody? Can anybody help?

Thanks!

---

### Post by TheFu on 2013-09-05
Can you plug in the ethernet port to a switch or router that is already connected to the internet?

---

### Post by Barbe_Rouge on 2013-09-05
> **TheFu said:**
> Can you plug in the ethernet port to a switch or router that is already connected to the internet?

It is already plugged through ethernet to the modem. I think I has access to the internet because it finds the mirrors in different countries

---

### Post by TheFu on 2013-09-05
Where exactly is the "modem" located? Inside the PC or in a different device?  
Could you be confusing "modem" with "network card"?

---

### Post by Barbe_Rouge on 2013-09-05
What I meant is I am plugged through the ethernet port of the laptop to the router itself connected to internet. There is also WiFi built-in the router. 
As I understood it's better for the installation to be plugged rather than wireless.

---

### Post by TheFu on 2013-09-05
> **Barbe_Rouge said:**
> What I meant is I am plugged through the ethernet port of the laptop to the router itself connected to internet. There is also WiFi built-in the router. 
As I understood it's better for the installation to be plugged rather than wireless.

Yep, I was just confused, mentioning a "modem" in your first post had me thinking about a setup very common in India - wifi-only configs for ISP connections. You are doing it correctly - wired.

I've seen where regular installs that are on a network, but not on the internet take hours, lots of timeouts - over and over and over and over. Discovered that removing the network connection was best to avoid timeouts, then post-install, I'd connect up to the internet, run patches, and everything was fine.  Don't know if the minimal install ISO will allow that or not.  Just a thought.

Clearly installing a non-PAE kernel and LXDE DE so things work with i386 and greater hardware?
Just how minimal is this hardware?  RAM, Disk, CPU?  

On really limited RAM systems ... could something like [TinyCore]("http://distro.ibiblio.org/tinycorelinux/welcome.html")  be a better choice?

---

### Post by Barbe_Rouge on 2013-09-06
Yes! It got it working. The hardware specs is not so bad but the laptop didn't age so well. One of the problem I was having during installation was that it rebooted after a while, most probably because of the heat.
I lifted it from where it was to let air circulate better and the installation completed fine though it took a lot of time.
It thought many time I froze but something was going on.
Now Lubuntu is installed, XP forgotten and I get to start in the world of Linux which is unknown to me.

Thanks for the help!

---

### Post by TheFu on 2013-09-06
> **Barbe_Rouge said:**
> Yes! It got it working. The hardware specs is not so bad but the laptop didn't age so well. One of the problem I was having during installation was that it rebooted after a while, most probably because of the heat.
I lifted it from where it was to let air circulate better and the installation completed fine though it took a lot of time.
It thought many time I froze but something was going on.
Now Lubuntu is installed, XP forgotten and I get to start in the world of Linux which is unknown to me.

Thanks for the help!

Was the overheating the only issue?  Was there anything else you did to make it install?  Others will want to know.
Also, if you could please mark this thread as solved, that would help too.

---

### Post by sudodus on 2013-09-07
Now that you have Lubuntu running, you can get brave and try [Lubuntu-fake-PAE]("https://help.ubuntu.com/community/Lubuntu-fake-PAE") or the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") to be able to install the newest released Lubuntu, 13.04, or even the not yet released 13.10. There is an image for Saucy Beta 1, that works well with my IBM Thinkpad T42 with Pentium M 1.7 GH without the PAE flag but with full PAE capability.

---

