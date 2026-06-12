---
title: "can't install ubuntu 10.04 netbook"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by canetti on 2010-06-07
I'm unable to install Ubuntu 10.04 netbook-i386.iso on a Toshiba N205 netbook from a flash drive.  The installation starts ok, but everytime I get to the third step, Keyboard Layout, the installation hangs, even if the netbook is connected to my wireless LAN.  I tried choosing the suggested option, USA, when my actual preferred keyboard, USA-Alternative international, didn't work, but that didn't work either.  The netbook has Windows 7 Starter installed on it.

---

### Post by gpetrov on 2010-06-07
Same problem!
I have ubuntu 7.04 on my netbook.
I'm trying to install 10.04 netbook remix from USB stick, but instalation hangs on 3rd step indefenetely. ?!?!

---

### Post by cphuntington97 on 2010-06-09
Just wanted to chime in that my 10.4 netbook install also hangs after selecting a keyboard layout and clicking "Forward."

Installing from USB flash drive. Asus eee s101.

---

### Post by cphuntington97 on 2010-06-09
I've been reading that this may be a kernel bug having to do with ssds. Here's some log that might be helpful:

Jun  9 18:47:16 ubuntu ubiquity[2655]: switched to page console_setup
Jun  9 18:47:28 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Jun  9 18:47:28 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Jun  9 18:47:28 ubuntu ubiquity[2655]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Jun  9 18:47:28 ubuntu ubiquity[2655]: Step_before = stepKeyboardConf
Jun  9 18:47:28 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Jun  9 18:47:29 ubuntu ubiquity: Backtrace has 14 calls on stack:
Jun  9 18:47:29 ubuntu ubiquity:   14: /lib/libparted.so.0(ped_assert+0x2a) [0x9f9f4a]
Jun  9 18:47:29 ubuntu ubiquity:   13: /lib/libparted.so.0(+0x424b7) [0xa314b7]
Jun  9 18:47:29 ubuntu ubiquity:   12: /lib/libparted.so.0(+0x432c7) [0xa322c7]
Jun  9 18:47:29 ubuntu ubiquity:   11: /lib/libparted.so.0(+0x445bc) [0xa335bc]
Jun  9 18:47:29 ubuntu ubiquity:   10: /lib/libparted.so.0(+0xf7f1) [0x9fe7f1]
Jun  9 18:47:29 ubuntu ubiquity:   9: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0xa02072]
Jun  9 18:47:29 ubuntu ubiquity:   8: /lib/libparted.so.0(+0x45f53) [0xa34f53]
Jun  9 18:47:29 ubuntu ubiquity:   7: /lib/libparted.so.0(+0x4614f) [0xa3514f]
Jun  9 18:47:29 ubuntu ubiquity:   6: /lib/libparted.so.0(ped_disk_new+0x75) [0xa02e55]
Jun  9 18:47:29 ubuntu ubiquity:   5: parted_server() [0x8055644]
Jun  9 18:47:29 ubuntu ubiquity:   4: parted_server() [0x8055840]
Jun  9 18:47:29 ubuntu ubiquity:   3: parted_server() [0x805609b]
Jun  9 18:47:29 ubuntu ubiquity:   2: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xe12bd6]
Jun  9 18:47:29 ubuntu ubiquity:   1: parted_server() [0x804a0c1]
Jun  9 18:56:29 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Jun  9 18:56:30 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Jun  9 18:58:51 ubuntu ubiquity[4945]: Ubiquity 2.2.24
Jun  9 18:58:55 ubuntu ubiquity[4945]: log-output -t ubiquity laptop-detect
Jun  9 18:58:56 ubuntu ubiquity[4945]: log-output -t ubiquity laptop-detect
Jun  9 18:59:02 ubuntu ubiquity[4945]: switched to page language
Jun  9 18:59:07 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
Jun  9 18:59:07 ubuntu localechooser: info: Set localechooser/languagelist = 'en'
Jun  9 18:59:07 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jun  9 18:59:07 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jun  9 18:59:07 ubuntu ubiquity[4945]: switched to page language
Jun  9 18:59:17 ubuntu localechooser: info: Language = 'en'
Jun  9 18:59:17 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Jun  9 18:59:17 ubuntu localechooser: info: Set debian-installer/language = 'en'
Jun  9 18:59:17 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jun  9 18:59:17 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Jun  9 18:59:17 ubuntu localechooser: info: Default country = 'US'
Jun  9 18:59:18 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Jun  9 18:59:18 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jun  9 18:59:18 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jun  9 18:59:18 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'en_US.UTF-8'
Jun  9 18:59:24 ubuntu ubiquity[4945]: Step_before = stepLanguage
Jun  9 18:59:26 ubuntu clock-setup: rdate: ntp.ubuntu.com: Name or service not known
Jun  9 18:59:27 ubuntu ubiquity[4945]: switched to page timezone
Jun  9 18:59:39 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
Jun  9 18:59:39 ubuntu localechooser: info: Set localechooser/languagelist = 'en'
Jun  9 18:59:39 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jun  9 18:59:39 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jun  9 18:59:39 ubuntu localechooser: info: Language = 'en'
Jun  9 18:59:39 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Jun  9 18:59:39 ubuntu localechooser: info: Set debian-installer/language = 'en'
Jun  9 18:59:39 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jun  9 18:59:39 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Jun  9 18:59:39 ubuntu localechooser: info: Default country = 'US'
Jun  9 18:59:39 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Jun  9 18:59:39 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jun  9 18:59:39 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jun  9 18:59:39 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'en_US.UTF-8'
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Jun  9 18:59:40 ubuntu 50mounted-tests: debug: mounted as ntfs-3g filesystem
Jun  9 18:59:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jun  9 18:59:40 ubuntu 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Jun  9 18:59:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jun  9 18:59:40 ubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Jun  9 18:59:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jun  9 18:59:40 ubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Jun  9 18:59:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jun  9 18:59:40 ubuntu 20microsoft: debug: /dev/sda1 is a NTFS partition
Jun  9 18:59:40 ubuntu 20microsoft: result: /dev/sda1:Microsoft Windows XP Home Edition:Windows:chain
Jun  9 18:59:40 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Jun  9 18:59:40 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Jun  9 18:59:40 ubuntu 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Jun  9 18:59:40 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
Jun  9 18:59:40 ubuntu 10freedos: debug: /dev/sdb1 is a FAT32 partition
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
Jun  9 18:59:40 ubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
Jun  9 18:59:40 ubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
Jun  9 18:59:40 ubuntu 20microsoft: debug: /dev/sdb1 is a FAT32 partition
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
Jun  9 18:59:40 ubuntu 30utility: debug: /dev/sdb1 is a FAT32 partition
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Jun  9 18:59:40 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdc1
Jun  9 18:59:41 ubuntu 50mounted-tests: debug: mounted as vfat filesystem
Jun  9 18:59:41 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jun  9 18:59:41 ubuntu 10freedos: debug: /dev/sdc1 is a FAT32 partition
Jun  9 18:59:41 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jun  9 18:59:41 ubuntu 10qnx: debug: /dev/sdc1 is not a QNX4 partition: exiting
Jun  9 18:59:41 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jun  9 18:59:41 ubuntu macosx-prober: debug: /dev/sdc1 is not an HFS+ partition: exiting
Jun  9 18:59:41 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jun  9 18:59:41 ubuntu 20microsoft: debug: /dev/sdc1 is a FAT32 partition
Jun  9 18:59:41 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jun  9 18:59:41 ubuntu 30utility: debug: /dev/sdc1 is a FAT32 partition
Jun  9 18:59:41 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jun  9 18:59:41 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Jun  9 18:59:41 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Jun  9 18:59:41 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Jun  9 18:59:41 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Jun  9 18:59:41 ubuntu ubiquity[4945]: Step_before = stepLocation
Jun  9 18:59:42 ubuntu ubiquity[4945]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Jun  9 18:59:42 ubuntu ubiquity[4945]: switched to page console_setup
Jun  9 19:00:01 ubuntu ubiquity[4945]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Jun  9 19:00:01 ubuntu ubiquity[4945]: Step_before = stepKeyboardConf
Jun  9 19:00:01 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Jun  9 19:00:02 ubuntu ubiquity: Backtrace has 14 calls on stack:
Jun  9 19:00:02 ubuntu ubiquity:   14: /lib/libparted.so.0(ped_assert+0x2a) [0x799f4a]
Jun  9 19:00:02 ubuntu ubiquity:   13: /lib/libparted.so.0(+0x424b7) [0x7d14b7]
Jun  9 19:00:02 ubuntu ubiquity:   12: /lib/libparted.so.0(+0x432c7) [0x7d22c7]
Jun  9 19:00:02 ubuntu ubiquity:   11: /lib/libparted.so.0(+0x445bc) [0x7d35bc]
Jun  9 19:00:02 ubuntu ubiquity:   10: /lib/libparted.so.0(+0xf7f1) [0x79e7f1]
Jun  9 19:00:02 ubuntu ubiquity:   9: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0x7a2072]
Jun  9 19:00:02 ubuntu ubiquity:   8: /lib/libparted.so.0(+0x45f53) [0x7d4f53]
Jun  9 19:00:02 ubuntu ubiquity:   7: /lib/libparted.so.0(+0x4614f) [0x7d514f]
Jun  9 19:00:02 ubuntu ubiquity:   6: /lib/libparted.so.0(ped_disk_new+0x75) [0x7a2e55]
Jun  9 19:00:02 ubuntu ubiquity:   5: parted_server() [0x8055644]
Jun  9 19:00:02 ubuntu ubiquity:   4: parted_server() [0x8055840]
Jun  9 19:00:02 ubuntu ubiquity:   3: parted_server() [0x805609b]
Jun  9 19:00:02 ubuntu ubiquity:   2: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x553bd6]
Jun  9 19:00:02 ubuntu ubiquity:   1: parted_server() [0x804a0c1]

