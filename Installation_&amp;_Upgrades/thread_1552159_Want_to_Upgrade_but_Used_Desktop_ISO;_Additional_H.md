---
title: "Want to Upgrade but Used Desktop ISO; Additional Help Requested"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by 'Gator on 2010-08-13
Someone,

Please define "live CD".  I have received much information from dvacet (many thanks for that), but no advice works.

Please see [http://ubuntuforums.org/showthread.php?t=1509808](http://ubuntuforums.org/showthread.php?t=1509808) for my original post for help.  I didn't understand that the DESKTOP .iso and the resulting CD do not allow upgrading from a previous version, but only a fresh new installation.  In the process, my master boot record must have been altered.  I can only boot Ubuntu from the DESKTOP CD which uses Wubi to create a restricted (i.e., read-only) shell.  Using the ALTERNATE CD results in an error message which flashes by too quickly to read, followed by a "grub>" prompt.

This grub process apparently runs as a stand-alone process, not a child of an Ubuntu shell.  This fact is evidenced by such behavior as not recognizing the "find" command that is critical to some solutions to my problem.  I got around this situation, but every solution offered in the responses to my previous thread fail in the final suggested command.

I've searched the documentation exhaustively, but I can't seem to find a definition of a "live" CD.  Please help me with at least that information, and with any other suggestions you may have to help me restore my boot record so I may upgrade from the ALTERNATE file.

Thanks in advance for your help.

---

### Post by bcbc on 2010-08-13
> **'Gator said:**
> Someone,

Please define "live CD".  I have received much information from dvacet (many thanks for that), but no advice works.

Please see [http://ubuntuforums.org/showthread.php?t=1509808](http://ubuntuforums.org/showthread.php?t=1509808) for my original post for help.  I didn't understand that the DESKTOP .iso and the resulting CD do not allow upgrading from a previous version, but only a fresh new installation.  In the process, my master boot record must have been altered.  I can only boot Ubuntu from the DESKTOP CD which uses Wubi to create a restricted (i.e., read-only) shell.  Using the ALTERNATE CD results in an error message which flashes by too quickly to read, followed by a "grub>" prompt.

This grub process apparently runs as a stand-alone process, not a child of an Ubuntu shell.  This fact is evidenced by such behavior as not recognizing the "find" command that is critical to some solutions to my problem.  I got around this situation, but every solution offered in the responses to my previous thread fail in the final suggested command.

I've searched the documentation exhaustively, but I can't seem to find a definition of a "live" CD.  Please help me with at least that information, and with any other suggestions you may have to help me restore my boot record so I may upgrade from the ALTERNATE file.

Thanks in advance for your help.
The live CD is the same as the ubuntu cd: most ubuntu installation images have the ability to "Try without installing". This is referred to as live CD (probably because it used to be a separate CD at one time). See [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD) for more info. 

To help us see how your computer is setup, boot from the Ubuntu CD. Select Try without installing. Then post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") (instructions in link).

---

### Post by 'Gator on 2010-08-13
bcbc,

No need to try.  I've done it dozens of times with the DESKTOP CD.  It boots fine, giving me Ubuntu 10.04--from the CD.  My problem starts when I decide to install.  Upgrading isn't an option from the DESKTOP CD, only from the ALTERNATE CD.  When I select "Install", I've started the process of creating an entirely new partition with a fresh copy of Ubuntu 10.04 ("Lucid Lynx") in addition to my current copy of 8.04 ("Hardy Heron").

For some reason, I can't use the ALTERNATE CD which supports upgrading; i.e., copying files from Hardy to Lucid.  Doing so manually would be massively laborious and certain to miss many "hidden" (file name starts with ".") initialization files.

That's where I'm coming from.

---

### Post by snowpine on 2010-08-13
Please read the Upgrade Notes in the link below; it sounds like you are missing one or two obvious steps in the process. :)

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

Assuming you have an internet connection, the easiest way is to just let the Update Manager do its thing.

Personally I would just back everything up to an external drive and do a fresh reinstall. It is a little bit of work, true, but only once every 2 years. ;)

---

### Post by 'Gator on 2010-08-13
Thanks for the suggestion, snowpine, but it's too late.  I can't boot Ubuntu in any way except as a Wubi process from the DESKTOP download.  Since that results in my file system being read-only, with any writes going to temporary files, upgrade-manager can work its little heart out; but the results will vanish when I exit Ubuntu.

...or, at least, so sayeth the documentation.

---

