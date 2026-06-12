---
title: "Segmentation fault, dropping to BusyBox shell"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by ager-wick on 2006-06-17
Hi!

I'm fairly new to Linux, having tried only a couple of distributions before deciding on Kubuntu, which I am now very comfortable with. However, as a recent (6 months) windows convert, I don't yet have the skills for fixing everything when I have really messed up the box. My Kubuntu system has survived with only minor problems since newyear, which is probably a personal record for any operating system.

Now my system is "bricked" to use a router expression, or to put it another way, it a vegetable! It does nothing.
I don't even get the boot loader (I think, since I reboot something like every other month, I can't really remember how it looked).
This is what I get after the BIOS has done it's stuff:
  Booting ´Ubuntu, kernel 2.6.12-10-386 ´

root  (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel  /boot/vmlinuz-2.6.12-10-386 root/dev/hdc1 ro quiet splash
   [Linux-bzImage, setup=0x1c00, size=0x124d05]
initrd  /boot/initrd.img-2.6.12-10-386
 [linux initrd @ something something] (can't read it coz it's too fast and Pause doesn't work here)
savedefault
boot
Uncompressing Linux... OK, booting the kernel

Then the screen goes blank for a second and the next thing I see is a screenfull of Segmentation fault and a shell on the bottom. To be exact:
Segmentation fault
Segmentation fault
Segmentation fault
(repeated 22 times in total)
Segmentation fault
ALERT! /dev/hdc1 does not exist. Dropping to a shell!


BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter ´help´ for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

Side note: I'm pretty sure this is the same shell I'm getting at my Linksys WRT54GL router, but I would really like my desktop box to do more than that!

It is correct that it attempts to access /dev/hdc1, not /dev/hda1, as the hard drive is the first disk on the second ide controller. Please correct me if I'm wrong. Anyway, I haven't changes this, adn ti worked before.

Anyway, the cause is probably what I did yesterday: I ran synaptic and updated loads of stuff. My guess is that the new Dapper repositories caused that. Anyway, being a bit sceptical about upgrades that required uninstalling xserver, I skipped those for now, upgrading about 1/3 of the packages. I wrote down some of the packages that had to be uninstalled so I could reinstall these later when everything was up to date:
hal
hplip-base
hplip-ppds
ivman
k3blibs
k3b-mp3
kaffeine
kaffeine-gstreamer
konq-speaker
libapache2-mod-php5
mplayer-k6
openoffice.org2-kde (I know this one is not needed anymore)
totem-xine
wireless-tools
mysql-common-4.1
there were more, but I didn't see them as important, so I sisn't waste any ink writing them down.

Here are the outputs of a few ls commands:
# ls
dev bin etc modules scripts usr proc var
root conf lib sbin init sys tmp

#ls sys/bus
platform eisa pnp serio
pci MCA pci_express

#ls sys/class
pci_bus tty graphics misc input net mem vc

#ls dev gives me console, usplash_fifo, null, fb0 and tty0-8

running ./init will show the kubuntu splash screen for half a second (three lines of text appears below, the last being "waiting for the root file system", before it gives me the same screen as above (loads of Segmentation faults, and dropping to shell).

I guess it can't find my disk, but why and how can I make it find it?
Any tips or hints in almost any direction will be greatly appreciated.

---

### Post by zxee on 2006-06-17
is this hard drive failure? Can you hear or reach in and feel the drive operating?
You could run SMART but if the system can't find the drive/partition then that's not going anywhere. I'm assuming that hdc1 is one partition=the whole drive.

---

### Post by ager-wick on 2006-06-17
Update:
The drive is OK, no hardware failure.
1st I was wrong, the boot loader does run, but it was hidden.
I burned a Dapper install CD using another computer and booted this.
Then I opened a konsole terminal session and listed the available IDE/ATA hard drives and partitions (ls -l /dev/hd*) so I could see what is what.
Then I created a directory (mkdir tmp) and mounted the drive (mount /dev/hdc1 tmp) and I was able to access it all (from ~/tmp).

At this time I shut it down and switched the IDE cables to that the hard drives comes before the CD rom drive, which is more logical. I restarted on the Dapper install CD and could see that my hard drive was snow hda, not hdc. So I mounted hda1 (cd ~ && mkdir tmp && mount /dev/hda1 tmp), changed to directory ~/tmp/boot/grub and edited menu.lst (nano menu.lst).
Here I changed the config so the boot loader is no longer hidden and in addition corrected all hdc to hda.

Similarly, I edited ~/tmp/etc/fstab to reflect my changes from hdc to hda.

I do realize that swapping the hard drives around and then changing all hdc to hda is not really necessary to solve this problem, but it is too confusing with the hard drives on the second controller, so I might as well change this now.

Anyway, after doing this (and restarting), I got the boot loader, so I tried an older kernel (2.6.12-9), which to my suprise and relief booted with no problem!

Now, having been able to boot again, do anyone have a good tip on how I should upgrade to Dapper? Just follow the instructions here [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades) ? 

Thanks!

---

### Post by ager-wick on 2006-06-17
Since I'm impatient, I already started upgrading to Dapper.
I did the following:
Edited the repositories list (just did it from synaptic, however you can also type kdesu kate /etc/apt/sources.list from the shell).
I commented (removed) everything exept this:
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

then I simply ran this command:
sudo apt-get update && sudo apt-get dist-upgrade

which at the moment is still running...
will post back when I know the result.

---

### Post by ager-wick on 2006-06-17
That did the trick.
It's all working fine now :)

---

### Post by tyreth on 2008-02-27
Just thought I'd add my extra bit, for others, in case their problem is similar to mine.

After reinstalling 7.10, I noticed that /dev/hd* doesn't exist still.

Seems that my IDE drive is now /dev/sd* instead.  So maybe check if this is what's wrong, and set your boot to be sda1 or sdb1 or whatever.

---

### Post by the_new_z on 2008-06-10
Thank you, guys.  Just wanted to let you know that you saved another lost soul :)

I was adding a new hdd and after switching the cables a couple of times, the system refused to boot.  The problem was that /dev/hdd was renamed to /dev/hdc.  So, I did as you said - booted with a live cd, mounted, changed menu.lst and fstab, and everything was fine.

Thanks again!

---

