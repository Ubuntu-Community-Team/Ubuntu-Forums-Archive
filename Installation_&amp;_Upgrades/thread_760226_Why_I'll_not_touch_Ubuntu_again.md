---
title: "Why I'll not touch Ubuntu again"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by norrisg on 2008-04-19
Finally, Ubuntu 8.04 release candidate will actually run on my notebook without freezing, so I installed it on an 8GB Expresscard SSD.

Unfortunately, it has installed the Grub MBR on my hard drive and the Grub configuration on my Expresscard SSD. The Ubuntu install provides no choice in this matter, it just decides to take over the hard disk's MBR. This is presumably because it is deemed too complicated for a user to decide for themselves whether they want their existing setup taken over.

The result is that in order to boot anything I have to have this particular Expresscard SSD inserted. This is bad enough, but then Ubuntu compounds the problem by supplying no method of changing the Grub configuration other than editing menu.lst. This of course has no effect on MBRs. I assume this is also because it is deemed too complicated for a user.

Because Ubuntu has stolen the MBR of the primary disk, the notebook's recovery tools won't boot from that disk either. Now, instead of using Ubuntu, I'm forced to set about recovering my system.

I'm sure I can download this, that, and the other to fix this, but I don't need to: I already have the tools I need to sort out this mess. It's just that Ubuntu should never have created this situation in the first place. The fact that it omits important system-level tools which most other distributions include (in this case a proper Grub configuration tool), means that I personally regard it as unsafe to use, and therefore will not do so again.

---

### Post by Whiffle on 2008-04-19
For a complicated install like that, you're much better off using the alternate CD...

---

### Post by LaRoza on 2008-04-20
> **norrisg said:**
> Finally, Ubuntu 8.04 release candidate will actually run on my notebook without freezing, so I installed it on an 8GB Expresscard SSD.

Unfortunately, it has installed the Grub MBR on my hard drive and the Grub configuration on my Expresscard SSD. The Ubuntu install provides no choice in this matter, it just decides to take over the hard disk's MBR. This is presumably because it is deemed too complicated for a user to decide for themselves whether they want their existing setup taken over.

The result is that in order to boot anything I have to have this particular Expresscard SSD inserted. This is bad enough, but then Ubuntu compounds the problem by supplying no method of changing the Grub configuration other than editing menu.lst. This of course has no effect on MBRs. I assume this is also because it is deemed too complicated for a user.

Because Ubuntu has stolen the MBR of the primary disk, the notebook's recovery tools won't boot from that disk either. Now, instead of using Ubuntu, I'm forced to set about recovering my system.


Use the Super Grub Disk to restore the Windows MBR. (See the link in my sig)

Ubuntu does allow Grub to be installed elsewhere. You should have be more attentive, it isn't psychic.

---

### Post by mrsteveman1 on 2008-04-20
First of all this problem is a by product of the 20 year old bios. As far as i know, grub has to be installed by referencing bios disk numbers like 0x80, which don't always correspond to the scheme that modern OS kernels use. There isn't any good way to do that without guessing most of the time.

Second, you could in fact have installed grub to another device, from inside the installer (yes, the graphical live cd installer). Its the last screen, theres a button called options i believe that lets you select the bios device to install grub to. 

Grub isn't the greatest bootloader in the world, thats for sure, but every linux distro uses it at this point because Lilo is worse.

What brand laptop is this? You should be able to boot your recovery stuff by partition, by chainloading from the grub menu when the system boots (regardless of how it booted).

---

### Post by norrisg on 2008-04-21
@Whiffle: I don't see anything complicated about installing an operating system on a removable secondary hard drive, unless you are suggesting that for Ubuntu a secondary hard drive is complicated. Both Fedora and OpenSUSE had no problems in an identical setup. In any case, putting GRUB's MBR on one drive and its menu.lst on another is a recipe for problems even with "fixed" disks: no installer should allow this, let alone do it, without pointing out the potential for problems.

@LaRoza: Thank you, but I already pointed out that I have the tools to fix my primary MBR. I am, maybe suprisingly, aware that Ubuntu's installer isn't psychic. Oddly enough though, neither am I, hence the absence of anywhere to configure this during install combined with the fact that neither OpenSUSE nor Fedora had this problem in an identical setup, did not lead me to expect it would happen. (I also like the "blame the user" attitude.)

@mrsteveman1: I understand the history, I have the original IBM BIOS source code in fact, but the problem isn't grub per-se, it's what Ubuntu's installer does with it. If there is an option to avoid Ubuntu's installer taking over the primary MBR when installing on a secondary (and removable) drive it is not at all apparent. The obvious place, and where I would expect to find it, is when partitioning the drive, but it isn't there (unless I need to get my psychic skills brushed up to find it). I'm not quite sure what you mean by the "last screen": when the Ubuntu installer summarizes what it is about to do there is an "Advanced" button, but since by this stage configuration has finished, it seems unlike it is going to provide further configuration options, just more details of configuration. Again, maybe if my psychic powers were up to scratch, then I would know what was behind this button.

The bottom line however is that Ubuntu's installer did something stupid (put part of GRUB on one disk and part on another, removable, one), rendering the system (temporarily) unbootable without the removable drive. This is something at least two other well known distros managed to avoid.

---

### Post by strabes on 2008-04-21
You can control where GRUB is installed on the final page of the installation program on the ubuntu live CD. This is your own fault.

