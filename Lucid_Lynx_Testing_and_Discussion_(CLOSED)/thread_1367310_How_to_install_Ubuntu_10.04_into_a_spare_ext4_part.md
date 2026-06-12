---
title: "How to install Ubuntu 10.04 into a spare ext4 partition? Please help!"
date: 2009-12-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Pipps on 2009-12-29
I have Grub installed in its own partition. I also have a spare partition in which I would like to install Ubuntu 10.04 Lucid Alpha 64-bit. 

I have installed [Ubuntu 10.04 Lucid Alpha 64-bit]("http://cdimage.ubuntu.com/releases/lucid/alpha-1/") seemingly without a hitch. During the installation, I deselected the 'install bootloader' at the 'Advanced' tab on the final insall screen. I then booted back into LiveCD and attempted to make the necessary updates to the menu.lst file to allow the separate Grub to point to the new Ubuntu.

I used the 'uname -r' command to find the name of the Ubuntu 10.04 Alpha kernel. I have understood this to be 'vmlinuz-2.6.32-7-generic'. I pasted this into the relevant section of the menu.lst file. I then also applied this same '2.6.32-7-generic' identifier to the 'initrd' field in order to update that as well. Both of these can be seen below.

On attempting to boot in Ubuntu, I am presented with the following Grub error:

> Error 17: Cannot mount selected partition.

What could be wrong? 

How else should the Grub menu.lst file appear in order to allow Ubuntu to  be mounted?



My menu.lst file on my separate Grub partition is attached below:

```
*sudo gedit /media/GRUB/boot/grub/menu.lst*

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color white/black white/aqua

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Linux Mint 10.04 (Alpha)
root         (hd0,2)
kernel        /boot/vmlinuz-2.6.32-7-generic root=/dev/sda3 ro quiet splash
initrd        /boot/initrd.img-2.6.32-7-generic
quiet

title Windows XP Performance Edition SP3
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

title		memtest86+
root		hd(0,2)
kernel		/boot/memtest86+.bin
quiet
```

---

### Post by Herman on 2009-12-29
```
Error 17: Cannot mount selected partition.                      
```If I remember correctly, Legacy GRUB wasn't going to be upgraded anymore since it was decided it would be easier to start again and make GRUB 2. 
Since then, the ext4 file system has begun to replace ext3. I think ext4 is a lot better myself.
I don't think you will be able to boot a kernel in a new ext4 file system directly from your Dedicated GRUB Partition containing the old 'Legacy GRUB'.

---

### Post by Herman on 2009-12-29
You could install your [Ubuntu 10.04 Lucid Alpha 64-bit]("http://cdimage.ubuntu.com/releases/lucid/alpha-1/") Lynx's GRUB to MBR and use that for booting your operating systems with.

Advantages would be you'd be using the most up to date, advanced GRUB and the new os-prober works great. No more need to go manually editing your grub files, just run 'sudo grub-mkconfig -o /boot/grub/grub.cfg and your grub.cfg will be automatically updated for you.

---

### Post by Herman on 2009-12-29
If you didn't want to do that you could install Lucid Lynx's GRUB to the boot sector of your Lucid partition and then chainload Lucid Lynx from your old GRUB Legacy.
When you chainload, that means GRUB Legacy will pass control to GRUB2 at Lucid Lynx's boot sector, and Lucid Lynx's own GRUB will take over from there.

---

### Post by Herman on 2009-12-29
Another idea might be to upgrade your 'Dedicated GRUB Partition' from Legacy GRUB to GRUB2.

---

### Post by Herman on 2009-12-29
No matter which of those three options you choose, you'll need to either 

[LIST]
[*]re-install Lucid Lynx and make sure you install it with a boot loader next time,
[*]or, you can boot Lucid Lynx and install GRUB2.
[/LIST]
How?

You can download the latest Super Grub Disk 1.21 or a more recent version if any are available, from [Super Grub Disk Downloads]("http://www.supergrubdisk.org/index.php?pid=5").

