---
title: "help installing ubuntu on thinkpad 380z"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by u4m on 2008-02-08
pleeeze! help can anyone help me install ubuntu 7.10 on a thinkpad 380z, I am doing it for a friend and trying to help him switch to ubuntu. I'm getting a blank screen after the splash screen with blinking light which i believe indicates it's writing to the disk. Yet it takes hours with no result to my impatience. is there a boot parameter to type first >>>>???? Thank you for any help you my have

---

### Post by Mze on 2008-02-08
Are these the [same specs]("http://www.thinkwiki.org/wiki/Category:380Z") on the machine?

You might have to try a leaner distro for the machine, especially if the memory on board is less than 256 Ram, hard drive space less than 4 gig, etc.

Are you using the Live CD or alternate CD?

---

### Post by MDMS on 2008-04-08
I've installed Xubuntu on an IBM 380Z.  Here are the details:
--> I recommend _only_ to use Xubuntu (the other distributions are just way to big!)
--> You _must_ use the Alternate install CD.  I could never get the LIVE CD to work.  This machine only as a 4GB hard disk and about 168MB RAM (I think).
--> PROBLEMS encountered:  No Sound, its on the EISA bus and so Xubuntu doesn't find the sound chip automatically.  I haven't solved this yet but there are lots of threads about it in the forums.
--> BIGGER PROBLEMS encountered:  This laptop does not have a built in Ethernet interface and will not recognize a USB to Ethernet adapter that is attached during installation (although Xubuntu does see the Ethernet adapter and binds the correct driver for the ASIX chipset).  I have not been able to get any kiind of Ethernet connectivity working:  not static or dynamic IP, not by automatic or manual configuration, not by installing extra software like WICD.

---

### Post by MDMS on 2008-04-08
I forgot to mention that during the initial installation, Xubuntu binds the IBM 380Z infrared port to the Ethernet interface 'irda0'  (With my previous MS Windows ME OS installed, the infrared port was only ever configured as a serial device....  Again, I haven't figured out how to get my Ethernet adapter to work despite a lot of attempts by others in the forums to help me.)

---

