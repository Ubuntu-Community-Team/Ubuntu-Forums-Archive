---
title: "Grub error 17 on sole Ubuntu partition"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by Anstrell on 2008-03-21
I left my laptop on over the night but forgot to connect the power cord so when I wake up it is powered off. Upon startup it stops when grub is initialized saying grub error 17.

I have a zepto 3215 laptop with one samsung 160 GB hdd, one major partition and only Ubuntu installed.

I've been googling for solutions and all my attempts to mount the harddrive through the live cd have failed. I was planning to copy what I needed to an external drive and then reinstall. I still see that as an alternative if we can't fix the grub problem. I've also tried to change user both to root and to my ordinary user but without success.

As I'm sure you've noticed I'm still a noob so please be thorough in your explanations.

---

### Post by Pumalite on 2008-03-21
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by Anstrell on 2008-03-21
Thanks for helping.


"When trying to boot Linux (even if you only have one hard disk)
If you get GRUB error 17 , check your **/boot/grub/menu.lst** file and make sure to check your operating system entry's 'root (hdx,y)' details are correct."
I don't have a grub folder in my boot folder.

---

### Post by Pumalite on 2008-03-21
Bad installation. Let's start from scratch. DBan your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Get Gparted Live CD: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
Burn to disk and boot from it. Delete anything left in your hard drive. Make a new large parition of your whole hard drive and format ext3. Now install Ubuntu.
If you are dual booting; that's another story. Let me know.

---

### Post by Anstrell on 2008-03-21
The problem is that I have some stuff on the harddrive that I'd like to copy first. Is that doable?

It sounds like it would work though, but is it really necessary to wipe the hdd with DBAN, wouldn't just formatting it do the trick?

---

### Post by Pumalite on 2008-03-21
You can save your data if you can boot a Live CD: Ubuntu or Knoppix: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Your explanation of the problem led me to believe that you had a hard drive complicated by 'hidden' partitions' and/or debris from other OS's, especially Windows. That's why DBan.

---

### Post by Anstrell on 2008-03-21
That's great! The only problem is that I don't know how to copy it. I can't find the harddrive at all. I've tried mounting it as best I could. Could you help me out? I'm on the live cd right now on this computer.

---

### Post by Pumalite on 2008-03-21
Check your BIOS and see if it's recognized there.

---

### Post by Anstrell on 2008-03-21
It shows up in the boot order if that's what you mean.

---

### Post by Pumalite on 2008-03-21
Get TestDisk and run some test on your drive: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Anstrell on 2008-03-21
I managed to download it but it won't execute when I try to open the testdisk_static file.

---

### Post by Pumalite on 2008-03-21
Start checking your hardware. OTOH, your drive might have gone south. I'd check cables connections, batteries, etc anyway.

---

### Post by Anstrell on 2008-03-21
I don't think so since I had the same problem before the computer crashed. Can you make anything new of this?

---

### Post by Pumalite on 2008-03-21
To me; there is no file system in sda1 according to Gparted and to your experience trying to boot.

---

### Post by Anstrell on 2008-03-21
So it's impossible to get the data?

---

### Post by Pumalite on 2008-03-21
If you take it to a Hard Drive Recovery Shop; I'm sure they can, but is VERY expensive.

---

### Post by Anstrell on 2008-03-21
I have a friend who did that and it was very expensive indeed. Thanks for trying to help out.

---

### Post by Pumalite on 2008-03-21
You are welcome. Good luck.

---