Then take a look at this web page, [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") -  and Rescue your System.

From there, once you have Lucid Lynx booted up and running, it will be fairly simple to do whatever else you like as far as installing and configuring your bootloader(s). :)

---

### Post by falconindy on 2009-12-29
Use UUID mounting for the root partition rather than try to win at the guessing game of GRUB. For example,
```
kernel        /boot/vmlinuz-2.6.32-7-generic root=UUID=0a1b2839-9b60-4d36-b39d-1ee68207266d ro quiet splash
```
udev is included on the initrd that bootstraps the kernel so you have access to this information.

Herman, you're wrong on a number of points. Grub is deprecated, but only in terms of development. There are tons of people (myself included) still using Grub because it's far simpler and maintainable compared to Grub2 (which should still be a beta, imo). I boot a 2.6.32 kernel, and I'm sure there's plenty of others running even 2.6.33-rc1 on the legacy Grub.

The last versions of Grub had intrinsic ext4 support added. If you were so inclined, you don't need a separate /boot to reside on a non-ext4 partition.

This is a simple matter of Grub not "agreeing" with your definition of what is /dev/sda. You could just as easily edit the kernel linux live from GRUB until you find out which /dev/sdxy is the correct one.

---

### Post by louieb on 2009-12-29
> **Herman said:**
> ...you could install Lucid Lynx's GRUB to the boot sector of your Lucid partition and then chainload Lucid Lynx from your old GRUB Legacy.
When you chainload, that means GRUB Legacy will pass control to GRUB2 at Lucid Lynx's boot sector, and Lucid Lynx's own GRUB will take over from there.

Right now thats how I'm booting 10.4 alpha from Grub legacy. :P

---

### Post by Herman on 2009-12-29
> Use UUID mounting for the root partition rather than try to win at the guessing game of GRUB. For example,Well I strongly agree that the UUID mounting in the kernel options is a good idea. 
Up to date versions of Legacy Grub support the uuid command, so the root command could be replaced with the uuid command as well.

I'm still not sure those will help though, if GRUB Legacy doesn't have ext4 support. 
I was only working from memory there, so maybe I am wrong. 
Legacy GRUB didn't have ext4 support the last time I tried it.
Maybe Pipps can update to a newer version of Legacy GRUB.

---

### Post by Herman on 2009-12-29
Why would a person who is multi-booting want to use direct kernel boot stanzas anyway though?

It would be more sensible to use the chainloader command so the menu.lst won't need to be manually updated for every kernel update in each operating system?
That would then allow Lucid Lynx to boot with its own boot loader, GRUB2, which brings us right around in a circle again. :)

---

### Post by Herman on 2009-12-29
:) Well, okay, thanks for correcting me, I have a Jaunty Jackalope installation which still uses Legacy GRUB. It's version 0.97-29ubuntu53.
I was able to directly boot my Karmic Koala installation with it. :)

Pipps, you could look for a 0.97-29ubuntu53 GRUB stage 2 file and downloadit from somewhere, synaptic Package Manager in Lucid might have it, Karmic does, and copy-paste it into your 'Dedicated GRUB Partition'. 

Or do one of the other suggestions already mentioned, whichever you prefer, it's up to you.

EDIT: Hello there louib! Season's greetings! :)

---

### Post by louieb on 2009-12-29
Grub Legacy has ext4 support starting with v9.04 Jaunty.  (not sure about earlier releases - know Hardy does not support ext4) 

Found that out 1st time I used the ext4 file system and the configfile command quit working. IIRC in the dedicated GRUB partition was using GRUB out of a v8.04 Hardy install.  - Copied my GRUB legacy files from the Jaunty install to the dedicated GRUB partition - configfile problem solved. 

Hello Herman - and  holly happy days to all of you.:)

---

