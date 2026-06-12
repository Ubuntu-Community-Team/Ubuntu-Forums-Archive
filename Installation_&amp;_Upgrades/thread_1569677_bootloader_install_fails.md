---
title: "bootloader install fails"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by Brett636 on 2010-09-07
Hi, I am trying to install ubuntu 10.04(32 bit) on my freshly built computer, but I am running windows 7 as my primary OS.  When I built the computer I made sure to leave some free space for a future linux partition.   Currently I have 2 hard drives running in a Raid 0 format with each drive being 600GB(if that helps any).  When doing the install I get 93% done when I get an error in installing the bootloader and it gives me the option of installing it in a particular partition, installing it later, or cancelling the installation.  Should I try installing the bootloader onto a certain partition or is there another way to get it working so that i can dual boot windows 7 and ubuntu?  I have to apologize beforehand as I am a linux novice, and would simply like to learn more about this OS but I know very little at the moment.  

Thank you for your time and patience.  :)

As a quick side question, as a new linux user should I continue working with the 32 bit version or can I safely use the 64 bit version of ubuntu without additional headaches?

---

### Post by garvinrick4 on 2010-09-07
Where are you installing the boot loader in page 8 advanced tab of Ubuntu install?

---

### Post by ronparent on 2010-09-07
And it informs you it is a fatal error? I have fared best by contiuing to install without grub and then reinstalling grub from the live cd. This is the reference you need: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

As I have found, the install to a raid 0 is a special case. The grub boot loader has to be written to the raid array (that is the overall raid and not one of the raid partitions). The name of the raid device may be found in /dev/mapper of your install. It is the first of similarly named symbolic links listed and is without the appended partition number which follows the raid name (look in /dev/mapper and you should see what I mean).

If you follow method 1, in step 4 you mount the target raid partition in /mnt. In step 5 you will write the grub MBR to the link I described above. Just be sure to include the full path name (/dev/mapper/) each time you enter the raid names and otherwise write the commands in the exact form instructed. Post if you need help.

---

### Post by Brett636 on 2010-09-13
> **garvinrick4 said:**
> Where are you installing the boot loader in page 8 advanced tab of Ubuntu install?

Honestly I am not sure as I did not check it.  I will try the install again and see what it says.

> **ronparent said:**
> And it informs you it is a fatal error? I have fared best by contiuing to install without grub and then reinstalling grub from the live cd. This is the reference you need: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

As I have found, the install to a raid 0 is a special case. The grub boot loader has to be written to the raid array (that is the overall raid and not one of the raid partitions). The name of the raid device may be found in /dev/mapper of your install. It is the first of similarly named symbolic links listed and is without the appended partition number which follows the raid name (look in /dev/mapper and you should see what I mean).

If you follow method 1, in step 4 you mount the target raid partition in /mnt. In step 5 you will write the grub MBR to the link I described above. Just be sure to include the full path name (/dev/mapper/) each time you enter the raid names and otherwise write the commands in the exact form instructed. Post if you need help.

I do recall an error prior to the one installed above regarding GRUB.  At the time I was not aware of what GRUB was so I just clicked ok and went ahead.  If a 2nd install attempt doesn't work I will do this instead.

---

### Post by ronparent on 2010-09-13
You just have to reinstall grub 2 per the reference I gave you. It is a common problem encountered by people who have done he install right - but, it is easily fixable. The second install may work - for some reason it seems to work right when you hit the advanced box the second time around. the fix is easier.

---

