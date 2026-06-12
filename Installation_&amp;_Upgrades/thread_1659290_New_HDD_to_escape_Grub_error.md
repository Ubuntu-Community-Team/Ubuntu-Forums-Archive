---
title: "New HDD to escape Grub error?"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by ETW Grumpy on 2011-01-03
I keep getting the dreaded Grub error 21 due to a botched Ubuntu installation. I have tried everything suggested here and cannot get it to work. If I replace the HDD with a new one, will Grub still come up or will it be gone with the old drive? :confused:

---

### Post by wilee-nilee on 2011-01-03
Okay your missing a bit of background here. 

Explain the botched install a little more, what OS, any other OS's?

Answering your question about grub, probably, but I doubt if the HD is the problem, unless it is just fried.

You have a dell correct are you dual booted.

---

### Post by kansasnoob on 2011-01-03
> **ETW Grumpy said:**
> I keep getting the dreaded Grub error 21 due to a botched Ubuntu installation. I have tried everything suggested here and cannot get it to work. If I replace the HDD with a new one, will Grub still come up or will it be gone with the old drive? :confused:

Looking back at your previous posts there's a
huge gap:

[http://ubuntuforums.org/showthread.php?t=1214272&page=2](http://ubuntuforums.org/showthread.php?t=1214272&page=2)

[http://ubuntuforums.org/showthread.php?t=1415967&page=2](http://ubuntuforums.org/showthread.php?t=1415967&page=2)

Like a 10 month to 18 month gap, so we really need you to bring us up to date. It looks like you were using Ubuntu 8.10, what version are you now using?

Also you previously stated in one place that you couldn't get past BIOS but if that were true you'd never see a grub error.

For that matter you could totally wipe your drive using Gparted by selecting the device and clicking on Device > Create partition table, so I can't imagine needing a new hard drive.

We really need to know much more. Can you boot a Live CD now?

---

### Post by ETW Grumpy on 2011-01-03
I was installing Ubuntu 8.10 alongside Windows XP on a Dell desktop. I thought it hung up in the middle of the install and I rebooted it. After that all I get is the Dell splash screen then the Grub error 21. I can't access the hard drive at all and the Windows CD, the Ubuntu 8.10 CD and the Fedora CD that I tried to use wouldn't boot. As for the time that has passed, I started school and haven't had time to mess with it. I'd like to get it fixed and give it to my nephew.

---

### Post by kansasnoob on 2011-01-03
If you can't boot a Live CD changing the hard drive will do no good. What exactly happens when you try to boot a live CD?

---

### Post by ETW Grumpy on 2011-01-03
> If you can't boot a Live CD changing the hard drive will do no good. What exactly happens when you try to boot a live CD? 

I get the Dell splash screen then the Grub error 21 message and that's it.

---

### Post by kansasnoob on 2011-01-04
Well Ubuntu 8.10 is no longer supported so it would be pointless to try and fix it's grub.

We need to concentrate on getting a Live CD to boot, then I'd suggest downloading and burning either 10.04 or 10.10. Just looking back here:

[http://ubuntuforums.org/showpost.php?p=10312656&postcount=14](http://ubuntuforums.org/showpost.php?p=10312656&postcount=14)

> From the splash screen, it gives me the option to hit F2 to go to setup or F12 to go to Boot Device menu. When I hit F12, I get a list:

1. Normal
2. Hard Disk Drive C:
3. IDE CD-ROM Device
4. System Set Up
5. IDE Drive Diagnostics
6. Boot to Utility Partition

4 takes me to the BIOS, 5 does a diagnostic that tells me the cd roms don't support the diagnostic and everything else gives me the Grub error.

What happens if you repeat that procedure and enter 3 with a Live CD inserted?

Getting some live media (live CD or Live USB) to boot is job #1!

---

### Post by ETW Grumpy on 2011-01-04
Downloading Ubuntu 10.10 now. 

> What happens if you repeat that procedure and enter 3 with a Live CD inserted?


I tried this with a Fedora CD inserted and got a "Strike F1 to retry boot or F2 to go to setup" message but no boot. I'll try this with 10.10 when it downloads.

---

### Post by ETW Grumpy on 2011-01-04
I downloaded 10.10 and tried it-got the same Error 21. I found a setting in the BIOS to use USB so I burned the Ubuntu 10.101 to a thumb drive and tried that. No luck. I'm thinking it may be new hard drive time. Any thoughts??

:confused::confused::confused::confused:

---

### Post by kansasnoob on 2011-01-05
Well, if the BIOS is set correctly it shouldn't even be trying to boot from the hard drive if you're using either a Live USB or Live CD.

Can you tell us the exact model of Dell?

Maybe I can find some specific BIOS instructions for you.

---

### Post by presence1960 on 2011-01-05
[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html)

Check that link for an explanation of GRUB error 21. It would seem to me that the problem is your BIOS, because that is what determines what hardware your machine tries to boot from. For whatever reason the device that BIOS is looking for does not exist.

---

### Post by kansasnoob on 2011-01-05
> **presence1960 said:**
> [http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html)

Check that link for an explanation of GRUB error 21. It would seem to me that the problem is your BIOS, because that is what determines what hardware your machine tries to boot from. For whatever reason the device that BIOS is looking for does not exist.

Prior to the OP saying that a USB would also not boot I'd even wondered if the new CD-ROM was IDE and possibly the "settings" jumper was set wrong.

But this certainly sounds to me like a BIOS problem.

---

### Post by ETW Grumpy on 2011-01-05
> Well, if the BIOS is set correctly it shouldn't even be trying to boot from the hard drive if you're using either a Live USB or Live CD.
 
The BIOS is set to boot from the CD Rom first and then the Hard Drive. 


> Can you tell us the exact model of Dell?

 It's a Dimension 2400.

> Prior to the OP saying that a USB would also not boot I'd even wondered if the new CD-ROM was IDE and possibly the "settings" jumper was set wrong.


 This could be true, it's been so long since I installed the CD ROM unit I don't remember what the jumper settings were or were supposed to be. Any instructions here?

Is there any way I could flash the BIOS with it not booting? Could that even be the problem?

---

### Post by ETW Grumpy on 2011-01-08
No new ideas?

---

