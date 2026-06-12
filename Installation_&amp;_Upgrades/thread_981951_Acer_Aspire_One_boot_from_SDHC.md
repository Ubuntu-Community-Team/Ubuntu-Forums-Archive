---
title: "Acer Aspire One boot from SDHC"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by thor2002ro on 2008-11-14
Ok heres what i want to do...
I what to boot from the sdhc card while keeping the hdd for storage
I managed to install 8.10 umpc version on the sdhc .... now i know the aspire one can't boot from sdhc because its pcie but i can have grub on the hdd and boot sdhc and then turn off hdd
now the problem...
i dont know how to setup grub(i allready have grub on the hdd) to boot sdhc... as far as i can tell grub doesn't see the sdhc i tried "geometry hd" and tab and only see's the hdd not the sdhc can anyone help?

PS: For the SDHC "write" limit spamers witch is in fact erase limit DONT NEED WARNINGS!!!

---

### Post by thor2002ro on 2008-11-14
anyone?

---

### Post by jimv on 2008-11-14
So you installed to the SDHC from the CD?  Probably the easiest thing to do would be to reinstall, and on the last screen, click the advanced button and install GRUB to the SDHC.  Then set the SDHC as the default boot device in your BIOS.

---

### Post by thor2002ro on 2008-11-14
> **jimv said:**
> So you installed to the SDHC from the CD?  Probably the easiest thing to do would be to reinstall, and on the last screen, click the advanced button and install GRUB to the SDHC.  Then set the SDHC as the default boot device in your BIOS.

if you read my post closly , you see that the aspire one bios cant boot from sdhc because of the sdhc card readers are pcie .i have grub on the hdd and with this grub boot the sdhc card ... but grub doesnt seem to see the sdhc slot that my problem....

---

### Post by thor2002ro on 2008-11-16
common none can help mee ](*,)?????????????

---

### Post by blackest_knight on 2008-11-16
probably not possible to do what you want unless perhaps acer change the bios (maybe). 
I've been playing around with suspend, hibernate on the aspire one. with the Swap on the sd card it can't find it early enough to restore from.

So i'd think it's not going to be possible to boot from your SD Card, USB drives obviously can work and perhaps a usb card reader with an SD card in it would work also. 

Actually if your really determined perhaps you could hack in a usb card reader into the trap door underneath the aspire one. There is enough room for it.

---

### Post by thor2002ro on 2008-11-16
you cant see the sd early enough because you need to load sdhci in initrd ... the problem here is grub ...., tryed grub 1 (legacy) and grub 2 no luck 
the problem here is that grub cant see the device.... i dont think its got mmc drivers . as far as i could find it needs a patch but i never compiled grub before so not much luck 

look here
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/263654]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/263654")

---

### Post by Thermophilus on 2008-11-18
The idea is just great.
If you find a way pls inform us, that could save as from the bad perfomance of the SSD.

What about putting just the /boot directory on the SSD and the other parts of th OS on the SDHC ? That could speed up the sytem.

Regards
Mauro

---

### Post by timdream on 2008-12-09
> **Thermophilus said:**
> The idea is just great.
If you find a way pls inform us, that could save as from the bad perfomance of the SSD.

What about putting just the /boot directory on the SSD and the other parts of th OS on the SDHC ? That could speed up the sytem.

Regards
Mauro

Hey, thanks for your idea. I just done that and it **works**!

The only trick required is to put the following modules into initrd.img that is in /boot:

* mmc_block
* sdhci
* sdhci-pci

grub (and the kernel it boots) can then find the sdhc device contains the root directory. Once booted successfully, the ide device can be turn off to conserve energy; one can even unmount /boot after booting (not recommend).

I can write a tutorial if you want. It basically  involved manually setting partition and mounting points and mkinitramfs.

---

### Post by larko on 2008-12-21
> **timdream said:**
> I can write a tutorial if you want. It basically  involved manually setting partition and mounting points and mkinitramfs.

Hi, don't suppose you've got any more details on how you got this working?  I've set up a new boot partition and initrd image with the mmc_core, mmc_block and sdhci modules and changed the root option in grub.conf, but linuxrc falls over when trying to mount /sysroot (mount: error 6 mounting ext2).

Cheers.

---

### Post by anfy on 2008-12-28
I'm interested in this as well... please post if you have more progress!

---

### Post by Forinti on 2008-12-30
A short description of your process would be great, timdream.  Also, about how much space does the boot directory take up with this method?  I'd love to add another, larger linux distro to my Dell Mini 9, and bounce booting from a small partition onto a SDHC this way would be great, since the bios can't see my memory card and I'm already pushing the space limit on the SSD.

