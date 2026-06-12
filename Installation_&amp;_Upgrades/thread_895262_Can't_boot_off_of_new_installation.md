---
title: "Can't boot off of new installation"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by broof on 2008-08-20
So I just installed Ubuntu 8.04.1-Desktop for the first time. I have 4 hard drives attached to this system, so I did my partitioning manually. I took my primary IDE master drive and created a new ext3 partition of 20gb as well as a 2gb swap partition, then clicked install and figured that was that.

After removing the cd and rebooting, I was given the following message:

Reboot and select proper boot device 
or insert boot media in selected boot device and press a key

I'm 500000% sure that I installed everything into the correct drive, as I booted off of the cd and found the files exactly where I expected them to be. Furthermore, I know that this is the primary IDE master because it is the only drive of this size I have and it says it right there in the BIOS. Finally, I know that this is the only drive I have my system set to boot off of because I've been booting off of it for the past year (I've also confirmed this in the BIOS).

Is there anything extra I need to do to get this OS to boot correctly? Anything I'm overlooking? Anything I can do to troubleshoot?

Thanks in advance for your help!

---

### Post by manishtech on 2008-08-20
When you did the installation, the MBR of hard drive attached to master is altered. 
Are you sure that you have connected the hard drive to the master or in other words have you altered the hard drive arrangement after installation process?

---

### Post by broof on 2008-08-20
I haven't touched any of the hardware in this system. I just reinstalled windows onto the same drive (different partition) and it worked fine, so i can't see how this would be an issue with the physical configuration or the bios settings.

---

### Post by manishtech on 2008-08-20
Means you installed Windows after Ubuntu, now you would not have been getting GRUB, must be directly booting into Windows...

Try installing again or recover the GRUB

---

### Post by broof on 2008-08-20
It looks like this may have been an issue with the cd I was using; I tried installing while in windows, and it kept failing while making the image. I mounted Ubuntu onto a virtual drive and was able to install off of that, and now I'm dual booting without any problems.

If it was indeed an issue with the cd, it seems like the installation software should have notified me outside of the windows environment.

---

### Post by broof on 2008-08-20
To clarify, I tried reinstalling and troubleshooting ubuntu well before I ended up installing win server, so that couldn't have had anything to do with the problem.

---

### Post by manishtech on 2008-08-20
> **broof said:**
> It looks like this may have been an issue with the cd I was using; I tried installing while in windows, and it kept failing while making the image. I mounted Ubuntu onto a virtual drive and was able to install off of that, and now I'm dual booting without any problems.

If it was indeed an issue with the cd, it seems like the installation software should have notified me outside of the windows environment.
That is also provided in the CD. There is an option called "Check CD for Defects". Try that next time before installing :)

---

