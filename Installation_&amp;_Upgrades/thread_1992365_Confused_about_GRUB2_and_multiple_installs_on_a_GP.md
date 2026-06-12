---
title: "Confused about GRUB2 and multiple installs on a GPT drive"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by NTL2009 on 2012-05-31
I've read quite a bit, and sort of understand some of GRUB2, but I'm confused on this point. Say I've got a bunch of partitions on an external USB drive, partitioned as GPT (so all primary partitions). Internal drive is sda, this external is sdb:

So say I install Ubuntu as follows:

[FONT="Courier New"]sdb1 - / ... [UBUNTU}
sdb2 - /HOME [UBUNTU}
sdb3 - SWAP[/FONT]

I tell the installer to install GRUB on the root of device sdb. It installs and boots fine. Now I add a second installation (say Xubuntu), to sdb4 and sdb5, using same swap - so now we have:

[FONT="Courier New"]sdb1 - / ... [UBUNTU]
sdb2 - /HOME [UBUNTU]
sdb3 - SWAP
sdb4 - / ... [XUBUNTU]
sdb5 - /HOME [XUBUNTU][/FONT]

Again, I tell the installer to install GRUB on the root of device sdb. It installs and boots fine.

**Here is where I am confused:**

I now have a /boot/grub/grub.cfg on sdb1 and sdb4. So which one is actually used to create the start up menu where I select the OS I want to boot? It seems to me that since the sdb4/5 was the most recent install, that the boot process will look at the sdb4 /boot/grub/grub.cfg, so does that mean if I select the install on sb1, that the grub.cfg on sdb1 is ignored? I just don't follow the order of events here.

Can anyone explain, or point me to some references? Thanks.

-NTL2009

---

### Post by ajgreeny on 2012-05-31
To simplify things a bit, I hope, you can just let the installer of an OS put its own grub on the root of the device and from then on the grub configuration files used will be versions from that final installed OS.  So it looks as if you have got it right in your "Here is where I am confused" paragraph.

If you should later decide that you would prefer to use the grub configurations from a previous OS installation you can simply boot to that OS and run ```
(sudo) grub-install /dev/sda
``` assuming sda is the boot priority device.

It doesn't really matter which OS supplies the grub.cgf, as both versions will have al OSs listed; it's just the order in the list that will differ, each putting its own OS at the top of the menu.

---

### Post by oldfred on 2012-05-31
If you are using gpt, you should also have a bios_grub partition if booting with BIOS not UEFI. If UEFI then the first partition has to be efi.

If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

There is only one MBR so whichever grub is in the MBR is the one in control. When you get more than one install it can get confusing. It is easier to keep the one you boot the most in the MBR. If not the one currently in the MBR ajgreeny, gave you the command to reinstall. If the kernel in the other install gets updated, you do have to reboot into the one in the MBR and run sudo update-grub to find the new kernel.

Both grub also store where they were installed. On a major grub update it may reinstall, if you do not want the "wrong" one to reinstall you can do this can unset all choices.

Both installs will proably show the same drive, unless one was installed to your internal drive originally.
#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by drs305 on 2012-05-31
Just to add a bit more to the discussion, when you boot the Grub menu most likely appear. On the menu, the top entry belongs to the system that is controlling the boot process. Additional installations appear lower on the menu and also include the partition on which they are installed.

One thing I do on installations using the same kernel, (which makes it a bit harder to tell which is which) is to use different background images (or only have an image on one) for each system.

Placing a background image in the latest grub is very easy. You just add a suitable .png, .tga or .jpg image in the /boot/grub/ folder. For more information on this technique: 
[https://help.ubuntu.com/community/Grub2/Displays#Installing_Splash_Images]("https://help.ubuntu.com/community/Grub2/Displays#Installing_Splash_Images")

---

### Post by NTL2009 on 2012-05-31
Thank you. 

Now does that mean that the code/files in the root of the device 'point' to and use the /boot/grub/grub.cfg from sdb4 (in my example - the most recent installation)? **[EDIT:]** *I only saw the first response when I replied - I think DRS305 answered this later.*[/EDIT]

Or is there a copy of these files in the root of the device?

And so then, if I performed an update-grub (and/or install-grub?) while booted into sdb1, then it is the sdb1 grub menu that would appear as I boot?

If so, I think I'm 'getting it' now.

Ok, (and I could set up and try this, just to understand things) - so that seems to me that in my example, after I installed #2 on sdb4&5, I could then actually delete the /boot/grub/grub.cfg from sdb1 and still boot into it, because I would actually be using the menu based on what is on sdb4? Not that I would do that, I'm just trying to understand this.

-NTL2009

---

### Post by drs305 on 2012-05-31
The MBR info acts as a pointer, as you describe it. You have a good understanding of how grub works.  :-)

---

### Post by NTL2009 on 2012-05-31
> **drs305 said:**
> The MBR info acts as a pointer, as you describe it. You have a good understanding of how grub works.  :-)

Thank you, 'good understanding' might be over-stating it, but I think I see a glimmer of light now! ;)

So it this why I see, when people are updating grub on SYSTEM 'A' while booted into a different system (or LIVE CD/USB), they are given instructions to mount and chroot into that SYSTEM 'A'? So in effect, the commands act as if they were being run from that SYSTEM 'A'?

-NTL2009

---

### Post by drs305 on 2012-05-31
> **NTL2009 said:**
> Thank you, 'good understanding' might be over-stating it, but I think I see a glimmer of light now! ;)

So it this why I see, when people are updating grub on SYSTEM 'A' while booted into a different system (or LIVE CD/USB), they are given instructions to mount and chroot into that SYSTEM 'A'? So in effect, the commands act as if they were being run from that SYSTEM 'A'?

-NTL2009

Yes, but the 'chroot' procedure has to be considered a pretty abnormal operation wherein system files have been corrupted to the point that the system will no longer work on its own.

Otherwise you could simply mount the problem OS and edit the grub.cfg (or other files) directly so that it would work the next time that system boots. And for changing which OS controls the boot, by far the easiest thing to do on working systems is to simply boot into that system and run "sudo grub-install /dev/sdX" (usually sda). That command doesn't install most Grub files but does reset the MBR to point to the currently operating system.

---

### Post by NTL2009 on 2012-05-31
Got it - I'll mark this SOLVED (not really a problem that was solved, but my confusion on this point is SOLVED).

Thanks to all.

-NTL2009

---