---

### Post by anfy on 2008-12-31
i got it working after 3 days of painful trial-and-error.

basically, add the mmc_block, etc to the file listed, update the initramfs file (choose a diff location), the point grub to it.  I will post a tutorial when I get time (hopefully soon), on the aspire one forum.

---

### Post by Forinti on 2008-12-31
> **anfy said:**
> i got it working after 3 days of painful trial-and-error.

Been there.  ](*,)
Just hit this thread with the link whenever you do get something written down.  No rush though, it'll be a week before I can even try anything.  Many thanks in advance!

---

### Post by damoisture on 2009-01-09
A little more guidance would be great, but I'm going to give this a shot this weekend anyway and see what I can do with it!

---

### Post by james_w12345 on 2009-01-18
Please can someone post a tutorial of how to do this.
i have a vista(university supplied) laptop which id rather not install to, so im trying to use the sd card to boot ubuntu. i can install to sd card no problem, but dont know where to put the grub loader. 

also apparently, this might be useful, my laptop has an option to boot from floppy/sd card, but as yet i havnt managed to get this to work.
any help/tutuorial would be very useful.

---

### Post by ios77 on 2009-02-06
[Here]("http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_One") you can find a weel done guide. But following it I have a problem...
During the second installation on the esternal SD the grub installation on it failed. If I boot from the distro installed on the internal SSD and try to manually install grub on the external SD I have the same error. The device is correct but it doesn't appar as /dev/sdXX but /dev/mmxxxxxxx. 
How can I solve?

---

### Post by superJoel on 2009-02-28
> **ios77 said:**
> [Here]("http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_One") you can find a weel done guide. But following it I have a problem...
During the second installation on the esternal SD the grub installation on it failed. If I boot from the distro installed on the internal SSD and try to manually install grub on the external SD I have the same error. The device is correct but it doesn't appar as /dev/sdXX but /dev/mmxxxxxxx. 
How can I solve?

using that guide at osnews didn't work at first, but it was an easy fix.

Follow the guide.  After you finish installing your ubuntu version onto your SDHC card while in the SDHC USB adapter, reboot and run it that from the SDHC card in the USB Adapter.  While started up edit the following file with gedit, nano, kate or whatever.

/etc/initramfs-tools/modules 

