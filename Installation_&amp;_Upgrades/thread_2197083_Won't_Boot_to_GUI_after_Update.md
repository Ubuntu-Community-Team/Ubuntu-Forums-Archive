---
title: "Won't Boot to GUI after Update"
date: 2014-01-02
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2014-01-02
I updated my system and now it always boots to a tty1 instead of the GUI. I tried booting in recovery mode, repairing broken links, but it always returns to tty1 command line login. I also tried booting to safe graphics mode, but now it always boots to the following command line:
[FONT=Courier New]> BusyBox v1.18.5 (Ubuntu 1:1.18.5-1 ubuntu 4.1) built-in shell (ash)
(initramfs)
[/FONT]
The GRUB says the latest version is 3.2.0-57-generic and I tried the previous version 3.2.0-56-generic with the same result.

I had to boot to my Windows 7 drive to get here. What happened and how do I restore my system so I can boot back to the GUI?

---

### Post by Bashing-om on 2014-01-02
HDTimeshifter; Hi !

Difficult to say; 
Booting to a busy box: Only happens on occasion I would suspect a "race" condition. Happens on my system, I ignore it and "exit" and reboot when it does happen. I  have yet to see any adverse effects from this practice.

Else it indicates that grub cannot find the remaining boot code, or that the 2nd stage code is corrupt.
Try and check the file system:

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s);
```

sudo fdisk -lu

```
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
```

sudo e2fsck -f -y -v /dev/sda1

```

Else if: (re-)install grub. That advise pending knowing what operating systems are installed and how/where the bootloader is installed. Maybe no big deal at all .. UEFI. (??) well that is a whole new ball game !

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by HDTimeshifter on 2014-01-02
I also tried several 3-finger reboots as well as a hard reboot and a 5-second power button off reboot without success.

Then I decided to download Ubuntu 13.10, burn a DVD, and upgrade my system. Well the upgrade seemed to get stuck at saving packages and files for several hours. I let it run for a couple of hours, then had to go to bed to get a couple hours sleep. This morning it was still stuck (after about 4 hours), so I started thinking it is a disk problem. I'm surprised Linux gives no warnings of serious disk errors like Windoze does (by going to the blue screen of death with error messages).

