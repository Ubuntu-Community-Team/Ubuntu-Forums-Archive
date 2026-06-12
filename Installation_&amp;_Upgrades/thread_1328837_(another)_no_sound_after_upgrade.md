---
title: "(another) no sound after upgrade"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by CovenStine on 2009-11-16
So, I just updated from 9.04 x64 to 9.10 x64... and my sound doesn't exist anymore.  I'm running an ASUS M3A32-MVP, using the onboard Analog Devices ADI AD1988 card.  It doesn't even show up in my 'Hardware' tab of the Sound Preferences dialog.  Everybody else seems to be having issues where they can see/ adjust the card, but no sound comes out.  My card apparently isn't even installed according to Ubuntu.
Thoughts? Suggestions?
TIA

(oh, and in an attempt to work this out, GRUB's list has been fixed to include the correct build, and since I don't have an intel sound card, I can't find any other solutions)

---

### Post by SurferGTO on 2009-11-16
how did you fix the grub list to boot of the correct kernel?? i cant find out how to do that anywhere...

i opted to use the current installed version of menu.lst during the install rather than the one provided by the package maintainers, and so grub boots off the older kernel, and the newest one isnt even listed, tho its showing installed on my machine...

---

### Post by CovenStine on 2009-11-16
Maybe I misunderstood the thread I read.  Anyhow, when I updated to 9.10, grub was still looking for the 9.04 version.
That caused a problem with an intel sound card, and since I could see that I had the same problem, I played with grub until it (at least to my highly noobesque eye) seems correct and behaves.
Essentially, I added a third entry because my menu.lst- like yours- had no 9.10 entry.
Still; no sound.

---

### Post by SurferGTO on 2009-11-16
during the upgrade, youre given an option to use the current version of menu.lst installed on the local machine, or to update to the newest one provide, i opted to keep the one installed on my computer because i know i edited it a bit for functionality purposes, and i would have lost those edits if i updated. if you chose that like i did, that means grub is told to boot using the older build version (from what i understand). which is what im having a problem with now. type in a terminal uname -a and uname -r, what is the output

---

### Post by SurferGTO on 2009-11-17
my muted problem like yours was fixed in another thread by user Magnesiums post. there are two different posts with two different file attachments, one for generic-14 and generic-15 of the latest kernels. following magnesiums directions in the other thread for whichever build kernel you have:

[http://ubuntuforums.org/showthread.php?p=8201048#post8201048]("http://ubuntuforums.org/showthread.php?p=8201048#post8201048")

not sure if it will help you but it fixed my sound, as well as graphic card problem.

---

### Post by CovenStine on 2009-11-17
> **SurferGTO said:**
> during the upgrade...i opted to keep the one installed on my computer... type in a terminal uname -a and uname -r, what is the output

Yeah, I did too because I didn't want to lose my windows loader entry... whups.  I'll post the results this evening when I get the chance.

> **SurferGTO said:**
> my muted problem like yours was fixed in another thread by user Magnesiums post. 

My search didn't yield that as a result I noticed; that's what I get for not being more general in my search terms.
Will post back with results.

---

### Post by CovenStine on 2009-11-17
Yeah, that thread didn't suggest anything I hadn't done code-wise, but the rebooting in Recovery once, I never would have thought of that... and that did the trick.

---

### Post by Amaroq on 2009-12-08
I had the same problem using the same motherboard.

It turned out I had two issues to contend with. One, GRUB was booting the wrong kernel, and two, I had to upgrade ALSA.

Here's how I fixed the issue with grub.

First, go to your boot folder and see what kernels you have to choose from.

```
cd /boot
ls | grep -e initrd -e vmlinuz
```

As far as I know, those two sets of files are the only ones you're going to need to worry about.

Open your grub's menu.lst file and find the entry for your ubuntu installation. You probably have two settings, kernel and initrd.

The newest kernel I have is 2.6.31-16-generic, so I changed the numbers in those two settings to say the following.

```
kernel /boot/vmlinuz-2.6.31-16-generic root=/dev/sda5
initrd /boot/initrd.img-2.6.31-16-generic
```

Alter it however you need to. But make sure the kernel and initrd you choose are listed by the ls | grep command we did earlier. Also, the partition you are using is probably different than mine, so make sure you set that accordingly as well.

Once that's fixed, reboot.

As for the actual sound issue, following these instructions fixed my problems. But it wouldn't work until I was using a new enough kernel.
[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

I do have a question though. Since the OP is using the same motherboard as I am, I'd like to know if you've figured out how to make ubuntu distinguish between the speaker and the headphones. The best I've gotten is a hacky solution where muting my audio mutes the speakers, but doesn't mute the headphones. There is no headphone autodetection whatsoever.

Technically, my mobo is actually M3A32-MVP Deluxe, and the audio is AD1988B, but it shouldn't make a difference I think.

---

