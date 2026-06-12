---
title: "MacBook triple boot success!"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by slouken on 2006-06-03
I just got Mac OS X, Windows XP, and Ubuntu 6.06 triple booting on my new MacBook Pro.

Here's how I did it:
(Note, these instructions assume that you want to triple boot with Windows XP.  If you just want to install Ubuntu and Mac OS X, I believe the procedure is much simpler)
[LIST=1]
[*]Install Mac OS X, on the whole disk (you can skip this if you already have a working  Mac OS X install)
[*]My MacBook is new, so it already had Mac OS X 10.4.6 and the latest firmware updates, which are necessary for this process.
[*]Download and install Apple BootCamp:
[http://www.apple.com/macosx/bootcamp/](http://www.apple.com/macosx/bootcamp/)
[*]Run BootCamp (in the Applications/Utilities directory) and create a Windows XP driver CD.  Do NOT repartition your drive yet, cancel and quit BootCamp.
[*]Download and mount the disk image for rEFIt:
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)
[*]Drag the efi directory from the disk image to the root of your MacOS X drive.
[*]Enable rEFIt:
```
cd /efi/refit
./enable.sh
```
[*]Get your Windows XP SP 2 install CD handy.  If you have an older Windows XP install CD, you can create an SP 2 CD, as described here:
[http://www.theeldergeek.com/slipstreamed_xpsp2_cd.htm](http://www.theeldergeek.com/slipstreamed_xpsp2_cd.htm)
You need to have Windows SP 2, or the MacBook driver CD won't install correctly.
[*]Partition your disk for three operating systems:
```
sudo diskutil list
```
You should see the Mac OS X partition - make a note of the size in MB.
```
sudo diskutil resizeVolume disk0s2 65G Linux Ubuntu 12G "MS-DOS FAT32" WinXP 15G
```
The first number is the size of the Mac OS X partition, the second is the size of the Linux partition, and the third is the size of the Windows XP partition.  The total of the three should match the original size of the Mac OS X partition.
WARNING: Plan your partitions in advance!  If you decide later you want to change them, you'll have to reinstall all three operating systems from scratch.
[*]Put your Windows XP install CD in the drive and reboot.
[*]Install Windows XP normally, selecting the Windows OS from the rEFIt boot menu.  Make sure you install onto the C: drive, which is the last partition listed.
[*]Boot into Windows XP and install the MacBook device drivers from BootCamp.
You can eject the CD in Windows by opening My Computer, clicking on the CD icon, and selecting the "Eject" task from the left hand menu.
...
Congratulations!  You now have a working dual boot system.  But we're not done yet...
[*]Insert the Ubuntu "alternate" install CD and select it from the rEFIt boot menu.
The normal desktop install CD tries to install GRUB, which fails, crashing the installer, so it's important to use the "alternate" install CD (ubuntu-6.06-alternate-i386.iso)
[*]Begin the install and STOP :!: at the partition option screen.  DO NOT CONTINUE or you will lose your partitions and must reinstall from scratch.
Ubuntu uses parted, which understands the MacBook partition table format (GPT), but overwrites the MBR used by Windows XP (and Ubuntu in these steps)
[*]Use ALT-F2 to switch to a console, and make a backup of the master boot record:
```
dd if=/dev/sda of=/tmp/sda.mbr bs=512 count=1
```
[*]Switch back to the installer with ALT-F1 and continue the disk partition setup, making sure only to modify mount points and format the Linux partition, mounting it at /
Here's the partition layout:
/dev/sda1 - EFI boot partition
/dev/sda2 - Mac OS X
/dev/sda3 - Linux partition
/dev/sda4 - Windows XP
[*]After setting up partitions and networking, but before you continue to install packages, stop and switch to the console with ALT-F2 and restore the master boot record:
```
dd if=/tmp/sda.mbr of=/dev/sda
```
You can even do this while packages are installing, but if you forget to do it before ELILO is installed, the installation will hang, and if you reboot forgetting to do it, you'll have to reinstall everything from scratch.
You also might want to save the MBR to your install drive (mounted at /target), in case you have to restore it later, booting from the Ubuntu Desktop CD.
You can check to make sure that your partition table looks okay by using fdisk /dev/sda.  If you run parted, you're likely to have to restore the MBR again, so be very careful!
[*]Finish the install normally and try booting your installation via the rEFIt boot menu.  If this works for you, you're done!  In my case, the ELILO boot sequence hung after loading the initrd, so I set Ubuntu up to boot with LILO instead.
[*]Boot from the Ubuntu Desktop CD, setting up networking.
[*]Uninstall ELILO from the EFI partition:
```
mount /dev/sda1 /mnt
rm -r /mnt/efi/ubuntu
umount /mnt
```
[*]Grab lilo, either from the Ubuntu repository, though I'm not sure what the install steps are, or directly from the lilo website, like I did: [http://lilo.go.dyndns.org/](http://lilo.go.dyndns.org/)
I extracted the tar archive onto the Ubuntu installation like this:
```
mount /dev/sda3 /mnt
tar zxvf  lilo-22.7.1.bin.tar.gz -C /mnt
```
[*]Create a lilo.conf file for booting:
```
cat >/mnt/etc/lilo.conf <<EOF
boot=/dev/sda3
delay=3
default=Ubuntu

image=/boot/vmlinuz-2.6.15-23-386
        label=Ubuntu
        root=/dev/sda3
        read-only
        initrd=/boot/initrd.img-2.6.15-23-386
        append="quiet splash"
EOF
```
Notice that we're installing lilo to the Linux partition, not the beginning of the disk.  rEFIt will see the boot record on the Linux partition, and boot it from there.
[*]Install lilo:
```
cp -av /dev/* /mnt/dev/ # This creates the disk device files, ignore any warnings
lilo -v -r /mnt
```
You should see some warnings about /proc/partitions, and name remappings which you can ignore, and then you should see a line near the end mentioning that lilo has written the boot sector.
[*]Reboot!  If everything has gone well, you'll see all three operating systems on the rEFIt boot menu, and be able to boot into all three.  If Windows can't boot, you've likely messed up the MBR and need restore it or reinstall everything.
[/LIST]

Thanks to all the great folks who have blazed this trail and made it possible!
[http://www.ethicalhack.org/howto/triple_boot_howto.html](http://www.ethicalhack.org/howto/triple_boot_howto.html)
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

Good luck!
--Sam

---

### Post by amonsul on 2006-06-03
Cool!!!!!!!

Im waiting for Macbook with MEROM and i will take care of your suggestions! ;)

---

### Post by Roner on 2006-06-03
Dear Sam, you are my hero. For the most part, your howto worked for the 20" iMac, with one big problem: the installation of ubuntu got stuck in the elilo stage.  When I rebooted and completed the subsequent lilo installation I discovered that my username was not set up, and I could not log into ubuntu at all.

To repair it, I used the rescue option of the alternative setup CD, which allowed me to have a shell mounted at the root of /dev/sda3.  I proceeded to creating my group and the admin group:
```

addgroup --group --gid 1000 <myname>
addgroup --group --gid 112 admin

```
Then I added myself as a user:
```

adduser --home /home/<myname> --shell /bin/bash --gid 1000 <myname>

```
The following prompts set me up nicely.  Now I added myself to all of the relevant groups:
```

adduser <myname> adm
adduser <myname> dialout
adduser <myname> cdrom
adduser <myname> floppy
adduser <myname> audio
adduser <myname> dip
adduser <myname> video
adduser <myname> plugdev
adduser <myname> lpadmin
adduser <myname> scanner
adduser <myname> admin

```
I had to shutdown the hard way.
Next I used the rescue option from the CD again, and this time I chose the second option for the mount: I mounted /dev/sda3 as /target and continued working in the installer environment. The reason for this is that from the actual sda3 environment I could not edit the sudoers file.

Now I edited the sudoers:
```

nano /target/etc/sudoers

```
and added the line
```

%admin     ALL=(ALL) ALL

```

Now I can log in and everything is going well - so far. I will get back to you with updates.

In the meanwhile, I have a "constructive criticism" suggestion: your howto skips some steps that I had to poke around to figure out (well, I am rather newbish). For instance, the path for running lilo (/sbin/lilo), or the necessity to have both the regular live installation CD (for lilo installation) and the alternative one (for installing the actual system and recovering from mishaps). You did mention it, but not clearly...

I am trying to set up a swap file now (another point to emphasize is that the number of partitions is limited to 4 in triple boot and a swap partition cannot exist). 

Let's share information about all of the necessary tweaks: xorg, kernel, etc.

Once again - You are my hero.

---

### Post by Roner on 2006-06-03
Making a swap file:
For a 2GB swap type
```

sudo -s
dd if=/dev/zero of=/swap bs=1024 count=2097152
mkswap /swap
swapon /swap

```

For other sizes, you can also determine the size in MBs. For instance, for 512:
```

dd if=/dev/zero of=/extraswap bs=1M count=512

```

After that check the system monitor to see if a swap appears in the resources tab.

If all works, add to /etc/fstab the following line:
```

/swap         none         swap         sw         0         0

```

Reboot and check the system monitor again.

---

### Post by ShmengeTravel on 2006-06-09
I have a Macbook Pro and even mine got stuck at the ELILO installation. I followed his guide to installing LILO, but to no avail. Filenames are different, for example lilo-22.7.1.bin.tar.gz downloaded as lilo-22.7.1.bin.tar.tar, because the ELILO installation froze there was nothing to uninstall, and installing LILO directly via his method resulted in bash not knowing what the lilo command was. I've never had so much trouble getting a system to triboot before. :(

---

### Post by bluetoad on 2006-06-17
I was wondering if suspend to RAM and suspend to disk are working reliably? It would be worth trying them after the latest kernel upgrade.

How is the MacBook generally running?

---

### Post by longinus on 2006-06-17
Cool! I don't have a powerbook yet, but I'll soon.. and of course I'll do this! :D 

A good software to slipstream Service Pack 2 into a normal XP install, is [nLite]("http://www.nliteos.com/") (good also to remove stuff from XP, like outlook, msn, etc). And you can also incorporate all the others updates from microsoft after SP2, with [RyanVM's Windows XP Post-SP2 Update Pack]("http://www.ryanvm.net/msfn/updatepack.html").

---

### Post by chikoo on 2006-06-21
i'm having a problem.

being a nervous noobie to the whole ubuntu scene AND attempting to install it on my new black macbook (i got windows XP running fine), i'm wondering what to do with the partitions.

the installer is giving me this warning that says i haven't selected any partitions for swap space.

how do i add a partition for swap space when i can only have 4 partitions on my hard drive?

can i just add swap space onto the linux partition after i install ubuntu in like a terminal in the operating system?

---

### Post by majestikmoose on 2006-07-14
I seem to be suck on the elilo installation.  It gets to 50% and then locks up.  I haven't found a way around this, any ideas?

---

### Post by sir romualdo on 2006-07-18
> **majestikmoose said:**
> I seem to be suck on the elilo installation.  It gets to 50% and then locks up.  I haven't found a way around this, any ideas?

Happens same thing to me. Gets stuck at 50% while elilo-installing and won't go on. Im using a macbook 13" 512mb 60hd intel gma950, guess you figure out which one is. I think it's trying to install itself in the /dev/sda1 partition (going to a console and running a "ps aux" command returns a "elilo --configure --boot --/dev/sda1" process running) and that's probably why it gets stuck. It never gave the option to install in the /dev/sda3 partition which i guess should be the right one although that partition was formatted to a ext3 and / mount point, no swap. Any tips welcome, gheez...

---

### Post by jedsen on 2006-07-24
Where does one find the Ubuntu Dapper "alternate" install CDs?

---

### Post by th3t1nm4n on 2006-07-25
> **jedsen said:**
> Where does one find the Ubuntu Dapper "alternate" install CDs?

[http://releases.ubuntu.com/dapper/]("http://releases.ubuntu.com/dapper/")
They are labeled as "alternate" instead of "desktop", you can also check [http://www.ubuntu.com/download]("http://www.ubuntu.com/download") for mirrors that may be closer to you for a faster download. These are .iso image files, you would have to burn the image to a CD, info on how to do that here: [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

I didn't use an alternate CD however, I managed to install Dapper for i386 on my MacBook following this guide: [http://bin-false.org/?p=17]("http://bin-false.org/?p=17")

---

### Post by Donnut on 2006-09-18
Hi, First of all, I's like to thank you for doing this, the macbooks are just barely out, and there is jist new stuff every day!

However, I have a slight problem, here is the error message:

/dev/disk2
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *10.0 MB  disk2
   1:    Apple_partition_map                    31.5 KB   disk2s1
   2:              Apple_HFS rEFIt              10.0 MB   disk2s2

stephen-boyds-computer:/efi/refit steve$ sudo diskutil resizeVolume disk0s2 74.2G Linux Ubuntu 20G "MS-DOS FAT32" WinXP 15G
Started resizing on disk disk0s2 Steve's Drive
Verifying
Resizing Volume

Resizing encountered error The chosen size is not valid for the chosen filesystem (-9962) on disk disk0s2 Steve's Drive
stephen-boyds-computer:/efi/refit steve$

What do I do?

---

### Post by Ziktar on 2006-09-18
Donnut,

That's probably because you're trying to squeeze every last MB out of the partition, and are slightly too large. Try just 74G for the first parition, or even just 73.8G.

---

### Post by Donnut on 2006-09-18
OK, i did it in various sizes, like 74G, 73, 72, 71, 70, I tried free space which is 50 gig, got another error;

stephen-boyds-computer:/efi/refit steve$ sudo diskutil resizeVolume disk0s2 50000M Linux Ubuntu 20000M "MS-DOS FAT32" WinXP 15000M
Password:
Started resizing on disk disk0s2 Steve's Drive
Verifying
Resizing Volume

Resizing encountered error No space left on device (28) on disk disk0s2 Steve's Drive

Don't know what this is...

---

### Post by packhater on 2006-09-21
OK I have a wierd issue. I had already done this on a mini mac that I have had for about 3 months. After a few glitches in my install, everything went fine. I am triple booting!!!!  :)

BUT I ordered a new macmini and recieved it last week. I intended to do the exact same thing (my first minimac was a test for this new machine). HOWEVER when trying to run bootcamp I get a "you need to update firmware" message. Everything is updated including the firmware which is the latest 1.3f4! Now the only thing I can't do upto this point is RUN bootcamp and create a cd. No big deal right? I can use the diskutil command to do my partitions. So I do this and not think about bootcamp. Obvisouly BootCamp does something to the HD to enable booting but I don't know what it is.

 The wierd thing is that I can't even BOOT to ANY NON mac CD! efi gives me this legacy boot loader message because of firmware. I can use efi to boot to the cd that came with this mac, install disk and HT disk but not ubuntu or windows install disk.

Did Apple do somethign to these new macs coming out??? This is wierd! I doubt it!

I did however get an error when running the HT. 4sns/1/40000000: 'TC0P'

any ideas????

[email]packhater@yahoo.com[/email]

---

### Post by packhater on 2006-09-21
Additional note.....I tried to do a reinstall of the OS. I tried using the disc that came with my first mini mac. Those discs would not load this machine. It kept failing during install. I tried the discs that came with this machine and they worked fine. 

Bare in mind, these are identical machines....1.66 intel mini macs.

Something HAS to be different about this machine.

---

### Post by packhater on 2006-09-21
ok one more!   :)

I noticed that in Profiler, the Boot ROM version was different but everything else was the same....

"old"  mac mini - MM11.0055.B03 (boot camp running fine, triple booting machine)
"new" mac mini - MM11.004B.B00 (boot camp won't run, getting firmware message)

Can anyone else veryfiy their Boot ROM version?

---

### Post by packhater on 2006-09-21
FIXED!!!!!!! It WAS the boot rom! Apple confirms this. There is an aadditional update NOT found when using Software Update. 

[http://www.apple.com/support/downloads/macminiearly2006firmwareupdate101.html](http://www.apple.com/support/downloads/macminiearly2006firmwareupdate101.html)

This will update the Boot ROM version to what I mentioned above.

:)

---

### Post by rupy on 2006-09-24
My Windows wont boot:

> Windows could not start because of a computer disk hardware configuration problem.

Could not read from the selected boot disk. Check boot path and disk hardware.

Please check the Windows documentation about hardware disk configuration and your hardware reference manuals for additional information.

I am using rEFIt and triple booting ubuntu, osx and windows. windows was working initially but since I upgraded rEFIt/lilo I think it broken...

I think its the MBR being overwritten or something, because if I hold down the option key and choose 'Windows' it boots lilo.

Anyone have any idea's?

---

### Post by sentinel105 on 2006-10-26
> **slouken said:**
> 
After setting up partitions and networking, but before you continue to install packages, stop and switch to the console with ALT-F2 and restore the master boot record:
```
dd if=/tmp/sda.mbr of=/dev/sda
```
You can even do this while packages are installing, but if you forget to do it before ELILO is installed, the installation will hang, and if you reboot forgetting to do it, you'll have to reinstall everything from scratch.

I found that doing this while packages were installing, or even during the base system installation, the setup would continue to hang at the ELILO installation (50%).

I finally got it to work when copying the sda.mbr back to /dev/sda at the time-zone selection screen, before beginning any type of installation, and right after saving changes to the disk.

Hope this helps!

---

### Post by ruicovelo on 2006-11-17
Hi!

I see some of you using LILO and some using ELILO. What are the main differences? Do you need refit if you're using elilo? If lilo works, why use elilo? Thanks!

---

### Post by la3875 on 2006-11-28
Reading through the posts it seems success has been marginal and requires much patience. I am considering a macbook and intend to do the same but have to ask: Wouldn't it be easier and more stable to run multiple OS's using Parallels? Looking forward to your comments and congratulations on the successes.:-k

---

### Post by Donnut on 2006-11-30
It is harder but more satisfying.  U can run ubuntu on parallels but it will run far faster natively.  Oh, it will also not run widescreen in Parallels.

---

### Post by Donnut on 2006-11-30
OK, got a problem, I almost succesfully have a trible boot laptop, but every time I try installing ubuntu (using alternative cd) it gets to the part where it is configuring xserver-xorg and freezes.  Anybody else have tis problem?

---

### Post by cdiew on 2006-12-16
Thanks a lot. It worked for my  20' iMac. Have you tried installing Grub?

---

### Post by vengeance316 on 2006-12-16
I also managed to get a triple boot going, although mine is between OS X, Yellow Dog 4.1, and Xubuntu 6.10. My only problem was getting the bootloader to actually load all 3 correctly, every time I installed the last OS it would majorly screw up my boot settings for the others. It just took a lot of trial and error, but I finally got it working without a hitch!

---

### Post by mustang on 2006-12-18
Hi guys.

Quick question---will this also work for windows vista instead of windows xp?

Thank you

---

### Post by ndrw on 2007-01-08
more success, I did a little writeup about it here:

[http://ndrw.net/blg/2007/01/08/triple-boot-macbook-pro-17-success-osx-winxp-ubuntu-linux/#more-83]("http://ndrw.net/blg/2007/01/08/triple-boot-macbook-pro-17-success-osx-winxp-ubuntu-linux/#more-83")

hope this helps somebody

---

### Post by ominiverdi on 2007-01-15
With Ubuntu 6.10 you can say the installer not to install grub. Instead you can directely tell it to install lilo on your /dev/sda3.
that's all. All OSs are working fine for me. The most important part is then to save and then recover the MBR.

If you have a lots of ram you don't even need the swap partion.

:-)
Lorenzo

Mac Book Pro 2.13, 2GB RAM

---

### Post by zack509 on 2007-01-25
Lorenzo, ti ho scritto un messaggio privato.

Grazie

Ciao

Zack

---

### Post by Chrisj303 on 2007-03-07
Hi there!,
I am a complete Linux virgin, so please excuse me if my questions sound absurd!
I have got the OSX/UBUNTU/XP TripleBoot working fine using GRUB Bootloader, however every guide i read on the subject talked of using LILO. Are there any glaring problems with this?
I have also found that my Macbooks keyboard does not seem to respond on the GRUB Bootload screen every 3/4 reboots. When this happens, my macbook boots to the default kernel - where it runs fine!
This is a pain in the **** as i can't boot into into XP if GRUB dosen't respond to the keyboard!
Can't find proper fix on the net..

Cheers,
Chrisj303

---

### Post by Chrisj303 on 2007-03-14
Triple Booting! had to use LILO.

---

### Post by [-Ghost-] on 2007-04-10
Hi, 

New Mac user here. First of all, congrats on the innovative success with the triple-booting. I did have some questions i was wondering about before making the attempt myself. Is this setup possible:

Partition 1: Mac OSX
Partition 2: Kubuntu Feisty Fawn 7.04
Partition 3: Windows XP
Partition 4: Data

If i wanted a data partition to keep my data safe amongst the OS realignment carnage, does that prevent me from making another partition for a Linux Swap? Also, i was wondering what the min partition sizes i'd need for each OS would be (new macbook only has 60GB HD)

If i can't get the above setup to run stable, i might just eliminate Windows XP from the picture and try with the dual boot (leaving the triple boots to you pros)

Thanks for any input, sorry if this is misplaced or too noobish.

---

### Post by gyga-byte on 2007-08-01
> **ominiverdi said:**
> With Ubuntu 6.10 you can say the installer not to install grub. Instead you can directely tell it to install lilo on your /dev/sda3.
that's all. All OSs are working fine for me. The most important part is then to save and then recover the MBR.

If you have a lots of ram you don't even need the swap partion.

:-)
Lorenzo

Mac Book Pro 2.13, 2GB RAM

I just confirmed this! I have a black macbook gen. 1 (Intel duo) and I have been tried to triple boot for an almost entire two days! needless to say i never would have gotten it to work if it wasn't for the info on this section so big thankx to you guys! Once more i'm luckily not a noob but when it comes to linux i'm not really a genuis so yeah.

Using 6.10 alternative disc you can install LILO and choose which partition it goes on. I tried installing it under the /dev/sda3 probably a million times, deleting and formatting both Windows & Linux partitions each time. I just couldnt get it to work and it was starting to annoy me. So just on a whim i decided to try to install LILO under /dev/sda  and it finally worked! I did however get it to work like this, but I only created the partition for Windows prior, so I haven't installed windows yet, just the part. so that i could do it after I finally got linux on. 

Once more 3 cheers for you guys for finding this stuff out. I envy you. I plan to try to learn some coding and programming to hopefully become a hacker (not a bad one, lol) I already know computers inside and out (linux, mac, and windows based) but i want to be able to expand my knowledge, i use OSX for my college work and just playing around. Windows is used for typing college papers, and Linux will be used during my spare time to try to understand the language its built on, which is almost identical to Mac so that helps. I hope my little info can help others having issues with this aswell, but i've confirmed it so if you get 6.10 you can totally skip the last section of the tutorial (about LILO) thank you guys again. you people help me wake up everyday. If anyone has any interest in helping a Linux novice understand it a little better please let me know. Thanks :-)

**EDIT: Ok, well I just tried installing Windows after using LILO installed  under /dev/sda and as soon as the system restarted to finish up the windows install, neither windows nor linux booted successfully, not even after updating & syncing the MBR. So i'm back at square one. Thats ok though because I have the alterative disc for 7.04 too and i'm gonna try to install windows first and use the LILO on that install it under /dev/sda3 and see what happens then. I will get this to work, i'm slowly learning whats going wrong, sadly i can't try to test my theory until tomorrow, gotta wake up at 7am for work....blah :-( i think the reason why it keeps failing to load windows and linux after the install of both plus LILO is because i didn't sync the MBR before trying to load them. i'll let you all know what happens.**

---

### Post by krzee on 2007-08-05
I have finished my setup now and just wanted to let it be known how i got past a problem I had.  I could not find any answers on google, so I am posting this here in hopes that it will get spread and others will not have a problem getting past this error.
When trying diskutil resizeVolume or bootcamp I would get an error:
Resizing encountered error No space left on device (28) on disk disk0s2
After trying many things I tried using idefrag.  HFS+ is said to never need to be defragged, which is generally true... but in this case it solved my problem.  It took a long time to defrag my 120GB drive, and it should not be done often... but I dont see myself needing to do it again now that I have my disk resized.   diskutil is able to move data in order to resize a volume, but it is not able to move metafiles; so if you have metafiles in the space that diskutil wants to free, you cannot resize the volume in diskutil or bootcamp.  Basically, if you have enough free space that resizeVolume should work, and it just wont, give idefrag a try.
Thank you to everyone that has posted so much information about getting a MBP to run ubuntu in dual boot, the information was invaluable!

---

### Post by fredscripts on 2008-03-08
Hi!

I'm trying to get triple booting for some weeks, I've read the first post and seems a good guide. Will work with this?:

Mac OS Version 10.5.2

Windows XP SP2

Ubuntu 7.10 (I have the standard live CD, I need another one?)


Thanks!

---

