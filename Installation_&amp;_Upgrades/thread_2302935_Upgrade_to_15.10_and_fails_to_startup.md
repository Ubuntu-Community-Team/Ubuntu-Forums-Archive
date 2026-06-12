---
title: "Upgrade to 15.10 and fails to startup"
date: 2015-11-14
forum: Installation &amp; Upgrades
---

### Post by russkyca on 2015-11-14
I clicked to upgrade to 15.10 and now I cannot boot it.   I also have Xubuntu on another partition and it fails while at the graphics screen.

When I try to boot the upgrade, I have the text output but when it gets to the Ubuntu startup graphics screen, it just flashes like crazy.   I can boot my Windows 7 install on the NTFS partition and that's what I am using now.

I am sorry to say I am not sure where to start on diagnosing/troubleshooting and how to fix it.   Can anyone identify or recognize what's going on and give me advice of what to do?

I so far suspect something went wrong when it was upgrading XServer/X/graphics as I have a Nvidia card, a GTX 750 to be exact.   When I upgraded 14.10 to 15.04, the upgrade went smooth.   I suppose that is why I foolishly assumed all would go well and I didn't back anything up.   

I cannot recall what to do when I run into this problem or perhaps, it's somewhat different than what others see?   I can only think of using a usb .iso that I have (if I can find one that has Ubuntu or something else on it) so that I can access my files and perhaps find the problem in the configuration (files) somewhere?   I can boot in 'safe' (i.e. recovery) mode but I'm not sure what to do or look for there.  

Can anyone help?

Is there any other posts similar to this one that might help or have answers?   I will search the forums but it's difficult to find something exactly since all configurations are different to some extent.   I am just wondering if the failure to start the OS is due to Xorg and/or graphics drivers being borked.   Perhaps, I was supposed to remove previous graphics drivers?   I don't know what driver version I was at but the kernel was 3.16.   It now gives the option of booting 4.2 or 3.16 and with recovery modes for each.   

Thanks in advance for any help or attempts at help.  I appreciate your time in posting replies.

---

### Post by grahammechanical on 2015-11-14
Before running the upgrade from 15.04 to 15.10 did you revert to using the open source video driver?

There is something that you can try. At the Grub boot menu select Advanced Options for Ubuntu and then select recovery mode. At the recovery menu select resume. If that gets you to a working desktop go to System Settings>Software & Updates>Additional drivers tab and experiment with different video drivers. We have to be connected to the internet and allow the utility to search for the relevant drivers.

Regards.

---

### Post by russkyca on 2015-11-14
> **grahammechanical said:**
> Before running the upgrade from 15.04 to 15.10 did you revert to using the open source video driver?

There is something that you can try. At the Grub boot menu select Advanced Options for Ubuntu and then select recovery mode. At the recovery menu select resume. If that gets you to a working desktop go to System Settings>Software & Updates>Additional drivers tab and experiment with different video drivers. We have to be connected to the internet and allow the utility to search for the relevant drivers.

Regards.No, I didn't revert or change video drivers at all.   I just selected to upgrade and clicked 'okay' to the messages.   I can go to the recovery menu but it doesn't boot up a working desktop.   So, I can't try any of those options. :-(

---

