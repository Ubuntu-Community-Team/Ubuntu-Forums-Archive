---
title: "Grub2 install on root (NOT mbr) won't boot - anyone else?"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by tbessie on 2009-11-27
Hello all...

I'm using a 3rd-party boot loader on the MBR, and install grub2 (during Ubuntu 9.10 install) to my Ubuntu root partition (/dev/sda5).

However, grub2 install to anything but the MBR seems to not provide a bootable system.  No 3rd-party boot loader can boot from the root partition, even though the Ubuntu installer didn't complain when I installed grub2 to the root partition.

Is ANYONE else having these problems?  All the grub2 documentation seems to guide people to installing grub2 to the MBR, but I don't want to install it there, and installing it anywhere else appears to fail.

- Tim

---

### Post by meierfra. on 2009-11-27
Installing Grub2 to a boot sector can be tricky. But let's first see whether Grub2 is correctly installed in the boot sector:  Follow these [instruction]("http://ubuntuforums.org/showthread.php?p=8279056#1") to download and run the boot info script and to post the results.

---

### Post by inertz on 2009-11-27
My grub2 detect SuSE but cannot boot to it.

---

### Post by meierfra. on 2009-11-27
inertz: Could you start a new thread with your problem? Thanks.

---

### Post by tbessie on 2009-11-27
I seem to have discovered what the problem was (or, rather, a limitation with grub2, possibly?) - when my root partition was a LOGICAL partition, booting to GRUB2 failed.

So I reinstalled, this time making my root and swap PRIMARY partitions, and /home on a logical partition, and this time, GRUB2 installed and booted correctly.

Is there a known limitation of GRUB2 not being able to install correctly on logical partitions?

My partition table had been like this:

Primary 1gb FAT32 (support for 3rd party boot loader)
Extended
... Linux Root (logical)
... Linux Swap (logical)
... Linux Home (logical)

Installing Grub2 to Linjux Root wasn't working.

So I changed to:

Primary 1gb FAT32 (support for 3rd party boot loader)
Primary Linux Root
Primary Linux Swap
Extended
... Linux Home (logical)

and reinstalled, and it worked.

- Tim

---

### Post by presence1960 on 2009-11-28
Changing or Moving GRUB 2

The command to change the GRUB 2 installation device or boot files is grub-install run as root. This command allows the user to modify the installation by setting the ROOT directory, preload modules, run specific setup files and more. When executed, grub-install may run one or more other commands, such as grub-probe, grub-mkimage, and grub-setup. Here are some considerations when running grub-install:

    *

      The grub-install command should be used rather than grub-setup under normal circumstances. grub-setup will be called by grub-install when needed.
    *

      The command should specify a device and when executed will install the required GRUB files to the location called for in the options. (example: sudo grub-install /dev/sda )
    *
> 
      ***If the user attempts to run the command with a specific partition (example: sudo grub-install /dev/sda6 ) a warning will be issued. Specifying a partition is not recommended due to the use of blocklists, which the developers consider unreliable. An option is provided on how to override this recommendation if the user still wishes to do so.***
    *

      The list of options available for grub-install can be displayed in a terminal with grub-install --help.
    *

      The man page for grub-install currently does not display the all the available options. 
-----------------------------------------------------------------------------------------------------------------------------------------------

