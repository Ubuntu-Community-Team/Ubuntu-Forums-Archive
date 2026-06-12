---
title: "Segmentation fault on reboot following attempted upgrade"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by jkeenan on 2006-11-04
I am unable to restart my computer following an attempted upgrade to Breezy.  I am getting error messages described in other posts in this forum and elsewhere.

I have been using Ubuntu for about 7 months.  I know I started with Hoary and I *thought* I had upgraded to Breezy.  But I can't be certain of that, as my /etc/apt/sources.list continued to show me at Hoary.

In any event, today I decided to upgrade to Edgy, jumping over Dapper Drake.  (God, how I hate these cutesy names!)  That upgrade didn't go so well, I got reports of broken packages, etc.  I think that one of the error reports made reference to 'initramfs'.  The upgrade did not succeed.

At that point I figured it would be better to just go up one step.  I googled and learned that if I edited my etc/apt/sources.list file, I could target the distribution I wanted (Breezy) and then install it with a couple of
apt-get commands:  apt-get install and apt-get dist-upgrade.

This worked fairly well.  The apt-get dist-upgrade command completed without listing any errors.  I saw the expected directory structure at my terminal and my desktop was as expected.  I could ssh to other servers where I do work and I had Internet access.

The only problem was that when I clicked on the new Thunderbird icon to look at my mail, I got a message that said that another instance of Thunderbird was running and that I would either have to shut that process off or restart.  This was puzzling, because I had closed Thunderbird before starting the upgrade to Breezy.

I figured this would be an appropriate point to restart my computer, and went to do so in the normal manner.  The Dell splash was normal and the first lines of the reboot (which I think refer to Grub) came up.

Then, all of a sudden, I got the following:

```
segmentation fault
segmentation fault
segmentation fault
segmentation fault
segmentation fault
segmentation fault
segmentation fault

ALERT!  /dev/sda1 does not exist.  Dropping to a shell!
Busy Box v1.1.3 (Debian 1:1.1.3-2 ubuntu 3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh can't access tty; job-control turned off (initramfs)

```
[Note:  I'm typing what I wrote down this afternoon, but it may actually have been /dev/hda1 does not exist.]

At this point, screen froze and no input was accepted from the keyboard. The only thing I could do was hit and hold the reboot button on the hard drive -- which only brought me back to the same point.  I repeated this several times, one time holding down the F12 key.  But the menu that came up via F12 didn't present any solutions that leapt out to me.

I've turned up several threads and other postings that make reference to "/dev/xxx does not exist.  Dropping to a shell", to Busy Box, to job-control turned off, and to initramfs.  But if my keyboard can't produce any input, I'm at a loss as to how to proceed.  Suggestions?

Thanks in advance.

---

### Post by aufumy on 2007-02-03
I am having the same problem, does anybody have any solutions?

---