---

### Post by norrisg on 2008-04-21
> **strabes said:**
> You can control where GRUB is installed on the final page of the installation program on the ubuntu live CD. This is your own fault.
Where does it tell me that I can configure GRUB? The right place for this is where the disk is partitioned, and it should be **obvious**. Don't worry though, I'm done now.

---

### Post by mrsteveman1 on 2008-04-21
Partitioning has nothing to do with installing a bootloader. The opensuse installer separates the partitioning from the bootloader installation as well, as do most installers. 

It is under the advanced button you saw. You of course will have to figure out which bios disk number goes to each disk.

If you use partition numbering like (hd0,1) etc, it will leave the MBR alone i believe. It may install generic boot code but it will in fact respect whatever partition is set active in the partition table and boot to it instead of directly to grub.

---

### Post by carolus on 2008-04-22
> **strabes said:**
> You can control where GRUB is installed on the final page of the installation program on the ubuntu live CD. This is your own fault.

There should be an up-front menu choice to write-protect the primary hard drive, for people like me who don't like to run the risk of corrupting Windows through ignorance, carelessness, or haste.  Since I don't want to take any chances with my OEM XP installation, I'll stick to Puppy Linux and Knoppix until someone describes a totally risk-free way to install Ubuntu to USB HDD (not flash) and to boot the USB HDD from CD (without meddling with BIOS, and without requiring great caution in choosing options on the boot CD). Once that becomes available, I'll switch to Ubuntu because of its extensive repositories. I know it can be done, from contributions to this forum.  There is just no officially supported method that seems totally risk-free.

---

### Post by The Cog on 2008-04-22
Out of interest, what do the other distros do if they don't put GRUB on the MBR? I don't see how they can boot if they put the bootloader on the removable disk - surely only the MBR can offer a boot menu when you power on?

---

### Post by carolus on 2008-04-22
> **The Cog said:**
> Out of interest, what do the other distros do if they don't put GRUB on the MBR? I don't see how they can boot if they put the bootloader on the removable disk - surely only the MBR can offer a boot menu when you power on?

To put things in perspective - I have two computers with OEM XP installations that I don't want to meddle with.  I'm hoping they will last until Microsoft comes up with something better than Vista. For me the Windows vs. Linux debate is irrelevant - I want both. I don't have an old computer to play with. I made the mistake of giving away my old computer.  It only had 48 Mb of memory, but I should have added more and kept it. 

Neither of my computers has a BIOS option to boot from USB, so I am  compelled to boot from CD.  With Puppy, I can put all but a couple of small files on USB flash or USB HDD, the rest on a CD to boot from, which can then be removed to free up the CD drive.
With Knoppix, I simply use the live DVD with persistent session save to USB drive.  Either way, my primary HDD is strictly untouched. 

Cons:  With Knoppix, I lose access to my CD drive and there is no easy way to configure wireless on my laptop. With Puppy, I have wireless and CD drive but the available software is limited.

---

### Post by arvevans on 2008-04-22
How many times do we have to say it:
[LIST=1]
[*]Linux is not Windows.  It works differently, has more features, etc.
[*]RTFM
[*]RTFM again
[*]When installing, read the on-screen options.  They do have some impact on how the resulting installation is configured.  In Linux you have a choice (actually, many of them).
[*]There are boot options for Linux which allow you to boot from MBR, Alternate Partition, Floppy Drive, CD-Drive, DVD-Drive, USB Drive, Network Server, or even boot code stored in your USB equipped camera.
[/LIST]
OK...enough with the rant.  

Most BIOS code in the past 8 to 10 years does support alternative boot sources.  It is usually something like "Alternative Boot Seek" or similar verbiage.  Try it, you might actually have USB boot capability and not realize it.

Windows has a not-advertised command to rebuild the MBR to a Windows Boot Track ("fdisk /mbr").  It runs this whenever you install Windows, whether you like it or not.  Linux gives you options for overwriting or not overwriting the MBR track.

As far as I know, all multi-boot programs will overwrite the MBR so that it runs their OS selection menu before entering any of the offered operating systems.

An alternative you might be interested in trying is to run Linux under Windows (i.e. WUBI  <http://wubi-installer.org/>).

Arv
_._

---

### Post by jfj1723 on 2008-04-22
norrisg,  
   I feel for you.:cry: I know that it would be nice if there was a menu at the beginning of any install. Something that would allow you to choose where you wanted it, what things you wanted installed, where your media, docs, pics would be located. But this just does not happen.:-({|= 
   Ubuntu was my first Non-Windows product since well the 8bit days. 
   RTFM is a good solid rule. But before I installed I asked questions, How, who, where, why... 
   I screwed up twice, well three times... But I just put my recovery disk in that I made before attempting to install. (You did do that did you not? Making a Ghost of your system before installing a new OS? If not, well that is a lesson learned... the hard way.)
   I have installed to the primary HDD, to a thumbdrive and even to an SD card. All bootable.
   3 Intel Desktop systems, 4 ASUS EeePC's (Although 2 are back on Xandros and one on XP Pro)
   Did I know how to do this? No I read forums, documents, and asked questions before committing to a path. Did I screw up? yep. Did I rant about it, no. I learned from it. :grin:
   Now for my question, have you gotten your computer back to the state that it was in pre-ubuntu?

---

