---
title: "RAID 5 install"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by genericlifeform on 2007-03-23
Hi,

I'm trying to install onto a RAID 5 creating using my chipset's (ICH8) onboard raid controller.  When trying to install to disk, it seems my hard drives as separate entities  in stead of as part of an array.  I've tried installing dmraid but it still doesn't see my hard drives.

Thanks.

---

### Post by notiones on 2007-03-26
I am going to assume there isn't a logical drive set up. Though if you are running RAID 5, that would imply otherwise. Make sure your drives are online and that you have your logical drive set. You may still see the drives individually, but you will also see your logical drive which is where you want to partition and install.

---

### Post by genericlifeform on 2007-04-19
I decided to try to wait to 7.04 but still no success.  I've read that I need to use something called a fakeraid and/or dmraid but it looks like that RAID 5 is unsupported.

So far as I can tell there is no logical volume -- at least one that Ubuntu can find.  Even after installing dmraid while using the live cd I still only see the separate drives.  Any help appreciated!

---

### Post by notiones on 2007-04-19
I am sorry, but I cannot help unless you are more specific about what you are trying to do. What type of hardware do you have? What would you like the end result to be? Are you looking at hardware or software RAID? Have you read up on either or are you trying to learn experientially? If you lay all of this out before you start it will be much easier and straight forward and easier for someone to assist. In fact you would probably have all kinds of people helping.

---

### Post by genericlifeform on 2007-04-20
Sorry about being unclear.  Here's some more info.

Hardware: MSI P965 Motherboard using an Intel ICH8 chipset for some kind of hybrid RAID (or "fakeraid") which apparently makes use of the main processor and RAM to do many of the RAID functions (such as running the XOR engine) that a stand alone RAID controller does on-board.  So, it is both a a hardware (RAID functionality is built into BIOS) and software (drivers must be installed in OS) RAID.

I wish to use the onboard RAID functionality and not the built in linux software raid implementation (I believe it is called mdadm) because I need to be able to boot to Windows as well.

I have read quite a bit on this issue but everything I find is either above my understanding, contradictory, or out dated.  I'm currently under the opinion from an article I read (sorry, I do not have a link and can't find it right now) is that the intel chipset is supported (many sources say it is completely unsupported) but that the RAID 5 configuration is not available, thought they hope to implement it.

What I am trying to do is install Ubuntu 7.04 onto a RAID 5 which is already running Windows XP.  I am an Linux user of about 6 years, but have always used Fedora and this is my first dip into Ubuntu.

The problem I am running into is that the Ubuntu installer only sees my hard drives individually and does not see the array that they are in and so I can therefor not install.

If you have any other questions, please let me know and thanks for your help.

---

### Post by ovizii on 2007-12-16
I have a asus p5b wifi deluxe with the same problem...
it seems I should really get a hardware raid controler or just use the disks a JBODs

---

