---
title: "Remove one distro without harming the other"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by rob300 on 2011-05-10
I have the following on my hard drive

Ubuntu 11.04
Mint 10.0
Windows 7

I would like to remove Mint and recover that space for Ubuntu, but since I installed Mint last, I think it is "in charge" of the grub bootloader, so I figured if I just expanded the ubuntu partition then I would lose the bootloader and not be able to log into anything.

Is this the case?  what is the best way to remove mint while still preserving the grub menu.

Thanks

---

### Post by coffeecat on 2011-05-10
You would need to reinstall grub to the mbr from Ubuntu so that Ubuntu's grub takes over the boot process. Then you would be safe to remove the Mint partition. If you installed Mint after Ubuntu, Ubuntu's grub.cfg will not have an entry for Mint, but that won't matter. What we need to do is to ensure that Ubuntu's grub.cfg has an entry for Windows.

Let's see what is on your system. Boot into Mint (you sometimes get some odd output with Natty and the boot script I'm going to recommend) and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the script as instructed there and post the contents of the RESULTS.txt file. Please remember to enclose the output between [noparse]```
 and 
```[/noparse] tags for clarity. You can use the # icon on the message toolbar for this.

I will need to log off within the next hour, so I may not be able to follow up on this until tomorrow, but I'm sure someone will be able to help you. Basically, your next few steps would be:

- Boot into Ubuntu and run grub-install. Check that the Ubuntu grub.cfg has an entry for Windows.

- Delete the Mint partition.

- Backup your personal data in case of a partitioning resize failure.

- Boot into a live CD and enlarge your Ubuntu partition into the freed space (if this is possible). Please note: at this stage someone often chips in and tells you that resizing a partition changes the UUID. **This is simply not so.** It is an urban myth. 

That's just an outline. We need to see the boot script output to see if there are any other factors to take into consideration.

---

### Post by rob300 on 2011-05-11
I do not have an internet connection that allows me to get to that script, but maybe this will give you enough information.

I looked at the grub.cfg (from within ubuntu), there are entries for the Ubuntu of course, for Windows and for Mint.

This tells me that even though I installed Mint later, it is still using the original grub (just with the Mint decals on it).

Looked at gparted.  I was trying to determine what the mount point is.  The sda5 (which has ubuntu on it) has a "/"  Does this indicate the mount point?  The mint partition (sda7) has a string of numbers instead of the "/", I am guessing this is the UID?

opened up etc/fstab, it has about 8 comment lines, then there are two lines but they are not designated with sda.... they have the UID, and I do not know which on is the mount point.  

What I want to avoid is deleting the mint partion, expanding the ubuntu partition and then discover that the mount point was in the mint partition that I deleted.

Then again, I look at grub and think that whatever choice I pick at startup, the mount point is determined by the selection that I choose.

So, I guess the question is how do I know if it is going to start up with the ubuntu grub.

Thanks

---

### Post by Quackers on 2011-05-11
Assuming that you haven't changed the menu order manually, which OS is first in the grub menu that you see at boot?

---

### Post by coffeecat on 2011-05-11
> **rob300 said:**
> I looked at the grub.cfg (from within ubuntu), there are entries for the Ubuntu of course, for Windows and for Mint.

This tells me that even though I installed Mint later, it is still using the original grub (just with the Mint decals on it).

No, not necessarily. If you have had a kernel upgrade in Ubuntu since installing Mint, the package manager will have run update-grub, detected Mint and regenerated your grub.cfg file with a Mint entry.

> **rob300 said:**
>  Looked at gparted.  I was trying to determine what the mount point is.   The sda5 (which has ubuntu on it) has a "/"  Does this indicate the  mount point?  The mint partition (sda7) has a string of numbers instead  of the "/", I am guessing this is the UID?

Well - you've told us what your Ubuntu / (root) partition is, so I can give you the commands to re-install Ubuntu's grub to be sure you do have Ubuntu's grub installed. Just one point first...

> **rob300 said:**
>  I do not have an internet connection that allows me to get to that script, but maybe this will give you enough information.

Er... you do. Since you are posting to the forum, you must have access to an internet connection. It doesn't matter what OS you are using. Even if Windows, you could have download the bootscript file and then transferred it via a USB drive to your Mint system.

Whatever...

To reinstall Ubuntu's grub if you are sure that Ubuntu's root partition is sda5: Boot into Ubuntu on your hard drive. No need for a live CD. Open a terminal, and:

```
sudo grub-install /dev/sda
```This will install Ubuntu's grub to the mbr. Even if, as you believe, Ubuntu's grub is in the mbr, it won't do any harm. now, for good measure:

```
sudo update-grub
```Make sure you can boot into both Ubuntu and Windows and then you will be safe to remove the Mint partition. By the way, there was another way to tell whether you were using the Ubuntu or Mint grub menu. In 11.04, the background colour to Ubuntu's is Aubergine Purple. Last time I looked at Mint - some time ago - it was green, although that may have changed now.

Leave any resizing of the Ubuntu partition until after you have deleted Mint and can still boot into Ubuntu and Windows. You would have to do any resizing from a live CD.

---

### Post by rob300 on 2011-05-11
Ok, seems like such an easy solution.

I have internet, but the link to that tool is caught by our firewall as "shareware", so I cannot get onto the sight at work.  I work away from home during the week, so my only internet is here at work.

In any case, I will run those commands and I am sure everything will work.

Thanks for your help

---

