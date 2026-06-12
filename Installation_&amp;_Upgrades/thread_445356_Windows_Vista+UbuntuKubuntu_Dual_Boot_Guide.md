---
title: "Windows Vista+Ubuntu/Kubuntu? Dual Boot Guide"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by UltraM4n on 2007-05-15
**_[SIZE="5"]The Noob Guide To Vista+Ubuntu[/SIZE]_**





Hi Folks. This is my first guide. I learned this the hard way -_____-

If your going to dual boot Vista+Ubuntu/Kubuntu?, you need to look at this guide!

NOTE: I did this in Feisty Fawn, if your using another Version, you may need to manually add Vista to the boot loader. Look At Other guides to do this.


DO NOT USE ANY OTHER PARTATIONERS OUT THERE! THEY WILL RUIN YOUR VISTA INSTALLATION


This is showing that vista is installed first.

First, install vista (obously..if you  need any help just PM me)

Setting Up Disk:

Next, once you've installed vista + all of the updates required, do this.
Start>Right Click On "Computer">Go To Manage. 

Vista's Built-In Partitioner is not very well known. Somebody really should make an easy access shortcut...


Anyway,once you have loaded up the Computer Manger, Go to storage, and then disk management.

It should then show the current disks and their partitions. I personally edited my External HD's space, but it's a good idea to select your main disk (Most of the time Disk 0)

Right Click on the main Partition, then go to shrink volume.
(NOTE: The Volume Size is in MB, so 2222 would be 2gigs and 222mb)
I picked about 30gigs for mine(30000mb) Then hit ok or whatever it asks. Then re-boot.

Installing Linux:

1.Burn a Linux/Kubuntu Live CD
2.Insert Into Computer
3. Reset With Disc in Computer
4. Either A.It will Boot Directly to the Disc, or B. You need to Go To Your BIOS' Boot menu(Usually F12,F9,Or DELETE during the BIOS boot-up)
5.Once booted into the LiveCD, choose Install.
6.Select Where you live and whatnot.
7. Once you are at the place where it asks for disc, pick Manual.
8.Once the Disk Manger shows up, choose the newly made un-allocated space. You could then split off a small 250mb for the Linux swap, choose that has the linux-swap partition, choose the other big chunk as the ext3, and use the mount for the bigger one as "/"
9.Enter in the user information.
10.Wait for Installation...
11.Reboot
12. If succesful, under grub it should show the Ubuntu Partition, and your Vista as (Vista/Longhorn Loader)
13.Try Booting into Vista
14.If it boots, CONGRATS
15.Reboot
16.Try booting into Ubuntu
17. If boots, DOUBLE CONGRATS


NOTE: This Method may be different with Kubuntu. I haven't tried it yet. But i will.


                                                          Thanks For reading My Guide ^______^
PM me or email me at [email]nightmarestudios1@gmail.com[/email] for any problems. Or just post here :P

---

### Post by Kingsley on 2007-05-15
Amazing work. I think it's in the wrong section though.

---

### Post by UltraM4n on 2007-05-15
> **Kingsley said:**
> Amazing work. I think it's in the wrong section though.

Hey thanks! If this is the wrong section, would a mod please move it?


THANKS :D


BTW, I'm currently Burning a Kubuntu Feisty Fawn CD...is it any good?

---

### Post by arandomperson on 2008-03-04
Great guide. It does work for 7.10 and the grub file autamaticly recognizes Vista.

---

