---
title: "Install on USB drive - how to avoid burnout?"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by jayach222 on 2007-02-09
I have xubuntu installed on a usb drive and my system boots exclusively from the drive.  I've read that doing so can burnout the usb drive: it can not take the multiple read/writes that occur with an OS installed on it.  

I've read a few forums and articles that mention in passing that modifications need to be made to the OS to minimize the read/write operations.  However, they never say what that is or where to find the information on how to do so.  I've been looking, and haven't really found anything.  

Does anyone know of any guides or tips in doing so?  So far I've hit a couple of low hanging fruit such as moving logs to a harddrive.  I've noticed a lot of writes to /sys and /proc too, should these be moved off of the usb as well? 

Thanks-

NOTE: I edited the title to be more specific to the usb drive type based on kidders question

---

### Post by kidders on 2007-02-09
Hi there and welcome,

> I've read that doing so can burnout the usb drive
Are you referring to a USB hard disk or flash memory?

> I've noticed a lot of writes to /sys and /proc too
Those directories don't actually exist ... they're virtual filesystems designed to allow applications get/set details about system behaviour easily.

---

### Post by jayach222 on 2007-02-09
> **kidders said:**
> Hi there and welcome,
Thanks!

> Are you referring to a USB hard disk or flash memory?

It is flash memory.


> Those directories don't actually exist ... they're virtual filesystems designed to allow applications get/set details about system behaviour easily.

ok, so are those strictly in memory then, they are not being saved to the flash drive?  Is there anything you know of that would benefit from moving to a hard drive, or configuration wise?

---

### Post by kidders on 2007-02-09
> **jayach222 said:**
> It is flash memory.In that case, you *do* have to worry about burning out your drive. Does it get hot? Of course, I/O performance is another reason to move stuff onto a disk with moving parts.