See quoted text above. taken from GRUB 2 Community documentation section Installing GRUB from Live CD. See [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD"). As you can see it is not recommended to install GRUB 2 to a partition.

---

### Post by oldfred on 2009-11-28
I did install grub2 from Karmic alpha into the partition and chainbooted to it. It chainboots fine for me, but now I am directly booting grub2. My grub2 PBR is a logical partition (sdc9). At the time I installed it to the partition I do not remember any messages, but every update since, I get the warning on blocklists.

I also did a clean install with the same intent but missed the advanced button and it installed to the MBR of the install drive not the boot drive, which was also what I wanted. When I reordered drives in BIOS, it does boot thru grub2 quicker, but all drive order in 9.10, 9.04 and grub's device.map is still based on the order installed in the Sata ports, not BIOS. The script does not identify the Grub2 in the partition possibly because it is an older version.

---

### Post by presence1960 on 2009-11-28
> **oldfred said:**
> I did install grub2 from Karmic alpha into the partition and chainbooted to it. It chainboots fine for me, but now I am directly booting grub2. My grub2 PBR is a logical partition (sdc9). At the time I installed it to the partition I do not remember any messages, but every update since, I get the warning on blocklists.

I also did a clean install with the same intent but missed the advanced button and it installed to the MBR of the install drive not the boot drive, which was also what I wanted. When I reordered drives in BIOS, it does boot thru grub2 quicker, but all drive order in 9.10, 9.04 and grub's device.map is still based on the order installed in the Sata ports, not BIOS. The script does not identify the Grub2 in the partition possibly because it is an older version.

I am sure GRUB 2 can be booted installed to a partition. It is just not recommended because it may not work.

---

### Post by tbessie on 2009-11-28
> **presence1960 said:**
> Changing or Moving GRUB 2

The command to change the GRUB 2 installation device or boot files is grub-install run as root. This command allows the user to modify the installation by setting the ROOT directory, preload modules, run specific setup files and more. When executed, grub-install may run one or more other commands, such as grub-probe, grub-mkimage, and grub-setup. Here are some considerations when running grub-install:

    *

      The grub-install command should be used rather than grub-setup under normal circumstances. grub-setup will be called by grub-install when needed.
    *

      The command should specify a device and when executed will install the required GRUB files to the location called for in the options. (example: sudo grub-install /dev/sda )
    *

    *

      The list of options available for grub-install can be displayed in a terminal with grub-install --help.
    *

      The man page for grub-install currently does not display the all the available options. 
-----------------------------------------------------------------------------------------------------------------------------------------------

See quoted text above. taken from GRUB 2 Community documentation section Installing GRUB from Live CD. See [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD"). As you can see it is not recommended to install GRUB 2 to a partition.

Thanks much for your extremely complete answer. :-)

Personally, tho' there may be good reasons for the decision to not encourage people to install to partitions, I have a couple of comments:

1. If what you say is the case, the Ubuntu installer should know about it and spit out said message, and also allow the user to override it via a checkbox, say, or button which will provide the correct override option on the command line.  I wouldn't be using Ubuntu if I wanted to do this kind of thing myself - I'd just go back to Slackware and Lilo. :-)

2. Since I don't know the reasons it is considered unreliable to install grub2 onto a partition, I will say - in my ignorance - that boot code should be able to be installed on ANY partition in a well-behaved OS environment; we don't want to be like Windows, do we?  And even my 3rd party boot program can boot Windows partitions.

3. Having boot code only available on the MBR is, well... a relic of The Ancient Days(tm).  New, Shiny, Modern OSes and bootloaders like Ubuntu and Grub2 should be flexible enough to not require it.

Feel free to give your opinions on my comments.

- Tim

---

### Post by presence1960 on 2009-11-28
> **tbessie said:**
> Thanks much for your extremely complete answer. :-)

Personally, tho' there may be good reasons for the decision to not encourage people to install to partitions, I have a couple of comments:

1. If what you say is the case, the Ubuntu installer should know about it and spit out said message, and also allow the user to override it via a checkbox, say, or button which will provide the correct override option on the command line.  I wouldn't be using Ubuntu if I wanted to do this kind of thing myself - I'd just go back to Slackware and Lilo. :-)

2. Since I don't know the reasons it is considered unreliable to install grub2 onto a partition, I will say - in my ignorance - that boot code should be able to be installed on ANY partition in a well-behaved OS environment; we don't want to be like Windows, do we?  And even my 3rd party boot program can boot Windows partitions.

3. Having boot code only available on the MBR is, well... a relic of The Ancient Days(tm).  New, Shiny, Modern OSes and bootloaders like Ubuntu and Grub2 should be flexible enough to not require it.

Feel free to give your opinions on my comments.

- Tim

Tim,
 I agree. The only thing is GRUB 2 is so new and all we have right now is documentation which is still incomplete by it's own admission on the document.

---

### Post by meierfra. on 2009-11-28
> Is there a known limitation of GRUB2 not being able to install correctly on logical partitions?

To my own surprise there does seems to be a bug in Grub 2 which only effects logical partitions:

```
sudo grub-install -f /dev/sdaX

```

does not work  if /dev/sdaX is mounted and /dev/sdaX is a logical partition. To make  matters worse, grub-install exits with "Installation finished. No error reported." So there is no indication that something went wrong (other than the warning about "blocklist", but that warning is also displayed when "grub-install" was successful).

If /dev/sdaX is not mounted or  /dev/sdaX is a primary partition then "sudo grub-install -f /dev/sdaX" works perfectly.

Thanks for posting your solution, I had not realized that this bug only effects logical partitions.

**Edit:**  I can no longer recreated the faulty behavior. Maybe the problem only occurs in Grub 1.97 beta 4  (I have Grub 1.97 installed).  I'll do some more testing.

