---
title: "[SOLVED] Troubles installing 8.10 beta"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pgranger on 2008-10-14
I am being driven gradually insane by attempts to install the Unbuntu 8.10 (Intrepid) beta, so I need to do a sanity check here and verify that others have been able to install it successfully, and if so, find out what I might be doing incorrectly.

I have downloaded the file ubuntu-8.10-beta-desktop-i386.iso. I have used a checksum utility to verify that it has the correct MD5 checksum (574c9b48dbb5cf471b05ff18a9adc082).

I have burned the ISO to CD. In fact, I have used *two* different PC's, *two* different CD burner utility programs, and *three* different CD burners, to burn the ISO to CD about a dozen times. I have done the CD burn at max speed, and at the slowest available speed (although in general I go with the slow speed).

I have attempted to use these CD's on two different PC's, since I want to install Ubuntu on both of them eventually. Both of these PC's are a little bit older, but not totally decrepit. In fact, one of them had Mint 5 (with its Ubuntu 8.04 substrate) running on it until today.

On one of the target PC's, the CD's I have burned do not work in any capacity. They always report read errors at the same sector and block. Normally I would think that this was indicating a problem with the CD reader when attempting to access that block; but it has no trouble reading and validating an Ubuntu 8.04 CD I burnt yesterday also, so there doesn't seem to be a problem with the reader.

On the other target PC (the one that had Mint running on it), I get widely varied results. At the Ubuntu boot screen, I am presented with options of:

[list]
[*]Check CD integrity
[*]Boot from CD without installing
[*]Install Ubuntu
[*]Test memory
[*]Boot from hard drive
[/list]

When I check CD integrity, sometimes I get success, sometimes I get failures *when testing the same CD*. Yep, that's right -- I can test the same CD 4 times, and get two successful checks, one report of an error (sometimes in one file, sometimes in several files), and one time the integrity check will hang completely.

I've been successful in booting from the CD without installing, several times. And sometimes this also hangs.

And attempts to install, no matter how many times the CD has passed the initial integrity check, have failed *every time*.

The obvious interpretation is that there is something wrong with my hardware -- either the CD burners I am using, or the readers on the target machines that I'm trying to use. But having *every* combination fail? It just doesn't seem plausible, especially since I've burned CD's of Mint 4.0 and Mint 5, and had it install successfully on the first try, on the same hardware. I've also had no trouble burning, validating, and booting from an Ubuntu 8.04 CD (although I didn't install from it).

I would welcome any suggestions that might allow me to actually install Ubuntu 8.10. I have lost two days on this already, and need to get it working soon. Thank you.

---

### Post by markbuntu on 2008-10-14
Well, it is still beta so there is hope. Personally, I have been unsuccessful in getting ANY version of Intrepid to boot on my machine. I am considering waiting intil maybe December or January before I try again.

---

### Post by handydan918 on 2008-10-14
Just for the "sanity check" part, try d/l-ing another distro. Also, try a non-live cd. For another live cd to try, check [Mepis]("http://www.mepis.org/mirrors")

For another non-live cd, I'd recommend [Debian (stable)]("http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/"). Same style of installer as the Ubu alternative installer.

---

### Post by pgranger on 2008-10-14
> **markbuntu said:**
> Well, it is still beta so there is hope. Personally, I have been unsuccessful in getting ANY version of Intrepid to boot on my machine. I am considering waiting intil maybe December or January before I try again.

Thank you, thank you, *thank you!*

You may have just succeeded in confirming my sanity... You seem to be vastly more experienced at this than I, and if you haven't been able to do it, then maybe it's Intrepid, and not me.

Normally I wouldn't even mess with a beta, but since it's less than three weeks from release, I figured what the heck, it's "as good as" released.

The other reason to go with 8.04 is that it's dubbed as an LTS version. Probably better to go with a known stable version with long term support than to try the newest version on the shelf.

---

### Post by pgranger on 2008-10-14
> **handydan918 said:**
> Just for the "sanity check" part, try d/l-ing another distro. Also, try a non-live cd. For another live cd to try, check [Mepis]("http://www.mepis.org/mirrors")

For another non-live cd, I'd recommend [Debian (stable)]("http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/"). Same style of installer as the Ubu alternative installer.

Could you explain what you mean by "live" vs. "non-live" CD? I'm not familiar with those terms.

I'm pretty new at this -- been playing around with Mint for a couple months, but decided it was probably a good idea to switch to straight-up Ubuntu. Not surprisingly, the Mint installs I've done were very similar to what I've seen with Ubuntu.

---

### Post by phidia on 2008-10-14
A live cd runs the OS from the optical drive, using system RAM of course, but it doesn't make any changes to your hard drive.

---

### Post by pgranger on 2008-10-15
I've put aside 8.10 for the time being, since 8.04 is working with no problem. I'm pleased to see that there seems to be an upgrade path built in, to go from 8.04 to 8.10 later if I want to. This was one of the main reasons I decided to move away from Mint -- there didn't seem to be any way to upgrade either Mint or the underlying Ubuntu from one major version to the next, so I'm very pleased to see that Ubuntu does include this capability.

The behavior I saw out of the 8.10 burns I did still doesn't make any sense, since it looked like a problem with either the hardware (CD burner or reader) or the media, rather than with the data contained on the CD. But since nothing but 8.10 showed anything like this, I remain baffled.

In any case, I'll consider this solved -- I didn't really find an answer, but it's been rendered irrelevant.

---