### Post by snowpine on 2010-08-13
> **'Gator said:**
> Thanks for the suggestion, snowpine, but it's too late.  I can't boot Ubuntu in any way except as a Wubi process from the DESKTOP download.  Since that results in my file system being read-only, with any writes going to temporary files, upgrade-manager can work its little heart out; but the results will vanish when I exit Ubuntu.

...or, at least, so sayeth the documentation.

You can't boot your existing 8.04 install?

You might just need to reinstall GRUB.

Or am I missing the question entirely?

---

### Post by 'Gator on 2010-08-13
snowpine,

You got it exactly right.  The only way I can boot Ubuntu now is from the Desktop CD.

I couldn't agree more with your next assessment.  Reinstalling grub should do the trick.  It just seems that, in order to do so, I must have the Ubuntu shell spawning a grub shell process.  The straightforward approach, booting and choosing "Ubuntu" as the OS to boot, results in that blink-of-an-eye error message followed by a "grub>" prompt.  At that point, I can't access UNIX/Linux commands such as "find".  Even after working around that problem, the "mount" command isn't available, so I can't mount the boot sector to the file system root, the only permanent place that I seem to be able to write to.

I've tried running Wubi and mounting various parts of my 8.04 file system as suggested by the many tips I received from zvacet (see my link to my previous request for help).  Some even make sense to me.  None work.  They all fail in the last command issued before "quit".

I'm not an OS programmer, so I have to rely on tips from others.
Thanks for offering yours.

---

### Post by snowpine on 2010-08-13
If your 8.04 install is a Wubi install, I'm afraid I can't help (never used Wubi).

If it's a full install to its own partition, and you can boot the Ubuntu Live CD, you should be able to install GRUB easily. There are some good how-to's on these forums and in the [Ubuntu Wiki]("https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB").

It sounds like you might be trying to reinstall GRUB using the Alternate CD, which I don't think is possible.

Personally I would back everything up and do a fresh, non-Wubi install of 10.04.

---

### Post by 'Gator on 2010-08-13
snowpine,

Thanks for your insightful information.  I'll search for the leads that you mentioned.

No, I'm not trying to reinstall grub from the Alternate CD.  I can't do anything with it.

No, my 8.04 installation isn't a Wubi install.  Wubi.exe is the program which allows an MS Windows user to preview Ubuntu without installing.  If one chooses to install, I'm not sure if Wubi does it or if it passes control to a separate Ubuntu installer.  If I sound like I know what I'm talking about, it's an illusion; maybe even an elaborate hoax.  I've read more documentation in the past 6 weeks than when I started my first programming job almost 40 years ago.  "Wubi", I learned, stands for something like "_W_indows _UB_untu (_I_mager?).

My search for techniques on reinstalling grub might take some time.  Besides, I've been up for over 24 hours; and I can't do that as well as I could 40 years ago.  May I contact you with further questions if I have any?  If "yes", how can I get your attention without starting an entirely new thread?

Thanks ever so much for helping an Ubuntu novice.  While I was first introduced to UNIX in 1982, I mainly managed and wrote shell scripts; but I fell in love with its straightforward simplicity yet enormous flexibility and power.  I, too, am an addict.

---

### Post by snowpine on 2010-08-13
No problem; I am 'subscribed' to the thread and will see any follow-up posts you make.

My suggestion is get some sleep :) then forget I ever mentioned Wubi (it was a red herring) and don't even worry about upgrading to 10.04 until you have repaired your 8.04 install. If all the partitions and files are untouched it should be a simple as reinstalling GRUB using an Ubuntu Live CD. Once you have restored Ubuntu to a working state, you can take it from there.

---

### Post by bcbc on 2010-08-13
> **'Gator said:**
> bcbc,

No need to try.  I've done it dozens of times with the DESKTOP CD.  It boots fine, giving me Ubuntu 10.04--from the CD.  My problem starts when I decide to install.  Upgrading isn't an option from the DESKTOP CD, only from the ALTERNATE CD.  When I select "Install", I've started the process of creating an entirely new partition with a fresh copy of Ubuntu 10.04 ("Lucid Lynx") in addition to my current copy of 8.04 ("Hardy Heron").

For some reason, I can't use the ALTERNATE CD which supports upgrading; i.e., copying files from Hardy to Lucid.  Doing so manually would be massively laborious and certain to miss many "hidden" (file name starts with ".") initialization files.

That's where I'm coming from.

I'm not asking you to install from the live CD. I'm asking you to boot it and post the bootinfoscript results - link in previous post. 

