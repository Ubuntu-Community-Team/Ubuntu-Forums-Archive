---
title: "&quot;Install them side by side, choosing between them at each startup.&quot; not an option."
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by legen_waitforit_dary on 2010-01-16
So, I want to dual boot Ubuntu 9.10 on my PC which already has Windows XP Media Center on it.

When I get to the partitioning, I get three options:
 - Erase and use entire disk
 - Use largest continuous free space
 - Specify partitions manually

Why isn't the option "Install them side by side, choosing between them at each startup."appearing? And how can I either make it appear or install Ubuntu in another way to let it run side by side with Windows without losing anything?

Computer info:
 - Intel Core Duo T2050 (Y)  1,6 GHz
 - 250 GB  SATA 3G (3,0 GB/sec) 7200 RPM
 - 2x 1GB Memory

---

### Post by gspat on 2010-01-16
That's the "Specify Partitions Manually" choice.

When you use it, you get to shrink/make/format the partition(s) you want to use for your install.

---

### Post by legen_waitforit_dary on 2010-01-16
So I checked out this guide: [https://help.ubuntu.com/9.10/switching/installing-partitioning.html](https://help.ubuntu.com/9.10/switching/installing-partitioning.html)

It says *"After finalizing the installation, however, the hard disk will be re-partitioned and all existing data stored on it will be lost."*

Doesn't that mean I'll lose everything or am I misunderstanding that?

---

### Post by Bartender on 2010-01-16
> **legen_waitforit_dary said:**
> So, I want to dual boot Ubuntu 9.10 on my PC which already has Windows XP Media Center on it.

Media Center?  How many primary partitions you got?  Betcha you have 4.

---

### Post by legen_waitforit_dary on 2010-01-16
It had:
 - Windows Media center (/dv/sda1) 226.8 GB
 - free space 7.8 MB
 - Windows NT/2000/XP (/dev/sda2) 6.1 GB

---

### Post by kansasnoob on 2010-01-16
It's because you have that "free space 7.8 MB".

But the safest way to install where there is more than one existing partition is to use the manual partitioning option.

Be patient and let me dig up some good info for you :D

---

### Post by kansasnoob on 2010-01-16
A couple of things you absolutely need to know:

#1. Never move the beginning (left end) of any Windows OS partition! So don't get silly and try to move "Windows NT/2000/XP (/dev/sda2) 6.1 GB" to the left just to make things pretty!

#2. You're only allowed four primary and extended partitions on any drive. You can create a nearly endless number of logical partitions inside the extended partition.

#3. You'd really be wise to create a separate /home since you're manual partitioning anyway. Three partitions: / (aka: root), /home, swap. You could place all three inside one extended partition.

#4. Ignore the separate boot partition in the following tutorial. You don't want or need one, they can actually cause problems!

Look at my mess:

[ATTACH]143796[/ATTACH]

My partitions are even named. You can see that I have Windows and five Linux OS's each with a separate /home sharing one swap. You'll also notice I have 2 primary partitions and everything else is in an extended partition.

If your current setup actually has one windows clear to left and the other clear to the right, you'll want to shrink the one on the left - that is move the right side of it to the left. Please boot Windows and cleanup and defrag first.

Then I'd recommend either creating one extended partition for all the Ubuntu partitions or creating one more primary for / about 5 or 6 GB, and another extended for /home and swap. Swap need be no larger than 1GB.

Anyway this tutorial shows how to use Gparted from the live CD:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Just be patient and ask more questions if need be. Better to get it right than to kick yourself for doing it wrong :)

---

