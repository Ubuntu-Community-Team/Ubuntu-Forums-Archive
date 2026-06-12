---
title: "installation issues and bad hdd? dont know"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by hirenpathak on 2013-01-28
hello all
  I have been using ubuntu on my asus eee pc for quite some time. I had an older xp windows machine lying around. i wanted to completely remove everything it had and install ubuntu. so i got the ubuntu 11.04 live cd. I booted to the disc and then tried to install ubuntu 11.04. half way through the installation.. the thing got stuck and out of panic i just rebooted the machine.

so now after that i tried several times re-installing ubuntu but the install doesn't work. i am currently running this off of 'try ubuntu'. I ran the gparted and disk utility and it shows that i have some bad sectors in the 'master reboot record'.

the internal hdd information

model- ATA Maxtor 4R120L0
firmware version - RAMB1T0U
location - Port 1 of PATA Host Adapter
write cache - enabled
Capacity 123GB

device - /dev/sda

SMART data shows that two rows with 'ID' 5 and 197 are bad with some warning and red color text. 

What I want to do is - do a clean install of ubuntu. I personally don't care about the existing data in the HDD. I just need a clean build

also i ran the gparted and it shows that it has total three partition under /dev/sda

-- /dev/sda1 -- shows warning icon with 'unknown' file system
--- /dev/sda2 with 'key' icon and shows 'extended' file system
---/dev/sda5 with 'key' icon and shows 'linux-swap' file system.

what can i do to fix this issue and do a fresh install of ubuntu?

any help would be appreciated. thank you in advance.

---

### Post by Mark Phelps on 2013-01-28
> **hirenpathak said:**
> ... half way through the installation.. the thing got stuck and out of panic i just rebooted the machine.

so now after that i tried several times re-installing ubuntu but the install doesn't work. i am currently running this off of 'try ubuntu'. I ran the gparted and disk utility and it shows that i have some bad sectors in the 'master reboot record'.

Almost certainly -- a failing drive.  IF you can't even get through the install, that indicates that even if you keep at it and end up being able to install, it IS going to fail shortly after that.

You need to replace the old 120GB with something newer.  Sorry.

---

### Post by hirenpathak on 2013-01-29
So if I am not wrong, the HDD I have is PATA and not SATA? What kind of harddrive I need to buy? I do have one older laptop's internal HDD lying around somewhere. Can I use it as a replacement HDD?

Thank you.

---

### Post by Mark Phelps on 2013-01-29
PATA and SATA are entirely different interfaces -- you need to replace your current drive with one of the same type. PATA has the two rows of small pins; SATA has the short strip of gold connectors.

The only limit you may run into is drive capacity limits with older PCs.  I upgraded an XP-era laptop (which had a 40GB drive) and was disappointed to find the largest drive it could handle was 120GB.

It's nearly impossible to find new 120GB PATA drives these days -- so I tried a 240GB, and the BIOS couldn't read it. 

You can certainly try an older drive, but laptop drives don't last long, so if it's over 5 years old, it's on its last leg, too.

---

### Post by Bucky Ball on 2013-01-29
Slightly off-topic and not your problem, but 11.04 reached end-of-life last October and is no longer supported. ;)

---

