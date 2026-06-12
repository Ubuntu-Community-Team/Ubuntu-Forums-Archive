---
title: "Ubuntu 20.04 Installation Keeps Failing"
date: 2021-01-10
forum: Installation &amp; Upgrades
---

### Post by nicholasjb1996-ai on 2021-01-10
[FONT=Ubuntu]I am trying to install Ubuntu 20.04 onto my desktop but it keeps failing with error “The attempt to mount a file system with type ext4 in SCSI5 (0, 1, 0), partition #2 (sda) at / failed.”. I created a bootable USB using Rufus 3.11, Rufus 3.13 and balenaEtcher. The drive created with balena wouldn’t even boot. Each time I boot with the USB created using Rufus I initially get a message at the top left hand corner of the screen stating “Initramfs unpacking failed: Decoding failed”. I have spent a lot of hours searching the internet about all these errors and possible reasons for the install to fail and none of the solutions I found were helpful. I purchased a new SATA HDD to rule out any issues with my old HDD perhaps being corrupted. I even tried installing the latest version of Ubuntu available i.e. 20.10 and that gives the same error right before I begin the installation. Not sure what else I can possibly do at this point so I decided I’d make a post here and hope for some advice from the community.

[/FONT]
[FONT=Ubuntu]Computer Specifications:
CPU: AMD Phenom II
Motherboard: GigaByte 970A-DS3P
GPU: NVIDIA Geforce GTX 1050Ti
HDD: WD SATA 500GB
PSU: EVGA 600B
OS: No OS Installed

[/FONT]
[FONT=Ubuntu]The image below is the error I keep getting when I try to install. 

[/FONT]

---

### Post by Impavidus on 2021-01-10
The "attempt to mount a file system" error isn't important. You can just wipe the drive clean before installation using the live disk.

The other error, "Initramfs unpacking failed", suggests there's a problem with your live disk. Maybe try a different usb drive. Sometimes a different usb port helps. Have you checked the integrity of the live disk and of the .iso?

---

### Post by nicholasjb1996-ai on 2021-01-14
My apologies for such a late response. 

Yes I have used a different USB drive and different USB ports to attempt the installation and I got the same result. I am not sure that I checked the integrity of the second drive I used but it was a new drive used to attempt installation. I have a rufus log of when I was creating the boot drive using the first USB drive, I did scan for any bad blocks and it returned "0 bad blocks found. (0/0/0 errors)". 

I can post the rufus.log file contents if you think it would help solve the issue.

---

### Post by TheFu on 2021-01-14
there is an integrity check image disk option on the first txt menu show after boot. Run that.  sorry, i don't recall the exact menu name.

---

### Post by nicholasjb1996-ai on 2021-01-19
Is that in the GRUB menu? 

Really sorry for late replies to this thread but I have not been getting notifications when someone has replied to it. I found that I needed to subscribe to my own thread to get email notifcations.

---

