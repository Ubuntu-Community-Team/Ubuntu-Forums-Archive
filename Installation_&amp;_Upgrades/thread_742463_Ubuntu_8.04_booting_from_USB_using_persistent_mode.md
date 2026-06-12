---
title: "Ubuntu 8.04 booting from USB using persistent mode for saving change s"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by wilsonB on 2008-04-01
Hia all,

I easily got Ubuntu 8.04 to boot up using a 1GB usb. (750mb fat32 partition) Boots fine into live CD mode.
The remainder space formatted ext2 -rw named casper.

At boot, I type persistent and it seems to go.

But then it barks and says 
ext2-fs error (device sda2): ext2_get_inode: unable to read inode bolock - inode=93, block=19
Buffer I/O error on device sda2, logical block 0
lost page write due to I/O error on sda2
It says this for many blocks 

I've been banging my head for a while with this and hope someone could shed some light. 
Did they fix Persistent mode in 8.04?

I even (after standards didn't work) edited the init file in the compressed initrd.gz  to reflect persistent as per;
[http://www.pendrivelinux.com/2007/09/20/how-to-make-ubuntu-704-casper-persistent/](http://www.pendrivelinux.com/2007/09/20/how-to-make-ubuntu-704-casper-persistent/)

Please let me know what file log to post if that helps trouble shooting. 

Thanks so much:popcorn::popcorn:

---

### Post by Pumalite on 2008-04-01
Maybe this helps:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by wilsonB on 2008-04-01
Followed that a few times without luck..

Thanks

---

### Post by prosys49 on 2008-04-03
> **wilsonB said:**
> Hia all,

I easily got Ubuntu 8.04 to boot up using a 1GB usb. 

But then it barks and says 
ext2-fs error (device sda2): ext2_get_inode: unable to read inode bolock - inode=93, block=19
Buffer I/O error on device sda2, logical block 0
lost page write due to I/O error on sda2
It says this for many blocks

I have had the same problem with a 2GB usb! I am following the instructions on the same links. I have been thinking of getting an 8GB SD Card and putting it in a USB Reader that I have and just trying to do a straight install. Is there any reason why this would not work? Must the Live CD be copied and then set to persistent?

Thanks for any help with this. I would love to be able to carry around my Ubuntu in my pocket! :p

---

### Post by wilsonB on 2008-04-03
Prosys49,

Ya, I would love to have a working portable Ubuntu.
I know that the last release of Ubuntu had persistent broken and I gave up on it after wasting hours.
I think it might still be broke. 
 Getting an 8gb SD  and doing an actual install and not using persistent mode might be the only way to go for now. You have to make sure the USB device is 'boot' friendly. You can find tested USB devices that boot. I used to boot from a 1gb sd fine then bought a 2gb sd (Same brand and everything) and it didn't boot. It varies bios to bios to..
 I thought I saw during the install it says it needs at least 20gb of space. 

I'm surprised there aren't more help or replies to this. Are others not trying to get USB fully up and running? Not to impressed with the community support so far. I used to play with [www.puppylinux.org](www.puppylinux.org) and got more than enough help when needed and that was a smaller community.

Anyway, keep in touch and let me know what you find out. Some people got it working and there was some type of 'hack' to get the older 7 ver. of Ubuntu working.

Here's an older article for installing on a external 40gb HD w/ 7ver. of Ubuntu
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

---

### Post by Captain Giraffe on 2008-04-03
I second the motion.
I have been trying to get an ubuntu install (8gb usb stick) working for quite some time now. 
It seems to be a difficult topic, i cant imagine its not a popular one. My goal is to have the bootable usb drive completely encrypted (not boot part). My last attempt was to physically remove the hard drive, and install from an alternate CD.  No luck, the installation itself completes without problems, but ubuntu wont start.  My biggest concern is actually that I cant see the difference between a usb drive and a regular hard drive, I wish somebody would explain this, or at least give an educated guess!

---

### Post by wilsonB on 2008-04-03
BTW: did you see this link?
[http://netpatia.blogspot.com/2008/02/install-ubuntu-on-usb-stick.html](http://netpatia.blogspot.com/2008/02/install-ubuntu-on-usb-stick.html)

---

### Post by prosys49 on 2008-04-04
> **wilsonB said:**
> BTW: did you see this link?
[http://netpatia.blogspot.com/2008/02/install-ubuntu-on-usb-stick.html](http://netpatia.blogspot.com/2008/02/install-ubuntu-on-usb-stick.html)

Thanks for the link! As soon as I can get a 8GB SD I will give it a try. :p

---

### Post by wilsonB on 2008-04-04
I think I got it working..
Don't ask me how :popcorn:
Seriously, I will post my syslinux.cfg file 
been learning.

I ended up following the common basic instructions for linux usb using a 2gb sd. Also booting up with HD and FD enabled in bios. 
The bootable SD shows up as /dev/sdb1 and 2
now the casper-rw is locked. Not sure if this has something to do with it.

I can save changes.

Feel free to reply for more info and will dig around.. it's almost to good to be true.. I'll let you know.

If it is saving it on no the SD and not the HD on this system I will let you know. It might be working now because my 1gb didn't have enough space on the casper-rw partition or something. I was getting a list of errors when booting up with the 1gb sd. Sda2 write error and such..

---

### Post by prosys49 on 2008-04-05
> **wilsonB said:**
> I think I got it working..
Don't ask me how :popcorn:
Seriously, I will post my syslinux.cfg file 
been learning.

Please post this.

> I ended up following the common basic instructions for linux usb using a 2gb sd. Also booting up with HD and FD enabled in bios. 
The bootable SD shows up as /dev/sdb1 and 2
now the casper-rw is locked. Not sure if this has something to do with it.

I can save changes.

Feel free to reply for more info and will dig around.. it's almost to good to be true.. I'll let you know.

Are the instructions you followed the link you mentioned earlier or some other instructions?

Let us know more as soon as you can. :-P

---

### Post by wilsonB on 2008-04-05
I did the standard fdisk and formating on a 2GB high speed pq1 brand. 
I set the primary boot partition with boot flag and lmb mode- FAT 32 @ 750mb not labeled

The second partition using the remainder space - ext2 named casper-rw 

I followed the instructions posted on 
[http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/](http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/)
[http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install-for-linux-users/](http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install-for-linux-users/)

The difference that I can think was;
I booted on a system that had the floppy drive enabled. It even booted with/without a HD enabled/connected.
The SD works as /dev/sda or /dev/sdb  

Also used a 2gb SD instead of the 1gb and it started to work this is the only change I think that mattered.



If there is still a problem, I will check my init file and see if it's using an edited version as per;
 the init file in the compressed initrd.gz to reflect persistent as per;
[http://www.pendrivelinux.com/2007/09...er-persistent/](http://www.pendrivelinux.com/2007/09...er-persistent/)

PLEASE POST IF YOU ALSO GO IT WORKING.


I wrote my syslinux.cfg as follows (just cut / paste bellow) ;
Copy bellow this line ________________________________

DEFAULT persistent
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xFFFFFF
APPEND  file=/preseed/ubuntu.seed boot=casper persistent initrd=/initrd.gz BOOT_DEBUG=2 splash vga=785 --
LABEL persistent
  menu label ^Start Ubuntu in persistent mode
  kernel /vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper persistent initrd=/initrd.gz ramdisk_size=523264 root=/dev/ram rw BOOT_DEBUG=3 --
LABEL live
  menu label ^Try Ubuntu without any change to your computer
  kernel /vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper initrd=/initrd.gz quiet splash --
LABEL live-install
  menu label ^Install Ubuntu
  kernel /vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/initrd.gz quiet splash --
LABEL driverupdates
  menu label ^Install with driver update CD
  kernel /casper/vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper debian-installer/driver-update=true initrd=/casper/initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel /vmlinuz
  append  boot=casper integrity-check initrd=/initrd.gz quiet splash --
LABEL memtest
  menu label ^Test memory
  kernel /mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

(stop above this line) _________________________________

---

### Post by wilsonB on 2008-04-05
One problem is, since it's using the live CD, you can't remove apps or do update manager.. 
Maybe there's another way to get full package updates..
I did; 
apt-get update
and that seemed to update important stuff, but not sure if it stuck.

I was able to do many other customizing and it stuck- like res and background/user accounts/network profile/etc..

I would like to make an iso image of the SD before I mess around and break it.. it took forever to figure it out and still not exactly sure how it started working. I am learning linux the hard way though ;-)

---

### Post by prosys49 on 2008-04-05
> If there is still a problem, I will check my init file and see if it's using an edited version as per;
the init file in the compressed initrd.gz to reflect persistent as per;
[http://www.pendrivelinux.com/2007/09...er-persistent/](http://www.pendrivelinux.com/2007/09...er-persistent/)

This link appears broken. The other links work fine. It appears that these are using the LiveCD copied to the USB to boot in persistent mode. I will give these a try and let you know if it works for me. I have had Ubuntu 7.10 up and booting successfully from a 2GB pendrive using similiar instructions. However, after 3 or 4 times booting some of my programs would no longer load and after a few more times booting I would begin to get the errors you mentioned in your first post:

> ext2-fs error (device sda2): ext2_get_inode: unable to read inode bolock - inode=93, block=19
Buffer I/O error on device sda2, logical block 0
lost page write due to I/O error on sda2
It says this for many blocks 

Things would get very unstable and programs might or might not load. I would reinstall and things would be fine a few times and the problems would start over.

That is why I was wondering about doing a regular install instead of copying the LiveCD. I was hoping to wait until I can get at least an 8GB SD for this because I think doing a full install on anything smaller would seem kind of senseless.

But I will try these instructions for the 2GB card and let you know if the install is stable for me or not.

---

### Post by wilsonB on 2008-04-06
I have booted up so far about 8-10 times now with it.

I still get the error I/O write ./read errors but it still works.

Ya a actual install would be best since it's not able to remove /add new programs and updates.

How much did you find the 8gb SD for?

---

### Post by wilsonB on 2008-04-07
I think it would be helpful to have some type of check disk in place at shutdown or boot up to fix errors.

For example;
e2fsch

I'm not familiar enough with it, but if it checked and fixed errors. It might work out.
This could be added to the syslinux.cfg file.
fsck -A -V -r -y /dev/sdb2 

replace sdb2 with whatever partition your casper-rw usb partition shows up as , (depends on what devices you have on the box your booting from)

---

### Post by wilsonB on 2008-04-07
Needing a testing reference similar to this
[http://puppylinux.org/wikka/USBWorking?show_comments=1](http://puppylinux.org/wikka/USBWorking?show_comments=1)
But for 2-8GB usb devices.

---

### Post by prosys49 on 2008-04-15
> **wilsonB said:**
> How much did you find the 8gb SD for?

I have not bought the 8GB SD but I did get an 8 GB USB pendrive for 34.00.

> Needing a testing reference similar to this
[http://puppylinux.org/wikka/USBWorking?show_comments=1](http://puppylinux.org/wikka/USBWorking?show_comments=1)
But for 2-8GB usb devices. 

Thanks for that link. I will give puppy linux a try. I have a few programs that I would love to be able to get up and running on a bootable pendrive.

Still have not had time to install the 8GB it may be another week or two before I can play around with it.

---

### Post by wilsonB on 2008-04-15
Heya bro,

This was just posted... this is what you need..
[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)
:popcorn:
BUT, it reminded me that the read/writes are constant so your USB device will wear quick.

That is why persistent mode was favorable. Writes once in a while and when shutting down.

---

### Post by wilsonB on 2008-04-17
Heya,:popcorn:

Thinking about it myself. Anyone know of how to minimize the read/writes of a regular Ubuntu install? Ram Disk?

Trying to decide between for booting Ubuntu;
 
8Gb dual USB 2.0 - Small size/USB integrated
[http://www.flashcardz.com/sdhc-class-p-239.html](http://www.flashcardz.com/sdhc-class-p-239.html)
$44.99
 
16Gb A-Data - Speedy Series 16GB Compact Flash
Large copacity and compatibility
[http://www.ecost.com/Detail.aspx?edp=38476485](http://www.ecost.com/Detail.aspx?edp=38476485)
$58.99
 
What are your thoughts?

I think I might go for the SD/USB for portability. 

Still not impressed with the support for Ubuntu though. :lolflag:

---

### Post by Huss on 2008-04-18
If I followed the pendrivelinux tutorial, would I be able to take my external hard drive and boot from any computer?

At the moment I have gutsy happily installed on an external HD. It doesn't, however, like to be moved to different systems. It seems like it would be a simple thing to overcome but I don't have the experience yet I guess.

Hoping the support for this picks up

Huss

---

### Post by flipside_tech on 2008-04-24
Anyone have any luck with this?

I am hacking the init filesystem trying to get it working properly.  I can boot now, but IO errors.  I add a filesystem check to the casper script, well see what happens.  Just thought I would see if anyone else has made any headway.

---

### Post by IHATEDLINK on 2008-04-24
check this video [http://www.cnettv.com/9742-1_53-32532.html](http://www.cnettv.com/9742-1_53-32532.html)

---

### Post by flipside_tech on 2008-04-24
Thanks for the video.  Been there, done that, with 7.10.  It's broken in 8.04.

---

### Post by daddyfizz on 2008-04-28
So anyone had any luck with 8.04 and persistent mode?  I've been scouring the web but haven't found anyone who has gotten it working yet.

~Fizz

---

### Post by flipside_tech on 2008-04-28
I got it working.  I have had a number of people ask about it.  Just finished writing up a how-to: [http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to](http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to)

---

### Post by daddyfizz on 2008-04-29
Thanks a lot man! took me a little while to go through all the steps, but looks like its working great on my 8gb drive

~Fizz

---

### Post by lptr on 2008-04-29
Wanted to tell you all, that I installed Kubuntu 8.04 on a 4 GB stick (NOT AS a Live-CD installation but a FULL INSTALLATION!). Works like a charm.

 Installed without connection of any harddrive and one DVD-drive installed at IDE bus. System using 2 GB RAM.
 
On stick: Using three partitions 150/boot, 3000/, remaining/home all ext2.

The system may present after partitioning some warnings like "incompatible features", "uncorrected errors" and lack of "swap partition". Simply ignore these warnings.

In ready to install dialog press ADVANCED at the bottom of dialog. I used as boot loader installation device:

/dev/sda

That's it. Did not patch /boot/grub/menu.lst - left all as is. Reboot. Worked flawlessly.

Shut down removed stick from my Dual2Core desktop box and plugged it into my Thinkpad Z60m (P5 mobile uP). Worked!

Thanks to all who made this possible. Great job folks! I'm really hooked.

rob*

---

### Post by msktje on 2008-04-29
Hello i also managed to get my persistent hardy stick (8GB micro cruzer)working after changing the initrd file. But i experience problems at shutdown, IO buffer errors wich makes my stick almost unusable (writes faults to the partition) after some boots for example firefox locks up with no reason (no high cpu load, the system just hangs for a moment).
I changed my syslinux, removed splash en quiet so that i can view the system messages. I also had that problem with gutsy.
I found [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/125702](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/125702). but is there not another way? edgy isn't supported anymore. For now i formated my casper-rw as ext3 and let the system check it at every boot. But it is not 100% 
Does someone knows a better solution and are there other people with the same problem?

greetz FW

---

### Post by georgeen on 2008-05-07
Yes, I've used Ubuntu since 6.06 and this "feature" is very useful and since 7.04 is a nigthmare to achieve, always is some kind of bug that avoid that persistent on USB HDD were a reality. Even I vote in some Ubuntu wishes, but nothing. This idea is better than Win counterpart Mojo, because I don´t need nothing to start, and UbuntuUSB project is dead. Please if some one knows the REAL solution for that, publish.

I tried with pendrive linux, solution (but for 8.04 doesn´t have persistent), the wiki solution, doesn't work (initramfs or something like that on a text mode), another that modify the init.gz/casper/scripts/... I don't remember. Nothing. I have 2 years and only with 7.04 I had some success, but after some reboots, a lot of errors and crashes :confused: I stop and wait for hardy (in gutsy the same bug hasn´t been corrected). And I don´t understand why this "feature" isn´t a priority, is a very impressive way to do marketing to Ubuntu and very useful carry out all the software stuff on a pocket.

---

### Post by lptr on 2008-05-08
> **msktje said:**
> Hello i also managed to get my persistent hardy stick (8GB micro cruzer)working after changing the initrd file. But i experience problems at shutdown, IO buffer errors wich makes my stick almost unusable (writes faults to the partition) after some boots for example firefox locks up with no reason (no high cpu load, the system just hangs for a moment).
I changed my syslinux, removed splash en quiet so that i can view the system messages. I also had that problem with gutsy.
I found [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/125702](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/125702). but is there not another way? edgy isn't supported anymore. For now i formated my casper-rw as ext3 and let the system check it at every boot. But it is not 100% 
Does someone knows a better solution and are there other people with the same problem?

greetz FW

Hello,

If I do understand it right, you are using a Live-CD copy booting from your stick with some room on a seperate partition to get persistence feature. 

Maybe you are using a crappy USB stick? The other point you have to remeber is that you are on a device that has only limited write cycles (although the number of writes to the flash device is very high).

ext3 is a Journaling File System (JFS). JFSs are known to have lacy commit feature. Means, is writing more often as for example ext2. This is by design. You should use for your USB installation ext2. ext2 follows lacy write design goal. 

Regarding a better solution
My suggestion is clearly: Install Ubuntu directly on a stick (see my short description some lines above). 8 GB is much enough, you have a full installation with all features you are used to have, when you are installing it directly to a harddisk. No hacks, no tweaks... all possibilities are waiting for you. Having fun :)

rob*

p.s. I predict this will be the MS desktop killer.

---

### Post by msktje on 2008-05-10
yes, i boot via live cd on my stick and a persistent partition.
I work on a laptop so it is difficult to deconnect all the hard disks.
I am affraid that i will mess up my whole computer.
I use ext3 because it has better recovery methods.
By the way the lag on firefox 3.0 was a bug of firefox. It was fixed with the updates.

greetz fw

---

### Post by craigc on 2008-05-16
I Have a problem with the persistent thing.  I can boot from my 8GB USB into "Persistent mode" however then I go to youtube, install flash player check the video is working then reboot and yep you geussed it no flash.

Had a little dig around and my casper partition doesnt appear to be mounted.  Looking at this partition under partition editor the casper partition appears as an unknown filesystem.

Is this normal? or is caspr-rw supposed to be mounted and used as my home folder etc?

Thanks

---

### Post by msktje on 2008-05-18
Are you sure that the persistent thing is working? If you add icons to the top bar, are they there still after reboot?
Normaly you can't see casper-rw as a partition in nautilus. I've checked with partition editor and there it is ext3.
I let it check everytime at boot for defect because everytime there are errors when shutting down.
I also found that there are some syslinux.cfg on the internet that do not work.

here is my syslinux.cfg

DEFAULT usb
GFXBOOT bootlogo
APPEND preseed/file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw splash --
LABEL usb
  menu label ^Start Ubuntu in persistent mode
  kernel vmlinuz
  append bootkbd=be console-setup/layoutcode=be preseed/file=preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw --
LABEL live
  menu label ^Start or install Ubuntu
  kernel vmlinuz
  append bootkbd=be console-setup/layoutcode=be preseed/file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel vmlinuz
  append preseed/file=preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw splash --
LABEL check
  menu label ^Check CD for defects
  kernel vmlinuz
  append boot=casper integrity-check initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw splash --
LABEL memtest
  menu label ^Memory test
  kernel mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 50
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

With this syslinux.cfg you can see the bootmessages and it uses azerty keyboard. If you don't won't azerty just erase bootkbd=be console-setup/layoutcode=be 

I also found that there are some packages that can't be updated f.e. hal and i think also mount. The update for xmlrunner for firefox is installable.
I format my stick with partition editor. and then i use mkfs.ext3 -b 4096 -L casper-rw /dev/sdx2 to label my ext3 partition.
I let it check everytime with tune2fs -i 1 /dev/sdx2 i think that the partition has to be unmounted to do this command. I'm not sure about that command but when you do mkfs.ext3 -b 4096 -L casper-rw /dev/sdx2 the terminal propose the wright command.

---

### Post by yogo on 2008-05-18
I got persistent going in 8.04 after two previous failures, not to do with the pendrive site but moreso the HH iso. Twice I had problems with the iso when checking disc for integrity, one time it found one error, another time it found two errors.

Anyways, it is on a one gig memory stick and the +750 is fat 16 and the other partition is ext2.

It does work to save settings as my panels have changes saved as well as desktop background.

I am assuming there is no need for me to use the method from flip_side tech?

I can say this, it was really simple to use the tutorial from pendrivelinux site. The two times with errors were due to a bad iso image.

Oh yeah, I did try it once via terminal in which you retrieve the iso, that took over two and a half hours following the pendrive tutorial and got stuck on step 16. 

[LIST=1]
[*]Type **cp -rfv casper dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines install/mt86plus /media/ubuntu8**
[/LIST]
 It wanted to install in a directory /media/ubuntu8 but that directory did not exist so I was not able to but from the live cd it worked perfect.

---

### Post by crakarjax on 2008-05-18
hmmm... im getting (initramfs) with the persistant option, but a working livecd without it.  What would cause this??

---

### Post by msktje on 2008-05-19
@ crakarjax : try the initrd.gz from here:
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192)
i haven't tried it but they say it works. I changed my file like Dafydd Walters said (comment in [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192) )

---

### Post by craigc on 2008-05-20
crakarjax

I had the same problem and it was the initrd.gz that solved that issue.  i extracted mine and changed a line in the config file then re-zipped it.  (I removed the permissions command (chmod=755 or something) from the "mount cowdevice" line.

msktje

Was prettu sure the persistent mode was not functioning.  I would even just create a new folder on the desktop and reboot to no effect.  Thanks for posting the config, I will take a look and get back to you on that one.

Soo close i think... a little more persistence and ill be there :D

---

