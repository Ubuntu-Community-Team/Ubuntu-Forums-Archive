---
title: "[SOLVED] Installing Ubuntu 7.04 on an Older Machine - p3/p2"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by Om1977 on 2007-08-16
I have gone through a lot of tough times trying to load the Ubuntu 7.04 on a P3 computer (laptop) .. and have been through most of the threads trying to gather information on a few things .. I had a lot of help from Logos and Confused .. but in entirity .. the problem as I see it from other threads as well is the fact that system BIOS for older machines are what need to be upgraded

I know that Vista has free (lol) drivers available to help you upgrade your system Bios but can find nothing in Linux .. there is one software available on linuxsoft.cz which can just copy an image and help upgraqde the BIOS but is meant only for people who can write scripts, not the uneducated types, such as myself.

Request everyone to please help in anyway that they can to point us in the right direction.

Thanks ion advance.

OM

---

### Post by jnorthr on 2007-08-16
It can really be a tricky business. Do you have a real need to upgrade your bios ? If ur machine works ok on windose, why bother ? You can possibly cause more harm than good if you attempt to burn a bios update and it fails, as you can then bin the machine or buy a brand new motherboard. Suggest you leave it alone. I had the same choice on my old laptop and decided not to chance it, even less so if you are not confident of doing it right.

---

### Post by Om1977 on 2007-08-16
I have seen the upgrade working on windows and it works fine all you have to be sure of is not to interfear with the machine while it is upgrading the BIOS .. which is about a 1 hour job .. my problem began with the fact that I have no primary drive and do not have the funds to buy a new laptop HD and a friend of mine was good enough to part with his USB HD .. which I have problems with owing to my BIOS as it is too old to have a "Boot from USB" feature .. hence the want to upgrade the BIOS

windows is not something I am very confident about .. though I work on it at work and all the other places that require a computer .. what I am looking for is a driver that can update the BIOS without any operating system being installed or requiring a HD to be installed .. is it possible or am I hoping for too much here?

I think that it should be possible .

OM

---

### Post by jnorthr on 2007-08-16
What you suggest sure sounds possible. You will need to get the bios upgrade on a floppy, if thats what you have. You can run it from there. You will not need a hard-drive installed just to  upgrade. Do you know the manufacturer of your bios and possibly the version of it ?

om namah shivaya

---

### Post by Om1977 on 2007-08-16
I have a dvd drive and the laptop details are as below:

Laptop - Toshiba Tecra 8100
Processor - p3 700 MHz
BIOS Version 2.04

Appreciate your help.

OM

Om Namo Vighanarajaya

---

### Post by logos34 on 2007-08-16
There's nothing to indicate you can add usb boot support by flashing the bios (v.2.50):

[http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlViewDL.jsp?soid=356848&moid=1073769806&rpn=PT810U&BV_SessionID=@@@@0241500640.1187291549@@@@&BV_EngineID=ccciaddljkdggkecgfkceghdgngdgmm.0&ct=DL&all_docs=false](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlViewDL.jsp?soid=356848&moid=1073769806&rpn=PT810U&BV_SessionID=@@@@0241500640.1187291549@@@@&BV_EngineID=ccciaddljkdggkecgfkceghdgngdgmm.0&ct=DL&all_docs=false)

Have you tried Confused57's suggestion in the other thread--using SuperGrub to boot the usb external drive?

If that doesn't work, the only other workaround I can think of would be to use SmartBootManager (SBM).

---

### Post by Om1977 on 2007-08-16
Well Logos tried that but it dosen't work .. I have to have the live cd in the drive and probably will work with a second CD drive so that Linux can intrepret the files and then use the live cd to run the program .. same will be the case I guess with the SBM .. I might just be acting a little too dum but .. in a real fix here 

Sorry for all the trouble.

OM

---

### Post by Om1977 on 2007-08-16
I checked out the smart boot manager on Linuxsoft.cz .. seems to be capable of resolving my issue .. but cant get into it's home page ..

Question:  Can I run this off a flopy or a CD RW - (to triger Grub to load off my USB) 

Please advise.

OM

---

### Post by logos34 on 2007-08-16
What about a SBM floppy?  you have a floppy drive, right?

---

### Post by Om1977 on 2007-08-16
Yes Logos .. do have a floppy drive .. but If I have been given to understand correctly SBM floppy will have to be written "RAW" using rawrite1 or rawrite2 on dos using another system .. which i am not too well versed with .. 

Thank you once again Logos.. really appreciate your help.

OM

---

### Post by logos34 on 2007-08-16
Here's one howto (but for windows):
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

Or do it in linux from the live cd  using 'dd':

Copy 'sbm.bin' (~1.4MB) file from /install directory on ubuntu CD to formatted floppy diskette:

**sudo mkfs.msdos /dev/fd0**    (*)
[B]cd /install
sudo dd if=sbm.bin of=/dev/fd0[/B]

*you may need mtools for this command; alternatively try '**mke2fs**' (edit: or maybe your must use dos for sbm to work, not sure)

You'll then have to install grub tot he mbr of the usb drive:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

basically:
[B]sudo grub
root (hd0,y)[/B]  -->for y substitute your root partition #
[B]setup (hd0)
quit[/B]

Edit: sorry, I'm always a few minutes behind your last post (I need to use the refresh button more often!)

---

### Post by Om1977 on 2007-08-16
Logos, thank you for the code .. please have a look at this link .. think this should suffice not sure though .. please advise.. [http://www.chrysocome.net/rawwrite](http://www.chrysocome.net/rawwrite)

Warm Regards,

OM

---

### Post by logos34 on 2007-08-16
> **Om1977 said:**
> Logos, thank you for the code .. please have a look at this link .. think this should suffice not sure though .. please advise.. [http://www.chrysocome.net/rawwrite](http://www.chrysocome.net/rawwrite)

Warm Regards,

OM

Yeah, I believe that's the one.  But you can do it more easily in linux from your live cd.  I just went through it to doublecheck (small path correction--see below).

Using ubuntu live cd:

> sudo mkfs.msdos /dev/fd0
cd /**cdrom**/install
sudo dd if=sbm.bin of=/dev/fd0

Then install grub per instructions above.  Set your bios to boot first from floppy and with some luck it might work.

---

### Post by Om1977 on 2007-08-16
Thank you Logos .. and yes you are right it *IS EASIER *in Linux, :) LOL.. a little excited right now .. but really appreciate the help Logos .. will try it out once I get home and drop you a message tomorrow if it works :)

Thanks again. 

Warm Regards,

OM

---

### Post by logos34 on 2007-08-16
> **Om1977 said:**
> Thank you Logos .. and yes you are right it *IS EASIER *in Linux, :) LOL.. a little excited right now .. but really appreciate the help Logos .. will try it out once I get home and drop you a message tomorrow if it works :)

Thanks again. 

Warm Regards,

OM


