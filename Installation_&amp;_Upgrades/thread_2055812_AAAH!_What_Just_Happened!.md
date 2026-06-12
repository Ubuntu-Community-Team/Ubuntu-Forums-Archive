---
title: "AAAH! What Just Happened!"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by AnUbunter on 2012-09-10
I was installing ubuntu via a usb and it somehow got loose and disconnected and it didnt finish getting installed so now i cant go on to ubuntu which is alright because i can just reinstall it, but then i noticed this made windows all weird (i was going to make it so i can dual boot it) so i had to go into recovery mode... eventually all fixed but the weird thing is, now the USB that I was using to install ubuntu isnt working! Nothing happens on Ubuntu and Windows says its corrupt. I have no problem if i cant fix the USB, my real big problem is that i have lost half of my HDD memory! The unsucessful instalation of Ubuntu stole my HDD space and now i dont know how to get it back! Please help!

---

### Post by jerome1232 on 2012-09-10
> **AnUbunter said:**
> I was installing ubuntu via a usb and it somehow got loose and disconnected and it didnt finish getting installed so now i cant go on to ubuntu which is alright because i can just reinstall it, but then i noticed this made windows all weird (i was going to make it so i can dual boot it) so i had to go into recovery mode... eventually all fixed but the weird thing is, now the USB that I was using to install ubuntu isnt working! Nothing happens on Ubuntu and Windows says its corrupt. I have no problem if i cant fix the USB, my real big problem is that i have lost half of my HDD memory! The unsucessful instalation of Ubuntu stole my HDD space and now i dont know how to get it back! Please help!
 

Ubuntu resized your partitions during the installation process, half for windows, half for Ubuntu. Having less space for Windows would be an expected outcome, also Windows doesn't understand how to read linux filesystems and may report them as "corrupted", they might actually be corrupted due to the interrupted install. I would reinstall Ubuntu but this time use the "do something else" option and manually select the partitions, so that it doesn't try to resize the Windows partition again. Keeping everything very far away from the usb stick so that it doesn't wiggle out this time!

You will need a small swap partition and a large ext4 partition mounted as / to complete the install.

---

### Post by AnUbunter on 2012-09-10
> **jerome1232 said:**
> Ubuntu resized your partitions during the installation process, half for windows, half for Ubuntu. Having less space for Windows would be an expected outcome, also Windows doesn't understand how to read linux filesystems and may report them as "corrupted", they might actually be corrupted due to the interrupted install. I would reinstall Ubuntu but this time use the "do something else" option and manually select the partitions, so that it doesn't try to resize the Windows partition again. Keeping everything very far away from the usb stick so that it doesn't wiggle out this time!

You will need a small swap partition and a large ext4 partition mounted as / to complete the install.
Hi thanks, i already reinstalled ubuntu and dont want to do it again so ill just let it be until i need more memory :P
Thanks for the info though

---

### Post by jerome1232 on 2012-09-10
I think I missread your post. The usb device you should be able to simply reformat it from Windows or Ubuntu. In Ubuntu use gparted to format it.

---

### Post by OhThatSysOp on 2012-09-10
> **AnUbunter said:**
> I was installing ubuntu via a usb and it somehow got loose and disconnected and it didnt finish getting installed so now i cant go on to ubuntu which is alright because i can just reinstall it, but then i noticed this made windows all weird (i was going to make it so i can dual boot it) so i had to go into recovery mode... eventually all fixed but the weird thing is, now the USB that I was using to install ubuntu isnt working! Nothing happens on Ubuntu and Windows says its corrupt. I have no problem if i cant fix the USB, my real big problem is that i have lost half of my HDD memory! The unsucessful instalation of Ubuntu stole my HDD space and now i dont know how to get it back! Please help!

Wow.:shock: Don't worry. Can you back up windows so you can get it later?
what version of windows do you have?
Internal HDD size?
What happerns when you run fsck?

---

