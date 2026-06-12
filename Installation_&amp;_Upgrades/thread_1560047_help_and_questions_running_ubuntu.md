---
title: "help and questions running ubuntu"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by red40y on 2010-08-24
im currently running ubuntu on virtualbox to get around the ATI headache, but the screen size is tiny compared to a regular sized desktop. is there a solution to the ATI problems? i already tried nomodeset and acpi=off for booting from cd, and thought it was going to work, but it didnt and i had to repartition the hd, and redo the mbr. fun huh? 
is there a virtual machine program that looks more like your looking at a desktop and not a tiny screen? or a method to getting ubuntu to run with ATI?

id like to get wubi to work, partitioning is a pain in the ***, lol.

---

### Post by stlsaint on 2010-08-24
You need to install the additional tools from virtual box. See here for [instructions]("http://www.smachado.com/2009/11/installing-virtualbox-additional-tools-on-ubuntu-9-10-karmic-koala/").

---

### Post by red40y on 2010-08-24
i cant seem to get past step1?

this is what im getting

Reading package lists… Done
Building dependency tree
Reading state information… Done
gcc is already the newest version.
E: Couldn’t find package linux-source-virtual

what am i not doing right?

---

### Post by howefield on 2010-08-24
Try some decent/current intructions. You might get further with the Virtualbox manual itself..

[http://www.virtualbox.org/manual/ch04.html#id2658274](http://www.virtualbox.org/manual/ch04.html#id2658274)

---

### Post by gordintoronto on 2010-08-24
"a method to getting ubuntu to run with ATI?"

My laptop has an ATI video card, and Ubuntu works fabulously. What is your problem with ATI? What video card?

---

### Post by red40y on 2010-08-24
i have the  ATI Mobility Radeon HD 4200, its one of the cards that has issues with linux. 

after a couple trys, i got virtualbox to run in a full fulscreen mode. (user error was the culprit for the malfunction) thanks for the help stlsaint, and howefield! =)

---

### Post by gordintoronto on 2010-08-25
> **red40y said:**
> i have the  ATI Mobility Radeon HD 4200, its one of the cards that has issues with linux.

Really? That's what I have in my HP G62, and I have no complaints at all in Lucid.

The hard drive was set up stupidly, and I had one audio issue, but the video has been great -- even driving my HD TV via the HDMI port.

---

### Post by GenBattle on 2010-08-25
> **red40y said:**
> i have the  ATI Mobility Radeon HD 4200, its one of the cards that has issues with linux. 

after a couple trys, i got virtualbox to run in a full fulscreen mode. (user error was the culprit for the malfunction) thanks for the help stlsaint, and howefield! =)

I couldn't boot of the live CD because of my ATi graphics card, but i would recommend you try adding/removing some options from the GRUB boot line before giving up completely: 
[http://ubuntuforums.org/showpost.php?p=9766336&postcount=8](http://ubuntuforums.org/showpost.php?p=9766336&postcount=8)

---

### Post by red40y on 2010-08-26
for now, i cant afford do have my computer down to try and fix the hardware problems. if i cant have it running with wubi i cant have at all. i still need windows for school and media, and im still learning the programing game. =) ill keep reading up on the matter, but unless some one can give me a for sure fix, then im content with running in a virtual machine. 

system specs are: AMD Turion(tm) II Dual-Core Mobile M500 2.2GHz processor--- 4 gig ram--- AMD M880G with ATI Mobility Radeon HD 4200---

---

