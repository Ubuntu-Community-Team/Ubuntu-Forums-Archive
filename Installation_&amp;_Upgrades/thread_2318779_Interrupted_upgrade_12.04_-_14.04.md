---
title: "Interrupted upgrade 12.04 - 14.04"
date: 2016-03-29
forum: Installation &amp; Upgrades
---

### Post by David_Leigh on 2016-03-29
Hi Ubuntu Community

I am hoping you can help me.  I have searched the forums for related content but have not found a similar problem hence this post.  I was upgrading from 12.04 to 14.04.  everything was going well and it had just finished downloading all the packages and had just started the process of removing the obsolete software.  At this point I really needed to go to sleep (at this point it was 2.30am) and thought that I might be able to suspend the computer and then recommence in the morning.  When I did log back into the computer it came up with a 'restart the computer' option.  I pressed cancel as I thought that I would be able to continue with the process.  Unfortunately not.  when I went to restart the computer the logging off part of the menu came up with square symbols and no option to shutdown so did a forced shutdown.
 
On booting the computer I get the following

mount: mounting /dev /loop0 on /root failed:Iinvalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on root/proc/ failed: no such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

At the command line (intramfs) when you type 'help' it comes up with the following

. : [alias break cd chdir command continue echo eval exec exit
export falst getopts hash help let local printf pwd read readonly
return set shift test times trap true type ulimit umask unalias
unset wait [ [[ash awk basename blockdev cat chmod chroot chvt
clear cmp cp cut deallocvt df dnsdomainname du dumpkmap echo
egrep env expr false fbset fdflush fgrep find grep gunzip gzip
hostname ifconfig ip kill in loadfont loadkmap is mkdir mkfifo
mknod mkswap mktemp modinfo more mount mv openvt pidof printf
ps pwd readlink reset rm rmdir sed seq setkeycodes sh sleep sort
stat static-sh stty switch_root sync tail tee test touch tr true
tty umount uname uniq wc wget which yes zcat

In case you have not noticed by now I am new to this so what these commands mean is lost on me and you are probably shaking your heads.  I am wondering what my options are.

Other possibly relevant info - running windows 10 and Ubuntu 12.04 on the same computer.  Windows 10 driving me insane hence the drift towards Ubuntu (have had Ubuntu loaded on for a couple of years).

Is it possible to

a) recover the computer and recommence the upgrade.
b) if not will I need to reinstall the original 12.04 and recommence the upgrade process again? (I am blowed if I know where the bootable usb is)
c) assuming this is not possible, what are my options?

Regards

Dave

---

### Post by kansasnoob on 2016-03-29
> (I am blowed if I know where the bootable usb is)

I assume you can still boot into Windows 10? If so step #1 should be creating a new 14.04.4 live DVD/USB!

Download here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

How to create a live DVD in Windows:

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

How to create a live USB in Windows:

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Step #2 should be checking the newly created live DVD/USB for defects by booting it to the advanced boot menu and selecting Check disc for defects:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

It's imperative to have a known good live DVD or USB before doing anything else just in case we'd even render Windows 10 unbootable.

Step #3 would be seeing if you can boot into the installed Ubuntu's recovery mode:

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

If so we may be able to help you resume the upgrade process from there but no need to go into great detail until we find out if the recovery mode is even bootable.

---

### Post by David_Leigh on 2016-03-30
Hi Kansasnoob

Thanks for taking the time to reply.  I have since located the bootable USB which was for 12.04.  I have borrowed a friends computer (for the purposes of accessing the internet) so that I can at least gain access to the forum while trying to get my own up and running.  The issue I have been having with Windows 10 is that it interferes with the wireless adapters and I am sick of having to go back to previous set points just so I can use the internet.  Thanks again.

---

### Post by kansasnoob on 2016-03-31
Have you tried booting into recovery mode yet? If you can I'll provide more info about trying to recover in recovery mode.

---

### Post by David_Leigh on 2016-04-03
So I got to the GRUB menu.  I have tried a couple of options such as 'drop to the shell' option which of course then comes up with the command line.  The generic Ubuntu notes give advice on the command required to get it out of readonly mode but nothing beyond this.  Clearly for people who know their command lines.  I also tried the 'failsafeX' mode.  This went to a command line.

---

### Post by mörgæs on 2016-04-03
Now you have been dealing with this for five days. Have you thought of a clean install of 14.04?

---

### Post by David_Leigh on 2016-04-06
Yes I have.  I did at least back everything up prior to starting the upgrade process.  Given that the upgrade was quite advanced when it went pear it might just be easier to start from scratch.  I was hoping that there might be a command or two that would get the process back on track but like all these things it is contingent on certain parts of the upgrade having taken place and I realise it is hard for people to know where this process might be up to.

---

### Post by kansasnoob on 2016-04-07
> **David_Leigh said:**
> So I got to the GRUB menu.  I have tried a couple of options such as 'drop to the shell' option which of course then comes up with the command line.  The generic Ubuntu notes give advice on the command required to get it out of readonly mode but nothing beyond this.  Clearly for people who know their command lines.  I also tried the 'failsafeX' mode.  This went to a command line.

In Recovery Mode the first thing you must do is select Enable networking. That not only enables networking but mounts the file systems in read/write mode which is necessary to do anything. You'll be asked for confirmation so just select yes and then you'll be returned to the menu again so select Drop to root shell. From there you'll need to run some commands to try and recover. It may be necessary to repeat these in no specific order as you proceed (no sudo needed because you are in a root shell):

```
apt-get update
```

```
dpkg --configure -a
```

```
apt-get dist-upgrade
```

```
apt-get -f install
```

Let us know how that goes. Remember it's quite common to have to repeat the above commands in no specific order.

---

