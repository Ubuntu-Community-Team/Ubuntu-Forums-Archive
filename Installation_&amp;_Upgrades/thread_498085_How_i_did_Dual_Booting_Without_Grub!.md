---
title: "How i did: Dual Booting Without Grub!"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by Del Piero on 2007-07-10
This is a personal experience that i decided to share, i am no linux expert in fact i am a complete newbie. This method is not an invention, it's something i collected from many points during reading alot of guides etc. If you feel that this thread isn't useful feel free to delete it or move it.

Well just like many people out there i am just a windows user who has no previous linux experience who decided one day to give linux a try. So i decided to create a dual boot machine like many others. 

And like many others i read tons of guides and howto's etc, thing is, for me as well as some others that i met along my long journey of dual booting GRUB caused problems by not loading or giving me error messages although it was configured properly according to some linux users who tried to help me with my problem. 

Some said that the problem is between Ubuntu and Sata Drives, other suggested it's Ubuntu and Grub others suggested that i have a bad hard drive....etc. Anyway whatever it was thats not the point of this thread, this guide is made for those who have/had problems with GRUB like myself. It's an alternate method that i sort of came up with by gathering hints and info from alot of other guides as i said it's not an invention, anyway Instead of grub we will use LILO and a multi boot manager called GAG.

Anyway this is how i did it:

First of all, you need GAG which is a free neat boot manager that can be downloaded from [here.]("http://gag.sourceforge.net/")

Once you download the GAG zip file open it and see how to make a gag bootable cd or a gag disk. And don't worry, you won't use a disk to load ubuntu or xp everytime as Gag can be installed on your hard drive from the disk without messing with Lilo (Linux boot Loader) or NTLDR (Windows Boot Loader).

Once you have GAG on a bootable cd  make sure that your bios is set to boot from cd's. Now insert your Ubuntu cd follow the installation normally, partition (REMEMBER TO SET UR LINUX PARTITION FLAG ON), do everything as mentioned in every other guide until your asked about the GRUB installation, do not install it, instead install LILO, you can do that by first choosing not to install GRUB on the mbr and leaving the next screen blank. GRUB will give u an error that u didn't specify a location for it, go back and you will find the installation menu, choose install LILO, choose to install it on the linux partition.

Now insert your gag bootable cd, choose to install GAG. Choose add an os (you will see the linux partition and the windows partition and any other os you have). GAG can support up to 9 operating systems :KS. Anyway assign a name and an icon :guitar: to each OS you add to GAG then set a timer with a default choice you choose (Optional). then press h in Gag installation menu to save it on the hard disk. remove the cd, reboot and you will see a fancy menu asking you to choose between windows and ubuntu make your choice and boot them up.

---

### Post by dfreer on 2007-07-10
Good info! You might want to make this a more detailed how-to, since it is directed to new users anyways who may not know how to set the bootable flag on a partition. Anyways, glad you got things running now!

---

### Post by confused57 on 2007-07-10
Impressive writeup, thanks for sharing.

Did you happen to use the alternate install cd or the desktop live cd?  I know that you can install lilo using the alternate cd, but it would be useful info to know if you did this with the live cd installer.

Also, did you try installing grub to the root partition as you did lilo and try booting with the GAG bootloader.  The reason I ask is that I'm currently helping someone who is having problems with grub and I'm going to provide him a link to your "howto"...Good job.

---

### Post by Del Piero on 2007-07-10
> **dfreer said:**
> Good info! You might want to make this a more detailed how-to, since it is directed to new users anyways who may not know how to set the bootable flag on a partition. Anyways, glad you got things running now!

Thanks, tomorow i will re-write this again in details.

> **confused57 said:**
> Impressive writeup, thanks for sharing.

Did you happen to use the alternate install cd or the desktop live cd?  I know that you can install lilo using the alternate cd, but it would be useful info to know if you did this with the live cd installer.

Also, did you try installing grub to the root partition as you did lilo and try booting with the GAG bootloader.  The reason I ask is that I'm currently helping someone who is having problems with grub and I'm going to provide him a link to your "howto"...Good job.

Thanks, i am glad you found this useful. I used an alternate install cd and yes i tried installing GRUB on the root partition and used GAG, GAG was able to boot windows, and when i chose Linux i got the grub menu who failed booting both linux andr xp.

---

### Post by confused57 on 2007-07-11
> **Del Piero said:**
> Thanks, tomorow i will re-write this again in details.



Thanks, i am glad you found this useful. I used an alternate install cd and yes i tried installing GRUB on the root partition and used GAG, GAG was able to boot windows, and when i chose Linux i got the grub menu who failed booting both linux andr xp.
Thanks for the update, your howto may be very useful for the OP in this thread:
[http://ubuntuforums.org/showthread.php?t=495944](http://ubuntuforums.org/showthread.php?t=495944)
I've also bookmarked this thread, for future reference...looking forward to seeing your write-up.

---

