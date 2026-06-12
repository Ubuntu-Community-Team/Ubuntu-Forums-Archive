---
title: "Vista64+Ubuntu64 - need some advice"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by MikeMLP on 2008-04-11
Hi,

My friend just got a new machine with Vista64 installed on it.  Her previous machine was a mac, and she wants to get her files off of that machine, since it is now bricked.  I hear that linux has read support at least (which is all I need) for HFS+.  As an aside, if someone could confirm that / direct me to any particular steps that need to be taken to get that working under Ubuntu, that would be great.

Now to the main issue:  As I said, her machine has Vista64 on it.  I want to dual boot Vista and Ubuntu.  I have heard that there are issues with both ntfs-resize's ability to resize in a timely manner with Vista's version of NTFS, and also that Grub will bork Vista if installed to the MBR.  This necessitates the use of something called EasyBCD: [http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1") .  

See also [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")
and [http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

So finally my questions:

1. What is the best way to install a dual boot Ubuntu64 and Vista64?  See what I've found on the web above.

2.  What is the best way to set up partitions on said configuration.  I would like to use 1 NTFS partition and 1 EXT3 partition.  I know that starting with Gutsy, NTFS read/write support is there and great with XP32, but does that also hold with Vista64?  **Please advise!**

3.  What version of Ubuntu should I use?  I have no qualms about installing the beta of 8.04LTS on this person's machine.  I hear it is stable, and she has no valuable data on the new machine anyway.  I would only do this, however, if it offered some advantage to supporting smooth installation on a machine of said configuration (Vista64+Ubuntu64 dualboot).  That is, if Grub is fixed, NTFS support for Vista64 is better with Hardy64 than Gutsy64, etc. etc.  Again,** please advise.**

I have experience installing both live and alternate versions of Ubuntu on my XP laptop since Ubuntu 6.04, so I'm pretty much well-versed in the installing.  I just need to know the quirks of this particular configuration, which I am not familiar with.  I don't want any surprises when I do this.  Thanks for the help!

Edit:** a further complication.  Having no experience with Vista or Vista64, can someone confirm if EasyBCD works on Vista64?  I notice that their download is an .exe file.  Windows, (obviously), but I don't see anything there about what versions are supported.  Does Vista64 need a special .exe?**

---

### Post by MikeMLP on 2008-04-11
Got another question for ya (which is why I'm posting this separately):
My friend's new Lappy has 4GB of ram (Woo!).  Shall I give Linux a swap space with all this?  (I assume that would be a yes) And if so, how much would you say would be optimal for that quantity of ram?

---

### Post by llcawthorne on 2008-04-13
> **MikeMLP said:**
> Hi,
1. What is the best way to install a dual boot Ubuntu64 and Vista64?  See what I've found on the web above.

I just ran the install and it worked.  Grub didn't mess anything up for me.  Have had Vista and Linux coexisting in multiple settings without major problems for a while now.  

> **MikeMLP said:**
> 2.  What is the best way to set up partitions on said configuration.  I would like to use 1 NTFS partition and 1 EXT3 partition.  I know that starting with Gutsy, NTFS read/write support is there and great with XP32, but does that also hold with Vista64?  **Please advise!**

Works like a charm.  No special setup required.  I have my Vista-64 on a BIOS fake raid partition formatted NTFS and am can read and write to it great.  Same as my NTFS partition sporting an old XP install.

> **MikeMLP said:**
> 3.  What version of Ubuntu should I use?  I have no qualms about installing the beta of 8.04LTS on this person's machine.  I hear it is stable, and she has no valuable data on the new machine anyway.  I would only do this, however, if it offered some advantage to supporting smooth installation on a machine of said configuration (Vista64+Ubuntu64 dualboot).  That is, if Grub is fixed, NTFS support for Vista64 is better with Hardy64 than Gutsy64, etc. etc.  Again,** please advise.**

The install of 8.04 went smoother for me than 7.10.  Good multiple monitor support.  Less 64-bit problems.  That being said, 8.04 release is out in like ten or eleven days if you aren't in a hurry.  If you are, then I'll at least say that the 8.04 beta is working well for me and had no problems installing alongside an existing Vista/XP dualboot setup with no special action required.

> **MikeMLP said:**
> Edit:** a further complication.  Having no experience with Vista or Vista64, can someone confirm if EasyBCD works on Vista64?  I notice that their download is an .exe file.  Windows, (obviously), but I don't see anything there about what versions are supported.  Does Vista64 need a special .exe?**

I'm not sure about that.  Never needed to use EasyBCD for anything.  It's a 32-bit apps, but most 32-bit apps work great in Vista as long as they don't need to install a driver or anything.  Like I said earlier though, grub is working great for me.

---

### Post by llcawthorne on 2008-04-13
> **MikeMLP said:**
> Hi,

My friend just got a new machine with Vista64 installed on it.  Her previous machine was a mac, and she wants to get her files off of that machine, since it is now bricked.  I hear that linux has read support at least (which is all I need) for HFS+.  As an aside, if someone could confirm that / direct me to any particular steps that need to be taken to get that working under Ubuntu, that would be great.

Mounting HFS in Ubuntu thread here:  [http://ubuntuforums.org/showthread.php?t=88590](http://ubuntuforums.org/showthread.php?t=88590)

---

### Post by MikeMLP on 2008-04-25
Thank you both very much.  I installed 7.10 for my friend with no hassle.  Grub worked as expected, and NTFS read/write support was fine.  

Her USB hard drive (I think it was HFS(+) formated) drive was auto-detected just fine, although writing to the drive was not possible unless she ran nautilus as an administrator. I'm not sure why this was the case.  Can anyone explain?  

She is new, so it is hard for her to remember that she has to go to the terminal and type "gksudo nautilus" in order to write to her drive.  I'm thinking about either trying to change the attributes of the drive to allow write support to users, or creating a little script for her to double-click as a desktop icon.  What do you think?

When I see her again, I'll get more info, such as the filesystem actually in use by the drive, and I'll also poke around with permissions.

Thanks again!

---

