---
title: "Wont boot from HD without using Install disk"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by siabost on 2009-11-26
Hi,

A friend was on Ubuntu 9.04 and all working fine.
He tried the "Upgrade" option to 9.10 and although it kinda worked he was getting errors and his computer would crash sometimes.
So, he did a clean "use all disk" re-install of 9.10 from a CD.

Now he finds he can't boot directly from the HD unless he goes via the installation disk's boot menu i.e. he has to leave CD in drive and scroll down to "Boot from HD" when menu appears.

How is this fixable as a re-installation doesn't do it?
He has also tried Mandriva since but had the same problem.

Would re-installing using the "Alternate CD" fix this as I recall it asks where to install the bootloader?

Many thanks for any help.

---

### Post by louieb on 2009-11-26
Just a guess that BIOS is looking for a partition with the boot flag on.  Using the live CD Open System>Administration>Gparted  - right click on Ubuntu's install partition - manage flags make sure the boot flag is on. 

if that does not help folllow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

---

### Post by siabost on 2009-11-27
Thanks louieb,

I can't view/check directly as my friend's PC is some distance away but I loaded Gparted on my own machine (which boots fine) and shows a nice view of my partition set-up plus the "boot flag".

I've e-mailed a pic of my set-up to my friend so he can check if he has a boot flag against his / partition.

I notice Gparted allows you to "manage Boot flags". I take it you can't change this on the same partition from which you have booted in a particular session? It would need to be from the Live CD, as you suggest?

Many thanks for your assistance.

BTW, Ubuntu 9.10 is excellent. I started on 8.04LTS and the improvements since then (and that was good) are incredible. Not tried Windows 7 but if the commercial apps were available for U9.10 it would really give MS a run for its (no) money!

:)

---

### Post by siabost on 2009-11-28
Hi,

Checked the boot flag and it's fine and in the right place.

The system does try to boot directly from the HD (without using CD) and this is the result:

Switch on. Small punctuation dash top left of screen for a second then white ubuntu logo appears for 10 seconds or so. Logo disappears & small dash reappears top left for a couple of seconds. Then screen goes a darker black and that's it - it never gets to the login window.

Using the CD menu and scrolling down to "Boot from Hard Disk" works every time.

Why should one work & not the other?

Many thanks.

---

### Post by phillw on 2009-11-28
> **siabost said:**
> Hi,

Checked the boot flag and it's fine and in the right place.

The system does try to boot directly from the HD (without using CD) and this is the result:

Switch on. Small punctuation dash top left of screen for a second then white ubuntu logo appears for 10 seconds or so. Logo disappears & small dash reappears top left for a couple of seconds. Then screen goes a darker black and that's it - it never gets to the login window.

Using the CD menu and scrolling down to "Boot from Hard Disk" works every time.

Why should one work & not the other?

Many thanks.


Hi,

have you tried ```
*sudo update*-*grub*
```

Just a thought .....

Regards,

Phill.

---

### Post by siabost on 2009-11-28
Thanks phillw,

Tried that and it booted without CD one out of three times - maybe a little improvement but it would boot very occasionally before.

All very odd.

:confused:

---

### Post by louieb on 2009-11-28
Very odd - really need the information provided by the  [Boot Info Script:]("http://ubuntuforums.org/showthread.php?t=1291280")  Would like to know how many hard drives and what if any boot loader is loaded by the MBR code,  Double check the boot flag.

---