If it's still stuck when I get home from work tonight, I'll try running e2fsck. If the disk is foobar'd, then it may be time to buy an SSD - just not sure if I can do a dual boot SSD with Ubuntu and Windows 7 - maybe I'll just make the SSD an Ubuntu boot drive and leave Windows on the remaining disk since I only boot to Windows once in a blue moon (for problems like above or when I have to remote in to work via Citrix since Citrix doesn't like Ubuntu).

Thanks Bashing-om!

---

### Post by Bashing-om on 2014-01-02
HDTimeshifter; Well.

As you have now tried to install 13.10, let's forget about fixing that prior install and concentrate on getting 13.10 to complete.
When you downloaded the .iso file did you verify the file ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Next did you check the disk's integrity (boot options menu on the disk) ?
Presently, I do not think a file system check is pertinent with the "partial" upgrade, may just confuse things more.

When you attempt a boot now with 13.10, how far do you get in the boot process ? Can you boot into a recovery mode or to a terminal (TTY1) ?

Are there important files on the prior install that you need to try and save prior to proceeding with the salvage operation ?

And Mind you, I am no longer Windows literate, and do not want to be !

I am running 13.10 (u)buntu and (L)ubuntu, and I must say I am impressed !

[INDENT][INDENT]see what it takes to get ya up on 13.10
[/INDENT][/INDENT]

---

### Post by HDTimeshifter on 2014-01-02
I didn't think to verify the checksum on the .iso, but did select the checkbox to verify the burn of the DVD.

By "boot option menu on the disk to check integrity", do you mean my boot ROM or a GRUB option or the Ubuntu install disc?

I'll try booting 13.10 when I get home from work tonight.

I try and manually back up all my data files to my Windows drive as well as my Ubuntu file server in the basement (although the file server is set to sleep after an hour of inactivity so it's not always so up to date). Someday I'll upgrade my file server with more disk space and set up an automated backup. I can copy Ubuntu files to my Windows drive with SAMBA but not the other way around as Windows can't see the Linux disk or I'd copy everything over from Windows to make sure the backups are current. I definitely believe in duplicate backups with my experience once upon a time in college where my external 10 MB! Unix drive crashed while I was backing up my program to floppy and as a result lost everything but some old dot matrix hard copy - I had to abandon the program and take a ZERO on it and get a D- on my CS course as a result. My boss, OTOH, used to rely on storing shared data on the network drive which is only backed up weekly. I migrated all my shared data to the network drive that is backed nightly as well as back up all my local data to that drive.

I wish I could abandon Windows and all things MS and just use open source, but sadly, work is an MS shop... :(

---

### Post by Bashing-om on 2014-01-02
HDTimeshifter; Roger all !

We will pick this back up when ya get the time. Apparently you know your way around, so I do not anticipate getting 13.10 installed to be too big of a deal.

If you do not find me active on this forum when you get back, Holler at me on IRC: #ubuntu. I bounce back and forth.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by HDTimeshifter on 2014-01-03
When I got home last night it was still stuck saving packages, so I rebooted it, and the GRUB showed the old 3.2.0-57-generic Ubuntu but it went back to the tty1 command line login. I verified the .iso checksum then ran booted live and ran e2fsck, fixing a block, so it appears it was a disk error. I tried re-installing 13.10 again, but it got stuck on logging into Ubuntu One for a couple hours. I wish the install process would have a progress bar and text output (like when you click on "details" for updates) of what's happening so you know something is going on and not locked up as the spinning cursor tells you nothing. I rebooted it again and the GRUB showed just "ubuntu" as the latest version, but it went back to the tty1 login, so I re-installed 13.10 again and this time the install completed.

13.10 now boots into the GUI, but I noticed that my PC doesn't wake up from the screensaver or sleep mode. One time it woke up with a blank screen and just the mouse pointer. The other time it woke up from sleep mode but there was no log-in field. Is this a bug in 13.10 that doesn't handle wake on screensaver or hibernation correctly?

---

### Post by Bashing-om on 2014-01-03
HDTimeshifter; Making progress !

As to problems with "waking up" ; Are you dual booting with Windows ? Many times we see where Windows has not relinquished control of the hard ware, particularly "hibernation".

Might also suggest that you check the hard drive for faults -> disk utility and run the S.M.A.R.T. test .

Then if problems are still existent we can do some more trouble shooting to determine the cause(s).

Learning to read the log files is a worth while experience .

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by j-timothy-y on 2014-01-03
Same issue here, updated ubuntu 12.04 and kubuntu 13.10

although xubuntu 13.10 updated fine

ubuntu 12.04 nvidia 302 kernel 3.2.56 to 58 - bricked
kubuntu 13.10 nvidia 331.19 to 331.20 and kernel 3.11.0.14 to .15 - bricked

ubuntu 12.04 updated nvidia to 331 and booting 3.2.56 - resolved

        ](*,)

---

### Post by HDTimeshifter on 2014-01-03
I boot either to Ubuntu or Windows, but not both at the same time (I reboot to switch OSs). Windows is on a separate drive. I've never had problems switching between the two.

Yes, I'm wondering if there are still disk problems. I'll run a SMART test as well as a full disk test with the disk utility.

Which log files should I look at?

Thanks.

---

### Post by HDTimeshifter on 2014-01-03
> **j-timothy-y said:**
> Same issue here, updated ubuntu 12.04 and kubuntu 13.10

although xubuntu 13.10 updated fine

ubuntu 12.04 nvidia 302 kernel 3.2.56 to 58 - bricked
kubuntu 13.10 nvidia 331.19 to 331.20 and kernel 3.11.0.14 to .15 - bricked

boot to previous kernel has no affect      ](*,)

I wonder if the wake from screensaver or hibernate is an nVidia support problem as I have an nVidia GeForce 9500GT card. It was strange that one single update to 12.04 would have bricked my system.

---

### Post by Bashing-om on 2014-01-03
HDTimeshifter; Well.

When exiting Windows, shut it down, do not hibernate windows, and then fire up ubuntu. Else, Windows will maintain control.

Log files:
Display problems look at ;
/var/log/Xorg.o.log
~/..xsession-errors
Hardware problems ;
/var/log/syslog
/var/log/kern.log
```

sudo dmesg

``` Realtime, or to see what has transpired:
```

cat /var/log/dmesg

```

In the logs one is interested in "ww" and "EE" (warning and error) .. Seeing the processes in and of it's self is interesting!

Also awaiting the SMART results.

OT: I must be away from the keyboard for a few hours at this time, I will see how you are doing later in my evening.

[INDENT][INDENT]it's all in a process
[/INDENT][/INDENT]

---

### Post by HDTimeshifter on 2014-01-03
Bashing-om,

I always reboot before switching OSs, never from hibernation. I actually select the other drive to boot first in SETUP. It wasn't until these problems a couple days ago that I noticed the GRUB option to load Windows instead of Ubuntu.

I also had problems with my file server hanging whenever I tried to boot to a 20" CRT. I had hooked up a 15" LCD, but when I tried going back to the CRT, the system hangs. I have another thread here from a month ago where someone was helping me and I didn't see anywhere in the Xorg logs where it was using a specific driver. Here is a link to that include the log file:  [http://ubuntuforums.org/showthread.php?t=2190081&p=12862150#post12862150]("http://ubuntuforums.org/showthread.php?t=2190081&p=12862150#post12862150")

I'm heading up to the mountains for the weekend for skiing right after work otherwise would run the SMART test and full disk test overnight/over the weekend. It'll have to wait until Sunday night.

---

### Post by Bashing-om on 2014-01-03
HDTimeshifter; Hey,

Your pastie did not take for the xorg file.
```

sudo apt-get install pastebinit
cat /var/log/Xorg.0.log | pastebinit

```
Copy and paste the URL from the last command into your next post.(ctl-c, ctl-v (??)) might work. - ctl-insert (??)

As to the "/etc/X11/xorg.conf" It's use is often depreciated - if it exist it will be used . You may or may not have that control file. But let's see what is:
To see your graphics card and info:
```

ls -la /etc/X11/xorg.conf ##to see if that file exist
sudo lshw -C display
lspci -nnk | grep -iA3 vga

```


[INDENT][INDENT]in pursuit of answers
[/INDENT][/INDENT]
Might also take a look and see what is set in bios for "hibernation/power down" settings.

---

### Post by HDTimeshifter on 2014-01-06
Hmm, when I click on the pasty, it comes up. I re-posted it inline:  [http://ubuntuforums.org/showthread.php?t=2190081&p=12893266#post12893266]("http://ubuntuforums.org/showthread.php?t=2190081&p=12893266#post12893266")

When I turned on (or resumed my PC - can't remember what state it was in) last night, it displayed an error message relating to graphics or xorg and I let it try and fix it as well as send in the crash info to Ubuntu. It seems like it fixed it as the next time I resumed from hibernation, the log-in prompt came up and I was able to log-in ok.

---

### Post by Bashing-om on 2014-01-06
HDTimeshifter;
From your /var/log/Xorg.0.log :
> 
 44804.284] (II) AIGLX: Suspending AIGLX clients for VT switch

I can not explain why the system keeps cycling !

PCI is identified, card is identified and the driver, i915, is assigned. Maybe the system worked the kinks out (?)

This is a smart system, but; Let us know if the problem continues.

[INDENT][INDENT]sometimes I wonder othertimes I do not know
[/INDENT][/INDENT]

---

