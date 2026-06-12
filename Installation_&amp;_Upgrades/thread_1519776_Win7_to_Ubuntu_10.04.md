---
title: "Win7 to Ubuntu 10.04"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by compelite on 2010-06-28
Hi everyone, I'm interested in installing ubuntu on my windows 7 64 bit machine but I'm curious if it's possible to install it without a dual boot. I just want the ubuntu operating system - but the problem is I have a lot of windows files that I want to keep, is it possible to install ubuntu and keep all these files. I know that in windows when you upgrade it will create a folder called "windows old" - is it possible I can keep my folders from windows when I move to Ubuntu? thanks!

---

### Post by WinRiddance on 2010-06-28
Set your bios to be able to boot from a CD/Rom disk. Use the Ubuntu LiveCD to try Ubuntu without installing it. Then use Gparted to create yourself a data backup partition in NTFS format. If it's just for file data within personal folders than a 10 GB partition is more than likely big enough ... unless you have tons of music files or numerous movies? Now mind you that any **actual windows7 programs will not run on Ubuntu** by default. Be very clear about this!

**Secondly** create another 4 GB partition. This would be a swap file partition. Just trust me on this, even if your computer doesn't need it, it won't hurt to have it, especially in this day and age of "outrageously sized" disk drives. 

Got those two partitions? Great. Go ahead and **exit the CD** and boot back into Windows7. Since you've created an NTFS partition Windows7 will be able to read that just fine. Now copy all of the files/folders that you wanted to keep from Windows7 over to the backup partition.

Done with that? Good, time to reboot and use the LiveCD again, but this time use the option to install Ubuntu. When asked about the installation partition use the option for **manual installation** followed by _selecting your Windows7 partition_ which will effectively wipe out Windows7 while installing Ubuntu instead. Without Windows there won't be a dual-boot option on your machine. Just Ubuntu ...

Later on, if you like, you can always install the free Virtualbox and then install your registered version of Windows7 on top of that. This will provide you the ability to keep your Ubuntu system while looking in on windows7 from time to time without even the need to reboot your machine. **Now how cool is that** ???

---

### Post by wilee-nilee on 2010-06-28
> **compelite said:**
> Hi everyone, I'm interested in installing ubuntu on my windows 7 64 bit machine but I'm curious if it's possible to install it without a dual boot. I just want the ubuntu operating system - but the problem is I have a lot of windows files that I want to keep, is it possible to install ubuntu and keep all these files. I know that in windows when you upgrade it will create a folder called "windows old" - is it possible I can keep my folders from windows when I move to Ubuntu? thanks!

You might just try a wubi install, and if is what you like do a real dual boot. You never know when you might like having both OS with just a reboot. This is the preferred method and the easiest way to go, don't be afraid of the dual boot it is easier to manipulate the MBR.

---

### Post by WinRiddance on 2010-06-28
Hmmmm, based on a lot of information that I've been reading online in the past 6 months the VirtualBox is actually supposed to be the safest way to go since you get the security and stability of Linux Ubuntu, while being able to access Windows as you would normally access Windows ... without having to use Wine which is not as secure as the VirtualBox.

That's what I did recently and the VirtualBox works like a charm. **Just like the full, unbridled installation of Windows**. Furthermore there are quite a few posts which mention potential compatibility issues between Wubi and 10.04 Lucid in a 64 bit environment. If a person asks specifically for a way to avoid the dual boot issue, then the VirtualBox method is really the only proper & safe (other) way to go. Sorry that I have to disagree with you wilee-nilee, but I answered this members question exactly as requested.
Peace!

---

### Post by wilee-nilee on 2010-06-28
You have answered the question without asking any questions. My first question would be is there a fear of the dual boot, and if so a explanation why this is. Really just confirming the user knowledge and toolset of abilities. So that when a solution is given it is understood and used without losing the data wanting to be saved.

---

