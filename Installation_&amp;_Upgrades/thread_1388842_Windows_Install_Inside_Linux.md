---
title: "Windows Install Inside Linux"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by coreys.pc.repair on 2010-01-23
Hello,

Here is my problem everyone.  Last night by accident, I deleted a Windows Partition I shouldn't have.  When I did that, I couldn't get Windows to load.  So I booted up through a Ubuntu Live CD.  When I did that, I backed up the files I needed (I was able to see my windows partitions) and I copied an ISO of Windows I had onto a USB Thumb Drive.  Now I need to make the Thumb Drive bootable where I can reload windows and do a dual boot.  Anybody know how to go about doing this inside Ubuntu?  I've been googling it for hours and have not come up with anything that will help.  

I've tried using the Virtualbox method but that didn't work.  Everytime I tried loading my Virtual Machine, I would get an error message.

Now, I'm a N00B at Ubuntu, so yall going to have to talk to me like such. 

Any help is appreciated. 

Thank You,
Corey

---

### Post by Leppie on 2010-01-23
you may be better off trying to recover the deleted windows partition first.
try testdisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by coreys.pc.repair on 2010-01-23
that didn't work, but thanks for trying

---

### Post by Leppie on 2010-01-23
> **coreys.pc.repair said:**
> that didn't work, but thanks for trying
have you tried other tools to recover the windows partition?
there's images like [Ultimate Boot CD]("http://www.ultimatebootcd.com/"), Hiren's Boot CD.

did you actually do anything else with the partition apart from deleting it (like formatting, etc)?

---

### Post by coreys.pc.repair on 2010-01-23
> **Leppie said:**
> have you tried other tools to recover the windows partition?
there's images like [Ultimate Boot CD]("http://www.ultimatebootcd.com/"), Hiren's Boot CD.

did you actually do anything else with the partition apart from deleting it (like formatting, etc)?


yes, just to get a working operating system on here, i backed up my data and reformatted and did an Ubuntu Install.

I've been searching for a way to make the USB Thumb Drive bootable inside Ubuntu, to run the ISO file of Windows 7 setup.

---

### Post by rogue_0111 on 2010-01-23
This may assist:

[http://philliptweedie.wordpress.com/2009/05/13/getting-windows-7-rc-on-a-usb-stick-from-ubuntu/](http://philliptweedie.wordpress.com/2009/05/13/getting-windows-7-rc-on-a-usb-stick-from-ubuntu/)

---

### Post by mrwilky on 2010-01-23
Here's a thought, Make an .iso on a cd of your windows 7 then erase your flash drive clean
re-install virtual box install your win7 cd .iso thru virtual box onto the flash drive or hard drive. VB makes its own .img file that should work for you.

---

### Post by Leppie on 2010-01-23
here's another tut: [http://geniushackers.com/blog/2009/06/26/how-to-installing-windows-xp-and-ubuntu-through-pendrive/](http://geniushackers.com/blog/2009/06/26/how-to-installing-windows-xp-and-ubuntu-through-pendrive/)

---

### Post by Yvan300 on 2010-01-23
Download wintoflash and just head over by a friend who has windows and make your flash drive bootable. That would be the least time consuming option.

---

### Post by coreys.pc.repair on 2010-01-23
Thanks everybody for your help, I got it.  I used this tutorial:  [http://philliptweedie.wordpress.com/2009/05/13/getting-windows-7-rc-on-a-usb-stick-from-ubuntu/#comment-152](http://philliptweedie.wordpress.com/2009/05/13/getting-windows-7-rc-on-a-usb-stick-from-ubuntu/#comment-152)

---

### Post by rogue_0111 on 2010-01-23
--

may the source be with u.


--

---

