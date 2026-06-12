---
title: "Clean install?"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by hungsolo on 2010-04-27
I just upgraded from 9.10 to 10.04, but would like to perform a clean install of 10.04 RC to see if it resolves some issues I currently have.  However, I keep running into issues when I try to bott from a CD.  First I received an "I/O error" message.  It would appear when I chose to run from CD or install from the CD (the menu after you select a language). Thinking that this may have been a bad burn or a corrupted download, I redownloaded 10.04 and tried again.  I then received a different error.  I was getting an "unrecoverable error" while booting.  I did not get any of the menus as I did previously.  My disc drive just kept spinning until the error popped up.  The message also said to remove the disc and restart without the disc.  

I'm not sure what I'm doing wrong, but I really want to re-install 10.04.  Any help would be greatly appreciated.

I do not have Windows installed by the way.

---

### Post by limey_rick on 2010-04-27
I had the same problem with the RC1 Live CD, so I downloaded the alternative version of RC1 and installed this instead. I did not experience the same issue and the install was fine. 

One caveat; GRUB installed the boot loader in the MBR of a disk that was not set as the first boot disk by the BIOS. So, when I rebooted, it booted my Windows system - I did not see GRUB. I then had to go back into the BIOS and change the boot order to reflect the disk GRUB installed the boot loader on and all was good. 

See this post: [http://ubuntuforums.org/showthread.php?t=1463179](http://ubuntuforums.org/showthread.php?t=1463179)

---

### Post by hungsolo on 2010-04-28
> **limey_rick said:**
> I had the same problem with the RC1 Live CD, so I downloaded the alternative version of RC1 and installed this instead. I did not experience the same issue and the install was fine. 

One caveat; GRUB installed the boot loader in the MBR of a disk that was not set as the first boot disk by the BIOS. So, when I rebooted, it booted my Windows system - I did not see GRUB. I then had to go back into the BIOS and change the boot order to reflect the disk GRUB installed the boot loader on and all was good. 

See this post: [http://ubuntuforums.org/showthread.php?t=1463179](http://ubuntuforums.org/showthread.php?t=1463179)

  Thanks!!!  It worked like a charm.  I really appreciate your help.  I was beginning to pull out my hair trying to get it to work.

---

