---
title: "How-To install Windows next to Ubuntu 14.04 on Fake RAID?"
date: 2014-06-18
forum: Installation &amp; Upgrades
---

### Post by SkOrPn on 2014-06-18
OK, I have finally got Ubuntu working on my Intel FakeRAID.

I created only two partitions, one for Ubuntu and one for Windows. The reason I only created one main EXT4 partition is because no matter what I did other than that the install would fail. If I let Ubuntu create its own partitions = fail, If I created the proper partitions myself, it would still fail, I even followed many guides here, all resulting in fail. Creating only one partition was apparently the trick, and it made it all the way through the installation without failing, without complaining one bit, lol, which was a surprising discovery to say the least. However, upon reboot, the system hung, lol of course so I was forced to use Boot-Repair disk, which was a hassle but it fixed it.

[IMG]http://i.imgur.com/Hnu5BYEl.jpg[/IMG]

Now I have a really fast working Ubuntu install on a Intel BIOS FakeRAID setup (x58 ICH10R). However, I still have a 190gb partition (2nd partition ready for Windows 8.1) that is intended for Windows. 

My question is, since I have done this many times this week all resulting in failure, HOW DO I INSTALL WINDOWS PROPERLY on the same array that Ubuntu is currently using? Or, maybe my question should be, what do I do AFTER installing Windows to recover the broken GRUB? I already tried using Boot-Repair to repair a dual boot, but it constantly spits out incorrect terminal codes to copy/paste, which had led to nearly a dozen failed attempts this week, 4 straight days now... Since boot-repair is always failing, should I try and fix the Bootloader problem in Windows? I already tried EasyBCD, and that thing completely killed my Windows install. I am now at a loss and asking here what to do next please.

Here is one thought I had. Is Boot-Repair spitting out incorrect terminal codes because I was in the live session, or because I need to be on either dmraid or mdadm? At the moment I am on dmraid, with no idea on how to migrate back over to mdadm.

My machine specs if it matters
Asus x58 R3E BIOS only, NO UEFI.
Intel RAID is ICH10R (a.k.a FakeRAID)
Intel Hexa-Core "6C12T" Gulftown XEON
2 x Samsung 840 Pro's (2 x 128GB = 256GB array)

Any help to proceed would be appreciated please. I know how to install Windows to the "other" partition but not sure if things have changed now because of the RAID setup. Thank You!

---

### Post by SkOrPn on 2014-06-18
Ok, this is confirmation of my problem. He also could not get it to work using anything other than a single partition. So I am not the only one... weird

[http://www.overclockers.com/how-to-dual-boot-windows-and-linux-on-a-fake-raid-array/](http://www.overclockers.com/how-to-dual-boot-windows-and-linux-on-a-fake-raid-array/)

---