Ok, I was just googling around reading snippits on SBM here and there, and it appears that it may not support booting USB devices...I knew about it not being able to boot usb-cdrom drives but I thought it would work with usb external hard disks...It claims to be able to 'automatically search out all of the floppy/hard drives and partitions that could be booted' and boot 'other OSes from the primary partition on ANY hard disk, not only the first HD'. but I guess they mean just internal (or non-usb) hard disks...Sorry to disappoint you--I thought this just might work.  But try it anyway.
([http://btmgr.sourceforge.net/docs/user-guide-1.html](http://btmgr.sourceforge.net/docs/user-guide-1.html))

---

### Post by Om1977 on 2007-08-16
will give it a try .. my spirits are still up .. I have some kind of a chance there rather than nothing at all .. will share with you what happend today .. if nothing else at least I learnt a little .. Cheers

Warm Regards,

OM

---

### Post by Om1977 on 2007-08-17
Tried the SBM but as you said it dosent work, guess I'll just have to get myself a new machine.. Thanks for your help Logos :)

---

### Post by logos34 on 2007-08-17
Just as I feared.  I totally feel your pain.

Give this howto a try:
[https://help.ubuntu.com/community/BootFromUSB?highlight=%28usb%29](https://help.ubuntu.com/community/BootFromUSB?highlight=%28usb%29)

(-->"Booting the kernel from a bootable CD")

---

### Post by Om1977 on 2007-08-17
You come to my rescue again .. appreciate this really .. been worried all night about my budget :) .. I am going to give this a try over the weekend and drop you a message on monday to let you know if this works .. I believe (with the little reading that I have done) that it will .. Really appreciate your help here Logos.

Warm Regards,

---

### Post by logos34 on 2007-08-17
> **Om1977 said:**
> You come to my rescue again .. appreciate this really .. been worried all night about my budget :) .. I am going to give this a try over the weekend and drop you a message on monday to let you know if this works .. I believe (with the little reading that I have done) that it will .. Really appreciate your help here Logos.

Warm Regards,

Yeah, I just carefully re-read through the [B]Booting the kernel from a bootable CD
[/B] section and it looks pretty straightforward--seems to be your best chance of getting this setup to work.  Basically you'll be working from the Ubuntu Live CD to create /reconfigure a new intitial ramdisk image to include the USB modules the kernel needs to boot usb devices.  Then you take the new initrd.img and vmlinuz for your kernel version (plus menu.lst) and basically make a customized, USB-capable Gnu Grub bootcd.  You make the .iso, save it to your /home/user (or /) directory on the usb hard disk (or flash drive if you have one), then take it to another machine and burn it to CD.

Look forward to your reponse.  good luck

---

### Post by Om1977 on 2007-08-17
Hi Logos, 
sorry for the trouble but another small issue, trying to run pseudo chroot command to mount-A to allow rebuild of iniprd by reconfiguring linux kernel. I am getting an unexpected error message "chroot: cannot run command ' /bin/bash' : permission denied"   Hope you can help me with this.

Warm regards,

---

### Post by logos34 on 2007-08-17
> **Om1977 said:**
> Hi Logos, 
sorry for the trouble but another small issue, trying to run pseudo chroot command to mount-A to allow rebuild of iniprd by reconfiguring linux kernel. I am getting an unexpected error message "chroot: cannot run command ' /bin/bash' : permission denied"   Hope you can help me with this.

Warm regards,

Post EXACTLY what you entered in the terminal (there's more typos in your last post than I can shake a stick at)

---

### Post by logos34 on 2007-08-17
By the way those are 3 separate commands you type, then hit ENTER key after each one:
> [B]
sudo mount --bind /dev /wherever_you_have_mounted_your_system/dev[/B]

then,
**sudo chroot /wherever_you_have_mounted_your_system**

and finally,
**mount -a**

---

### Post by Om1977 on 2007-08-17
hi logos, forgive the typos ... had a friend post that message for me .. the second command is what gives me the error mesage "chroot: cannot run command ' /bin/bash' : permission denied" cant go beyond that .. seems that sudo function is not enugh to carry out a "su" level command for the "chroot" comand line .. forgive my illitracy here ..

hope you can help

warm regards,

---

### Post by logos34 on 2007-08-18
> **Om1977 said:**
> hi logos, forgive the typos ... had a friend post that message for me .. the second command is what gives me the error mesage "chroot: cannot run command ' /bin/bash' : permission denied" cant go beyond that .. seems that sudo function is not enugh to carry out a "su" level command for the "chroot" comand line .. forgive my illitracy here ..

hope you can help

warm regards,

You need to mount your root partition with root admin priviledges--which won't happen if you just double-click on it in nautilus and it mounts as 'disk'.  So boot back into the live cd and mount root like this:
> 
**sudo mkdir /media/sda1**  (if your root partition is sda2 use that)

**sudo mount -t ext3 /dev/sda1 /media/sda1**

Then, 
> [B]
sudo mount --bind /dev /media/sda1/dev

sudo chroot /media/sda1[/B]

The following prompt should then appear:

**[COLOR="Blue"]root@ubuntu:/#[/COLOR]**

---

### Post by Om1977 on 2007-08-18
thanx logos for the help. I will try this out and will let you know by monday. Appreciate the help pnce again.

Warm regards,

---

### Post by jnorthr on 2007-08-19
Hi OM -
Anything new to report on this one ? Sounds like it SHOULD work booting from a floppy , as it almost seems like you are trying to run a 'diskless' machine meaning no internal hard drives.

---

### Post by Om1977 on 2007-08-20
Hello Jnorthr / Logos, 

Yea am running a "diskless" machine, I have been able to go upto the command set described below but am unfortunately clueless after that

cp /wherever_your_system_is_mounted/boot/initrd.img-<kernelversion> ~
cp /wherever_your_system_is_mounted/boot/vmlinuz-<kernelversion> ~
cp /wherever_your_system_is_mounted/boot/grub/menu.lst ~

Apologize for getting back to you a little late but had system issues at work as well :)

Really appreciate your guidance Logos.

Cheers

---

### Post by logos34 on 2007-08-20
ok, let me get the exact commands for you...

---

### Post by logos34 on 2007-08-20
[EDIT: I changed '/media/disk' to '/media/sda1' -- I forgot you have to manually mount to /media/sda1.  Also I forgot some sudos.  Also use /media/sda1/home/<user> format (of course substitute your username for '<user>')]

Here you go (hope I caught any typos).

Assuming you are mounting your root partition to /media/**sda1**, not default /media/disk (because of chroot issue above), and you're using the -15-generic (vs. -15-386) kernel: 
> 
cp /media/sda1/boot/initrd.img-2.6.20-15-generic ~
cp /media/sda1/boot/vmlinuz-2.6.20-15-generic ~
cp /media/sda1/boot/grub/menu.lst ~

> sudo mkdir bootcd
sudo mkdir bootcd/boot
sudo mkdir bootcd/boot/grub

> cp /media/sda1/usr/lib/grub/i386-pc/stage2_eltorito bootcd/boot/grub
cp /media/sda1/boot/grub/menu.lst bootcd/boot/grub
cp /media/sda1/boot/initrd.img-2.6.20-15-generic bootcd/boot
cp /media/sda1/boot/vmlinuz-2.6.20-15-generic bootcd/boot

> cd bootcd/boot/
mv initrd.img-2.6.20-15-generic initrd.img
mv vmlinuz-2.6.20-15-generic vmlinuz
cd 

**gedit bootcd/boot/grub/menu.lst**

Take out everything in the 'automagic' kernels section and paste the following:

> ## ## End Default Options ##

title          Ubuntu
root           (cd)
kernel         /boot/vmlinuz root=/dev/sda1 ro quiet splash
initrd         /boot/initrd.img
boot

title          Ubuntu Recovery Mode
root           (cd)
kernel         /boot/vmlinuz root=/dev/sda1 ro single
initrd         /boot/initrd.img
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

*Look for the 'default' and 'timeout' lines near the top of menu.lst and make sure they're set for 0 and 10, respectively:

[B]default  0

timeout  10[/B]

Now create the .iso:
> 
sudo mkisofs -R -b /boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o UbuntuBootCDForUSB.iso bootcd

Then save everything to the USB disk /home/<user> directory.

> sudo cp UbuntuBootCDForUSB.iso /media/sda1/home/<user>
sudo cp -r bootcd /media/sda1/home/<user>

Take the USB disk to another machine and burn the iso to a CD

[edited]

---

### Post by Om1977 on 2007-08-20
Hello Logos,

Will complete this tonight, have had my machine running since saturday morning, waiting.

Really appreciate your help .. will let you know what happened tomorrow.

Cheers,

---

### Post by Om1977 on 2007-08-21
Hi Logos,

This is going to sound really dumb, I have the iso and have it burnt .. before you gave me the "cp" comand lines .. i had run them using "sdb9" as the new destination dir .. I thought i had to specify a new dir or create a new dir for that matter .. now of the 160 gb hard disk I can read only 142 gb and the rest is not visible either in windows or Ubuntu .. any suggestions .. I am thinking of reinstalling .. but dont think that will work.

Please advise.

warm regards,

---

### Post by logos34 on 2007-08-21
> **Om1977 said:**
> Hi Logos,

This is going to sound really dumb, I have the iso and have it burnt .. before you gave me the "cp" comand lines .. i had run them using "sdb9" as the new destination dir .. I thought i had to specify a new dir or create a new dir for that matter .. now of the 160 gb hard disk I can read only 142 gb and the rest is not visible either in windows or Ubuntu .. any suggestions .. I am thinking of reinstalling .. but dont think that will work.

Please advise.

warm regards,

Not sure I understand the first part of your question.  Please clarify. 

As far as the drive space is concerned, a '160 GB' drive (where '1 GB = 1,000,000,000 bytes') is smaller as seen by any OS, in which 1 GB = 1,073,741,824 bytes.  So a typical 160 GB drive is actually ~149 GB.  Minus any installed OS and files, that sounds about right.  Right?

---

### Post by Om1977 on 2007-08-21
definately buy your point but guss it's something to do with the way the UBuntu live cd intrepreted the space at the time of installation because it very specifically read as 160 gb now it reads as 142 gb in totality .. that is why the confusion that i am in .. 

warm regards,

---

### Post by logos34 on 2007-08-21
not sure...Maybe there's unallocated space somewhere.  Post a screenshot of how Gparted sees it.

And/or post the output of any of these: 

[B]sudo lshw -C disk

df -h[/B]

---

### Post by Om1977 on 2007-08-22
> **logos34 said:**
> not sure...Maybe there's unallocated space somewhere.  Post a screenshot of how Gparted sees it.

And/or post the output of any of these: 

[B]sudo lshw -C disk

df -h[/B]

Hello Logos,

Will try that command set .. I have good news .. the machine is booting .. really appreciate all your help my friend .. Bless you .. 

Cheers.

Warm Regards,

---

### Post by logos34 on 2007-08-22
> **Om1977 said:**
> Hello Logos,

Will try that command set .. I have good news .. the machine is booting .. really appreciate all your help my friend .. Bless you .. 

Cheers.

Warm Regards,

heyhey!  that's great...so the usb-modified grub boot cd works as advertised...fill me in some more on how it's working

---

### Post by Om1977 on 2007-08-22
will let you know tomorrow Logos .. Cheers to everyone and to you specially .. (owe you a beer my friend) :)

I didn't have time to test it much but everything seemed fine .. will work on the machine some more tonight and let you know of anything abnormal.

Thanks again.

Warm regards,

---

### Post by rne1223 on 2007-08-22
Can I update the bios with a computer that has PS2?

---

### Post by Om1977 on 2007-08-22
Hello rne1223, I'm not an expert at these things either but any particular reason why you are looking at upgrading the BIOS?

---

