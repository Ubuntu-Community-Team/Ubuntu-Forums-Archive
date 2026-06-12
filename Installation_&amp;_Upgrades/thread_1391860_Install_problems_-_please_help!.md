---
title: "Install problems - please help!"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by Poloperson57 on 2010-01-27
I'm really sorry if this has been answered elsewhere, but I have spent 4 days and 3 long nights researching and experimenting but I am still not there and I need help.
 
My requirement is to install Ubuntu SERVER 8.04.3 LTS on a Dell 2550 machine.
 
Problem.
- Bug in ubuntu (desktop and server) stopping CD install on this hardware platform. It hangs half way through and is something to do with the SCSI CD drive. Lots of stuff on the net about it, but no fix as far as I can see, at least nothing that works for me.
 
- So, tried boot off CD and then used F6 and added a cdrom-detect/try-usb=true line together with putting a USB with the ISO burnt onto it in the USB port. Still hangs during install (can't see USB perhaps? USB not correctly burnt? Tried many many times though, and eventually gave up at 2am)
 
- Next tried PXE boot. Aha. Now getting somewhere. Ok I installed tftpd32 on my windows machine, and copied the netboot files from the ubuntu site to the tftpd directory. (I dont think this will help me install the server, just the desktop??) Anyway, it booted from the win tftp machine (wahey!), and went through install, BUT when it tried to find the mirror site it couldnt. In fact it couldnt find ANY mirror site. (Internet access from windows and all other PCs on the network is working fine).
 
Groan. So, to ensure I am installing the SERVER version, and to use PXE boot, and to NOT use the internet to download the files (i.e. load them up locally somewhere), 
what do I do?
 
Help. I'm losing the will to live. I'm also very much a newbie. My first contact with linux was last week.
 
Thanks.
 
Bleary-eyed.

---

### Post by Poloperson57 on 2010-01-27
....oh, and if this isnt the right place to ask such a question, could someone re-direct me?
 
Ta.

---

### Post by darkod on 2010-01-27
It is but there seem to be no server experts around. I have never installed server version and could mislead you. And if this problem is documented with Dell 2550 I have no experience with that machine. Usually the install would be problem free.
I know it looks long when waiting but be a little patient and hopefully someone will jump in. Sorry about your problems.

---

### Post by Poloperson57 on 2010-01-28
Thanks Darkrod....I shall be patient :D
 
It is very quiet though....do you think I've stumped everyone with this question ?!
 
I did try to follow the instructions here
 
[http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)
 
and it all looked as though it was going to work, but as I said, it couldn't find any mirror sites when it got to that stage, so I dont know what was happening there.
 
Anyway, hopefully a server guru will pop up soon and help out. 
 
Cheers.

---

