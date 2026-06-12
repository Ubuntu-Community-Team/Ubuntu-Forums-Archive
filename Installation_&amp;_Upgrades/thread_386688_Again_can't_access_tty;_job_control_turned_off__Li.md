---
title: "Again: can't access tty; job control turned off / LiveCD"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by heikor on 2007-03-17
I know others had similar problems, I searched these forums and google, but the answers I found didn't help me.

I downloaded the ubuntu-6.10-desktop-i386.iso, md5-checksum was okay, and wrote it on CD.
When I boot from CD, I get to the start menu, set my language and keyboard-layout and the choose "Start or install Ubuntu". Then an Ubuntu splash screen appears, and after some time, I get the following error:
```
BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) 
```

I can switch to the other consoles with Alt+1-7:
```
cp: unable to open '/root/var/log/': No such file or directory
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
```

It's an older PC with an Abit mainboard (I think KT7A), Athlon CPU 1.2 GHz, 1 DVD, 1 CD, 1 HDD, all connected via IDE (no SATA drives).
(Most of the people in the other threads I found had Intel Core2 and SATA drives)
I tried to add "noapic nolapic noacpi pci=noacpi" (or diiferent subsets of these parameters) to the boot options, I switched to the text-mode interface and tried "live noapic nolapic noacpi pci=noacpi" and variations of that.
I always get the same error, except one time, I got a blank black screen.
I installed a variety of other OSs before, including Gentoo, FreeBSD and Debian, they all worked fine.
As my download traffic is very limited, I don't want to download and try the alternate CD... I hope there is another solution.
Any ideas?

---

### Post by Arby on 2007-03-18
As you say, several people have had this problem recently. Do you have multiple partitions on your hard drive? Other threads I've read suggest that this problem is caused by grub being pointed at the wrong partition (or wrong drive if there are multiple drives). I wish I knew why this happens. You'll need to redirect grub to the right partition. Can you post the following information here.
1) The contents of the file /boot/grub/menu.lst
2) the contents of the file /etc/fstab
3) the output of the command 'sudo fdisk -l'
Hopefully we'll be able to spot what's wrong from that.

Arby

---

### Post by wpshooter on 2007-03-18
I don't think this error has anything to do with hard drive, grub, partitions, etc., etc., because I have received this error on a computer on which I had just completely WIPED the hard drive clean (there was ZERO, ZIP, nothing at all on the hard drive).

I believe this error is instead related to VIDEO.  Try using the F4 key to manually choose a video mode that is compatible with your video card and monitor.

Good luck.

---

### Post by heikor on 2007-03-19
Thanks for the answers so far.
I had FreeBSD installed previously and then formatted the whole drive to install SymphonyOS, which failed. I'm not sure what's left on my harddrive, but I tried to reformat it using the installer of some other distros, and finally deleted all partitions.
So I shouldn't have any /boot/grub/menu.lst or /etc/fstab and fdisk -l should return an empty table.
I didn't yet install any other OS, I was just trying to start the LiveCD.
I'll try it with some different video modes...

edit: I tried some standard video modes (VGA, 800x600x16, 1280x1024x32, ...). I know all these modes worked before. I don't think the problem is related to the video modes.

---

### Post by dannyboy79 on 2007-03-21
WOW, everyone is having this issue. I too have it. Although I don't want to install Edgy Eft 6.10 Live CD version, I merely was trying to use linux to see a windows hard drive that has the NTLDR is missing error. I tried various methods to FIXBOOT, use the ATTRIB command, copy files to it's root drive but no, windows won't boot. Anyway, back to the Live CD problem at hand. 

**Setup**
~Asus P4P800-E Deluxe (Bios 1009, i think)
   -North Bridge Intel® 865PE Memory Controller Hub (MCH); 
   -South Bridge Intel® Intel 82801ER Enhanced I/O Controller Hub (ICH5R); 
   -Interbridge link: Hub Link v1.5;
   -AGP 4x/8x
