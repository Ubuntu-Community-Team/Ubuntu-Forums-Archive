---
title: "Wubi and &quot;proper&quot; installation"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by HenryL on 2011-10-11
Hi folks,

I installed Ubuntu 11.04 through Wubi on my Vista PC a month or so ago.

I now want to make Ubuntu my primary OS (but keep the Vista install to run a couple of programs that Ubuntu won't do).

Unfortunately I have discovered that Wubi is really only an introductory tool for Ubuntu, with very limited hard disk size (it would be nice if the Ubuntu "download Wubi" page made this explicit!).

Questions:

1) If I understand correctly, this means if I want to have a decent hard disk size for my Ubuntu installation I need to do a "true" installation of Ubuntu by preparing an install CD. Is that right?

2) Will doing this harm my Vista install? I don't want to affect the latter other than to steal a bunch of its hard disk space for Ubuntu's usage.

3) What about everything I've installed on my Wubi install? Do I just lose all the customizing, program installing, etc, that I have done?

4) Do I have to also remove my Wubi install as a part of all of this? I'm assuming yes, otherwise I'd have a "true" Ubuntu install and a Wubi install, right?

5) Finally...is it really as simple as throwing in the install disk and following the prompts, as ubuntu.com promises? Because it seems to me the instructions for Wubi omitted what in hindsight was pretty crucial information.

I am NOT a tech-savvy person, so plain language explanations would be GREATLY appreciated.

With thanks,

Henry

---

### Post by drs305 on 2011-10-11
Henry,

I played with Wubi when Grub 2 was introduced to see how the two integrated. I haven't used Wubi in a long time, so I'll defer comments about it. However, this link by forum member *bcbc* is very good - he does a lot of forum work with Wubi.
[HOWTO: migrate wubi install to partition]("http://ubuntuforums.org/showthread.php?t=1519354")

---

### Post by HenryL on 2011-10-20
Thanks,

I have read that post. I guess where I got stuck was with the whole partitioning my drive thing.

According to the instructions linked from that link, the best way to sort out thepartitions before turning wubi into Ubuntu proper is to make an Ubuntu install CD or USB and then do the repartitioning from there.

Slight problem: I have done this...but my system does not notice either the CD or the USB boot disc when I start up...it just goes straight to the Windows menu for choosing whether to run Vista or Ubuntu(Wubi).

Frustrating? You bet. So how else can I get my partitions set up appropriately so that I can then get Ubuntu going? Wubi is installed on the disk drive that I want to use as my Ubuntu partition so I can't unmount it while in Wubi in order to resize.

All help greatly appreciated...this is starting to get a bit depressing...

H

---

### Post by drs305 on 2011-10-20
Have you entered BIOS and set up your USB or CD to be first in the boot order? Your system may have the hard drive as the first boot priority.

You could also try a commercial CD to see if it boots properly. If it does, it may be a CD burning issue; if your system boots Windows then the BIOS isn't recognizing the CD or doesn't have the boot priority set correctly.

---

### Post by HenryL on 2011-10-24
Aha! You're brilliant. Ok. Partition created.

Next problem! :)

I logged back into my Wubi install and downloaded wubi-move.sh.

I ran the following:

sudo bash wubi-move.sh /dev/sda6

And got the following response:

wubi-move.sh: line 4: syntax error near unexpected token `newline'
wubi-move.sh: line 4: `<!DOCTYPE html>'

Not, I am guessing, exactly what was meant to be...

---

### Post by Mark Phelps on 2011-10-25
In response to your question 5) ... unfortunately, in all too many cases, the answer is NO.

Why?

Because in some case, a byproduct of using the Ubuntu installer to shrink an existing Win7 install to make room for Ubuntu has left the Win7 OS partition in an unusual state, such that it fails to boot after that.

So, if you're thinking about dual-booting using the traditional multi-partition approach, instead of migrating your current Wubi install, then do the following:
s partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by bcbc on 2011-10-25
> **HenryL said:**
> Aha! You're brilliant. Ok. Partition created.

Next problem! :)

I logged back into my Wubi install and downloaded wubi-move.sh.

I ran the following:

sudo bash wubi-move.sh /dev/sda6

And got the following response:

wubi-move.sh: line 4: syntax error near unexpected token `newline'
wubi-move.sh: line 4: `<!DOCTYPE html>'

Not, I am guessing, exactly what was meant to be...
I have no idea how you got this error... but I suspect that the wubi-move.sh file on your computer is invalid (contents contain garbage). I downloaded it and tried to reproduce this problem but was unable.

In any case, you should be using the latest 2.1 version of the script and downloading it from the howto thread. Please feel free to post on that thread if you have any issues. Thanks

---

### Post by HenryL on 2011-10-25
the weird thing is...I got that file from the HOWTO thread...which directs one to github: [https://github.com/bcbc/Wubi-move](https://github.com/bcbc/Wubi-move) ... the 2.1 file seems...elusive...

Oh, no wait...found it here:

[https://github.com/bcbc/Wubi-move/archives/master](https://github.com/bcbc/Wubi-move/archives/master)


...here we go!

---

### Post by bcbc on 2011-10-25
Go to the end of that first post on that howto thread and you'll see all the downloads there. You can also download it from github, but it's right there on the thread.

---

### Post by HenryL on 2011-10-26
Awright! Everything is done. Thank you so much!!!

Once the transfer was complete had some challenges because I had to resize the partition again to reclaim the space that Wubi used to live in...which messed up Grub, and the boot-repair utility was ornery. But after some madcap fiddling this morning I got it all back into sync.

Really, _really_ appreciate the patient support!!!

Hurrah!

H

---