---

### Post by meierfra. on 2009-11-28
> - that boot code should be able to be installed on ANY partition in a well-behaved OS environment

The boot sector of a partition is to small for a decent  boot code.  

If grub2 is installed to the boot sector, it will look for "core.img" by its physical address. If core.img is moved or updated, or the partition is resized, booting will fail.  

If grub2 is installed in the extended MBR,  it is able to look for the grub folder  by the UUID of the partition and the path "/boot/grub/". This is more reliable.

---

### Post by tbessie on 2009-11-29
> **meierfra. said:**
> The boot sector of a partition is to small for a decent  boot code.  

If grub2 is installed to the boot sector, it will look for "core.img" by its physical address. If core.img is moved or updated, or the partition is resized, booting will fail.  

If grub2 is installed in the extended MBR,  it is able to look for the grub folder  by the UUID of the partition and the path "/boot/grub/". This is more reliable.

How big is the boot sector of a partition on modern hard drives?  And is it enough to contain simple filesystem-reading code so 2nd stage boot images can be found without looking in physical locations?

- Tim

---

### Post by tbessie on 2009-11-29
> **meierfra. said:**
> To my own surprise there does seems to be a bug in Grub 2 which only effects logical partitions:

```
sudo grub-install -f /dev/sdaX

```

does not work  if /dev/sdaX is mounted and /dev/sdaX is a logical partition. To make  matters worse, grub-install exits with "Installation finished. No error reported." So there is no indication that something went wrong (other than the warning about "blocklist", but that warning is also displayed when "grub-install" was successful).

If /dev/sdaX is not mounted or  /dev/sdaX is a primary partition then "sudo grub-install -f /dev/sdaX" works perfectly.

Thanks for posting your solution, I had not realized that this bug only effects logical partitions.

**Edit:**  I can no longer recreated the faulty behavior. Maybe the problem only occurs in Grub 1.97 beta 4  (I have Grub 1.97 installed).  I'll do some more testing.

Thanks much for trying it out!  Well, I guess the moral for me is, don't expect that boot loaders will always be able to be installed on the boot sector of any given partition.  Perhaps someday we'll have newer BIOS and boot standards that don't have these kinds of limitations (I know there are folks working towards that, but I'm sure it'll take a long time to actually be out there in most machines), but it's good to know what limitations exist.

- Tim

---

### Post by mk4umha on 2010-01-04
> **meierfra. said:**
> To my own surprise there does seems to be a bug in Grub 2 which only effects logical partitions:

```
sudo grub-install -f /dev/sdaX

```

does not work  if /dev/sdaX is mounted and /dev/sdaX is a logical partition. To make  matters worse, grub-install exits with "Installation finished. No error reported." So there is no indication that something went wrong (other than the warning about "blocklist", but that warning is also displayed when "grub-install" was successful).

If /dev/sdaX is not mounted or  /dev/sdaX is a primary partition then "sudo grub-install -f /dev/sdaX" works perfectly.

Thanks for posting your solution, I had not realized that this bug only effects logical partitions.

**Edit:**  I can no longer recreated the faulty behavior. Maybe the problem only occurs in Grub 1.97 beta 4  (I have Grub 1.97 installed).  I'll do some more testing.


I'm trying to use truecrypt as the bootloader on the MBR and then install Grub2 onto the /boot partition to load up Ubuntu when i hit ESC from truecrypt. I guess i'm having the same exact problem with Grub2 in which grub won't boot when i hit ESC at the TrueCrypt prompt. I'm currently on 1.97 Beta4.

How can I update the older grub2 to 1.97 while using the live CD to restore grub2 onto the /boot partition?

---

### Post by mopalinski on 2011-01-16
I know I'm about a year late with this reply, but after trying many manual ways of installing Grub2 on a boot partition instead of the disk MBR (and failing btw... I got the partition to boot with Grub prompt but was not able to proceed from there) because of the OK button graying out if I selected any partition instead of the disk that they were on (ie. /dev/sda3 instead of /dev/sda). 

I was amazed by that "oversight"/"preventative action to prevent ppl who dont know what they are doing from not being ableto boot their system" since I see Linux as the liberal OS. 

Anyways, this is gonna sound really simple and you are probably are going to slap yourself in the forehead as I did ;) all I did is started the setup over and when I got to that Advanced window once again, instead of selecting the device from the drop down menu I simply typed it in... Believe it or not, it worked like a charm.


Better later than never.

---

