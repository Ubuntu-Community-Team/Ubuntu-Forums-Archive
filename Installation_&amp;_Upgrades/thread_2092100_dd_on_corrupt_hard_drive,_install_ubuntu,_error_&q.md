---
title: "dd on corrupt hard drive, install ubuntu, error &quot;you need to load the kernel first&quot;"
date: 2012-12-06
forum: Installation &amp; Upgrades
---

### Post by robbiebloc on 2012-12-06
Hi, firstly sorry if this is in the wrong place, or the title didn't make any sense, it's a hard problem to be concise about.
So, the problem is this: my cousin dropped her laptop (I think while it was on), and after that her Windows 7 installation wouldn't work. It got as far as the splash screen, and that was all. We were able to recover files from the hard drive by plugging it into my Mac as an external drive. Instead of messing around trying to get her (Spanish) OEM version of WIndows, I figured it would just be easier to put Ubuntu 12.04 on the hard drive.
So, I did a dd on the drive (to zero), having heard that a low-level format, when encountering bad sectors, would add them to the drive's firmware as no-go areas, essentially making it a brand-new drive as far as higher-level things like OS installers are concerned (it's starting to sound a little ridiculous now I type it out).
Ubuntu seemed to install fine, and got as far as ejecting the DVD in order to restart, with no errors or anything like that. 
I changed the boot order back to hard drive first, and GRUB came up. Then when I tried to load Ubuntu, it came up with "error: couldn't read file" and "error: you need to load the kernel first".
So is there anything that can be done? Is that true about low-level formats making bad sectors (I think here we are talking about physically damaged parts of the disk) OK again?
Other possibly relevant information: I installed Ubuntu onto another known-good hard drive about 2 hours before trying it with the laptop hard drive, so I could do the dd, so the DVD is definitely good.
Thanks in advance

---