---

### Post by iskatyel on 2010-06-10
I have the same problem.  From what I have been reading (and what your log shows) this is actually the partitioner failing.  Some have encountered the same problem while using laptops with cdrom drives and were able to work around it by removing all SD and USB drives.  Obviously this is not useful for those of us without cdrom drives.  

To test this, though, I booted to the live disk from a USB stick, started the install and then pulled the USB stick before clicking continue on the keyboard selection screen.  The partitioner came right up and I was able to finish the install setup until it failed when it tried to access the data on the USB stick I had pulled.  

I created an alternate CD usb stick using unetbootin and with the text driven menus I could see that the install progresses to exactly 43% of the scanning partitions stage and then freezes.  Has anyone found a workaround when you have no cdrom drive?  Has anyone without a cdrom drive had a successful install?  

For reference, I am attempting to install on a Lenovo X61 tablet, 100GB SATA that currently has a full system encrypted truecrypt partition.

---

### Post by pctipsuk on 2010-06-11
I have also wasted a lot of time on this problem.
Basically the partitioner does not start as it should after the keyboard selection page.
Worryingly I have also had exactly the same problem with the full desktop version of 10.4.
So I have downloaded the 9.10 netbook remix and it has installed perfectly.

---

### Post by iskatyel on 2010-06-11
Found two bugs on Launchpad, [https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/572849](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/572849) and [https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/572878](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/572878)