> **jayach222 said:**
> Is there anything you know of that would benefit from moving to a hard drive, or configuration wise?The answer to this question really depends on the reason you're not using a hard disk in the first place. Most people suffer the massive performance hit USB flash memory tends to land you with because they simply can't (or *really* don't want to) use hard disks for storage.

If you *can* make use of hard disk space, the number one priority is to move swap space off the USB device. Both in performance and life expectancy terms, that will probably yield the greatest improvement for your USB installation, when you stress it.

If you really, really want to avoid involving a hard disk, things become much more complicated. I'll continue to think about this issue over the next few hours, but at the moment, the following jump to mind...

[LIST]
[*]Often, the most I/O tends to get done when applications are loading, rather than running. This is a weakness in Linux's tendancy to perform an execution step called "linking" at runtime ... something which, in other ways, is a tremendous strength. You could possibly cut down on the work that needs to be done here by prelinking (sometimes called prebinding in Linux, or "optimising performance" on a Mac) your applications.
[*]You could also reduce kernel swappiness, to make it less enthusiastic about swapping data to disk when it runs out of RAM.
[*]You could get more RAM, and make use of RAMdisks, rather than actual physical storage, where possible. How much RAM have you got?
[*]You could play around with I/O buffering. Under ordinary circumstances, Linux uses large amounts of free RAM as disk buffers, to boost performance. This could have a detrimental effect on flash devices, where anticipatory buffering leads to unnecessary disk reads. Toning buffering down would hit you in performance terms though, whereas prelinking would boost it slightly.
[/LIST]

So, I guess how easy/hard it is to address your concerns really depends on why you're using a USB device in the first place.

I hope this helps.

---

### Post by jayach222 on 2007-02-09
That is great information, thanks alot!  Gives me a lot to look into.  

I use the box as a file server for my family that is always on.  I'm using a flash drive primarily for these reasons:
1. lower power usage than a hdd
2. leaving a port open for more storage.  right now 3 out of 4 connections are being used for file space and I didn't want the OS to be on the same drives as the files.  I want that extra port available so I can add another drive in the future.
3. Tight budget, I do not have $ to buy a controller to support more drives
4. It is not possible to power down (hdparm -Sxxx) a usb hdd - at least from what I've been able to research - if this isn't true, this would be a great alternative

---

### Post by kidders on 2007-02-09
Ahhh... I see.

If I were short of storage space on a file server, to be honest, I would never even consider putting the OS on a USB device. If I *had* to put something there, it would be the data being served. How about these ideas:

**Suggestion 1**
Whether it is to save hard disk space or reduce I/O to a USB flash device, you could probably do without the added load of a graphical environment on a PC the sole function of which is to serve files.

**Suggestion 2**
You may be using the wrong distro. Ubuntu was not designed to be light on disk space, but there are several distros that were. You could switch to one of those. If you wanted to keep your current disk configuration, you could experiment with copying /usr and /var into RAM at boot time, and copying them back every few hours, and again on shutdown. (That would only be viable if you switched away from Ubuntu, but would largely eliminate I/O to the USB device.) On the other hand, you could switch to a conventionally stored OS and minimise the amount of space devoted to it either.


One observation I would make is that most low to mid-range spec machines waste an *awful* lot of CPU time waiting on I/O operations. If a system won't be doing a lot of it in practice, then storing the OS on a slow device won't be such a bad thing. On the other hand, if the system's entire purpose is to perform large amounts of I/O all day (as in your case), it doesn't make a lot of sense to penalise it performance-wise right from the start. Think of it this way: Ubuntu's performance depends, among other things, on how fast it can access the medium it's stored on. So, in your case, it's ability to serve data to your family is bottlenecked by the speed of the only storage device **not** being used to store the data in question.

Another thing I find myself wondering about is exactly what you're serving, and how much room it takes up. The following example may be completely inapplicable to you, but I just wanted to be sure...

Let's say you have 3x300GB hard disks = ~0.88TB of space. Now, imagine just one GB of that is devoted to small text files, icons, or similar data, averaging about 4k per file (262,144 files). Further, let's give your filesystems a block size of 8k. Naturally, that would equate, on average, to a second GB of wasted space that you couldn't reclaim. Now, if you managed to get back 75% of that space by, for example, using ReiserFS instead of Ext3, reducing the block size, and engineered yourself a Linux distro that would fit into 700MB. That would be less than 0.08% of the total disk space available to you ... and you'd have pulled it out of your a$$!

---

### Post by FractalBrain on 2007-02-09
Hey, Im VERY new to all of this, but who knows, it might help.   If not, let me know:

So the live CD installation of Ubuntu only had reads, no writes.  I wonder if it would be possible to make a liveUSB that is ONLY readable and is loaded into the RAM??  Then your IOs would be mostly in the RAM and you could just let it sit there.  Hmm.   -Fractal

---

### Post by jayach222 on 2007-02-09
> **kidders said:**
> 

**Suggestion 1**
Good advice...  I installed a command line ubuntu system, no gui, so beat you to that one! :)

> **Suggestion 2**
I considered other distros, particularly freenas.  I just decided to go with something I was more familiar with.  I've had a lot better luck with ubuntu than others, and some reliability issues I read about freenas wasn't making me comfortable with it.  (although my route using a flash drive sounds like it maybe worse in the long run). 

On your other points, space isn't much of an issue for me on the OS side.  The install I've done takes up about 350mb on a 1gb stick.  I mostly wanted to keep the OS separate for ease of maintenance.  Easier to swap my data disks in my lvm.  Easier to keep the OS backed up and replaced if the flash goes out.. which sounds like I maybe doing soon. ;)

Also, although speed isn't the greatest, it performs adequately for our needs, so not a great concern to me.

Thanks for all the extra info you provided.  I'll definitely be considering your points in what to move to.  I may bite the bullet and just use the extra slot I have available for a dedicated hdd for the os, perhaps buy a cheap 2.5", low power 4200rpm drive.

---

### Post by jayach222 on 2007-02-09
> **FractalBrain said:**
> Hey, Im VERY new to all of this, but who knows, it might help.   If not, let me know:

So the live CD installation of Ubuntu only had reads, no writes.  I wonder if it would be possible to make a liveUSB that is ONLY readable and is loaded into the RAM??  Then your IOs would be mostly in the RAM and you could just let it sit there.  Hmm.   -Fractal

I think this is an interesting idea - although I'm not sure how I would manage such a system.  I seem to tinker with lvm, samba, rsync, etc... quite a bit and not sure how that kind of stuff would be persisted.  Something else I'd like to look into for sure.  Thanks!

---

