---
title: "Ubuntu 13.10 Install Hangs"
date: 2013-12-12
forum: Installation &amp; Upgrades
---

### Post by Deanimator on 2013-12-12
I'm attempting to install 13.10 on a desktop machine.  I was previously able to install 12.10, albeit with difficulty due to the Nvidia card in the system.  The upgrade to 13.10 kept failing, so I tried installing 13.10 from CD.

I get to the location choice screen, when I get a very small dialog box with nothing in it but a white "-" on a black disk (like a European  "Do Not Enter" traffic sign) "??? ???".  I can click the "OK" button, but nothing happens.  Clicking the "X" to close the window doesn't work either.  It won't let me progress past this point.

I downloaded and burned the ISO twice and it seems to be valid.

I get the same result whether I do the install from "try" or "install".

The system is a home built server with two mirrored SATA drives.  It previously ran Fedora just fine.
ECS Nforce 4 A939 MB
1 gig RAM
Nvidia video card (works with manual configuration under 12.10)

I haven't found any references to this behavior.

Does anyone have any suggestions?

Thanks.

---

### Post by QIII on 2013-12-13
Hello!

Could you use the camera on a phone to capture an image of the symbol you see for the benefit of those who don't live in Europe and are not familiar with European traffic signs?

Cheers!

---

### Post by Bucky Ball on 2013-12-13
At the 'Try' or 'Install' screen hit F6, choose 'nomodset'. Proceed with boot. Any different?

---

### Post by Deanimator on 2013-12-13
While trying to get my ancient Linksys AT/PS2/serial KVM switch to work,  I set the system to halt on keyboard errors.&nbsp; When it powers  on it now says that the keyboard is "locked", so I'm going to have to  pull the CMOS battery, since just swapping the jumper wouldn't clear the  BIOS.&nbsp; After I get that done, I'll try the F6  solution.&nbsp; Thanks.

---

### Post by Deanimator on 2013-12-31
> **Bucky Ball said:**
> At the 'Try' or 'Install' screen hit F6, choose 'nomodset'. Proceed with boot. Any different?
I've got a working keyboard now.

I tried the F6, but nothing happened.  Is there a specific point when I should hit it?

Thanks.

---

### Post by ubfan1 on 2013-12-31
Try F6 when at the purple grub screen, offering the Try or install.  Then select the option.

---

### Post by Deanimator on 2013-12-31
> **ubfan1 said:**
> Try F6 when at the purple grub screen, offering the Try or install.  Then select the option.
I was able to select nomodeset, but it's been sitting at the first screen where you tell it to install updates while installing for at least 1/2 an hour.

---

### Post by Deanimator on 2014-01-01
I've tried running nomodeset a couple of times and it eventually hangs at the screen mentioned above, mouse and keyboard locked up.

---

### Post by Deanimator on 2014-01-12
Since I got the keyboard working, I've tried at F6:
nomodeset
noacpi
nodmraid (had to deselect it, since it then couldn't see the RAID mirror)

With nomodeset and noacpi set, I can now click through the "do not enter" box, but now when I get to the "where are you located" screen, the "continue" button is never enabled, and if I wait long enough (3-5 min.s), it just jumps back the "Type of Installation" screen.

Any suggestions?

---

### Post by ubfan1 on 2014-01-12
Did you ever hashcheck the download with md5sum?  That's the only way to be sure the download is good.  Burn the CD as slowly as possible, then boot and select the media-check.

---

### Post by Deanimator on 2014-01-13
> **ubfan1 said:**
> Did you ever hashcheck the download with md5sum?  That's the only way to be sure the download is good.  Burn the CD as slowly as possible, then boot and select the media-check.
No, I haven't.

I've downloaded it and burned it to CD three times.  All three times I've gotten it from the main Ubuntu download page.

I'll run the hash check when I get home tonight.

Assuming that it is bad, where's a known good download source other than the main download page?

I actually found that same ??? ??? "Do Not Enter" sign error message reported by others in other forums last night, but so far I haven't found any solutions.

---

### Post by ubfan1 on 2014-01-13
The errors typically come from the transmission, not the source. Nevertheless, get the hashchecks from the Ubuntu home page, and then download the iso from the nearest/fastest mirror, then check the download.  Torrents may offer some additional error corrections, but I have no experience with them.

---

### Post by Deanimator on 2014-01-13
> **ubfan1 said:**
> The errors typically come from the transmission, not the source. Nevertheless, get the hashchecks from the Ubuntu home page, and then download the iso from the nearest/fastest mirror, then check the download.  Torrents may offer some additional error corrections, but I have no experience with them.
Where would I find legit mirror sites?  Fedora's download page used to list a bunch, but when I go to the Ubuntu download page, I don't recall seeing any and I actually looked, since I figured a change in source would be a good idea.

---

### Post by Bucky Ball on 2014-01-13
Official Ubuntu download page fine. You haven't run a hashcheck to see if there are any defects yet. Out of three downloads, you must have a good one, perhaps all three. 

Torrents are the most reliable way to go (should be hash checked on the way). The torrents are available from the official site also. See 'Bit Torrents' a little down this page:

[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

---

### Post by Deanimator on 2014-01-13
I just checked, and the hash shows that it's valid.

---

### Post by ubfan1 on 2014-01-14
Maybe RAID is causing your problems, but I have no experience with it myself.

---

### Post by Deanimator on 2014-01-14
> **ubfan1 said:**
> Maybe RAID is causing your problems, but I have no experience with it myself.
Maybe, but why does it work in 12.10 but not 13.10?

---

### Post by Deanimator on 2014-01-14
> **ubfan1 said:**
> Maybe RAID is causing your problems, but I have no experience with it myself.
You may be right, not specifically regarding RAID, but two hard drives:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1241589](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1241589)

I can make 12.10 work with a little effort regarding the video card.

Any REAL reason why I NEED to upgrade to 13.10?

---

### Post by Bucky Ball on 2014-01-14
12.10 will not upgrade directly to 14.04 LTS in April. If you want to go further you will need a clean install or to follow the upgrade path of 12.10>13.04>13.10>14.04 LTS. Long, tedious and possibly problematic.

12.04 LTS and 13.10 both upgrade directly to 14.04 LTS.

But no, there is no NEED to install 13.10 (I'd probably go for 12.04 LTS if I was going to install anything personally and upgrade to 14.04 LTS when it comes out).

---

### Post by Deanimator on 2014-01-14
> **Bucky Ball said:**
> 12.10 will not upgrade directly to 14.04 LTS in April. If you want to go further you will need a clean install or to follow the upgrade path of 12.10>13.04>13.10>14.04 LTS. Long, tedious and possibly problematic.

12.04 LTS and 13.10 both upgrade directly to 14.04 LTS.

But no, there is no NEED to install 13.10 (I'd probably go for 12.04 LTS if I was going to install anything personally and upgrade to 14.04 LTS when it comes out).
Alright, that sounds like a reasonable solution.

I'll give that a try this week, though not necessarily tonight.

If 12.10 installs there's no GOOD reason why 12.04 LTS shouldn't.

Thanks for your help.

---

### Post by Deanimator on 2014-01-14
This looks like the problem, down to the weird error message:

[http://ubuntuforums.org/showthread.php?t=2182119](http://ubuntuforums.org/showthread.php?t=2182119)

I'll manually partition the array and see what happens.

Here's the infamous error message: 

[IMG]http://s8.postimg.org/nyuvpky5w/IMG_20131020_102626.jpg[/IMG]

It's hard to find a solution using a graphic of a street sign and six questions marks as search terms...

---

