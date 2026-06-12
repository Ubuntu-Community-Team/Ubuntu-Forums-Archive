---
title: "Does not appear to be installed"
date: 2015-11-23
forum: Installation &amp; Upgrades
---

### Post by dan205 on 2015-11-23
Hi y'all

I downloaded the latest Ubuntu version on a USB stick. Then I used the Windows 7 Starter disc manager to shrink an existing partition. I then proceeded to install Ubuntu. It seemed to be going fine. After the 'apparent' installation, it restarted but it went straight into Windows. There was no boot option presented. 

I tried another install. Same outcome. 

How can I check if Ubuntu was actually installed? How do I fix this problem?

Thanks for all help.

---

### Post by Bucky Ball on 2015-11-23
Welcome. How are you installing it? Is Windows installed in UEFI? Is Ubuntu being installed in UEFI? Have you tried running [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")? If not, perhaps you could post the link it provides to your bootinfo and we can have a look. 

If you've installed with no errors and it boots into Windows, don't waste time with another install. That is doubtful the issue. It would be a problem with the boot manager. The more installs you do, the more chance there is of screwing something up and wiping Windows, or worse, valuable data. :)

Run boot repair and let's have a look at that output before reinstalling again.

---

### Post by dan205 on 2015-11-23
I checked if my laptop runs UEFI. No.

Boot repair next?

---

### Post by Bucky Ball on 2015-11-23
Yep. Give it the recommended repair or use the option to install grub to sda. Make a note of the link it gives you at the end and if you're still having issues post it here.

---

### Post by dan205 on 2015-11-23
It worked! Thanks, Bucky! :D

---

### Post by Bucky Ball on 2015-11-23
Excellent news! Which worked? The recommended repair or installing grub to sda method? 

Please mark the thread solved to help others (first link in my signature). :)

---