It will help us to see what is going on. Since you can't boot your 8.04 installation. 

By the way, you're misunderstanding what wubi is. It does a full installation of ubuntu (not a read-only preview) and you can apply updates (it just does it to a virtual disk). But that's not the point, since you want to fix your 8.04.

---

### Post by 'Gator on 2010-08-15
snowpine,

Thanks for subscribing to this thread.  I value your insight and advice.

bcbc has suggested a way to determine if something might have gone wrong with my initial attempt to upgrade.  I want to pursue it; however, it requires an Internet connection to download a diagnostic program.  So far, I've been unable to establish one.

Please stay tuned.  Thanks for your help so far.

--'Gator sends

---

### Post by 'Gator on 2010-08-15
bcbc,

If you read my reply to snowpine, you know that I'm having trouble connecting to the Internet so I can download boot_info_script.

The fact that you picked up on my replies to snowpine tells me that you're subscribed to this thread.  I really appreciate your willingness to help me.

I need to establish that connection, but the help apps have changed since I originally connected in the olden days of Edgy.  Please be patient with me while I figure out what I'm doing wrong.  I'll post another reply with the boot_info_script results if I succeed soon; otherwise, I'll beg for more time to achieve success.

I'm somewhat out of my league here.  While I've acted as a UNIX system administrator, that ended in 1995.  I'm mostly a shell and C programmer, so I'm used to others setting up the resources that I count on in designing apps.

Back to you soon, I hope.

--'Gator sends

---

### Post by snowpine on 2010-08-15
If a 10.04 Live CD works well on your hardware, I suggest backing everything up and doing a fresh install of 10.04. 

Your original argument was basically "I want to upgrade instead of reinstalling because upgrading will be less time-consuming" however that was 2 days ago. :) I don't see the benefit of troubleshooting your 8.04 install if you aren't planning to stay with 8.04.

---

### Post by 'Gator on 2010-08-22
bcbc, snowpine, and any other potential responders,

I've come to the conclusion that most, if not all, of my problem upgrading from Ubuntu 8.04 to 10.04 result from my starting the process from the Desktop/Live CD instead of the Alternate/Install CD.  (If you've read my previous posts, you know this.)

My error resulted in the creation of a new partition on /dev/sdb.  My investigations have indicated that my original 8.04 installation still exists in sdb1, which was truncated by the creation of a new partition, sdb2, for 10.04.  Additional difficulties might have occurred because 8.04 used grub 0.97 as its bootloader, whereas 10.04 uses grub 1.98.  The latter almost certainly occupies more hard-disk (HD) space than the former, so I may be exceeding the truncated partition size of sdb1 in attempting to upgrade grub to grub2.

I'm still very much in the dark, but I've learned a lot in the past week.  I've come to the conclusion that I must (in reverse order):

1) Delete sdb2, and probably resize sdb1 to the full HD space; and

2) Back up sdb1 before trying the above operations.

I foresee the following possible obstacles in completing my proposed course of action:

- Choosing the most trustworthy tool to accomplish step 1, including deciding under which operating system to run this process; e.g., can I trust the "live" CD-spawned Ubuntu to make 
permanent changes?

- How do I back up sdb1?  I see many admonitions to do so, but never a suggestion about what program to use.  tar?  That should work even if the sdb1 file system is read-only, as I understand is the case when booting Ubuntu from the Desktop/Live CD.  Still, it's been 15 years since I used it to copy tapes (my facility wasn't concerned with data security then).  I seem to recall that tar can span volumes, and I'll use up multiple DVDs in backing up the partition; so tar seems to meet the need.  I guess I just need a little reassurance.

I'm currently researching "ghosting" backup programs for backing up.

I will appreciate any suggestions on any step(s) in my proposed course of action.

--'Gator sends

---

### Post by bcbc on 2010-08-22
> **'Gator said:**
> bcbc, snowpine, and any other potential responders,

I've come to the conclusion that most, if not all, of my problem upgrading from Ubuntu 8.04 to 10.04 result from my starting the process from the Desktop/Live CD instead of the Alternate/Install CD.  (If you've read my previous posts, you know this.)

My error resulted in the creation of a new partition on /dev/sdb.  My investigations have indicated that my original 8.04 installation still exists in sdb1, which was truncated by the creation of a new partition, sdb2, for 10.04.  Additional difficulties might have occurred because 8.04 used grub 0.97 as its bootloader, whereas 10.04 uses grub 1.98.  The latter almost certainly occupies more hard-disk (HD) space than the former, so I may be exceeding the truncated partition size of sdb1 in attempting to upgrade grub to grub2.