Add these each on one line (do not comment with #):

> mmc_core
mmc_block
sdhci
sdhci-pci

Save the modules file.

Now at the command line type:

sudo update-initramfs -u  

to update the initramfs file on your SDHC card.  

Copy your new initramfs file and your vmlinuz file from the SDHC's boot directory over to your SSD drive's /boot directory and finish up with the rest of his guide to edit your grub.

my grub for the SDHC portion looks like this:
> title		Ubuntu 8.10, 2.6.27-7-SDHC 
uuid=62191336-8e39-45b6-91e9-28d022f3fe6d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ec958856-dc52-4cf2-a36d-0a9f26b2a4df ro
clocksource=hpet
initrd		/boot/initrd.img-2.6.27-7-generic

the first uuid is my SSD not my SDHC card.  The kernel is pointing the kernel file that I copied from the boot directory off the SDHC card onto the boot directory on my SSD and the uuid on the kernel line is for my SDHC card (you can get this by typing in *blkid* in terminal).  If you get hangups due to clocksource you might want to add the clocksource=hpet line.

Hope this helps anyone trying to run dual boot off your SDHC card slot.

---

### Post by flubbard on 2009-03-14
I'm trying to do a similar thing with the Aspire One, with a couple of changes and I'm not making very much progress.  I have a internal HD (non SSD), but would like to boot from the SD card slot.  I would like to launch from a USB key, which I can then unmount and run with only the SD card.  I believe that I have grub loaded on the USB card and I have it configured to use the UUID, but when I try to boot, I get a file not found.  I believe that I have recreated the initram file with the SD modules loaded and I have put that on the USB card.

I would appreciate any thoughts from those that have been able to make it work.  I've been at this for about a week with very little success.

Thanks - flub

---

### Post by superJoel on 2009-03-14
> **flubbard said:**
> I'm trying to do a similar thing with the Aspire One, with a couple of changes and I'm not making very much progress.  I have a internal HD (non SSD), but would like to boot from the SD card slot.  I would like to launch from a USB key, which I can then unmount and run with only the SD card.  I believe that I have grub loaded on the USB card and I have it configured to use the UUID, but when I try to boot, I get a file not found.  I believe that I have recreated the initram file with the SD modules loaded and I have put that on the USB card.

I would appreciate any thoughts from those that have been able to make it work.  I've been at this for about a week with very little success.

Thanks - flub
This should be possible.  Did you install the system onto the SD card?  You should be able to boot up from SD card while plugged into a USB card reader... if that works then did you add the lines mmc_core, mmc_block, sdhci, and sdhci-pci to your /etc/initramfs-tools/modules on the SD cards OS?  Then you should have ran the *update-initramfs -u* and take that new initramfs file from the SD card and copy over to your USB's boot folder...  you will need to ensure that the GRUB/menu.lst file shows your USB's uuid as the one on the second it will be booting from, and then on the kernel line use your SD card's uuid to have it start  (your vmlinuz file probably should be on the usb as well as on your SD card)... what does your grub look like for what you are trying to accomplish?

---

### Post by flubbard on 2009-03-14
When I install to the SD Card, I cannot get the SD card to boot through the reader.  I am able to get a USB stick to boot when installed to the USB drive.  This keeps me from being able to grab the UUID from the SD instance of eeebuntu.  Any thoughts on why it may not be booting?  It appears to be installing through the ubuntu installer.

  - flub

---

### Post by superJoel on 2009-03-15
> **flubbard said:**
> When I install to the SD Card, I cannot get the SD card to boot through the reader.  I am able to get a USB stick to boot when installed to the USB drive.  This keeps me from being able to grab the UUID from the SD instance of eeebuntu.  Any thoughts on why it may not be booting?  It appears to be installing through the ubuntu installer.

  - flubRun a live CD or installer... install the OS to your SD card with it in the reader (or you'll have problems)... it should be able to boot up off the SD card while in the reader... then do the other steps.  Keep us posted.

---

### Post by flubbard on 2009-03-15
That is basically the process that I have tried.  I have the live CD (with installer) loaded onto a pen drive from which I boot.  I install eeebuntu from that drive onto the SD card, which I have in the reader.  I then reboot with only the SD card in the reader but it immediately bypasses it and boots the host operating system (Windows XP).  Are all readers created equally, or is it possible that the reader that I have is not making my SD card appear as a USB drive as much as another one would.  I am using a generic model which basically allows you to plug the SD card into a little dongle that looks very similar to a pen drive.

Thanks again for the input.  I'm sure I must be missing something very silly.

 - flub

---

### Post by superJoel on 2009-03-15
> **flubbard said:**
> That is basically the process that I have tried.  I have the live CD (with installer) loaded onto a pen drive from which I boot.  I install eeebuntu from that drive onto the SD card, which I have in the reader.  I then reboot with only the SD card in the reader but it immediately bypasses it and boots the host operating system (Windows XP).  Are all readers created equally, or is it possible that the reader that I have is not making my SD card appear as a USB drive as much as another one would.  I am using a generic model which basically allows you to plug the SD card into a little dongle that looks very similar to a pen drive.

Thanks again for the input.  I'm sure I must be missing something very silly.

 - flub Just to clarify... at boot, you are pressing F12, esc (or the required function key to get to the boot device selection menu), then you select your USB dongle with the SD card in it, or it's not showing up, and boots into XP anyway?

---

### Post by flubbard on 2009-03-15
I have the machine enabled to boot first from the USB port if available, in which case it does not find the SD card reader as a boot device.  When I hit F12 with only the SD card in (through the reader), it does not list it as a boot device.  It only shows the hard drive and the legacy network boot.

---

### Post by superJoel on 2009-03-16
> **flubbard said:**
> I have the machine enabled to boot first from the USB port if available, in which case it does not find the SD card reader as a boot device.  When I hit F12 with only the SD card in (through the reader), it does not list it as a boot device.  It only shows the hard drive and the legacy network boot.so with the SD card in your USB Reader dongle it doesn't see it at boot. hmmm. It might be your USB card reader.  I just bought an OHM SDHC card reader at Target for $5 that I know works to boot off of.  You might want to make sure that your SD card's boot flag is set first before you go off spending any money though.

---

### Post by flubbard on 2009-03-16
I checked and the boot flag was set.  It looks like I may be making a run to target to try a different reader.  I'll let you know how I make out.
 - flub

---

### Post by superJoel on 2009-03-16
> **flubbard said:**
> I checked and the boot flag was set.  It looks like I may be making a run to target to try a different reader.  I'll let you know how I make out.
 - flub
I just checked on my OHM SDHC Card reader that it will still show up on the boot device selection screen without an SD card in it... it's got to be your reader.

Good luck Flub.

---

### Post by flubbard on 2009-03-16
It works!  Thank you for your help...in the end here is what I found:
I bought a new SanDisk memory SDHC reader (I couldn't find the one that you mentioned at Target) and was able to boot off the SDHC card as expected, though I did end up having to reinstall the instance on the SD card which makes me wonder if there were some other issues with the first reader.

Also, the directions did not quite work for me, and would like your input if possible.  I formatted the thumb drive as ext2 and installed grub onto the device.  Then I copied over the initramd and the vmlinuz files.  Grub would load but gave me the error file not found.  In the end, if I eliminate the UUID line from the menu.lst that refers to the USB drive, it works.  I still refer to the SD card by UUID, but I think it automatically is assuming that the ram file should be the one on the boot device.  Is this correct, or will I wind up with other problems.

In the end, I am doing exactly what the original post talked about, but using a USB stick to jump start the process instead of the internal HD.  The nice thing is that the original Windows XP install has not been touched (including the boot sector on the drive).

Thanks again for the help.
  - flub

---

### Post by superJoel on 2009-03-16
> **flubbard said:**
> It works!  Thank you for your help...in the end here is what I found:
I bought a new SanDisk memory SDHC reader (I couldn't find the one that you mentioned at Target) and was able to boot off the SDHC card as expected, though I did end up having to reinstall the instance on the SD card which makes me wonder if there were some other issues with the first reader.

Also, the directions did not quite work for me, and would like your input if possible.  I formatted the thumb drive as ext2 and installed grub onto the device.  Then I copied over the initramd and the vmlinuz files.  Grub would load but gave me the error file not found.  In the end, if I eliminate the UUID line from the menu.lst that refers to the USB drive, it works.  I still refer to the SD card by UUID, but I think it automatically is assuming that the ram file should be the one on the boot device.  Is this correct, or will I wind up with other problems.

In the end, I am doing exactly what the original post talked about, but using a USB stick to jump start the process instead of the internal HD.  The nice thing is that the original Windows XP install has not been touched (including the boot sector on the drive).

Thanks again for the help.
  - flubYes this should be how it works. It will initially boot off your USB, but then go over and run off your SD card (now you should be able to startup without the SD card being in your USB reader... right?) in the left or right card reader.

---

### Post by flubbard on 2009-03-16
That is correct.  I have the SD card directly in the Storage Expansion slot on the left side.  This way it is most protected.  The whole goal was to avoid having the large USB stick exposed.

I can remove the USB thumb drive once I boot, otherwise it just shows as an additional mounted device.  Thanks again for the help.  I hope this might help someone else trying a similar thing.  By the way, during the process contaced Acer and it doesn't look like they have any intention of adding the ability to boot from SD card to their BIOS for now...oh well.

  - flub

---

### Post by superJoel on 2009-03-16
good stuff flub.  I'm glad you finally got it working.

---

### Post by nickblame on 2009-06-14
first of all nice thread!

well my experience with aspire one the one with the laggy 8gb ssd has been really bad. I tested windows on that and it was awefull. the shipped os is not for me either. then I saw the ubuntu netbook remix and ever since I am completely satisfied with what I can do with my netbook.

although the stupid internal ssd is really bad hardware and it breaks every now and then ruining my filesystem. I have to get into repair mode or wait for half an hour to get the os running again. so it would be great to have the os on the sd card. I think I can manage that with the helpful info in this thread one question though:

in terms of speed and os response times is it better to have the os on the sd?? do i have to get a super fast sd?

---

### Post by flubbard on 2009-06-15
I am finding that the sd card is slower than the internal drive by about a factor of 6 (when doing hdparm I get about 11.01 MB/sec out of the SD card and 62.88 MB/sec out of the internal platter drive).  I would expect the difference to be even greater with a solid state drive internal.  

That being said, I had a couple of reasons for trying to do what I did.  First, was to try to cut down somewhat on power consumption as this way I do not need to spin up the internal drive.  I believe this is helping, though I haven't really tried to quantify it.  Also, I have been able to keep the two os's completely seperate, without the need for a boot loader.  Granted, that is at the price of needing to have my "key" handy to boot from Linux.  It's small enough though that I normally have it with me if I have the computer.

Hope this helps - flub

---

### Post by SMIAN on 2009-06-19
Hello,

I am following your indications but I can not boot finally from the SD card. I am using the last Ubuntu Release 9.04 running inside an USB SD card reader. The system is an Intel Atom Embedded. 

I try to to the step: 

*"Copy your new initramfs file and your vmlinuz file from the SDHC's boot directory over to your SSD drive's /boot directory and finish up with the rest of his guide to edit your grub."*

The problem here is that I am running only over the USB SD reader, so I do not have any installation on the SSD. The second problem is that my knowledge about Linux, are not very deep and I can not find the UUID of the SD device.

Could you let me know how can I do it?

---

### Post by flubbard on 2009-06-19
The way that I did it was to first boot from the SD card through the card reader, which is what it sounds like you are doing now.  You will need a small pen drive to start the boot process when you want to boot from the internal SD reader (left side of aspire one).

If you are using a sd card in your usb reader, you have the installation on the SD card, even though you are not reading it through the slot.  Eventually, you should be able to take the card out of the usb reader and install run it out of the internal card reader.

As for getting the uuid of the card (you can do this through the usb reader), type

```

$ ls -l /dev/disk/by-uuid

```

You will see the UUID listed right before the '->'

Hope this helps - flub

---

### Post by SMIAN on 2009-06-19
I have read the UUID of my SDHC card and it is the same (I sould know it) as the USB SD Card reader. So apparently there is no reason becouse it does not work.

In fact, I am only able of booting when the SD card is plugged to the USB SD reader. If I pug the SD in the slot in my embbeded module (I do not use Acer), Linux does not work but the XP installed on my SATA hard dist is not able of starting neither.

The resutl of every try is:


[I]Grub Loading stage1.5.

 Grub Loading, please wait
Error 21

-[/I]

---

### Post by flubbard on 2009-06-19
The UUID of the sd card when placed in the reader will be the same as the SD card when not in the reader...this is true.  In order to boot from the SD card, however, you will need to install the bootloader (probably GRUB) on a second pen drive, which would otherwise have a different UUID.  Becuase there will be no mount point or any other way to identify that Linux should boot from the SD card rather than the usb pen drive, you will need to put, on the pen drive, the UUID of the SD card in the side slot as the source of the root directory.  

It's a little confusing process.

---

### Post by flubbard on 2009-06-19
I've posted some information on my experience at 

[http://www.barryhubbard.com/article.html?display=60-booting-acer-aspire-one-from-sd-card](http://www.barryhubbard.com/article.html?display=60-booting-acer-aspire-one-from-sd-card)

A lot of it is from the other howto already referenced on the site.

---

### Post by ostaja on 2009-06-20
> **flubbard said:**
> I've posted some information on my experience at 

[http://www.barryhubbard.com/article.html?display=60-booting-acer-aspire-one-from-sd-card](http://www.barryhubbard.com/article.html?display=60-booting-acer-aspire-one-from-sd-card)

A lot of it is from the other howto already referenced on the site.

Thx, nice guide. Can you clarify those steps into commands? A lot linux newbs does not know how to do those steps : ).

"
1.Partition the drive as a Linux drive using fdisk (ext2)
2.Mark the partition as bootable
3.Write the partition table
4.Unmount the drive
5.Make the file system using      # mke2fs -v /dev/sdc1 (substitute in the appropriate device)
6.Mount the new drive
7.Change directory to the new drive
"


Btw, how i need to do it when i want Ubuntu into SDHC, and **grub** + XP into 8gb SSD (acer aspire one A110). So i can always choose which one i need to boot, Ubuntu from SDHC or XP from SDD. Basically i need to resize XP partition (fat32) and do new partition to /boot (what size partition?) and follow [this]("http://http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_On%20e") quide?

---

### Post by flubbard on 2009-06-21
I have added some additional information on using fdisk to accomplish this at 
[www.barryhubbard.com/article.html?display=68-using-fdisk-to-partition-a-pen-drive-with-the-acer-aspire-one](www.barryhubbard.com/article.html?display=68-using-fdisk-to-partition-a-pen-drive-with-the-acer-aspire-one)

Also, if using the internal ssd on the aspire one, you should have a little easier time of it.  First, you will need to use a utility such as partition magic, or I'm sure there are other utilities availble to resize the partitions on your drive.  I would allow at least 2GB for the Linux partition.

Then use either the install CD installed on a pen drive, or the DVD through an external reader to install Linux onto the harddrive (together with Grub).  Let me know if you would like more detailed information.

 - flub

---

### Post by ostaja on 2009-06-21
I can resize XP partition with gparted, have done it few times earlier.

I just wonder, you said i need 2gb partition to ssd(?) for linux. But i need just very tiny partition for grub, maybe 20mb ext2/3, not install whole linux? (This computer /boot folder is about 14mb)

In big picture, my point was having:

8 gb SSD (sda) which include XP and grub. And grub need only tiny 20mb(?) partition from SSD, rest is for XP.
8 gb SDHC (mmc) which is devoted only for ubuntu.

So lets say, i have 20mb ext2/3 partition on SSD, so grub install command would look like this:

 #grub-install --o-floppy --root-directory=./dev/**sda2**
when **sda1** is XP partition.

Hopefully you understand now : ).

---

### Post by flubbard on 2009-06-21
I think I understand now.  My experience has been to normally install grub in the master boot record on the boot disk (/dev/sda) from the installation cd.  You are correct in saying that very little room is necessary for grub, however sometimes you will need a little more space for the initram disk which must contain the drivers for the memory card reader which otherwise will not be viewable to grub.  If they aren't viewable, then you won't be able to launch Linux.

As for the size of the image, mine is under 50MB, but you will need to have grub itself installed into the MBR (boot sector) on your primary drive to get it to launch and give you the menu.

Good Luck - flub

---

### Post by Nightwalker13 on 2009-08-22
Was wondering, do you think its possible to set up some kindov grub using the the D2D recovery partition (alt+f10 combo) with sdhc booting, so you can just put the card in, hold alt+f10?

---

### Post by flubbard on 2009-08-24
I would think that you could install grub to the harddrive in the MBR.  I would think that you could do this without destrying the recovery partition, but haven't tried it so wouldn't say for sure.  In my case, I was specifically trying not to alter the harddrive.  Part of this is becuase we have two of these at our office, and now I can grab either one as long as I have my key and the SD card.  

  - flub

---

### Post by prattmd on 2009-08-25
Ok, I am still having some troubles.  
Here are my steps so far:

Starting a live USB

Formatting the SD card in a USB card reader as EXT2 with boot flagged

Installing to the SD card with grub placed onto the SD card

When I restart and select F12, my USB SD card reader is not there.

Any ideas?

It is like it is not recognizing it as bootable...

Any ideas?

---

### Post by flubbard on 2009-08-25
I would expect that you will need to install Grub to the hard drive, not the SD card.  In my case, I have Grub installed on a USB flash drive since that is also bootable on the Aspire One.  The BIOS, as of the last time I checked with Acer, doesn't support booting from the SD card and there were no plans to make that available.

Are you trying to use the boot loader that came with the computer.  Otherwise, you could probably install grub on the hard drive, then include both the Windows XP partition and the recovery partition as optional boot devices.  I believe that the recovery partition is actually a seperate partition on the primary drive.

Hope this helps.

  - flub

---

### Post by prattmd on 2009-08-25
I have grub on the hard drive

I cannot boot from the USB SD adapter at the F12 prompt, it does not show up

---

### Post by flubbard on 2009-08-26
If you do not push F12, does the grub menu come up on normal boot?

  - flub

---

### Post by teh603 on 2009-08-26
I believe the issue is the computer not having some key piece of ROM firmware to make the SD readers accessable on startup. At least that's what its starting to sound like- and believe me, it won't be the first massive bug in the AAO ROMs.

*glares at the x.org screen brightness reporting bug*

---

### Post by aladi on 2009-08-27
HI Flub,
 With your instructions, I will be able to  boot to SDHC  from the  GRUB loader in the HDD.  My BIOS is able to boot to the SD Card.   My BIOS will treat this as a  HDD 0x80 ( sda) when we boot.  I would like to know how to configure the GRUB to boot from SD card directly. 

Thanks
Siva:guitar:

---

### Post by flubbard on 2009-08-27
> **teh603 said:**
> I believe the issue is the computer not having some key piece of ROM firmware to make the SD readers accessable on startup. At least that's what its starting to sound like- and believe me, it won't be the first massive bug in the AAO ROMs.

*glares at the x.org screen brightness reporting bug*
I think this is correct.  In addition to having grub, you will probably at least need the intraramfs with the sd card capabilities on the boot drive.

---

### Post by aladi on 2009-09-01
HI Flub, 
 In  the latest   Ubuntu 9.10 Alpha 4 ,  We dont need to  use the USB card reader to install.  You can insert in the sd card slot itself.

Thanks
Siva

---

### Post by teh603 on 2009-09-02
> **aladi said:**
> HI Flub, 
 In  the latest   Ubuntu 9.10 Alpha 4 ,  We dont need to  use the USB card reader to install.  You can insert in the sd card slot itself.

Has this been tested on all ROM revisions of AAO?

---

### Post by flubbard on 2009-09-03
I thought that this was more of a BIOS issue, not a ubuntu issue.  Are you using a different version of the BIOS?

---

### Post by *g!t5^_)*(H on 2009-10-24
> The only trick required is to put the following modules into initrd.img that is in /boot:

* mmc_block
* sdhci
* sdhci-pci

grub (and the kernel it boots) can then find the sdhc device contains the root directory

Does anybody know how to perform this with Grub2? In only one week Karmic will be out and I want to find the solution asap :s

Thanks in advance

---

### Post by *g!t5^_)*(H on 2009-10-25
At last I found a solution ... :P

> 
A. Install Ubuntu with :

148 MB partition on SSD (internal disk) as /boot
The rest of SSD as /media/extra (I will use as an extra unit to save documents, can contain another OS if you like)

750 MB partition on SDHC card as <swap> (Not sure if necessary but it works very well)
The rest of SDHC card as /

B. When Ubuntu installation is done, open a terminal (Applications>Accessories>Terminal) and:

1. Type: sudo gedit /etc/initramfs-tools/modules
2. Add the following lines at the end of the file:

mmc_core
mmc_block
sdhci
sdhci-pci

3. Save the file.

4. Type: sudo /usr/sbin/update-initramfs.distrib -u

5. Mount the SSD (boot) unit clicking at Places>148 MB Filesystem
6. Mount SD HC unit clicking at Places>(Unit size, in my case 7.4 GB Filesystem)

7. Copy the file into de boot folder from SSD:

sudo cp /boot/initrd.img-* /media/X (X is the SSD folder, can be a very long name like: ad73823737a-3923f98-k09sd8f798sd)

8. Add the following lines at the end of the file (/etc/initramfs-tools/modules) from the SD HC card:

sudo gedit /media/Y/etc/initramfs-tools/modules (Y is the SD HC folder, can be a very long name like: daba2355f-3454...)

mmc_core
mmc_block
sdhci
sdhci-pci

9. Save the file.

10. Restart the computer and remove the USB live Ubuntu it will boot Ubuntu installed at SD HC card (In my case there's a message error at GRUB2, but it still works after some seconds)

I don't know if it's necessary, but when Ubuntu is running again (its first run from SD HC) you can run: sudo /sbin/update-initramfs.distrib -u


Using one SDHC 30Mb/s R/W card, "Acer Aspire One" works very well (in fact is usable, it wasn't with the SSD internal drive). :D:D

---

### Post by sjpn on 2009-11-05
Hi,
Just wondering if anyone has been able to do this with WinXP on the SDHC. There are rare occassions where vmware or wine just doesn't cut it.
Thanks

---

### Post by flubbard on 2009-11-06
Do you mean running Windows XP from the SD card?  I'd have to think about that a little.  I would wonder about hardware / licensing issues when it comes to XP.  It looks like there are at least a couple of threads out there for booting XP from a pen drive which would be a good place to start.  What primary OS would you have on the HD?

  - flub

---

### Post by jorlando on 2011-04-30
The method still working for newer Acer Aspire Ones without the the left side SDHC reader.

I am using a AAO D255 with an ENE SDHC card reader.

The difference is that the /etc/initramfs-tools/module file must include a line for the keucr module.

This module is experimental. In Ubuntu 11.04 the module that comes with the instalation works ok.

version 10.10 and older need a recompiled version. Detailled instructions how to compile the keucr module here:

[http://community.linuxmint.com/tutorial/view/309](http://community.linuxmint.com/tutorial/view/309)

You'll need to reboot after generating the initrd module with the keucr module.

---

### Post by onely_ck on 2011-07-09
Recently installed the latest version of ubuntu on SDCARD and managed to boot from SDCARD expansion slot with the use of USB key as followed in the instructions above.
A snag came when Ubuntu was using grub2. Found out that if you keep the grub.cfg file simple it works the same. e.g.:

set timeout=10
set default=0

menuentry 'Ubuntu_on_SDCARD' --class Ubuntu*os --class gnu-linux --class gnu --class os {
	echo	'Loading Kernel'
	linux	/boot/vmlinuz-xxxxxxx root=UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx ro   quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-xxxxxxxx
}

That's it. I know that alot of manuals and guides say do not manually edit the grub.cfg, but this is such a small change it shouldn't matter.

Hope this helps anyone trying to achieve this a couple of years on from the start of this post.

---

### Post by Neva on 2011-07-16
Nice entries for fixing the SD card reader for different versions of Ubuntu here:

[https://help.ubuntu.com/community/AspireOne/AOA150](https://help.ubuntu.com/community/AspireOne/AOA150)

---

### Post by squashpup on 2011-07-27
Keep in mind, it doesn't technically boot from the SD card, but that's where most of the operating system is. 

First, I made a live USB key of Lubuntu 11.04.

Booted it in my Aspire, and opened Gparted.

Zapped the internal SSD, and partitioned it 1 GB EXT2 (sda1) / 15 GB EXT2 (sda2).  Set the 1GB partition with a bootable flag.

Stuck an SD card in the left drive and formatted it EXT2.

Started the installer.  When I got to the part where it offered to erase the disk and install Ubuntu, I chose Something Else.

Opened the manual partitioner.  

Clicked on the 1GB partition (sda1).  Selected "Use as /boot"

Clicked on the 15 GB partition (sda2). Selected "Use as /home"

Clicked on the SD Card (mmcblk0). Selected "Use as /"

At the bottom, chose to install the bootloader to sda(1)

No swap.  It will complain about this, but just click continue. 

Let the installation finish.  

Reboot without the USB key. Mine throws an error message about a partition not being found, but it boots just fine. 

Runs MUCH faster and smoother.  Even Firefox, which was horrible on the old SSD, is finally usable. 

BIOS screen to login takes 17 seconds. After you log in, the desktop comes up instantly (remember, this is with Lubuntu). 

Firefox opens in about 3 seconds.  Chrome opens nearly instantly.  Both run very smoothly.  Occasionally, you get a very slight delay in Firefox, but nothing that's really even annoying.

For the loss of one SD card slot and about $20 (the price of an 8 GB card...more than enough space for the operating system), you get a total of 24 GB of space, a 15 GB home partition, reduced SSD wear, increased speed, and the ability to replace or upgrade your OS drive in a few seconds without tearing the Aspire apart.  In the years that I've owned it, there was never one occasion where I used both SD slots anyway.

Popped the card out and checked it in my laptop...barely used up 2 GB of space.  

If I don't run into problems, this is a pretty cheap and easy way to improve the performance of the Aspire 110. It would probably work on other computers, too.

---

### Post by squashpup on 2011-07-28
This setup breaks suspend.

I left the netbook on overnight, and when I got up this morning, it was at what I call "the gibberish screen", where it says.

Starting NTP server....
Starting Bluetooth...

And it was unresponsive.

I shut it off and rebooted and everything still works as it should.  So, I tried to manually suspend with the same result. 

I'm going to have to disable suspend in the power management.

Which means, lots of booting and shutting down. 

Oh well.  It boots and shuts down quicker anyway.  If it becomes annoying, I can always go back to putting the OS on the SSD...

The Aspire has always been about tradeoffs, anyway!

---

### Post by t.h.w. on 2012-05-15
Hi all,

I have a Acer Aspire One (AAO for short) too, a D250 (...DK I think)

It was shipped with Windows Home Edition, so with booting from a Ubuntu-on-a-stick and using Gparted I have resized the partions to fit Ubuntu 10.04LTS Netbook remix next to it, dual-boot.

I now want it to use it as a XBMC-station also:popcorn:. So I did the next:
- Made with my other Ubuntu-laptop a XBMCbuntu-stick from the CD-iso, and booted the AAO with that. Works fine. Shut down.
- Next I inserted a 8GB SD-card in the cardreader on the right and booted from the XBMCbuntu-stick again. 
- Installed XBMCbuntu on the SD-card, it suggested to put a bootloader on it, yes please. After install shutdown and remove the XBMCbuntu-stick.
- Boot into bios: Make the SD-card primary bootdisc and presto!:guitar: Booting from SD-card into XBMC!

I have now the following system:
- On SD: XBMCbuntu
After shutdown I only have to remove the SD-card before booting to get the old grub with the dual-boot from the HDD:
- On HDD: Dual boot Windows XP and Ubuntu

The bios installed on my AAO is from 'Insyde H2O' and sees the SD-card as a usb-drive. 
I think it depends on your type of AAO if it is internally connected as usb or pci (see earlier posts and [http://www.overclockers.com/forums/showthread.php?t=592546](http://www.overclockers.com/forums/showthread.php?t=592546))

Cheers!:p

---

### Post by oldos2er on 2012-05-15
Old thread closed.

---

