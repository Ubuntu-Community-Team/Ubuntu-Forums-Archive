---
title: "Could not load 9.10 from External hard drive"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by trinaths on 2009-12-13
Hi All,

I installed Ubuntu 9.10 on External hard drive (WD Elements, 500GB), and sure that I selected mbr/grub on to External disk on last step.

**The problem is, after BIOS it was directly going to Windows XP on my  Thinkpad T43. **

I double checked that USB HDD was the primary boot option, and External Hard disk was connected.

Any suggestions please.......

Trinath

---

### Post by lawenlerk on 2009-12-13
> **trinaths said:**
> Hi All,

I installed Ubuntu 9.10 on External hard drive (WD Elements, 500GB), and sure that I selected mbr/grub on to External disk on last step.

**The problem is, after BIOS it was directly going to Windows XP on my  Thinkpad T43. **

I double checked that USB HDD was the primary boot option, and External Hard disk was connected.

Any suggestions please.......

Trinath
Well, i tried installing ubuntu on an external drive before.

The thing is, my desktop couldn't boot it although all the settings pointed to usb hdd. I also tried settings other than usb hdd.

But when i tried it on my dell laptop it booted alright.

I suggest you try it on another computer if possible.

---

### Post by trinaths on 2009-12-14
I tried on two more Laptops and got no luck.

---

### Post by Bartender on 2009-12-14
Is this a USB-powered device?

I have an external dock with its own power supply.  I plug an Ubuntu HDD into it, turn it on, it's already up and spinning before I turn on the PC and it works.

I've often wondered if USB-powered devices are going to spin up in time to be recognized by BIOS.

---

### Post by darkod on 2009-12-14
> **Bartender said:**
> Is this a USB-powered device?

I have an external dock with its own power supply.  I plug an Ubuntu HDD into it, turn it on, it's already up and spinning before I turn on the PC and it works.

I've often wondered if USB-powered devices are going to spin up in time to be recognized by BIOS.

Good point, they should be able to. However, not all laptops can provide enough power on one port for usb hdd. Can that be the issue?

---

### Post by trinaths on 2009-12-15
That was really a good point to consider. I will probably try with a Desktop computer and update you with result.

Thanks,
Trinath

---

### Post by PerryTrenton on 2009-12-28
I had a somewhat similar problem when I installed Xubuntu on an external hard drive.  After a good bit of research and thought I fixed my problem.  See question no. 90386 on the lauchpad:
[https://answers.launchpad.net/ubuntu/+source/hal/+question/90386](https://answers.launchpad.net/ubuntu/+source/hal/+question/90386)

---

### Post by jSalv on 2009-12-28
You should install via Wubi if you havn't done so.
This way, it will always prompt you which one to run (even if it hadn't been recognised by the BIOS). However, it will only occur in your current (installation) computer.

---

### Post by presence1960 on 2009-12-28
> **jSalv said:**
> You should install via Wubi if you havn't done so.
This way, it will always prompt you which one to run (even if it hadn't been recognised by the BIOS). However, it will only occur in your current (installation) computer.

I would stay away from wubi unless you are not sure you like Ubuntu. Wubi is not meant to be a permanent installation, but rather a method to try Ubuntu for those unwilling to partition their hard disk(s) until they are sure they like Ubuntu. Here is a link to an interview with one of the developers of wubi in which he echoes what I just told you: [http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/) Check the first sentence to the answer of the second question posed.

In case you haven't noticed there are quite a few threads now concerning wubi woes.

---

### Post by presence1960 on 2009-12-28
> **trinaths said:**
> Hi All,

I installed Ubuntu 9.10 on External hard drive (WD Elements, 500GB), and sure that I selected mbr/grub on to External disk on last step.

**The problem is, after BIOS it was directly going to Windows XP on my  Thinkpad T43. **

I double checked that USB HDD was the primary boot option, and External Hard disk was connected.

Any suggestions please.......

Trinath

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