I'm still very much in the dark, but I've learned a lot in the past week.  I've come to the conclusion that I must (in reverse order):

1) Delete sdb2, and probably resize sdb1 to the full HD space; and

2) Back up sdb1 before trying the above operations.

I foresee the following possible obstacles in completing my proposed course of action:

- Choosing the most trustworthy tool to accomplish step 1, including deciding under which operating system to run this process; e.g., can I trust the "live" CD-spawned Ubuntu to make 
permanent changes?

- How do I back up sdb1?  I see many admonitions to do so, but never a suggestion about what program to use.  tar?  That should work even if the sdb1 file system is read-only, as I understand is the case when booting Ubuntu from the Desktop/Live CD.  Still, it's been 15 years since I used it to copy tapes (my facility wasn't concerned with data security then).  I seem to recall that tar can span volumes, and I'll use up multiple DVDs in backing up the partition; so tar seems to meet the need.  I guess I just need a little reassurance.

I'm currently researching "ghosting" backup programs for backing up.

I will appreciate any suggestions on any step(s) in my proposed course of action.

--'Gator sends

I still think you should post the results of the bootinfoscript. You can download it from another computer if you're having trouble connecting.  

I've never heard of the cd installer shrinking an ext3 partition to install dual boot automatically.

The partitions are not read-only from the live CD, they're just not mounted automatically.

There is a howto backup that you can use - just plug in an external USB drive first. [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
If it were me, I'd also copy my data uncompressed - USB drives are so cheap that space is not an issue, and it's just easier to find data when it's not buried in an archive.

---

### Post by 'Gator on 2010-08-23
bcbc,

We must mean different things when we refer to a "live" CD--which wouldn't surprise me, since I've never seen the term defined in documentation.

Previously, the only way I could boot Ubuntu was to perform some operation I read about in documentation which added some files to the Desktop CD.  (I was unable to do anything with the Alternate CD.)  One of those added files was Wubi.exe which, when run, booted Ubuntu 10.04.  I was able to access the ENTIRE file system, but couldn't alter it permanently.

Now, mysteriously, I can read the Alternate CD which offers five (maybe four) options.  The last is "Rescue" which seemed like it would work but failed in the final step.  (That's getting to be a recurring theme.)  I also tried the "Reinstall grub" option, which also failed, maybe because I have grub 0.97 in the original partition but Ubuntu 10.04 uses grub 1.98.

I may have created the new partition (second one on the second HD) while I was confused about which CD (Desktop or Alternate) I should use to upgrade to Ubuntu 10.04.  In any case, I suspect that failures of the numerous restoration methods might have to do with the limited space left in the first partition.  I'd really like to delete this partition and expand the original one to include the whole HD, if for no other reason than to eliminate this possible source of failure.

I may have to do so from MS Windows since I suspect that Wubi.exe doesn't make permanent changes to the file system.

--'Gator sends

---

### Post by 'Gator on 2010-08-31
I'm about as disappointed as is possible.  I downloaded Knoppix 6.2.1 because SAYS it allows me to repartition my hard drive (HD).  That would allow me to delete the partition that I erroneously installed with the "live" (bootable from Windows) version of Ubuntu.  It would also allow me to "ghost" partitions that I want to protect from loss during the deletion.

When I attempt to run Knoppix, either at boot time or under Windows, I doesn't work.  I've tried running the Alternate Ubuntu 10.04 CD at boot time.  It no longer works.  In both cases, Windows boots.

When I try to run the Desktop Ubuntu CD, it won't start at boot time.  I have to wait for Windows to boot, then run Wubi.exe from the CD.  When I do this, Ubuntu 10.04 acts as if no HDs exist except for the one contains Ubuntu 8.04 (sdb)--this in spite of the fact that, not seeing my Ubuntu HD, the Alternate CD said it would install Ubuntu on the Windows C: drive (sda).

Why Ubuntu can no longer detect NTFS is beyond me.  If that's a change, I may well abandon Ubuntu as I relied on its ability to view other file systems, something Windows has never done.  (If it ain't Windows, it doesn't exist.)

--'Gator sends

---

### Post by snowpine on 2010-08-31
You need to boot from a Live CD if you want to repartition your hard drive (no, Wubi won't work). Check that you are burning the CD correctly and that your computer's BIOS for a boot menu that allows you to boot from CD. 

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

If your computer BIOS for some strange reason does not support this, you can create a Live USB that accomplishes the same thing: 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Also double-check that the Live CDs boot on another computer, if you have one. The fact that you cannot boot ANY Live CD (Knoppix, Ubuntu, etc.) says to me either you are burning them incorrectly or you have a hardware problem with your BIOS and/or CD drive.

---

### Post by 'Gator on 2010-09-01
bcbc,

I agree with you completely about posting the results of bootinfoscript.  I just have no way from Ubuntu to download it since I can't get an Internet connection.  Is it truly a script?  I.e., a file that I could download under Windows onto a USB stick?

As for the CD installer shrinking a partition, could it happen if I told the Live CD's installer to put a new installation on the same drive as the existing Ubuntu installation?  I.e., might it truncate the existing partition after the last file?

Thanks ever so for the link to the tar backup information.  From the start, I thought that tar was the answer to my backup need; but it's been 15 years since I used it to copy images from a RAID to several tape formats and back again.  In fact, it's been so long that I can't remember whether tar is one of the few backup programs which can "span volumes"; i.e., put one backup collection on multiple media volumes; e.g., write one HD partition to multiple DVDs which are made to look like "spliced tape" or other continuous medium (one table of contents encompasses the entire collection on multiple receiving volumes).  That capability was standard on the mainframes and minicomputers I worked on since the early 70s, but a rarity on microcomputers.

So as not to lapse into "History of Computing 101",

--'Gator sends

---

### Post by 'Gator on 2010-09-01
snowpine,

1) I know that my BIOS allows booting from a CD (and USB).  I did so successfully from, among others, the Ubuntu 10.04 Live CD.  The problem with using it is that it wants to create a new, clean installation whereas I want to upgrade from 8.04.  That's the province of the Alternate CD, which isn't live.

2) I don't have ready access to another computer which has Internet access, a CD or DVD drive, or anything remotely resembling a modern computer.  My other computer is a -486DX4 with only a floppy drive ("SneakerNet") to transfer files.  It still has C and Bourne shell code I wrote that I need to copy to something more modern.

I'll almost certainly use a USB stick to copy ISOs related to this issue.  Along that line, bcbc recommends that I not copy with compression (see bcbc's post).