I also tried it with another HDD that has a single NTFS partition on it with the same results, so the encrypted partition is not the problem.

---

### Post by ozdroggy on 2010-06-12
I am a complete newbie with Ubuntu so excuse any wrong terms. I have EXACTLY the same problem on a Dell Inspiron Mini 1012 but I did notice a 'crash notice' which mentioned 'parted_server' as the problem - which I note is in the 'log' posted above. I was running quite hapilly from the USB but have now decided to install to the HDD as I am so impressed with Ubuntu. Looks like I may have to wait until the problem is solved.

---

### Post by iskatyel on 2010-06-15
Okay, I got it to work.  I followed the advice [here](http://ubuntuforums.org/showthread.php?p=9467124) and tried using a different USB stick.  It worked perfectly and I am now working from my shiny new Lucid system.

---

### Post by pctipsuk on 2010-06-16
I will go out tomorrow and buy another make of USB stick to try this solution!

But if it does work, and it seems as though others have found that it does, then why?

Why does my USB drive work perfectly with 9.10 but not with 10.04?

Has the partition manager version been changed in 10.04?  If so can a version of 10.04 be produced with the old partition manager - it seems as though it would work with a lot more hardware!

---

### Post by pishta on 2010-06-16
I tried to install on a Inspiron 8000 600Mhz 512MB from either distro netbook or desktop. Neither got me through the keyboard, just hung. So I tried the "alternate" setup CD. Looks more command line and not so pretty, but boy did it race through the install screens! I had the thing up and running in about 20 minutes and this laptop is SLOW...either the CD/DVD is slow or the pokey 600/500 P3 chip. I recommend the "alternate" install if you are having trouble.

---

### Post by hobocaver on 2010-06-17
Hi  my name is hobocaver, and I did manage a successful UNR install on an Asus 1201T-MU that came w/o an OS. I had many of the same issues, but finally got it to work. My install on usb, using unetbootin, did not seem to work; I tried it twice, then got an idea from these forums that fixed it. It seems that the MBR was not there, but UNR was, so I used a dd command to fix the MBR, and voila, it booted. UNR looks and works beautifully on this laptop, even wireless and 3g worked right off. Thanks to the person who posted that idea, my blood pressure went way down.

---

### Post by deshowell on 2010-07-15
I had all these problems on my Acer Aspire One.  It has no HD and the installation stopped at step three every time.  It runs perfectly from the USB - it simply wouldn't install.  Just before I gave up I tried to install the earlier version 9.10 - this worked perfectly and installed very smoothly. After a bit of practice to make sure I was happy I selected  upgrade and asked it to upgrade to 10.04.  This took few hours but worked perfectly and I now have lucid lynx running smoothly.  The problem seems to be in the installation routine for 10.04.  You can get round it by going via 9.10.
Des

---

### Post by therrmann on 2010-07-22
I've tried to install 10.04 netbook version on my Asus 1000H, which runs an older netbook remix (can't recall which) just fine.  Ran the bootable USB program from my other Linux box onto a 4G USB stick, but did not want to erase the rest of it.  Would not even recognize the stick as bootable:  bypassed and went to the GRUB menu on the hard disk.   Maybe I'll look up what Hobocaver was referring to:  any more details?  As an alternate, I made a CD image of the ISO and tried loading it from my external CD. (That's how I installed the current dual-boot system.)  I loads after a LONG time but then wants me to log in.  Huh?  There's no user name or password established, so of course I can't.  It doesn't give me the option of installing at all.  I've never been so mystified, and I started using Linux by installing Debian from floppies years ago.

---

### Post by Avidon on 2010-10-22
I was getting the same problem as reported here - keyboard selection screen hanging when clicking next (USB install of ubuntu netbook remix 10.04).

After being completely stumped by this problem for ages, I decided to try an experiment.

I clicked next on the keyboard selection section, as normal, only this time I quickly pulled out the USB stick just after clicking - and it worked! I got to the drive formatting screen! I quickly plugged the USB stick back in and continued the installation as normal without any other problems!

Hope this helps!

---