### Post by legen_waitforit_dary on 2010-01-16
So, I'm at step 12 of the tutorial you posted, and kinda stuck again. I can't seem to resize it since he minimum new size is too low. *screenshot: [http://img689.imageshack.us/img689/4466/screenshothv.png](http://img689.imageshack.us/img689/4466/screenshothv.png))*

Also, when viewing the information of the disk, it says there's an error, could this be the source of the above problem? *screenshot: [http://img163.imageshack.us/img163/7430/errorcq.png](http://img163.imageshack.us/img163/7430/errorcq.png)*

---

### Post by legen_waitforit_dary on 2010-01-17
Bump

---

### Post by kansasnoob on 2010-01-17
> **legen_waitforit_dary said:**
> So, I'm at step 12 of the tutorial you posted, and kinda stuck again. I can't seem to resize it since he minimum new size is too low. *screenshot: [http://img689.imageshack.us/img689/4466/screenshothv.png](http://img689.imageshack.us/img689/4466/screenshothv.png))*

Also, when viewing the information of the disk, it says there's an error, could this be the source of the above problem? *screenshot: [http://img163.imageshack.us/img163/7430/errorcq.png](http://img163.imageshack.us/img163/7430/errorcq.png)*

Sorry to get back so late. I think you only need to install ntfsprogs, so from the Ubuntu Live Desktop go to Applications > Accessories > Terminal and:

```
sudo apt-get install ntfsprogs
```

Then close and reopen Gparted. I believe that will make the NTFS Windows partition readable so Gparted can see how much space is used and how much is free.

OTOH I have run into trouble recently on a Win OS that had AT&T's McAfee security suite installed and I couldn't make the Win partition readable until I disabled McAfee.

Did you defrag as suggested?

Also remember to untick the Round to cylinders box:

[http://members.iinet.net.au/%7Eherman546/p22/012.png](http://members.iinet.net.au/%7Eherman546/p22/012.png)

One last thing, how much of the Windows partition is used according to Windows own utilities?

---

### Post by kansasnoob on 2010-01-17
> **legen_waitforit_dary said:**
> Bump

Heh, heh, I was typing while you were posting :)

I'll hang close for a while this AM.

---

### Post by legen_waitforit_dary on 2010-01-17
> **kansasnoob said:**
> OTOH I have run into trouble recently on a Win OS that had AT&T's McAfee security suite installed and I couldn't make the Win partition readable until I disabled McAfee.

Only have AVG on here so shouldn't be a problem.

> **kansasnoob said:**
> Did you defrag as suggested?
Also remember to untick the Round to cylinders box:

[http://members.iinet.net.au/%7Eherman546/p22/012.png](http://members.iinet.net.au/%7Eherman546/p22/012.png)

Yes and yes :)

> **kansasnoob said:**
> One last thing, how much of the Windows partition is used according to Windows own utilities?

My C:-drive has 112 GB used and 114 GB free.


Gonna boot Linux from the disc now and try what you said above.

---

### Post by legen_waitforit_dary on 2010-01-17
> **kansasnoob said:**
> Sorry to get back so late. I think you only need to install ntfsprogs, so from the Ubuntu Live Desktop go to Applications > Accessories > Terminal and:

```
sudo apt-get install ntfsprogs
```Then close and reopen Gparted. I believe that will make the NTFS Windows partition readable so Gparted can see how much space is used and how much is free.

Didn't seem to help, it says the latest version is already installed and still can't resize it in GParted.

---

### Post by kansasnoob on 2010-01-17
Well, it's odd that Gparted won't read that. You see that triangular warning emblem at the left? That means Gparted can't read the partition.

Now this may be just a waste of a CD but if you have the ability I'd try burning an actual Gparted CD. I'm using GParted Live 0.4-6-1.iso:

[http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)

It's a very small download. Or if you have an older version of Ubuntu you might try gparted from it. Of course then just eject it and install Karmic.

I see the Gparted site has up some warning info:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

And I know Gparted is messed up in the new Lucid testing Live CD's.

---

### Post by legen_waitforit_dary on 2010-01-17
I found an old disc I had with Ubuntu 9.04 Jaunty which I used a while ago. Booted that one up and opened GParted (which is version 0.4.3) and the error was still there.

---

### Post by kansasnoob on 2010-01-17
> **legen_waitforit_dary said:**
> I found an old disc I had with Ubuntu 9.04 Jaunty which I used a while ago. Booted that one up and opened GParted (which is version 0.4.3) and the error was still there.

Hmmmmmmmmmm, I'm stumped :(

Obviously something is keeping Gparted from being able to read that NTFS partition. I know I puzzled over that issue with McAfee for hours before I figured it out.

Not sure what to think. Wish you lived next door, I'd loan you my Gparted Live CD.

---

### Post by legen_waitforit_dary on 2010-01-17
Burned the 0.4.6-1 .iso and booted up.

I choose load with default settings (something like that, your first default option)
Then it goes to some kind of command line where it checks your system and it always gets stuck with this error: (here's part of it)

```
Hardware error
Timeout on logical unit
end_request: I/O error, dev sr0, sector 204800
Buffer I/O error on device sr0, logical block
```

I've actually been stuck in this loop when booting Karmic once, and then I rebooted and it went back to normal, but I've done this one 3 or for times already without succes...

---

### Post by kayvortex on 2010-01-17
> 
So, I'm at step 12 of the tutorial you posted, and kinda stuck again. I can't seem to resize it since he minimum new size is too low. screenshot: [http://img689.imageshack.us/img689/4...reenshothv.png](http://img689.imageshack.us/img689/4...reenshothv.png))

Also, when viewing the information of the disk, it says there's an error, could this be the source of the above problem? screenshot: [http://img163.imageshack.us/img163/7430/errorcq.png](http://img163.imageshack.us/img163/7430/errorcq.png)

If Gparted is saying that /dev/sda1 has bad sectors, then maybe you should run chkdsk. To do this, boot up windows and then Hold the Windows button and press R (or just select "Run" from the start menu). In the run box that turns up enter "cmd". You should now see a DOS prompt. Into that, type:
```
chkdsk /f c:
```
And press 'y' when it asks you about doing a chkdsk next time the system boots up. Then, just reboot your system, let chkdsk run, and then do the whole thing again to make sure.

Edit: "/dev/sr0" is your CD drive, so *that* looks like a CD Drive problem. Then again, it might just be a bad CD; but the message "Hardware error" makes me think the former. Try running chkdsk on your HDD first and seeing if that helps Gparted stop complaining, and then coming back to this problem.

---

### Post by legen_waitforit_dary on 2010-01-17
Still no success after chkdsk, wouldn't be surprised if it was a CD-drive problem actually, it seems to do strange things sometimes (a lot of my cd's I burn don't end up to work).

So if I can't boot it through my cd-drive, can this be done through a USB memory stick or something?

---

### Post by kansasnoob on 2010-01-17
You can create a Live USB with UNetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

It's fairly straightforward.

---

### Post by kayvortex on 2010-01-17
Well, all problems that I come up against I fix with [SystemRescueCD]("http://www.sysresccd.org/Main_Page"). This has all sorts of tools to fix a Linux installation, and a fair few for dealing with Windows problems. The SystemRescueCD on a USB instructions are [here]("http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick"), and for Gparted are [here]("http://gparted.sourceforge.net/liveusb.php").

But, gparted and ntfsprogs should work, and the fact that you tried it without success with two LiveCDs of different versions suggests that's not where the problem is; although you can still try SystemRescueCD/Gparted LiveCD just to make sure.

What did chkdsk report? Is the same error you showed before,
> Also, when viewing the information of the disk, it says there's an error, could this be the source of the above problem? screenshot: [http://img163.imageshack.us/img163/7430/errorcq.png](http://img163.imageshack.us/img163/7430/errorcq.png)
still showing up?

---

### Post by legen_waitforit_dary on 2010-01-17
> **kayvortex said:**
> What did chkdsk report?

No idea, it started doing the check and I didn't have any idea how long it would take so went away from the computer. Came back about 15 minutes later and it was normally started up, so I assumed it didn't find any problems.

> **kayvortex said:**
> Is the same error you showed before still showing up?

Yes

---

### Post by legen_waitforit_dary on 2010-01-17
GParted doesn't even want to boot from my USB, followed all instructions and it just goes straight to Windows...

---

### Post by kansasnoob on 2010-01-18
> **legen_waitforit_dary said:**
> GParted doesn't even want to boot from my USB, followed all instructions and it just goes straight to Windows...

The BIOS must be set to boot from USB before hard drive. I have mine set to try CD first, USB second, and hard drive last.

---

### Post by kansasnoob on 2010-01-18
Really take a close look at the warning here:

[http://img163.imageshack.us/img163/7430/errorcq.png](http://img163.imageshack.us/img163/7430/errorcq.png)

I'd overlooked that earlier.

Kudos to kayvortex for pointing that out. Proves that two pair of eyes are better than one :)

Gparted will continue to refuse to re-size that until the error is straightened out.

---

### Post by legen_waitforit_dary on 2010-01-18
Gonna try all this again when I have time someday soon (what the warning says).

---

### Post by legen_waitforit_dary on 2010-01-19
MMkay, did what the error says (chkdsk-thing and reboot twice), still got the error, gonna try again later this week (the chkdsk takes a while).

---

### Post by kayvortex on 2010-01-19
OK, well, I forgot the /r flag, which is important since it will tell chkdsk to recover any data on the bad sector. You'll still see that error message about the bad sectors existing, but then there won't be any data on there to lose.

Detecting bad sectors is generally bad news because it may mean that your HDD might fail soon ("soon" depending on how many bad sectors, and even then could still mean not for some time yet). Propriety demands that I advise you that you should probably think about getting a new HDD (it's not too difficult to replace one on a PC and it's *relatively* inexpensive), and should **definitely** think about backing up your data (which may mean getting a new HDD anyway). Seriously, I'd **really, really recommend backing up your data**!

Also, if your HDD has a lot of bad sectors, then it'd probably be better not to install another OS on it since the more intensive read/writing done on the disk will make it fail all the faster. Chkdsk prints out a summary when its done: try to catch how many bad sectors it has (the summary disappears very quickly, so try to catch it on your phone or something).

Now, if you decide to carry on with the HDD and install a dual-boot Ubuntu this is what you'll have to do:
[LIST=1]
[*] Backup your data. (Did I mention that before?)
[*] Run chkdsk /f /r. This will move your data off the bad sector(s).
[*] Then it would probably be best to do a defrag.
[*] I don't know if gparted has an option to use ntfsresize with the "--bad-sectors" flag, so I'm going to point you to this ntfsresize FAQ [here]("http://darkstar.ucd.ie/timosh/links/ntfsresize.html#example"). Read through the steps and make sure you understand what it says and what to do (even if what it is telling you to do is unfamiliar to you). Ask about anything you're not sure on and I'll be happy to help: don't be afraid of asking LOTS of questions.
[*] Put the LiveCD in and install Ubuntu in the freed up space.
[/LIST]

Looking at all this, you may decide it's not worth it. Installing ANY operating system generally involves messing about with hard disks so some about of work (and a bit of learning if you've never done it before) is inevitable; but for a system that **may** (and I stress the word "may") fail it's your call.

My advice would be this: if you are happy with buying a new HDD, are happy that you can put it in when needed to (not really too difficult once you know what you have to do), and can backup all your data now, then **and only then** continue. Otherwise, decide on what you plan to do with your PC in the near future and research on how to do whatever you plan to do. As always, we're happy to answer any questions you might have.

---

### Post by legen_waitforit_dary on 2010-01-20
I backed up before starting all of this, and back up frquently (after learning it the hard way though :P). I'll do some more research etc. this weekend and then decide how to move on.

---