### Post by Pipps on 2010-01-01
I must thank everyone for assisting with my question and for providing such useful advice. There seems to be a number of options available.

It would appear that perhaps the simplest long-term solution would be to chain-load from GRUB1 into GRUB2 - as Herman insightfully points out - to avoid updating the GRUB1 menu.lst every time Ubuntu is updated and the kernel changes in the future.

However, it would conversely seem a little pointless to embrace the Lucid 'reduced boot-times', by using two GRUB boot-loaders as part of the overall boot process. I would like to make things as efficient as possible in any event. So in pursuit of the best solution, I must ask two more questions. I hope this would be ok.

Firstly, would simply reinstalling GRUB2 over GRUB1 most likely provide the simplest possible solution? Would this be best performed by formatting the dedicated GRUB partition, and asking Lucid to install a boot-loader as part of a fresh Ubuntu reinstall? Would this then allow a fresh GRUB2 to boot Ubuntu 10.04 first time and to also automatically pick-up the existing XP partition which resides on (hd0,0)? Would this approach present any immediate issues?

Secondly, thinking more long-term instead, and to enable a situation like this to be avoided in the future every time Ubuntu is updated, would simply replacing GRUB1 with GRUB2 be a more future-proof solution? Or would this issue still arise in any event whenever a future Ubuntu update is installed? For instance, when Lucid Alpha is updated to the full release in April, would the update procedure change the kernel and present new boot problems? If so, would the chain-loading of GRUB1 into GRUB2 be a preferable in the long-term for this reason?

Further advice would be much appreciated. Thank you.

---

### Post by Herman on 2010-01-01
If you want fast boot times and you were using Karmic Koala, which is the current officially released Ubuntu version at the time of this post, you would probably find it simplest to just install GRUB2 to MBR in your first hard disk at installation time.
Then GRUB2 will take care of everything.

Since you're testing Lucid Lynx, which is under development, booting via the 'Dedicated GRUB Partition' is a slightly more cautious approach. If anything bad happens to Lucid, it won't affect your Dedicated GRUB, so you'll be able to boot right into your other Ubuntu, mount Lucid, chroot into it or whatever you need to do, and fix the problem.

If you have a Live CD though, you can do the same thing with a Live CD.
Besides that, if you know how to re-install GRUB and recover your boot you'll be okay anyway, so you can use whatever boot loader you like. Just install Lucid's GRUB2 to MBR and enjoy the reduced boot times and the new improvements GRUB2 brings with it compared with Legacy GRUB.

There are lots of different things you can do. It's up to you. 
Are you adventurous and willing to learn new ways and able to cope with changes? Confident with using GRUB commands? Maybe you don't mind spending a bit of time reading and experimenting to learn how the new GRUB works?
Or are you the cautious type and in a hurry, don't have time for this right now, more important things to get on with, need a system that will boot reliably without you having to worry about anything?

If you're confident and adventurous, it will probably be okay to boot with Lucid Lynx's GRUB2. I don't think they're planning any radical changes in Lucid Lynx. Still, it is in testing at the moment.
If you have important work to do, keep booting the way you have been. and just add a chainloader command for booting Lucid when you're in the mood for play.

---

### Post by Pipps on 2010-01-01
Herman, thank you for all your help! :)

I have just heard a rumour that GRUB2 does not allow booting into NTFS. Is this true?

I have probably not made this sufficiently clear, but I have an XP system at (hd0,0), which I will still need to boot into from time to time.

Would GRUB2 as the sole bootloader still be possible?

---

### Post by phillw on 2010-01-01
> **Pipps said:**
> Herman, thank you for all your help! :)

I have just heard a rumour that GRUB2 does not allow booting into NTFS. Is this true?



Works fine with my Vista install which is ntfs

Regards,

Phill.

---

### Post by Pipps on 2010-01-01
Phew! That is a relief! Thank you! :)

---

### Post by phillw on 2010-01-01
Oooh, you've been moved !!!