~Intel P4 Prescott 2.8E (originally overclocked 20% using asus option BUT I ended up clicking on the global setting to make it all default, NOT optimum or best, but standard or default. this depends on bios)
~ATI AIW 9800 Pro, DVI Interface (AGP 4X/8X) 
~1.5gb RAM (Kingston Value Ram)
~2 Optical Drives (Toshiba as slave and NEC as master both on ide0 [ide1 not being used])
~Floppy (unknown)
~120gb Samsung Sata drive-simply NTFS storage for my winbloz xp pro box (connected to ICH5R controller)
~Synergy714 17" flat panel monitor (DVI)
~iogear mini-kvm 2 computers ([http://www.iogear.com/main.php?loc=product&Item=GCS612A&name=MiniView&#8482;%20Micro%20PS/2%20Audio%20KVM%20Switch](http://www.iogear.com/main.php?loc=product&Item=GCS612A&name=MiniView&#8482;%20Micro%20PS/2%20Audio%20KVM%20Switch))
~wireless (RF, ps/2) mouse and dell keyboard (ps/2) plugged into kvm (wireless keyboard is acting weird so not using it) [[http://www.newegg.com/Product/Product.aspx?Item=N82E16823201019]](http://www.newegg.com/Product/Product.aspx?Item=N82E16823201019]) this is the same model I have but when I bought it, the wireless module box had 2 ps/2 connectors instead of 1 usb!
~80gb sata windows hard drive-OS=Windows Media Center-1 fat16 partition, 1 NTFS partition, 1 fat32 partition (originally connected to Promise controller BUT switched it to ICH5R)
~originally had left all usb plugs in, printers, usb extender cables, etc, etc BUT removed them all and ran bare min! keyboard connected to kvm and RF wireless mouse to kvm as well and monitor staright to box. See I only use the kvm for mouse and keyboard because my monitor has 2 inputs, so i just use the input button on the front of the monitor and hit scroll lock twice and I am in my other computer. i love it.

No matter what I did I could NOT boot any live cd, I tried Knoppix (i think 5.0), DSL (latest as of 3-17-07), Puppy (latest 3-17-07), Edgy and everyone either stalled during bootup or ended up at the infamous black screen that doesn't do s__t. NO, ctrl-alt-F1 thru F6 didn't bring up a console, and no vga= didn't do anything, trying boot to safe mode didn't work either. Even tried to remove "splash" and then add break=bottom after the "--". I followed this guide: [https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)
but even when I got to the initramfs and used the command as noted, I get an error that says that nano doesn't exist. YES, I did verify the cd and I checked my RAM. All ok!! I was like come on, I can't win!!!!!! So, I was thinking to myself, gosh what else can I try.  Well I read somewhere that you can add other options for "broken bios" but I knew my bios wasn't broken but I figured, I'll try anything!!! I did what the above guide said but also added noapic and nolapic to see what would happen. Still it either wouldn't make it to the initramfs or nano didn't exist? Then I remember reading that people suggested removing all devices like usb devices plugged in etc etc, just base min, keyboard, mouse, monitor. I also thought I would try a different sata port as my motherboard has 4 total, 2 of them are built into the ICH5R and 2 are on a promise controller. I had the windows drive in the promise port and the other storage NTFS drive in the built in sata port. I thought maybe I'll not use the promise and just use the built in ones because I wasn't sure about support for the controller within the livecd. Still NOTHING!!! AWWWWWW. I have spent 3 hours total gogling and just booting live cd's and still nothing. So I happen to watch the output of it booting 1 time and it suggested trying irqpoll as a boot option and I thought, well nothing to lose. I get to the menu, click F6, edit the boot line like the above guide BUT also REMOVED quite and added irqpoll noapic nolapic AND I GOT IN!!!!!!!!! YES, I screamed as loud as I could and thought, persistance always wins out!!!!!!!!!! 

**_Let's recap some important things, at least for my situation._**
-make sure you have bare min hooked to your computer: monitor, keyboard, mouse period! (i am surprised that it worked with the kvm. i also was about to try and remove 1 of the optical drives so Ubuntu had to check less hardware)
-maybe change bios to defaults, some have reported that changing bios agp to 4x instead of 8x helps but I don't have that option in my bios. nor did I have an option for fast writes which I have also read works if you DISABLE it.
-use controllers that you know are supported by Ubuntu or the native ones (in my case I had a promise sata controller as well as a RAID ide controller built into my mb, DON'T use these, try the ones built into southbridge if you can)
-At the boot screen where it says the following: Start or Install Ubuntu, run in safe graphics mode, Check CD, boot first hard disk, memtest etc etc (see this link for awesome guide with pics: ([https://wiki.ubuntu.com/EdgyKnownIssues/59618)](https://wiki.ubuntu.com/EdgyKnownIssues/59618)), follow the guide BUT also delete "quite" and add these options if that guide alone didn't work. irqpoll noapic nolapic. so the final end of the line would be: .............../ram rw irqpoll noapic nolapic -- break=bottom  (NOTE: the "dots" just represent the begining of the boot line that doesn't need changing). There are also other options that may work if these didn't. you can also try: 
acpi=off
pci=irqroute
xmodule=vesa
vga=normal
vga=771
pci=irqroute
framebuffer=false

You should end up in Ubuntu Edgy Eft Live CD Environment!!!!!!! YEAH

There are also so many guides out there for various situations where certain things didn't work for this bug (there is also more than 1 bug so I am going to post 1 and also post the bug report to reference.
-ATI X700 on a Asus laptop Turion Amd: [http://linuxmint.com/forum/viewtopic.php?p=8065](http://linuxmint.com/forum/viewtopic.php?p=8065)
-https://launchpad.net/ubuntu/+bug/67487

(NOTE: I haven't tried to install just so that everyone realizes this, this is all only to run a live cd. So, once you're install finishes and it tells you to remove the cd and it reboots, once grub appears, you can edit that boot line also by hitting E again, just use the same options and do that same thing again using "vesa" to get into your graphical environment. Then you can install another driver or whatnot. I might suggest ENVY, it worked wonders for my GeForce 6200 but I can't speak for ATI cards as I didn't install Edgy onto this machine. This is my winbloz xp pro box, only using it to troubleshoot friends windows install. Long story short my main ubuntu box is in pieces cause I need to install the E4300 and ASRock 775dual-VSTA motherboard I just bought to replace a Celeron 2.66 and Foxconn MB both of which worked fine I am just a computer freak. I can't wait!!!! GOOD LUCK TO ALL. We should maybe sticky this if something like this isn't already!!

---

### Post by heikor on 2007-03-22
Thank you for that long reply...
But I'm afraid it didn't help...
I tried all those boot options and also had nothing but mouse, keybord (PS/2) and monitor attached.
The last lines it gives me, before this BusyBox thing appears are:
```
[   118.817312] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   118.818083] 8139cp: pci dev 0000:00:09.0 (id 10ec:8139 rev 10) is not an 8139
C+ compatible chip
[   118.818152] 8139cp: Try the "8139too" driver instead.
[   118.822135] 8139too Fast Ethernet driver 0.9.27
[   118.823100] PCI: Found IRQ 11 for device 0000:00:09.0
[   118.823909] eth0: RealTek RTL8139 at 0xe883a000, 00:e0:7d:96:8d:b9, IRQ 11
cp: unable to open '/root/var/log/': No such file or directory
Done.
Spawning shell within the initramfs


```
And now this BusyBox appears (see above).

So is my ethernet card making problems? It's a no-name card with nothing special and always worked with all other distributions.
Also note that the computer doesn't freeze, I can still enter commands but don't know what I should type there...

---

### Post by dannyboy79 on 2007-03-23
no it's because your /root/var/log/ directory is either missing or currupt on the live cd, I am not sure how livd cd's work, if it makes a RAM image and puts everything in it, so maybe you have bad ram. So you need to either download the cd again I would say or maybe test your ram 1 stick at a time using memtest and see what happens. do you possible have another cd-rom you could try? Verify the connectors on the cd-rom also, and or try it on an ide channel by itself or if you can't, make sure you use master and slave jumper settings instead of cable select. These are my suggestions. Hope one of them helps.

---

### Post by heikor on 2007-03-24
After trying all that, I think the CD is broken... The strange thing is, that the md5-sum of the downloaded image is correct. And I burned it to 2 CDs, one didn't work at all, the other one had this error... I need to get new blank CD-Rs on Monday, and if that doesn't help, download the image again. The problem is, I can just download 2GB a month, so I would have to wait till April 1st.
Thank you for your help, and I'm sorry, I might have wasted your time...

---

### Post by dannyboy79 on 2007-03-26
that's what I stated. why don't you just request the cd's. they should be shipped to you about the same time you'd be able to download them. request dapper, edgy and fiesty all at the same time if you can. I have never had linux shipped to me because I don't have a limit.

---

### Post by tatster on 2007-03-28
Hi all,

I had this error when I built a new system about 6 weeks ago - I struggled for ages - googled, forum'd, ICQ'd and banged my head.  Many people suggested that it was my CD's but I only got the error with an Ubuntu Live CD not Xubuntu.

I found a solution that worked for me, but I can't remember off the top of my head what it was - I think it was adding --acpi=force   but I can't be certain - I have a page bookmarked at home ( I am at work at the mo)

I'll look it up and post back here.

Tat.

---

### Post by HwyXingFrog on 2007-04-08
I have tried this with Ubuntu 6.10, Ubuntu 6.10 Ultimate, Ubuntu 5.10, GParted, and Linux Rescue CD.

All of them won't install
I either get the "can't access tty; job control turned off" error, or it won't mount the cdrom

This is a brand new system that I originally had Vista installed on planning on doing a dual-boot with ubuntu ultimate 1.3.

I can't even do just Ubuntu.

I have Intel D965RYCK Motherboard, Core 2 Duo E4300, 500gig WD SATA.

Why won't any of this work?

---

### Post by dannyboy79 on 2007-04-09
> **HwyXingFrog said:**
> I have tried this with Ubuntu 6.10, Ubuntu 6.10 Ultimate, Ubuntu 5.10, GParted, and Linux Rescue CD.

All of them won't install
I either get the "can't access tty; job control turned off" error, or it won't mount the cdrom

This is a brand new system that I originally had Vista installed on planning on doing a dual-boot with ubuntu ultimate 1.3.

I can't even do just Ubuntu.

I have Intel D965RYCK Motherboard, Core 2 Duo E4300, 500gig WD SATA.

Why won't any of this work?

this to was happening to me. and I finally found the awesomest soltution ever. here is the guide ([http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)).

I owe him tons of credit otherwise I would have never installed xubuntu on my old Celeron 600mhz with 196 ram. the cdrom is only 4x4x24, and everytime the install kept failing to copy files from cd. anyway, this is not that hard. good luck

key points are:
*have to use the alternate install cd iso image. i used xubuntu edgy but it supposed to work w/ all flavors of X/K/ubuntu Dapper, Edgy, or Firsty versions according to his guide.
*Have to have 1 partition formatted as fat32 total size 1 gb. this is where you'll put the iso image along with the 2 boot files. I was doing a dual-boot w/ Win2000 so I first used Gparted Livecd to shrink my 10.2 gb hard drive down to 4.5. then I created a 1gb fat32 partition and left all the remaining space unallocated for the Edgy Install. ******NOTE***** **I would make the fat32 parititon at the END of the disk. you'll see why later.
*I used a Grub Boot Floppy. It was easy for me though because I just copied the stage1 and stage2 files from my main Ubuntu install (from another computer) I added the menu.lst to the boot floppy and made sure the menu.lst had exactly what he told us for booting to the Edgy Install .iso image.
*Creating the loop filesystem is awesome although I thought about it and I have no idea how it works but it did!!
*After the Ubuntu install finishes it tells you to remove the cd. HA, we didn't use a cd. Anyway, then simply reboot and you should go right into Ubuntu.
Don't go into Windows if you plan to get rid of that temporary 1gb fat32 partition that we saved the alternate iso image and boot files to. Only go into windows if you dual boot AFTER you have gotten rid of that fat32 partition!!  

******NOTE*******I had a huge mess with this, i went into windows and windows assigned this fat32 partition 1gb drive letter E. Well I realized that I didn't want E anymore and that I wanted to add more space to my Ubuntu install. So I exited Win2000 and booted up using the Gparted Live CD again. I deleted both the fat32 partition and the swap partition. Then I made a new 1gb swap and grew the old ext3 ubuntu partition so it added that extra 1 gig of space. In linux, that's a lot!  :-)  Make sure before you exit the gparted livecd, that you make sure your menu.lst located in your ubuntu install calls for the correct partition now since we deleted one from inbetween windows and ubuntu. Also, make sure your /etc/fstab is still correct. 

Anyway, due to me going into windows and it assigning that partition E, I have really caused a big mess. I am having to use testdisk and what not to get my partition table corrected and it's not fun. good luck

---

### Post by freeflyer57 on 2007-09-29
I am having the same problems of not being able to boot linux, but I have an real ubuntu 7.04 install disc.

---

### Post by hardy747 on 2007-10-03
I was like you, trying to set 7.04 up. I was using a live CD install onto all of a second hard drive behind win XP sp2. It failed miserably and I couldn't even start XP. so big panic. The mag from which I got ubuntu had a problem page that gave a solution of booting from the windows install CD and going to recovery console to use fixmbr . That got windows back with no further pain.
I physically disconnected the windows drive and tried again. Several times. Finally I lifted hard drive 2 out of it's slot, plugged into the primary IDE cable, where  windows used to be, and did a clean install. My take on it is that the GRUB file that does the ubuntu booting needs to be written on a primary HDD (ide 0) and doesn't write to a 2nd HDD.(ide 1) 
I went back to my original configuration of XP on disk 1 and Linux on disk 2 in a caddy tray. I set the boot up by catching F8 at startup and choosing whichever from there and both work fine. 
It was a bit scary to have 121 updates to install on first run up of ubuntu as an installed system but it all just slotted in fine.
Hope this helps you.

---

