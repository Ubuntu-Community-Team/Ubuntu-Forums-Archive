---
title: "New install will boot neither Windows nor Ubuntu"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2008-05-27
(Attempt 4)
Greetings new family.  I need a safety net!

Bottom line 1: I can't boot either Windows or Ubuntu (8.04).  I do get the menu for which OS I want to boot but it goes nowhere from there.

Bottom line 2: What is the best emergency boot software I can buy/download so I can repair the Windows partition?  (I am smarter about Ubuntu and will install differently next time.)

The details:
My primary hard drive is 200GB and I had used Partition Magic to set up my Windows-XP partition at ~ 100GB (ok, 97GB & change), leaving 92GB unused.  (That was years ago.)  When I installed Ubuntu last night, I chose "Guided, using largest unused partition" and it seems to have done so.  And when I boot from the main drive, I do get the dual boot menu.  And then the fun begins: :mad:

[LIST]
[*]If I choose Windows, I get the banner page with the slider flashing left & right but I never thee the login screen. :(
[*]If I choose Ubuntu, I get an error (can't recall it at the moment) and a menu of alternate "boot devices".  All but one give me an error and a repeat of that menu.  One gives me a command line but I don't know what to do next. :confused:
[/LIST]

Booting to Windows Safe Mode yields a godzillion error messages but no Windows.

I have booted from the Ubuntu installation CD to get out this far.  The partition editor tells me the ntfs partition is still there but the information page on said partition, it displays errors when "Checking filesystem consistency".  (Interestingly, I cannot select text from that page to copy here.)

Cluster accounting failed at 492 (0x1ec); extra cluster in $Bitmap
...
Cluster accounting failed at 498 (0x1f2); extra cluster in $Bitmap
...
A few more such messages.

The summary: 
Filesystem check failed! Totally 23109 cluster accounting mismatches.
ERROR: NTFS is inconsistent.  Run *chkdsk /f* on Windows, then reboot it TWICE!

There you have it, folks.  The obstacle: Booting into Windows.  Hence, my request for advice on an emergency boot CD.

[LIST]
[*]I am looking for the Partition Magic disk but I don't recall if it is bootable.
[*]My very talented son suggests I boot from the original Windows CD, that this will give me the chance to run chkdsk.
[*]I am about to ride to J & R or another sotware retailer to purchase a product that purports to do this.
[/LIST]

Any better ideas?

Thanks.

-- Rasputin Paskudniak (Silly nom de guerre, I know, but it's *mine*!)

---

### Post by hal8000 on 2008-05-27
Well, as the error message states, you have an unclean windows volume.
Booting with the ERC on windows and running chkdsk /f is one way around this, however a successful Ubuntu install would not be stopped by a faulty windows install- so I think you have more than one problem.

The Hardy 8.04 live install cd may contain ntfsfix (havent checked, but running ntfsfix /dev/sda ) is a linux method of checking an ntfs filesystem.

Boot with the Hardy 8.04 live CD and post the output of

fdisk -l

---

### Post by Rallg on 2008-05-27
Sounds as if your Grub does not have a correct partition list.

Before doing anything else, boot to the live CD, use GParted. What does it report for the partitions you have? That is, what are the partition numbers, file systems, sizes? Which one is marked "boot" (probably not the problem, but worth knowing)? Are the partitions primary, extended, logical?

Then, use the Terminal:

ls -l /dev/disk/by-uuid

Put that information here, and maybe one of the forum experts can help you.

Also, post the contents of the Grub menu.lst on your hard drive (not the live CD's own file, but the one on your hard drive where you expect to boot).

---

### Post by Kevbert on 2008-05-27
If it's Windows XP you can use the original CD.  The install menu will run.  at some point it will ask you whether you want to have a new install or go into recovery mode.  In recovery mode you'll get a terminal prompt. Perform your chkdsk /f.  Enter fixmbr (return) and then fixboot (return) and then when it finished you should be able to reboot (Ctrl-Alt-Del) into Windows.

---

### Post by rpaskudniak on 2008-05-27
Kevbert,
Thanks very much.  Your is the solution I will initially go for; I have printed them out and will let y'all know how it went.  (I did have a mildly scary moment looking for the XP disks I had not looked at in 4 years. ](*,)

-- Rasputin II  (I see the name Rasputin is already taken.:shock: )

---

### Post by JCSalomon on 2008-05-27
> **Kevbert said:**
> If it's Windows XP you can use the original CD.

&#8195;Do note that you will have to re-install GRUB (the bootloader) afterward, but I can walk you through that easily enough.&#8194;(It’ll be a limited run of the Ubuntu installer.)
—Joel

---

### Post by rpaskudniak on 2008-05-27
Kevbert,
I'm sory to report another obstacle to running the chkdsk /f command.  My XP installation disk is pre-SP; my SP2 was a separate download.  The chkdsk command does not recognize /f, only /p and /r.  The /r purports to recover bad sectors and recover data.  "The /f command automatically fixes 
any errors encountered."  The output of /p states there are no errors, so I suspect no bad sectors - only some stuff in the partition header page[s], which I think will not be affected by /r.

If I could borrow a neighbor's recent XP installation disk, perhaps I could get the correct version of chkdsk.  My son is looking for his old CD, although he may have tossed it since he installed Ubuntu.  (He will never go back to Windows; I still have much committed in there.)

Q. Will the Vista install disk have the correct chkdsk for ntfs?

Q reprise: So what is the best emergency boot software I can buy ASAP?

Responding to Hal8000 (Scarier moniker than Rasputin :-) ): My WIndows install has been quite robust until now.  It developed faults only with the Ubuntu install.  However, I will take up your other suggestions on Wednesday.

Rallg: I will take up your suggestions as well, posting what I can of the GParted output.  The ls output will be easy enough.  But the GParted windows seem to resist select for copy/paste.  How do I capture a whole window as a graphic, so I can post it? (Yucch - all that space!)

(Whew) Sorry about the long-windedness here.

Thank much for the suggestions.

-- Rasputin II

---

### Post by Kevbert on 2008-05-28
Have a look at this post first: [http://ubuntuforums.org/showthread.php?p=5055068#post5055068]("http://ubuntuforums.org/showthread.php?p=5055068#post5055068")
Try the ntfs fix first.

[QUOTE=rpaskudniak;5059606]Kevbert,

Q. Will the Vista install disk have the correct chkdsk for ntfs?

Q reprise: So what is the best emergency boot software I can buy ASAP?
/QUOTE]

A1.  I don't know as I've tried to keep away from Vista.

A2.  You could try using super grub which can be found here: [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")
See RHS for download.  It gives you an option to boot windows and is free.
Documentation can be found here: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by darexx on 2008-05-28
Just curious. You say you chose the option:

"Guided, using largest unused partition"

However AFAIK there is no such option. There is an option:

"Guided using largest contiguous space" or something like that. Is that what you used?

I am asking because also being new to UBUNTU the contiguous space option is not immediately clear as to what it means. Does it actually mean largest unused partition or not?

---

### Post by Kevbert on 2008-05-28
> **darexx said:**
> Just curious. You say you chose the option:

"Guided, using largest unused partition"

However AFAIK there is no such option. There is an option:

"Guided using largest contiguous space" or something like that. Is that what you used?

I am asking because also being new to UBUNTU the contiguous space option is not immediately clear as to what it means. Does it actually mean largest unused partition or not?

Largest contiguous space means that the installer will look at partitions that have data on them and will try to shrink the used partition, create a new one and install Ubuntu on that.  Often the install can fail (especially in the case on WinXP) as a paging (ie swap) file is put towards the end of the partition.
More often than not its better to install Ubuntu (and its derivatives) with manual partitioning rather than guided.  The system files should be given at least 10Gb, formatted as ext3 and mount point as /  The swap partition has no formatting and should be a minimum of two times the ram memory in the PC.
Hope this is of use.

---

### Post by darexx on 2008-05-28
> **Kevbert said:**
> Largest contiguous space means that the installer will look at partitions that have data on them and will try to shrink the used partition, create a new one and install Ubuntu on that.  Often the install can fail (especially in the case on WinXP) as a paging (ie swap) file is put towards the end of the partition.
More often than not its better to install Ubuntu (and its derivatives) with manual partitioning rather than guided.  The system files should be given at least 10Gb, formatted as ext3 and mount point as /  The swap partition has no formatting and should be a minimum of two times the ram memory in the PC.
Hope this is of use.

Thanks Kevbert that clears it up. I had suspected that it was something like that but wasn't sure.

This also explains what went wrong for rpaskudniak (although not how to fix it). Whereas he wanted to install into an empty partition he ended up installing into his XP partition with the resulting problems.

Using a manual install he should be able to install into the empty partition and at least get one working copy of UBUNTU (assuming that grub writes OK).

---

### Post by rpaskudniak on 2008-05-28
Gulp!  That's what happened!  I couldn't remember the exact quote of the prompts.  I had been assured that it would issue warnings before messing with the Windows partition.  Lawn fertilizer! as I now see.

OK, I will have to install Unbuntu again at a later date.  In the meantime, my top priority is to **_get windows working again_**, with a correct partition size, not shrunk.  When I am ready for that, I will share my scheme and aske for corrections.

Thanks for the help so far, Kevbert.  Like the cat you just fed, I will be back for more.  ;-)

-- Rasputin II

---

### Post by rpaskudniak on 2008-05-29
Kevbert,
thanks for the reference to supergrub.  It opens a whole new can of worms. (But they're nice worms.)

My priority right now is to remove Ubuntu altogether and just get Windows working again.  I will Try Ubuntu later, as I mentioned. If my flawed install has indeed shrunk my Windows partition, I will have to move my kid's media someplace else for protection so that I don't start with a full partition.  (I'm backing it up now; I can access the windows files.)

I have found wiki documentation for what looks my exact problem:

[INDENT]
[FONT="Century Gothic"][[COLOR="Blue"]How to boot Windows without problems.,  I had Linux and Windows in dual boot and then Windows no longer boots.,  I had both Ubuntu and Windows installed and now Windows boots just hangs.[/COLOR]]("http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems")[/FONT][/INDENT]

I only hope the CD-booted Ubuntu I am now using works for burning CD's.

Wow! I'm all overdaplace this morning! :???:

Thanks mucho!

-- Rasputin II

---

### Post by rpaskudniak on 2008-05-30
(Warning - long-winded post) :popcorn:

Kevbert & company,
as I write this, I am printing out the big doc you referred to in the URL:
[http://users.bigpond.net.au/hermanzo...bDiskPage.html]("http://users.bigpond.net.au/hermanzo...bDiskPage.html")

However, I did take the time to join the supergrubdisk.org forum, and do some thinking out loud while reading Adrian15's replies to a shockingly high number of similar problems with Ubuntu 8.04. In the process, I have some output that might help Kevbert help my situation.

First, FWIW, here is the output of sfdisk -l:

[FONT="Courier"]
ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/hde: 24792 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hde1   *      0+  12748   12749- 102406311    7  HPFS/NTFS
/dev/hde2      12749   24791   12043   96735397+   5  Extended
/dev/hde3          0       -       0          0    0  Empty
/dev/hde4          0       -       0          0    0  Empty
/dev/hde5      12749+  24556   11808-  94847728+  83  Linux
/dev/hde6      24557+  24791     235-   1887606   82  Linux swap / Solaris

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+  38912   38913- 312568641    7  HPFS/NTFS
      end: (c,h,s) expected (1023,254,63) found (1021,254,63)
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
[/FONT]

(I happen to have an additional, external hard drive, 320B, on a USB port, not involved in this ubuntu installation.)

In my most recent post on that forum, I manually typed in a "transcript" of a down & dirty sesison having booted from the SuperGrub CD.  I think it might be relevant here.  But first a preface:

My box is a Dell XPS-T500 500 mhz CPU, purchased in 1999.  ***_The BIOS is incapable or seeing past 137GB_***.  This is a key point, I think.

In 2003 or so, I bought a 200GB hard drive, replaced the original 28GB drive and installed XP instead of the original Win-98.  It was OK that it could not see the whole drive because I intended to install Linux on the latter 100GB.  Using Partition Magic, I created a 100GB partition for windows and left the rest alone until this week.

Now, that transcript.  I was trying to restore GRUB to the correct partition.

OK, I boot it and get the prompts to select:
[FONT="Courier"]
ENGLISH ->
ADVANCED ->
Gnu/Linux (Advanced) ->
Fix Boot of Gnu/Linux ->
Manual Restore of GRUB in Hard DIsk (MBR) ->

Now I get a list with a heading:
Natural  LINUX-IDE  LINUX-SCSI  GRUB   HURD
  1        HDA        SDA       (hd0)  hd0

Well, that's only one possible row. I select it and get this list:

N  IDE   SCSI  GRUB    HURD  TYPE       OS
1  hda1  sda1  (hd0,0) hd0s1 HPFS/NTFS  WINDOWS
5  hda5  sda5  (hd0,4) nd0s5 ex2fs      UBUNTU 8.04 \n \l

Naturally, since I want the GRUB on the Ubuntu partition, I choose the second row, where N == 5.

I get a repeat of a display I saw earlier:

Natural  LINUX-IDE  LINUX-SCSI  GRUB   HURD
  1        HDA        SDA       (hd0)  hd0

Of course, I select the only row shown. Now I get:
Error 18:  Selected cylinder exceeded maximum supported by Bios
[/FONT]

CURSES! Foiled again! ](*,)

There is an option to "fix boot of windows" but I am awaiting a complete read and advice from Adrian on its usage.  But I am now more convinced that I should not install Ubuntu on the same hard drive, rather on a 120GB partition at the end of the external drive; no BIOS restriction there, I think.

I will get back to Y'all on the results of my quest.  This is all still better than reinstalling Windows and all those apps I have installed as well.

Kevbert, thanks for the guidance so far.  But the sheer number similar posts on the supergubdisk forum suggests to me that some installation kinks in 8.04 still need to be worked out.

-- Rasputin II

---

### Post by meierfra. on 2008-05-30
Just a couple of comments:

> blocks of 1024 bytes,
 #blocks Id System
102406311 7 HPFS/NTFS
This tells us  that your windows partion is still 100GB. So  the ubuntu installer did not touch the Windows Partition.  I think there is a very high chance that you can rescue  Windows.


Error 18 together with you old bios, does indeed mean that you will not be able to boot Ubuntu, unless you either reinstall  ubuntu to a different location or at least create a separate boot partition. Although sometimes this problem can be solved by upgrading the Bios.


You might also see whether you can access  your Windows partition from the Ubuntu Live CD. Go to Computer->Places and double click the icon for the Windows partition.

---

### Post by rpaskudniak on 2008-05-30
Thanks for the encouraging word, meierfra.

Yes, I know my data is still there.  I have been using the file browser to back up my daughters's recent work to the secondary drive.  (They are thoroughly p****d at me for this escapade. :-(  )

Has anyone used the "Fix boot of windows" in SGD?  Please share your story here.

Also, I just saw a tidbit from Adrian15 in the SGD forum: In [Super Grub Disk 0.9716 release]("http://www.supergrubdisk.org/forum/index.php?topic=73.msg212#msg212")  he describes the following issue:

> It seems that there are some firewalls or antivirus or securities policies that when booting into Windows delete the sectors just after the MBR, that's where usually grub's stage1_5 is stored.

This latest release, 0.9716, has a fix for that problem. (I had downloaded SGD 0.9677.) He has added a new option:

> Choose Language & Help -> Linux -> Linux (Advanced) -> Fix Boot of Linux (GRUB)-> Manually restore grub to MBR (!NO stage1_5)

Since my intention is to remove Ubuntu from my machine completely (and make some diffent partitioning decisions before my next try) this is not immediately useful to me.  I still need advice (and reading) on "Fix boot of Windows".

But my data does seem safe (albeit imprisoned) in the meantime, as long as I don't need to reinstall Windows.

-- Rasputin II

---

### Post by rpaskudniak on 2008-06-01
Greetings.

I have just posted this on the supergrubdisk forum, if with slightly different wording:
----
[non-]progress report:
I cannot use the acer "Recovery disks" [that I borrowed from my son] because the instructions clearly tell me that it will wipe my disk and install windows fresh.  Not a desirable result.

OK, I am now copying the entire contents of my 104GB Windows partition to a new backup directory on the external drive.  Kinda slow on a USB-1 bus (I said my machine is a dinosaur! :-) ) but with the cp -pR command, it should get everything with time-stamps intact.... Well, not quite - some media files are getting errors e.g 
> cp: cannot stat `/media/disk/Documents and Settings/All Users/Documents/My Music/Keith Brion/Babes in Toyland The Red Mill/07 Eccentric Dance (Gavotte).wma': Input/output error
> cp: cannot stat `/media/disk/Documents and Settings/Guest/Application Data/Real/RealPlayer/DRM': Input/output error

But I think these are tolerable.

OK, lacking better information, I think I will boot my original XP installation CD and run chkdsk -pr from the recovery console.

HMMmm... I see now that I could edit the boot.ini file with vi.  Here are the contents:
> [font=Courier][SIZE="2"][boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
c:\wubildr.mbr="Ubuntu"
[/SIZE][/font]

Now, what can I change to get Ubuntu out of the picture and give Windows a monopoly on my machine (until my next try)?

Thanks much.

---

### Post by rpaskudniak on 2008-06-01
I have posted this in the supergrubdisk forum as well:

To follow up my my recent post about boot.ini:

My current, flawed boot.ini:
> [boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
c:\wubildr.mbr="Ubuntu"

Here is the boot.ini from my XP laptop:

[boot loader]
> timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

The only difference here is the last line of the flawed boot.ini: the line > c:\wubildr.mbr="Ubuntu"

Empowered as I am with Ubuntu (booted from the CD), I can easily [make a copy of the flawed version and] edit the flawed version to remove that ubuntu line.  I believe that will only get rid of the boot menu that includes ubuntu; the MBR is still damaged, a state I hope will change after I run > chkdsk -pr from the recovery console.

The backup "cp -pr" is still running since 11:00 PM last night.

Thoughts?

---

### Post by abn91c on 2008-06-01
you may want to try this rescue cd if all else fails [http://distrowatch.com/table.php?distribution=systemrescue](http://distrowatch.com/table.php?distribution=systemrescue)

---

### Post by rpaskudniak on 2008-06-01
Thanks abn,
I'm investigating that extensive site now.

---

### Post by rpaskudniak on 2008-06-01
Again, thanks, abn.  I'm still reading the docs.  However, linke much of this forum (as well as the supergrubdisk forum) the orientation seems more at rescuing Linux boots, rather than Windows, thoug I do see windows mentioned.  There a LOTTA doc in there!  I will continue reading the docs until my eyes cross 8-)

Not giving up...

---

### Post by rpaskudniak on 2008-06-01
SIGHHhhh.... ](*,)

This system rescue CD business is looking like another wild goose chase. I have wasted 3 cd's so far and Brasero always comes up with an an error at the very end of the data integrity test.  The third time, I tried version 1.0.2 rather 1.0.3.  I used brasero rather than the default burner because brasero allows me to slow the write speed to 2x.  It was Brasero that allowed me to successfully burn the SuperGrubDisk when the default burner failed me.

I may take it up with the author of SystemRescueDisk, joining yet another forum, but I feel I am getting nowhere with this approach.:cry:

Thanks for the efforts.  I will keep looking back in case someone has other ideas.

---

### Post by rpaskudniak on 2008-06-05
[FONT="Arial"]Thanks to all those who have sent helpful suggestions.

Despite my depressing most recent note (with the ](*,)  ), the SystemRescueCD did actually burn successfully.  (I guess a Brasero bug kept giving errors.)  I discovered this when I inadvertently booted it and accepted some defaults.  As far as I can see, I have Ubunto off my system, though it may still be there in the second partition.

All is not yet well - the Windows banner page still slides for 23 minutes (better than forever) before finally presenting the login screen.  I tried to run Partition Magic (from before Symantec bought it as a slum property :mad:) and it complained about the disk geometry, not a ghost of an attempt to fix the blessed thing! #-o

Since my problem is no longer an Ubuntu issue, I will consider this now a Windows problem.  I have some ideas on how to fix the partition and I will post them on  PC Help Forum ([www.pchelpforum.com](www.pchelpforum.com)).

Once this is fixed, I will retrun to this forum with my scheme for partitioning my main hard drive as well as my external drive for a (hopefully) more fortuitous installation.

Again, thanks for the leads.
[/FONT]

---

### Post by rpaskudniak on 2008-07-03
Ahh, after 3 weeks, I finally got my Windows straightened out. :popcorn:

I walked into J&R and bought Acronis Disk Director Suite 10.  Scandalous to actually pay for commercial software but nont of the free options were working.

I booted the ADD disk and used the app to display the partitions.  It showed 2 partitions: the 92GB NTFS partition and the 90GB EXT3 partition.  I used ADD to delete the EXT3 and it again displayed the partition table.  This time, in place of the EXT3 partition, was a 1.8GB Linux boot partition.

So I now see what was wrong: The "Guided" Ubunto install overlapped the boot and  EXT3 partitions.  Unfortunately, since this was booted from the Acronis CD, there are no screen images to post.  It would have been a clearer explanation of the problem.

Now that both extra partitions are gone,  my PC boots in is usual, sluggish way.  (It is, after all, a dinosaur.)

In a totally different thread, I will post my schemes and ask for feedback on their possibility of success.

Thanks very much for the help you have provided.  It got me past the initial big disaster (when it would never come up).

---