It's 7 A.M. my time and I haven't slept (again), so I'm signing off.

--'Gator sends

---

### Post by 'Gator on 2010-09-01
bcbc, snowpine,

Thanks for hanging in there with me.

--'Gator sends

---

### Post by snowpine on 2010-09-01
> **'Gator said:**
> bcbc, snowpine,

Thanks for hanging in there with me.

No problem! I am enjoying the ride. I am a little fuzzy on what the actual question is at this point :) so I will repeat my original advice: a fresh reinstall from your (apparently fully functional?) Ubuntu 10.04 Live CD may be the quickest and cleanest route to a functional 10.04 system.

---

### Post by 'Gator on 2010-09-11
bcbc, snowpine,

Good news and bad news, folks.  The bad news, esp. for bcbc, is that running boot_info_script almost certainly won't tell you anything useful.  The good news is that it's because I can boot 10.04 error-free from my hard disk.  If I can figure out how that happened, I'll apply for a professorship at a prestigious institution of higher learning.  All I did was to try one thing on the Live CD, another on the Alternate CD, and so forth until suddenly I had a full-blown 10.04 on the HD.

The disappointing issues:

- My 8.04 files weren't integrated into the 10.04 file system.  They're on a separate node.  I guess I'm stuck with merging them into the 10.04 file system manually, which is what I was trying to avoid when I started the post that y'all have responded to.

- 10.04 doesn't have as intuitive an interface for my DNS connectivity.  I just can't connect.  I think that I have to establish a PPPoE connection between the Network Interface Card (NIC) and the ADSL modem, then send the modem the details of the DNS, setting up the DNS IP address, setting the password, etc.  It just doesn't work.  I wish I could be more specific.  The PPPoE part seems OK, but the modem-to-DNS just halts and looks dumb.  Any ideas?

On the positive side, when I found that NFS doesn't still access my NTFS drive, it was a trivial exercise to create a script to mount it.

I hope life goes well with y'all.  If you have any insight about some method of integrating the old filesystem into the new, or if you have any suggestions about the proper procedure for establishing an Internet connection for ADSL, I'll appreciate your input.

--Steve ('Gator) sends

---

### Post by ronparent on 2010-09-11
I have found this useful: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by 'Gator on 2010-09-12
ronparent,

Thanks for the link to that document.  I'll see what it can do for me.

---

