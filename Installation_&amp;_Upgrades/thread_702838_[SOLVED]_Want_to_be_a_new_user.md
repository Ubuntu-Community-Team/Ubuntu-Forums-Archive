---
title: "[SOLVED] Want to be a new user"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by SpaceCowboy41706 on 2008-02-20
I am currently using windows xp pro sp2 and i am downloading Ubuntu 7.10 from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) 

I have a couple questions about Ubuntu before i start installing, that i was hoping someone could answer, as i cant seem to find reliable answers anywhere else.

Question 1
I only have 1 hard drive that already has windows xp pro installed on it with only the one partition that windows creates on install. I have found a guide that says i can still install Ubuntu on to the same drive and same partition without messing up my XP. Is this true? Here is the guide i found: [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

Question 2
I have a new video card that is designed for PCIE 2.0 but is backwards compatible with PCIEx16, which is what i'm using now, as there isn't much on the market right now for PCIE2.0 motherboards. Will Ubuntu have drivers for my video card and if so does anyone know if the ATI Catalyst Control Center is installable and does it work with Ubuntu. Here is my card: [http://www.newegg.com/Product/Produc...82E16814102713](http://www.newegg.com/Product/Produc...82E16814102713) (HD3870)

Question 3
I am a gamer on World of Warcraft and Crysis and I was curious how these two games performed on Ubuntu. i currently run both games on full settings at max resolution with windows and average about 60 - 70 FPS on Warcraft and about 30 - 40 FPS on Crysis. My System has a dual core processor, 2gb ram, hd3870 video card, 80gb sata3 hd, 1333Mhz FSB  motherboard.

Thanks in advance, to anyone who can help me with these questions?

---

### Post by stoneybroke on 2008-02-20
Hi Well I can answer your 1st question yes when you install Ubuntu it will ask you to ether A. format the entire hard drive B. Use existing space or C. user defined chose user defined and select the unused space on your hard drive to create the partition.

As for the other 2 questions I have no idea about the video card but I expect it will and a program called WINE might allow you to load your windows games and play them WINE is a program that allowa most of windows programs to be run.  it can be found at [www.wine.com](www.wine.com) I think or just do a google search if I'm wrong.

---

### Post by SpaceCowboy41706 on 2008-02-20
Can anyone else answer the last two questions from experience or a really good Ubuntu educated guess :)

---

### Post by dstew on 2008-02-20
> I have found a guide that says i can still install Ubuntu on to the same drive and same partition without messing up my XPYou misunderstood the guide. Read carefully, and you will find that you have to shrink the XP partition, and then create a new partition for Ubuntu out of the freed-up space.> Will Ubuntu have drivers for my video card It appears that this card should work under Linux. A Phoronix card with the same ATI chipset has been shown to work. See [http://www.phoronix.com/scan.php?page=article&item=944&num=1](http://www.phoronix.com/scan.php?page=article&item=944&num=1) I don't know about the Catalyst Control Center. If that is a separate application, it depends on whether it is open source, and can be ported to Linux, or if it is a WIndows binary.> I am a gamer on World of Warcraft and CrysisSorry, I can't help you there, I have no experience with these games. But [here]("http://ubuntuforums.org/showthread.php?t=120615") is a thread that talks about using Wine to play WoW.

---

### Post by Pumalite on 2008-02-20
Here are a few links for you:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
As for games; sorry, no gamer here.

---

### Post by SpaceCowboy41706 on 2008-02-20
> You misunderstood the guide. Read carefully, and you will find that you have to shrink the XP partition, and then create a new partition for Ubuntu out of the freed-up space.

Does that mean that i will not have to reformat and then create 2 new partitions and then reinstall windows in one and ubuntu in another? And does it mean that i can follow the guide and that when i'm done i will have windows on one partition and ubuntu on another partition with a menu at boot time to decide which one i want to boot into...

I'm just trying to make sure my windows isn't gonna get messed up while trying to put ubuntu on here as well...

---

### Post by Partyboi2 on 2008-02-20
> **SpaceCowboy41706 said:**
> Does that mean that i will not have to reformat and then create 2 new partitions and then reinstall windows in one and ubuntu in another? And does it mean that i can follow the guide and that when i'm done i will have windows on one partition and ubuntu on another partition with a menu at boot time to decide which one i want to boot into...

I'm just trying to make sure my windows isn't gonna get messed up while trying to put ubuntu on here as well...
You will not have to reinstall windows, you will be shrinking the windows partition down and then with the free space creating another partition(s) for ubuntu. When you have installed ubuntu you will have the option at the grub menu to choose whether to boot into windows or ubuntu.
But remember its always best to backup your important stuff.

---

### Post by SpaceCowboy41706 on 2008-02-21
Cool, thats what i needed to know. 

I have the download complete and the disc burnt and ready to go but i thought i would make sure i could find the drivers i needed for the video card before hand to have them ready at install and at the ATI webiste [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)  i could not find linux drivers for my model of card [http://www.newegg.com/Product/Product.aspx?Item=N82E16814102713](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102713) (HD3870)

Does anyone know where i can find these drivers at or are they included automatically with the install?

---

### Post by jcitguy78 on 2008-02-21
The Update Manager might pick up on the video card drivers. This is the driver Phoronix used to test that card in their review, **fglrx driver**, they tested on Ubuntu 7.10.

---

### Post by SpaceCowboy41706 on 2008-02-21
Alright here goes nuthin.. Installing now!!!

---

### Post by SpaceCowboy41706 on 2008-02-21
OK installed fine now except when the grub menu comes up my usb keyboard doesnt light up and i cant move the highlighter up or down. Would that be a BIOS setting or a setting inside ubuntu somewhere?

---

### Post by Pumalite on 2008-02-21
Try changing your keyboard to a different USB port. (once you have booted)

---

### Post by SpaceCowboy41706 on 2008-02-21
moved it around to all the ports... no change... the keyboard lights flash when the pc first starts to boot up.. then they go out when the grub menu comes up and i cant do anything.

PS.. rebooted after changing it to each different port...

---

### Post by SpaceCowboy41706 on 2008-02-21
I'm a dork. It was in the BIOS settings. Thanks for all your help... MY Ubuntu is up and working fine now except the drivers for this video card are horrible, but I will try to solve that problem on my own and if I cant I'll open another thread.

---

### Post by Partyboi2 on 2008-02-21
you could use [envy]("http://albertomilone.com/nvidia_scripts1.html")

---

