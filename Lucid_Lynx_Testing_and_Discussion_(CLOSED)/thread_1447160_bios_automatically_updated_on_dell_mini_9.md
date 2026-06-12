---
title: "bios automatically updated on dell mini 9?"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by das88 on 2010-04-05
Hi all,

I just tried lucid with a live usb and somewhere between a few reboots my bios was flashed automatically.

I have a dell mini 9 and I used a persistent live usb with the 10.04 desktop image (I think I downloaded it yesterday or the day before if that makes any difference). Previously I've had to use a wired network connection to get a wireless driver for ubuntu via

sudo apt-get --reinstall install bcmwl-kernel-source

in order to get a working wireless connection. 10.04 realized it needed the driver and prompted me to download it but I don't have a wired connection where I am right now. I grabbed the .deb from my current os on this system (crunchbang 9.04.01) and tried to install that on the live usb. 10.04 needed the dependencies patch, fakeroot and dkms to install the driver so I rebooted and got those from #! using

sudo apt-get -d install {patch, dkms, fakeroot}

when I rebooted to get into the live usb again I discovered that usb was no longer the first boot device on my bios. Further investigation revealed that somehow my bios was updated to a new version without my knowledge. 

I *believe* I had phoenix bios version A01 before (it may have been A00 but I don't think so). The updated version is A04. I think there had been some contention as to whether the A04 update was breaking people's systems on the mini9 in the past so I was extremely concerned about this, although everything seems to be working fine. 

My actions before I discovered the update were:

boot to persistent live usb
reboot to #! to grab a network driver
boot to live usb again
run package installer on 
bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb
package not installed, lucid requests patch, fakeroot, and dkms as dependencies
reboot to #! and download the new packages,
reboot

When I got back into ubuntu (and after I installed the packages mentioned above), I got a bug report about the plymouthd package hanging on shutdown. I generated a bug report but network manager still doesn't have wireless so I couldn't automatically put it online. If someone can tell me where ubuntu stores the report and how I can post it manually I'd be happy to do that. Also, after I generated the report and closed the dialogue, all the colors on my LCD went crazy. Everything was still responsive though so I shutdown and got back into crunchbang without a problem. Oh, I also had my ipod plugged into my laptop the whole time to charge it.

I realize this situation could easily be my fault but my concern in posting this (if lucid did update the bios on its own) is that I wasn't notified of the bios update. The update may be valuable and it may be beneficial to lucid but I very strongly object to any software modifying my hardware without my approval.

I'm super excited about 10.04 despite the above. I was especially pleased that lucid not only recognized my ipod out of the box but I can actually access an ipod touch from linux now! I had no idea anyone had cracked the touch yet. Thanks for all your hard work developers and testers!

---

