---
title: "The grub-pc failed to install"
date: 2016-11-10
forum: Installation &amp; Upgrades
---

### Post by doeonethousand on 2016-11-10
This error message appears toward the end of the Lubuntu 16.10 installation process and it is due to the fact that apt-install doesn't find it, I guess (no such candidate).
Does anyone know what problem causes such disruptive situation? Have the programmers ever tested this product marketed as "lightweight, fast, easier"?

---

### Post by yancek on 2016-11-10
Your post doesn't really contain enough information for anyone to begin trying to help.  I would suggest you go to the site below and download boot-repair and burn it to a CD and run it so that we will have some useful information.  Select the option to Create Bootinfo Summary and do not try to make any repairs.  It should give you a link you can post here so that members can view it and try to help.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some questions which would need to be answered:

Does the computer have any OS currently installed?  If so, what?
How new/old is the computer?
Is it using MBR or UEFI?
Details on hardware, manufacturer, CPU, RAM, etc..?

That and more will be provided with the boot repair software.

> Have the programmers ever tested this product marketed as "lightweight, fast, easier"? 				

Yes, the have.  Lubuntu has been in use by millions of people since October, 2008.

---

### Post by thanais on 2016-12-28
I don't know if it helps but I will post my experience. I was trying to  install lubuntu 16.10 to a laptop with WIndows Vista already installed. I  had the same problem even when I tried with another bootable usb stick.
After trying to install and reaching the point where the message "*grub-pc failed to install...", *I  hit Ctrl-Alt-Del, booted to try Lubuntu without installing, where I  managed to connect to the wifi and run a Boot-Repair which gave this  report after the repairing
[http://paste2.org/Ud5zmmsX](http://paste2.org/Ud5zmmsX)

I tried to reboot and I couldn't even boot to Windows. I got a black **" grub > "** command line that I had no idea what to do with.
So  gave it another shot and installed lubuntu again, having for the first  time the ability to connect to the wifi during installation and it  happened! I now have Windows Vista and Lubuntu installed and working on  my laptop.

Sorry for the long reply, I am no specialist, I have  no clue what was it that fixed the problem, I just hope someone that  understands will be able to help others.

---

### Post by oldfred on 2016-12-28
You always install grub to a drive like sda, not to a partition like sda5.

@thanais
In your case you show a core.img in sda3 the extended partition. Core.img is normally in the sectors just after the mbr where grub is installed when you specify a drive like sda.
So it looks like you initially installed grub to sda3. But may have had an old grub in mbr that then was not configured for new install.

---

### Post by camicov on 2017-04-06
> **thanais said:**
> I don't know if it helps but I will post my experience. I was trying to  install lubuntu 16.10 to a laptop with WIndows Vista already installed. I  had the same problem even when I tried with another bootable usb stick.
After trying to install and reaching the point where the message "*grub-pc failed to install...", *I  hit Ctrl-Alt-Del, booted to try Lubuntu without installing, where I  managed to connect to the wifi and run a Boot-Repair which gave this  report after the repairing
[http://paste2.org/Ud5zmmsX](http://paste2.org/Ud5zmmsX)

I tried to reboot and I couldn't even boot to Windows. I got a black **" grub > "** command line that I had no idea what to do with.
So  gave it another shot and installed lubuntu again, having for the first  time the ability to connect to the wifi during installation and it  happened! I now have Windows Vista and Lubuntu installed and working on  my laptop.

Sorry for the long reply, I am no specialist, I have  no clue what was it that fixed the problem, I just hope someone that  understands will be able to help others.



many many many thanks!!!   "...where I managed to connect to the wifi ..."

that made me think on a solution, i´ve spend (lost) 3 full days working on a solution on this matter without success, i´ve succesfully installed 3 lubuntu computers and wasn´t able to do it on a 4th machine, i´ve tried a every solution i found, supergrub disk, install debian first, anything, then i read your post and voila!, when i installed the other computers i had to do it with a USB wifi adapter, on this one i had ethernet, so i took off the eth cable and tried with the wifi plugged and that´s it, no more grub to deal with!!!!  


I hope that may help someone else....  best regards!!

---

### Post by doeonethousand on 2017-04-07
Good to know there is a solution to this annoyance, but where on lubuntu  site it is said that you gotta have an active wifi connection to be  able to install it?

Secondly, last summer I didn't even know what  to expect from a Linux distro, I never used one until then, not even  seen one in action. So, when I got stuck at  the grub problem, went to this forum to get some help and find out that I have to use diagnostic tools I knew it's time for me to forget about it.

BTW:
> [QUOTE]Have the programmers ever tested this product marketed as "lightweight, fast, easier"
Yes, the have.  Lubuntu has been in use by millions of people since October, 2008.[/QUOTE]
Really?

---

### Post by zaphod.b2 on 2017-07-09
> **camicov said:**
> ...where I managed to connect to the wifi ...

I can confirm this is still an issue. I experienced the grub-pc problem today installing the Lubuntu 16.04 LTS on a 5 or 6 year old Sony VAIO VGN-N21S.

Connecting to a Wifi-Network at the beginning of the installation resolved the issue for me.

---

