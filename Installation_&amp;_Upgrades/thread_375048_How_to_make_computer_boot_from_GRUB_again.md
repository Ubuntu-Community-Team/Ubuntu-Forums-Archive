---
title: "How to make computer boot from GRUB again"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by rafaelperrone on 2007-03-03
I had Ubuntu 6.10 installed on one partition booting from GRUB. THen I installed WinXP in another partition on the same SATA drive and now my computer doesnt boot from GRUB anymore and it just boot into Windows instead. 

How do I make it boot from GRUB again giving me the option of Ubuntu and Windows? Do I have to reinstall GRUB (hope not). If answer is yes, how do I do it?

Thanks

---

### Post by Gerard Barberi on 2007-03-03
Yes, unfortunately you will have to reinstall grub.

Check [this post ]("http://ubuntuforums.org/archive/index.php/t-24113.html")for how to do this.

---

### Post by rsambuca on 2007-03-03
You will have to re-install Grub to the MBR (Main Boot Record) of your drive since XP will have overwritten it.  Don't worry, it is actually really easy to reinstall if you have the liveCD.

Boot up from the live CD, and from a terminal (Accessories -> Terminal), enter these commands:```
sudo grub
```
You will then see a grub> prompt.  Enter ```
find /boot/grub/stage1
```
It will then give you a location for your grub stage 1 instructions eg. (sd0,1)
Then enter (you will have to replace the (0,1) with the numbers that you get back from the "find" command```
root (sd0,1)
```
Then to write the instructions to the MBR```
setup (hd0)
```  You might need setup (sd0), depending on your settings, but one of them will work.

then type quit to exit grub, and reboot.  should work.  If it doesn't, you can boot from the live CD and get more help, but this should work.

---

### Post by rafaelperrone on 2007-03-03
Thanks for the answers.
I got a problem, though. After installing windows, the ubuntu cant boot anymore. I select the option Start or install ubuntu and after a long time i just get a black screen. I can boot with a knoppix live CD though. Will it work too? Or must I use the Ubuntu CD?

---

### Post by Gerard Barberi on 2007-03-03
[This ]("http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html")has the info for a knoppix CD.

---

