---
title: "CD-ROM not detected in xubuntu 7.10"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by cupantae on 2008-03-23
OK, I know this sounds very similar to other posts, but none of them have quite the same problem as me.
I'm trying to install xubuntu 7.10 on a PIII 128MB machine because I am told my Edimax EW-7128g PCI wifi card will be recognised and work "out of the box". However, when I use the (alternate install) CD, the CD-ROM isn't detected. When I first press "enter" on "install" (in the main menu), it gives me "I/O error"s and "end_request"s and it's the same when I put dmesg into a terminal.
Putting
```
dmesg | grep CD
```
or
```
dmesg | grep -i cd-rom
```
or anything else like that yields no results.:confused:
For some reason, xubuntu 7.04 alternate install has no such trouble detecting the cdrom, but getting the wireless card working requires that I compile the driver from source, and I am sorry, but doing that without already having a network connection seems to be simply too difficult for me!
I have also installed Debian Etch and DSL with only network-related problems.

Help, anyone? Possible solutions are:
Getting the wireless to work on any distro
Getting 7.10 to detect the cdrom
Telling me of another distro where the PCI card will work "out of the box"

Thanks in advance!
Mark

---

### Post by lcason on 2008-03-23
Mark,

I'm a fellow "configuration hostage" at the moment, and after posting my problem, thought I'd see if there was someone I might help here.   Looks like results vary on your make of Wifi card. Since I'm a newbie to this site, it appears that posting rules don't allow me to post HTML code, but if you Google this string, the top result should point you to a LinuxQuestions forum on your hardware:  **Edimax EW-7128g PCI "linux hcl"**  where you'll find that two people found it easy to make work, and two people had to struggle to  made it.

Since you are willing to pick a different distro to get your wireless NIC to work, it seems that WiFi is very high on your requirements list. If you can afford it, wouldn't it be easier to get a new NIC that is known to work well with the distro you like, rather than switch distros?  

If you have to make it work with the NIC you have, and if you don't get help on Ubuntu, you might check out [www.mepis.org](www.mepis.org) MEPIS, like Ubuntu, is also based on Debian, and seems to cater more to home rather than business hardware.  Their website (sorry, can't post the link) says "Cards with ralink 2500 chipsets are normally recognized on the interface ra0 or rausb0 using the native driver that comes with MEPIS 6.5"

Good luck!

Lee

---

### Post by lcason on 2008-03-23
Mark,

Looks like maybe I was trying too hard on the URL post previously as I see that the mephis domain reference got hyperlinked automagically. So, let's see what happens if I post the Linux Questions deeplink as raw text rather than "insert hyperlink":

[http://www.linuxquestions.org/hcl/showproduct.php/product/2361/cat/136](http://www.linuxquestions.org/hcl/showproduct.php/product/2361/cat/136)  

Lee

---

### Post by cupantae on 2008-03-24
Thanks for the reply, Lee, but I did manage to compile the driver in xubuntu 7.04 in the end, so I'm just going to leave it.
I really liked Debian, but they didn't provide the tools to compile source from a fresh install, which seems strange to me. It seemed a bit nippier on my dated hardware, but compatibility is more important to me.
I don't know why 7.10 wouldn't work, but now I think it was most likely a faulty CD-R or something as simple as that. In any case, I'm quite happy with my current setup.

Regards,
Mark

---