Welcome to the 10.04 Dev forum. There's a couple of stickies at the top of the page, well worth a read.

We don't bite, so don't worry about asking questions !!

Regards,

Phill.

---

### Post by Pipps on 2010-01-01
Herman, PhillW, thank you for your advice!

I am going to attempt a complete Lucid and GRUB2 reinstall right away! :)

---

### Post by Herman on 2010-01-01
> I have just heard a rumour that GRUB2 does not allow booting into NTFS. Is this true?No, that's not true, the opposite is true.

GRUB2 comes with a module called ntfs.mod and can be found in everyone's /boot/grub/ directory if we're using GRUB2.
Legacy GRUB didn't have any NTFS support at all.

We didn't need NTFS support for Legacy GRUB because we didn't use GRUB for chainloading Windows, the Windows boot loader does that well enough by itself.
GRUB's job is only to wake the Windows boot loader up by chainloading its boot sector.
GRUB doesn't need to be able to understand the file system just to stimulate the Windows boot sector.  :)

Years ago Linux used to have trouble writing to the NTFS file system, but now it seems to have excellent NTFS support. It looks like GNU GRUB is now able to provide the same degree of safety as Linux does for Ubuntu users who need to dual boot with Windows for some reason.

There are so many cool new things about GRUB2 that I haven't had time to try everything out yet. 
The fact that GRUB2 has the NTFS module opens up a lot of interesting new possibilities though. :)

A new Ubuntu user in another thread accidentally installed GRUB in a Windows operating system and probably it will not do any harm, and maybe even good.

---

### Post by Herman on 2010-01-01
> Would GRUB2 as the sole bootloader still be possible?
:) Absolutely. 

:) Recommended.

---

### Post by Pipps on 2010-01-01
I have just performed the installation for [Ubuntu 10.04 Lucid Alpha 64-bit]("http://cdimage.ubuntu.com/releases/lucid/alpha-1/") from scratch - intending to install Ubuntu Lucid and GRUB2.

Sda2 is my Ubuntu partition, sda3 is my swap, and sda4 is my dedicated GRUB partition. Sda1 is XP.

I set the mount-point for sda4 as '/boot' and the mount-point for the sda2 as '/'.

I selected 'install bootloader' at the installation procedure's advanced options. I selected sda4, the dedicated GRUB partition, for the location of the GRUB2 bootloader for this purpose.

When I reboot, I am faced with the following black screen error message:

> GRUB Loading Stage1.5
GRUB loading, please wait...
Error 15

I went through the entire installation procedure again from scratch. Exactly the same outcome arose on reboot.

Now I cannot boot in either Ubuntu or XP at all. :cry:

What could I have possibly done wrong?

---

### Post by Herman on 2010-01-01
> I selected 'install bootloader' at the installation procedure's advanced options. I selected sda4, the dedicated GRUB partition, for the location of the GRUB2 bootloader for this purpose.The installer is referring here to the IPL (pointer code) for GRUB, which is very small so it can fit inside a hard disk's MBR or in a partition boot sector.

Since you want Lucid's GRUB2 to be your main boot loader, you don't need to bother doing anything here, just leave the 'Advanced' button alone and Ubuntu will install GRUB, (meaning the IPL for pointing to GRUB), in the MBR of the first hard disk.

It will also install another part of GRUB in the first track of your hard disk.

Your actual GRUB files are already in your /boot partition, but nothing in the MBR points to them.

---

### Post by Herman on 2010-01-01
Instead of re-installing, the quick way to fix it is to use the [grub-setup]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-setup") command.

Here's a link for you that explains how to do it from a Live CD, [How To Re-install GRUB 2 from a Ubuntu Live CD]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD") - without the need to chroot.

---

### Post by Pipps on 2010-01-01
Herman, thank you for coming so swiftly to my rescue!

I performed the installation again, doing exactly as you said. I left the 'advanced' tab well alone. I didn't point the bootloader installation to sda4 - I let it simply remain with the default 'sda'. To my delight, this worked!

