---
title: "Help with copying Windows 7 to VirtualBox"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by Stonecold1995 on 2012-03-27
I have Windows 7 installed on my HP laptop. I've also installed Kubuntu 11.10 (I might upgrade to 12.04 when it comes out soon) using Wubi. After using Kubuntu for a while, I've decided that I prefer Linux to Windows. Now I only use Windows for the rare times when I need to run an .exe file that Wine won't run. Because of that, I want to set Kubuntu as my ONLY operating system, so not a duel-boot. But I still have stuff on my Windows installation that I need to keep and that can't be simply copied. My end-goal is to have Kubuntu as my only OS and the Windows installation in VirtualBox, so this is what I'm asking how to do:

1. Copy my Windows installation to a virtual disk (I'll copy it to an external drive for later).
2. Migrate the Wubi install to a true install (after formatting my drive).
3. Put the Windows virtual disk on my Kubuntu install so I can run it in VirtualBox.

I want to put my Windows install in VirtualBox because I don't use it often enough to duel-boot and I don't want to mess with partition sizes. And I don't mean creating a fresh install in VirtualBox, I mean moving it entirely, carbon-copy, to the virtual disk so running it under VirtualBox will have it act EXACTLY as if it were running as a true install without a bunch of extra limitations imposed by Microsoft to prevent piracy or whatever (I bought the copy of Windows that I want to move to a virtual disk).  I know Windows is very hardware-specific, so it might not work in VirtualBox.  So maybe creating a fresh install in VirtualBox and then using Windows Backup and Recovery to move the data from the true install to the VirtualBox install would work?

I think tools like Disk2vhd will allow me to copy a Windows install to a virtual disk, but then how do I move my Wubi install to a true OS and the ONLY OS while keeping all the settings and data exactly as is?

Here's my idea of how to do it (please correct me if I'm wrong, lest I inadvertently f*ck up my computer):
1. Clone my entire current HDD to an external drive.
2. Convert that image to a virtual disk image (still on the external drive).
3. Migrate the Wubi install to a true install by overwriting the HP Tools partition (I can't have more than four partitions).
4. Delete all of the other partitions and re-size the current one to fit the whole disk.
5. Move the virtual disk from the external drive to VirtualBox in the Kubuntu install.
6. Run Windows 7 from VirtualBox and uninstall Wubi from it (because the Wubi was already moved to a true install).

Could someone give me a list of tools of how to do this and take me step-by-step through the process?  I'm still relatively new to this and I need a lot of help because I don't trust myself not to mess up horribly on one of those steps.

---

### Post by Mark Phelps on 2012-03-29
For detailed Win7 problems, you should really go to a Win7 forum: sevenforums.com.  They have sections and tutorials dealing with this situation.

But, not having done this, my guess is you can NOT copy an existing Win7 installation intact into a Virtual space.  I know that you can do interesting stuff with .vsd files, but those are the same thing.

But... check on the Win7 forums.  I could be wrong about this.

---

