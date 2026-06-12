---
title: "Ubuntu 11.04 install auto-deleted my backup hard disk"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by markling on 2011-05-02
My backup hard disk is connected by USB cable. After I installed Ubuntu 11.04 the disk had been wiped and a version of Ubuntu installed on it.

I had forgotten to disconnect the external disk's usb cable before running the install in case something like this happened.

I then just took whatever the installer said regarding partitions: I trusted it; and the installer's manual partition manager is a little too technical to be user-friendly. Mostly, I just trusted the automated partition manager to be making the right decisions for me.

The installer's auto-partition manager said it was erasing two partitions. I thought, oh that must include some sort of swap drive then.

The auto-partition manager said it was using 500Gb of space. I thought, well there's more HD space on my desktop than I thought. I recently acquired the machine. It was a hand-down.

The installer said do you want to install Ubuntu with, over or beside whatever existing versions there are. I said, over. I wanted a clean install since my attempt at making Ubuntu do an upgrade install had already failed. ([http://ubuntuforums.org/showthread.php?t=1745937](http://ubuntuforums.org/showthread.php?t=1745937))

This was clearly stupid of me. But it was not as stupid as issuing an O/S installer that did what this one did.

The installer completely wiped my external usb backup drive. Not only that, but it installed another instance of Ubuntu on it. The install routine actually installed two instances of Ubuntu 11.04: one on my local HD and one on my now erased external HD.

Just to rub salt in the wound, the update manager only updates the version that's running: the version on my internal HD. The version the installer copied over my backup data is redundant.

I have fortunately a second backup of most essential data. But the external HD contained data that was not copied elsewhere. It has been permanently erased. It will probably possible to retrieve this data from original sources at a considerable inconvenience. I do not know at this time whether and how much of the data that was erased is now lost forever and what the consequences of the loss would mean.

This should not have happened.

---

### Post by markling on 2011-05-02
Confirmed that the O/S files installed over my backup drive are 11.04 files: they include, for example, kernel version 2.6.38...

---

### Post by causeitsme on 2011-05-16
Confirmed, deleted all backup partitions on drive. WTH is up with that?

---

### Post by markling on 2011-05-16
I don't follow your question, causeitsme.

---

### Post by MoonStomper on 2011-05-17
same thing happened to me a couple of days ago. before installing natty on my 2nd hdd, i made a backup of its contents on an external drive. i left the usb cable connected and proceeded with the installation. next thing i knew all my backup was gone. :icon_frown:

---

### Post by Quackers on 2011-05-17
If you used manual partitioning and the installation went where you told it to, how can you possibly blame the installer?
It's up to you where the installation was to take place. You need to know which drive you intend to install to.
The installer only did what you told it to.

There is a program called testdisk which may get your old partitions back. It may be worth a try.
Here is a good "howto"
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by markling on 2011-05-17
I left it to Ubuntu's automated process. It chose to install itself on my backup USB drive. I foolishly allowed it.

---

### Post by markling on 2011-05-17
Just so this is clear. It was Ubuntu's automated process. It deleted by backup hard disk. I'm rather upset about losing it.

---

### Post by Quackers on 2011-05-17
I understand, and I also understand that you are not pleased about it.
When your USB HDD backup drive is plugged in please start gparted and see which drive is designated as /dev/sda. It should be your internal hard drive, but maybe it is your external.
Any time you are partitioning or installing something and it states anything that you are not sure about (like "erasing two partitions") it is wise to stop and check first. You can always start the installation again, but you can't always fix something that's gone wrong.
Did you take a look at testdisk?

---

### Post by markling on 2011-05-18
Quackers, I don't think seeing which drive is designated as /dev/sda will do any good now. Not only has the damage been done, but the install failed (see: [http://ubuntuforums.org/showthread.php?t=1745937](http://ubuntuforums.org/showthread.php?t=1745937)). I had to go back and install 10.10 again on my local disk.

Your suggested precautions (stop and check anything you are unsure about during install like "erasing two partitions") are also a poor substitution for a well designed, i-d.i-ot-proof install procedure.

(The last time I used the word i-d.i_ot on this forum, in reference to myself, it was censored).

That means making sure the install procedure does not automatically propose subsuming someone's usb hard drive, and then mirroring the installation when they fail to catch it.

Partitions and device files are not familiar territory among the sort of users, like me, who rely on automated install procedures.

I don't know what testdisk is. Perhaps you can recommend a good undelete utility?

---

### Post by Quackers on 2011-05-18
Looking at the drive designations would forewarn you for the future. 

In reality, the installer has only done what you allowed it to. Relying blindly on automated procedures is not the most reliable way to go about partitioning a drive. The installer gave you the option to check what was being done when it informed you that 2 partitions would be erased and you also reported that it seemed to suggest to you that you had 500GB of space, which was more space than you thought you had. These should have raised alarm bells to you and the installation should have been stopped at that time to enable a check of what was proposed, in my opinion.
When all is said and done, you allowed the installer to use the wrong hard drive and whilst I sympathise (having made similar mistakes myself) blaming the installer is in my opinion, just passing the buck.
I hope you can get all your data back. There is a link for the use of testdisk in post #6. Another is below. I am not familiar with any undelete programs, I'm afraid.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by markling on 2011-05-26
No, Quackers. No.

I made clear in my previous posts on this that I was mistaken to trust Ubuntu's install procedure would be watertight. It was late. I had been very busy. Etc. Etc.

But the simple fact is the installer was at fault. I may have been at fault for not spotting that the installer was at fault and was about to delete my backup drive. But the Ubuntu installer was at fault.

One more time.

Ubuntu's install procedure automatically opted to install itself twice: once on my local hard drive and once on my external hard drive, which was connected by a USB cable. I did not 'opt in' to this.

The result was two identical instances of Ubuntu: one on my local disk and one on my external disk. The one on the external disk erased my backup data.

It would not take a genius to work out that the copy of Ubuntu that is now on my external disk is utterly redundant (that, in case you aren't sure, means much more than simply redundant - it's sort of comparable to infinitely redundant, only a little more so). There can be no further proof that this is a fatal flaw in the Ubuntu install procedure. It needs to be changed before it causes any more damage. And someone needs to report back here that the change has been made. <snip>

---

### Post by ILoveYorkies on 2011-05-26
Hi Markling,

I am sorry that you accidently allowed 11.04 to install itself on your  backup drive but Windows could have done the same thing. Quackers is  right on the point that you should have been more careful as WE ALL  SHOULD BE WHEN PARTITIONING OUR DRIVES WHETHER MANUALLY OR ALLOWING ANY  SOFTWARE TO  DO IT FOR US! 

As for 11.04 installing 2 versions of itself being a flaw, I can't  comment because I chose to manually install Natty on my netbook.Also I  haven't seen any other posts complaining about that happening with the  automatic choices, but that doesn't mean it hasn't happened to someone  else. You might ask MoonStomper if Natty installed ionto both his backup and internal drive since MoonStomper that it erased his usb drive too when he left it plugged in during install. I suppose Ubuntu formatted your usb drive as ext?? instead of Fat32 or NTFS. I know more about Windows than Linux, I know there are several undelete free and trialware on download.com for Windows because this happens alot with Windows software too. I'm not so sure about those for Linux though. There are 2 rescue disks I know of one is by Knoppix livecd or there's one called SystemRescueCD livecd. I downloaded but didn't need the repair tools yet. But it did boot for me, that much I tested. [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) I just found this one  [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) I also found this one [http://trinityhome.org](http://trinityhome.org) /Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en   I think this is what Quackers suggested  [http://linux.die.net/man/1/testdisk](http://linux.die.net/man/1/testdisk)
I think the last 2 maybe harder for you to use. READ these through before using them but I think SystemRescueCD might be easier. Before downloading for myself I read about the list of software it includes and the advanced descriptions of them.This  lists even more from  [http://en.wikipedia.org/wiki/List_of_live_CDs](http://en.wikipedia.org/wiki/List_of_live_CDs)

**Rescue and repair live CDs**


[LIST]
[*][Billix]("http://en.wikipedia.org/wiki/Billix")  &#8211; a multiboot distribution and system administration toolkit with the  ability to install any of the included Linux distributions
[*][BootMed]("http://www.bootmed.com/") &#8211; a Live CD that was made to help those not familiar with Linux repair or recover their Windows Computer from a Live CD.
[*][Inquisitor]("http://en.wikipedia.org/wiki/Inquisitor_%28hardware_testing_software%29") &#8211; Linux-based hardware diagnostics, stress testing and benchmarking Live CD
[*][Parted Magic]("http://en.wikipedia.org/w/index.php?title=Parted_Magic&action=edit&redlink=1")
[*][RIP: (R)ecovery (I)s (P)ossible]("http://en.wikipedia.org/wiki/Recovery_Is_Possible") is a Linux-based CD with partition tool and network tools ([Samba]("http://en.wikipedia.org/wiki/Samba_%28software%29")), based on the 2.6.17 kernel.
[*][System Folder]("http://en.wikipedia.org/wiki/System_Folder") of [Mac OS]("http://en.wikipedia.org/wiki/Mac_OS") on a [CD]("http://en.wikipedia.org/wiki/Compact_Disc") or on a [floppy disk]("http://en.wikipedia.org/wiki/Floppy_disk") &#8211; works on any media readable by [68k]("http://en.wikipedia.org/wiki/68k") or [PowerPC]("http://en.wikipedia.org/wiki/PowerPC") Macintosh computers.
[*][SystemRescueCD]("http://en.wikipedia.org/wiki/SystemRescueCD") is a Linux-based CD with tools for Windows and Linux repairs, based on the 2.6 kernel.
[*][Trinity Rescue Kit]("http://en.wikipedia.org/wiki/Trinity_Rescue_Kit") &#8211; Mandriva Linux-based CD for use on a Windows or Linux-based system.
[/LIST]

 I hope this list of websites helps. Good luck.

---

### Post by markling on 2011-06-30
Dear Yorkies. Thanks very much for the list of recovery tools. That's very helpful of you.

Regarding your comments about how I should have been more careful, the reason why you know I needed to be more careful was because I told you what actions of my own contributed to the loss of my data. I do not to need be told again and again how I should have been more careful. This is quite insulting to me. I made it clear in my original post how certain I was of my own error. I did this to remove any question of that and so clear the way for the point and complaint I was trying to make about the Ubuntu install procedure. The procedure failed. I shall say this again: it installed two identical copies of itself: one on my local hard disk and one on my external USB hard drive. This is clearly a most ridiculous thing for an install procedure to do. It seems from my vantage to have been a particularly reckless thing for an install procedure to do as well, since it had to delete my backup disk in order to install the second copy of itself. Please, please refrain from telling me how stupid I was to let the Ubuntu installer delete my backup disk. I know this. I said this myself from the outset. I don't expect to retrieve my lost data. I just want to be told that someone who is responsible for this clumsy Ubuntu install procedure has noted my problem, regrets what happened, and is looking to ensure that it doesn't happen to anyone else.

Markling.

---

### Post by markling on 2011-07-03
Just for fun, I've just booted from the USB hard drive where my backups used to be.

It's booted up beautifully into Ubuntu 11.04. This really is the icing on the cake. The install of 11.04 on my local HD failed. I had to got back to 10.10. But the instance of 11.04 the Ubuntu installer copied over my backup disk works just fine when I boot it from the same computer that didn't like 11.04 on the local disk.

So at this very moment, I am writing this post from the 11.04 instance that used to be my USB backup drive.

Someone please tell me I ought to take more care to prevent Ubuntu's automated install procedure from overwriting my backup drive in future. Losing my data hasn't been lesson enough already. I think there must be plenty more people who know better than I do how much of a mistake I made.

---

### Post by markling on 2011-07-03
The final word on this is that a consumer operating system ought to have a fail-safe / fool-proof installer.

These suggestions that I should have been more careful are rendered groundless when one considers the results of this failed install procedure in their broadest sense. That is, it installed *two* instances of Ubuntu: one on my local HD and one on my USB backup HD, (from which I am writing this email, having booted it up).

This is utterly useless. Think about it. You install an O/S on your desktop computer. It is usual that this install is done on its local HD. Why on earth would anyone want the install procedure to install another instance of itself on your backup HD as well?

But of course, no-one wants to listen because saying this sort of thing in this forum is blasphemous.

---

