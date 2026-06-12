---
title: "&quot;Operating System not found&quot; after installation - ubuntu 13.04 64-bit, Lenovo X120e"
date: 2013-05-24
forum: Installation &amp; Upgrades
---

### Post by lufusol on 2013-05-24
I've tried twice in a row, now, to install Ubuntu 13.04 (64bit) on a Lenovo ThinkPad X120e netbook via USB stick I created with LiLi.  I'm sure I made the stick correctly, I've been doing this on a number of netbooks for the past few days, just did another X120e with 12.04 LTS last night and it worked on the second try.

When I examine the drives from a live boot off the usb stick, the installation went through... I let it erase and use the whole 320GB HDD.  I allowed the LVM option (didn't try this with 12), maybe that's an issue?  On the netbook, in the BIOS, there is an option "UEFI/Legacy Boot" with the options "Both", "UEFI Only", or "Legacy Only".  I chose "UEFI Only".  Right on ubuntu's website it says if you want to install with UEFI support get the 64bit version, so I assume that would automatically detect and use (I actually wanted to avoid it doing legacy boot).  I think I also set this option on the other X120e netbook with Ubuntu 12, last night.  Don't know if it might also be a problem.

Is there any other info I can offer to help someone walk me through troubleshooting this?  It looks like all the files installed fine (both times, first time I blew away Windows and the second time it detected Ubuntu on the drive and I removed/reinstalled over it using the automatic options, again, checking LVM, if that matters).

Is there something I can possibly do from the live USB to repair the part of this that makes it bootable via UEFI without running through the entire installation process again?  Halp!  Thanks!

-Pete

---

### Post by lufusol on 2013-05-24
I want to say that I joined #ubuntu on IRC and was directed to a support webpage regarding repairing GRUB (specifically it was about repairing grub after installing Windows, but the information also applied where GRUB did not boot properly after a fresh installation of Ubuntu, which was my problem).

I read the instructions, made sure I comprehended them, and followed them.  They described how to boot from my LiveUSB, obtain and use the boot-repair utility which, though it required inputting some terminal commands, was very simple if instructions are followed carefully, and the end result was that my netbook became bootable.

I hope anyone else having this issue after a fresh installation will also investigate the use of boot-repair as it solved the problem for me and may also solve it for you.  After grub is repaired, it does prompt you to choose ubuntu at startup even if it is the only OS installed on the computer.  Searching for how to set up and use grub quickly provided me with the information needed to make the prompt go away and automatically launch Ubuntu upon boot.  So, I have the result I was looking for. 

thank you support community!

---

### Post by dino-amino on 2013-10-18
> **lufusol said:**
> I want to say that I joined #ubuntu on IRC and was directed to a support webpage regarding repairing GRUB (specifically it was about repairing grub after installing Windows, but the information also applied where GRUB did not boot properly after a fresh installation of Ubuntu, which was my problem)....

Hi, would you be able to share the link to that support webpage with us? It would be very helpful to people who come to this post from a search.

---

