---
title: "Upgrade 10.10 to 11.04 option missing on CD"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by VideoRoy on 2011-04-28
I downloaded the release version of 11.04 desktop 32bit today and ran into a problem with the upgrade.
 
Not sure if I missed a step or not, but when I booted the CD to do an Install of 11.04 desktop 32bit over 10.10 desktop 32bit I expected to see the upgrade option similar to what is in this link (red arrow pointing to it):
 
[http://www.techdrivein.com/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html](http://www.techdrivein.com/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html)
 
On my install screen all the other options were there except the upgrade.
 
Since I was on a schedule for this particular computer I am doing the Update Manager Network upgrade instead but I have 3 other computers to do as well.
 
Any ideas on what I might have missed?  Should I have booted to Live version first instead of Install then look for an upgrade option somewhere?  I read something that alluded to that on a website.
 
Thanks!

---

### Post by VideoRoy on 2011-04-28
I just found this link:
 
[http://www.webupd8.org/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html](http://www.webupd8.org/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html)
 
And the option I used was exactly the second one choosing install after boot the CD.  The Upgrade option was definitely missing.
 
Anyone else have luck with this?  I am dual booting with Win7 if that makes any difference but I have 10.10 installed on a second drive in it's own partition.  The installer did find the 10.10 installation no problem but my only options were to erase all Ubuntu and install 11.04 or Erase all Ubuntu and Win7 and install 11.04.
 
I would much rather upgrade with CD for all my other computers if possible.

---

### Post by gcd1094 on 2011-04-28
Exact same problem here. Made a live usb, rebooted, tried to install, and the upgrade option was missing. Also, before I installed I booted into the live version so that's probably not what did it.

However, right now I have a dual-boot with win7 and Ubuntu 10.10. Maybe Win7 (or having a dual-boot in general) has something to do with it... that's my best guess.

EDIT

Just read your last post, looks like we both have the exact same problem. :(

---

### Post by Hedgehog1 on 2011-04-28
The 'upgrade' option will not always show of the installer cannot figure out your disk partitioning layout.  Mine stumped it as I had 10.10 and two test 11.03 installs, pleas windows 7.

You will need to use the 'Something Else' option that is always the last item on the list:

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

However - this works if you have a separate '/home' partition, you select the '/' (root) partition to format, and the '/home' partition **NOT TO FORMAT**.

If you have all your stuff in the '/' partition, you will need to backup your data and do a full 'clean install'.

**Always backup your data before any large install/upgrade like this anyway, not matter what option you choose.**

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-28
Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]




The last partition to setup is the '/home' one:

[SIZE="4"]**DO NOT CHECK THE FORMAT BUTTON IF YOU ARE DOING AN UPGRADE!!!**[/SIZE]

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]




***The Hedge***

---

### Post by gcd1094 on 2011-04-28
Thanks! Will definitely try this. And I'm assuming that if everything is saved to one partition, this method can be used to create a newly formatted /home partition?

---

### Post by Hedgehog1 on 2011-04-28
> **gcd1094 said:**
> Thanks! Will definitely try this. And I'm assuming that if everything is saved to one partition, this method can be used to create a newly formatted /home partition?

Yes you can create a new empty partition here, but it is often easier to do that using gparted in the 'TRY' option on the LiveCD/LiveUSB and then use that new partition as '/home'.

So long as you backup your data, you are set.

***The Hedge***

:KS

---

### Post by VideoRoy on 2011-04-28
> **Hedgehog1 said:**
> The 'upgrade' option will not always show of the installer cannot figure out your disk partitioning layout.  Mine stumped it as I had 10.10 and two test 11.03 installs, pleas windows 7.

You will need to use the 'Something Else' option that is always the last item on the list:

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

However - this works if you have a separate '/home' partition, you select the '/' (root) partition to format, and the '/home' partition **NOT TO FORMAT**.

If you have all your stuff in the '/' partition, you will need to backup your data and do a full 'clean install'.

**Always backup your data before any large install/upgrade like this anyway, not matter what option you choose.**

***The Hedge***

:KS
Hedge,
I actually did go to Something Else but bailed out since I was already partitioned the way I wanted.

However, I think you have nailed it.  The first system I upgraded is the only one that does NOT have a separate /home.  I normally always do that but this system is a test / development system and did not require it.  I had thought of something like this being the case but did not realise the installer would care.

I will be upgrading some other systems tonight so will get a chance to confirm and report back.

Thanks!!!!!

---

### Post by VideoRoy on 2011-04-28
Well bad news is that even on systems with a separate /home I still do not get the upgrade option.

It must be because of the dual boot and my partitioning scheme.  I normally use Windows as my boot manager and load the Ubuntu boot loader in it's own partition.  Old habit that I have used for a long time.

So I need to either Upgrade over the network or install clean over 10.10.  The upgrade worked pretty good on my first unit but took 5 hours.

---

