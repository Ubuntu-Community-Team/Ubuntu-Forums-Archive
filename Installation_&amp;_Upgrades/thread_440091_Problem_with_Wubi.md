---
title: "Problem with Wubi"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by discobay on 2007-05-11
First of all I am a Linux dunce.

I thought I would try this as it seemed to be very user-friendly. First time around it installed just fine except for the lack of sound. I searched these forums with "no sound" and a suggestion was to remove something to do with "alsa" and reinstall. After the reboot I was left at the command prompt to login. After login I was left in a shell - no gui. I rebooted back into Windows XP and re-ran the Wubi-7.04-test1 executable and chose reinstall C:\wubi. This completed but I was still presented with the command prompt. I rebooted and re-ran Wubi-7.04-test1 this time choosing Uninstall C:\wubi leaving the option "Backup downloaded files" ticked. Now it won't boot with this log:

+ PREREQ=
+ . /scripts/lupin-functions
+ . /scripts/functions
+ ERR_MNT_ROOT=1
+ ERR_NO_INIT=2
+ ERR_RUN_INIT=3
+ ERR_MNT_HOST=4
+ ERR_NO_HOST=5
+ ERR_LOOP_ROOT=6
+ ERR_LOOP_HOME=7
+ ERR_LOOP_SWAP=8
+ ERR_LOOP_EXTRA=9
+ ERR_MNT_ISO=10
+ ERR_NO_ISO=11
+ ERR_INVALID_ISO=12
+ ERR_LOOP_ISO=13
+ ERR_NO_PRESEED=14
+ ERR_FAIL=15
+ ERR_MNT=16
+ ERR_LIVE_ISO=17
+ ERR_ALTERNATE_ISO=18
+ ERR_NO_FILESYSTEM=19
+ ERR_WRONG_FILESYSTEM=20
+ . /conf/param.conf
+ ROOT=/dev/loop7
+ ROOTFSTYPE=ext3
+ ISOMNT=/cdrom
+ ROOTMNT=/root
+ HOSTFOLDER=/host/wubi
+ SUITE=
+ SETUPISO=
+ HOSTMNT=/host
+ ROOTDEV=/dev/loop7
+ HOMEDEV=/dev/loop6
+ SWAPDEV=/dev/loop5
+ EXTRADEV=/dev/loop4
+ PAUSEFORDEBUG=n
+ pause_for_debug
+ cd /
+ cp_logs
+ [ -e /logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /logs/
+ [ -e /host/wubi ]
+ [ -e /host/wubi/logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /host/wubi/logs
+ [ n = y ]
+ return 0
+ grep -q /dev/loop7 /proc/mounts
+ grep -q /root /proc/mounts
+ log_success_msg NORMAL BOOT
+ _log_msg Success: NORMAL BOOT
+ echo Success: NORMAL BOOT
Success: NORMAL BOOT
+ [ ! -d /root/var/log/installer ]
+ fail 
Cannot boot wubi, probably the installation
was interrupted. Please try to run the installer again.
+ quit_usplash
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write PROGRESS 100
+ /sbin/usplash_write SUCCESS ok
+ /sbin/usplash_write QUIT
+ log_failure_msg 
Cannot boot wubi, probably the installation
was interrupted. Please try to run the installer again.
+ _log_msg Failure: 
Cannot boot wubi, probably the installation
was interrupted. Please try to run the installer again.
+ echo Failure: 
Cannot boot wubi, probably the installation
was interrupted. Please try to run the installer again.
Failure: 
Cannot boot wubi, probably the installation
was interrupted. Please try to run the installer again.
+ echo -------------------------------------------
+ echo ERROR:
+ echo
+ echo 
Cannot boot wubi, probably the installation
was interrupted. Please try to run the installer again.
+ echo -------------------------------------------
+ cp_logs
+ [ -e /logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /logs/
+ [ -e /host/wubi ]
+ [ -e /host/wubi/logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /host/wubi/logs

Should I now reinstall and untick the option "Backup downloaded files" ? Alternatively, I see that there is an iso names "ubuntu-7.04-alternate-i386" in C:\wubi\install that is 696MB in size. Could I use this to burn a bootable CD?

---

### Post by zvacet on 2007-05-11
If you have iso image just burn it like image,not data.Let burn be very slow.

---

### Post by discobay on 2007-05-11
Well the iso burned fine and the bootable CD works. However it wants to partition my hard disk which is to be expected as the CD contains Ubuntu. What I wanted was Wubi and leave my partitions and Windows XP installation intact.
I am now downloading Wubi again after having uninstalled.

---

### Post by discobay on 2007-05-11
I now have a slightly different problem. On reboot and selecting Ubuntu from the boot menu I get a lot of activity with a white on black text screen followed by some blue background activity with % bars. Then I get left with a blue screen where the bottom line is black. I can type into the black line but nothing is recognised. There is no hard drive activity and leaving for 10  minutes makes no difference. I power off and choose Ubuntu again and this time it halts at a command prompt with "previous installation incomplete" error.

Did Wubi recently change to download 7.04? Two/three days I ran the Wubi setup and I could swear that it was named 6.**. Well that installation went fine and I logged into Ubuntu and messed around a bit. There was no sound so hence this thread and now it's gone all horribly wrong. Did Wubi change in the last few days?

---

### Post by anon11 on 2007-05-11
I'm having the exact some problem as discobay. I have yet to find the solution.

---

### Post by discobay on 2007-05-11
Found it. Reinstall using the Wubi setup. When it finishes choose reboot manually. Reboot back into Windows and log into your user. Reboot into Ubuntu and it should complete the installation.
Now I need to figure out my sound problem!

---

### Post by TeatroAbsurdoAshes on 2007-09-04
Well...i am running into the same problem and found no answer...I do wondering if you- i hope- did fix the sound problem and can share with me...i have no problem with the boot section- even a strange blue-screen do jumping around in my life and the installer holds on some part of my Xp registry...Still cannot find the answer, to fix the sound problem....if you have any good solution..please: let me know it!
Thank You:
Bela Rado
'Director
TAA

---