I now have Ubuntu Lucid up and running. Now, to set it up properly.

And more importantly, to make GRUB2 look slicker! :)

Thank you for all your help!

---

### Post by Herman on 2010-01-01
:) Okay, it's been my pleasure! Happy GNU GRUB2ing and happy Ubuntuing! :)

---

### Post by phillw on 2010-01-02
Thanks Herman,

I'm sorry Pipps - I've been busy coding on my Dad's Web-Site - Posting here is usually far quicker than sending a PM - although, you are always welcome to do so.

I would have recommended exactly what Herman said - 10.04 actually runs a slightly newer version of Grub2 than 9.10 does.
Dave (drs305), who seems to be the ubuntu guru for Grub2 tells me that there are no major changes between the two variants.

I have been meaning to post, re: /home on 10.04

When I was making my 10.04 area, I bit the bullet & finally made a seperate /home area - I followed these rather excellent instructions here --> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)   Written by one of the Mods.

The only alteration I made is that I popped it on the extended partition as primary partitions are pretty scarce when you dual boot.

Now, I was warned to keep my production /home away from my 10.04 /home in case 10.04 borks. - But, you can mount the /home partition for a little while onto /media and then rsync the contents over to your 10.04 /home  This is a handy trick, as it brought over all my FFox bookmarks and Passwords, pidgin passwords, desktop etc. So, some of the links needed repairing like to my Muzik, that still lives on my Vista Partition, but it was a really painless thing to do.

If I've been spending a while in 10.04 (and I spend most of my time in it) I do rsync my 10.04 /home back to my 9.10 one - **BUT** I do keep a seperate backup of my 9.10 /home, as well. (Programmes & Operating Systems can be replaced ...... your bookmarks & passwords .... Well, it's the most valuable part of a mobile(cell) phone)

As per the introduction - You will find the people on here very helpful & patient (heck, they've not kicked me off, for some of the n00bie questions I've asked) - The fact you're making the effort to test out 10.04 speaks bundles. Just please do expect it to bork & keep backups of your /home -- even if not on a dedicated partition, just somewhere.

At least it has been proven that we don't bite !!!!

:lolflag:

Regards,

Phill.

---

### Post by Pipps on 2010-01-03
Dear PhillW

The single greatest thing about Ubuntu is the most incredible level of user support provided by the members of this amazing forum and the internet worldwide!

What makes it all even more amazing is that it is all somehow provided absolutely free! For the collective furtherance of joyful personal computing!

I am most grateful for your link to the Psychocats website. There are some extremely useful looking articles on there. I look forward to reading them!

PS: Hello from the South West! ;)

Best wishes

Pipps

---

### Post by ikki_72 on 2010-03-20
hi, i had installed ubuntu 10.04 on my /dev/sda3, after that i reinstalled debian on /dev/sda1 (/ partition. /home on /dev/sda2)

after that i could not boot ubuntu as grub does not detect ext4 partition.

i installed grub2 but os-prober cannot detect ubuntu

how do i make it realize ubuntu partition is in /dev/sda3 and make it bootable from grub2 menu?

---

### Post by VMC on 2010-03-20
> **ikki_72 said:**
> hi, i had installed ubuntu 10.04 on my /dev/sda3, after that i reinstalled debian on /dev/sda1 (/ partition. /home on /dev/sda2)

after that i could not boot ubuntu as grub does not detect ext4 partition.

i installed grub2 but os-prober cannot detect ubuntu

how do i make it realize ubuntu partition is in /dev/sda3 and make it bootable from grub2 menu?

If you download boot_info_script (see my blue link), then we can tell how your booting right now with all the needed outputs in one single file. After you run boot_info_script it will dump the contents into a file RESULTS.txt. Bring that file back here.

---

### Post by ikki_72 on 2010-03-20
the RESULTS.txt is attached

---

