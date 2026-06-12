---
title: "Dual boot with xp - ntldr as primary - blinking cursor"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by snakewood on 2010-12-27
Six months ago I installed Ubuntu 10.04 to my otherwise Win XP work laptop. I decided to continue to use Windows' boot loader as primary: I told the Ubuntu installer to put grub2 onto a separate partition, then used dd to copy the first 512 bytes into a file in my Windows C partition, then edited boot.ini to link to it - its a common technique that is described in many support forums and blogs. This worked fine, and continued to work until a few weeks ago. One day I chose the Ubuntu option at the Windows boot loader and got a blinking cursor at top left of screen and no grub2 menu. I was able to use SuperGrub2Disk to discover and boot from my grub2 install - so that didn't appear to be broken. I finally fixed it by dd'ing a fresh copy of the first 512 bytes of my /boot partition over to the Windows C partition. So somehow the Windows boot loader decided it no longer liked my original dd'ed file. The only things I can think of that might have changed and caused this to happen are (on Ubuntu) an update to security packages using the graphical update manager that pops up (I rarely do a command line apt-get upgrade/dist-upgrade and certainly not in this time frame) and (on Windows) a Windows Update - as it is a work laptop I tend to take whatever essential updates it suggests.

As you can see I managed to fix the problem. However does anybody have any similar experience or any explanation why this may have happened? Could an over-zealous Windows Update have caused it?

Rob

---

### Post by oldfred on 2010-12-28
When you installed grub2 to the partition so you could copy it did it not give you the warning message about blocklists?

 Note: It is possible to install GRUB to partition boot records as well. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is not recommended. 

Block lists as I understand it is hard coded addresses on the drive to jump to to boot. If anything moves the file then you have to reinstall grub. 

As long as you understand that you can use grub2 in a partition but may have to reinstall on occasion.

---

### Post by snakewood on 2010-12-28
Hi oldfred, thanks for your reply.

I used the standard ubuntu 10.04 desktop graphical installer. It was a few months ago so I can't entirely recall how it went but I think it gives you the option of not putting the boot loader into the MBR and instead nominating a separate partition, which was what I chose. As I recall there was no warning message.

I have heard about the limitations of the blocklist mechanism. However to fix my problem I did not have to reinstall grub2 - I just had to copy the boot record (first 512 bytes of the partition - using dd). Does this sound like it might have been caused by the blocklist?

Cheers,
Rob

---

### Post by oldfred on 2010-12-28
No, it does not sound like blocklist problem as I would think the code in the MBR would have a wrong address to jump to. Not sure why just recopying the boot sector would work, unless grub2 did update it internally as part of a change to grub in Ubuntu?

Next time you could save the old & new and compare them to see if they are different if real curious.

---

### Post by snakewood on 2010-12-28
Thanks for your replies oldfred - marking this thread as solved.

---

