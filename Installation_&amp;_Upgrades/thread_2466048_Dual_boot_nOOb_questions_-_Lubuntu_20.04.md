---
title: "Dual boot nOOb questions - Lubuntu 20.04"
date: 2021-08-18
forum: Installation &amp; Upgrades
---

### Post by steve234 on 2021-08-18
Hiya,

I need help setting up a new machine, as my dual-boot knowledge is very rusty, and my google-fu must be weak!

I've had dual-boot setups in the XP days, but nowadays run lubuntu 18.04 or 20.04 single-boot setups on all my 3 PCs / laptops. 

I've got a new (to me) laptop - an old, but upgradable Samsung 400B - and want to carry on using Lububtu, but with the preinstalled win10 as backup for family.

I've managed to muddle through Win10's recovery mode, and get booted into a live environment, but have many nOOb questions if you don't mind:

(1) I'm unfamiliar with how Win10 machines do booting / security. The machine boots straight to w10 unless I restart via win10 recovery. Not even an "enter bios" option.
I assumed it would be a UFEI boot machine, so I could follow a tutorial. However once in the "bios" it says
```
Samsung electronic BIOS Team u5.4 c2.10.1208 
```
At the bottom. This doesn't  seem to be a UFEI setup, and there is no secure boot option. I'm therefore a little lost as to how to approach a full (dual boot) install.

(1.5) I have spare ssd's - will I mess anything up by simply switching out the SSD and installing on a spare one to test?

(2) I can only run the 20.04 live USB in live mode, persistent mode glitches out after starting a disk check.

(3) Trying to watch a youtube video in Firefox (live USB to ram) causes all sorts of weirdness / freezes - not quite a full crash, but unusable.

(4) I have a few days in which to test this machine. A search here shows others have had various issues with the Samsung 400b some of which are unfathomable. How do I go about testing?

Presumably I need to install lububtu, or use the live USB and then:

- try web browsing;
- try media playback; and
- try various other workflows (like light video editing on the mighty i3-2310m, audio / video capture using OBS, and remote meetings (Zoom))

Are there any other compatability issues you recommend that I should consider, and test for?

---

### Post by ubfan1 on 2021-08-18
Don't confuse UEFI with Secure-boot.  Your 2011 machine may be a 64bit UEFI machine without Secure boot -- one less thing to worry about.  The boot mode should have controls in the BIOS/UEFI settings, maybe CMS (compatibility mode for legacy, off for UEFI). Some machines allow you to set a preference (UEFI preferred over legacy or vice versa) when both boot methods are possible (like the Ubuntu ISO). The mode in which you install Windows should be the mode in which you install Ubuntu.

---

### Post by steve234 on 2021-08-18
Thanks, I'll see if I can work out which mode windows boots in. I think there is a shell command for that

---

### Post by MAFoElffen on 2021-08-18
I think, where I explained this to someone else, should answer allot of your questions: [https://ubuntuforums.org/showthread.php?t=2465918&p=14054155#post14054155](https://ubuntuforums.org/showthread.php?t=2465918&p=14054155#post14054155)

---

### Post by steve234 on 2021-08-19
Thanks, that is a very useful explanation. I think windows fast boot / hibernate thing was confusing me (XP didn't have that) into thinking there was some windows-y stuff outside of the HDD somehow.

So in terms of "testing" use cases, I can just plop in an SSD and install 20.04, and just put the win10 drive back in if it doesn't work out?

---

### Post by MAFoElffen on 2021-08-19
Yes...Thaat would be the best scenario and safest.

 And if you do that and want both, you could then add the old drive back in. Then set the boot drive in BIOS to the drive with the new Linux install, with the old one later... Boot it... Upgrade the Grub2 bootloader... It will find the Installed Windows on the other drive, and add it to it's Grub Menu, without changing anything on your origianl drive.

---

### Post by steve234 on 2021-08-19
Its a laptop, so only one drive. But great. The machine is pretty old and low spec, so there's a chance I'll return it (undamaged) to its rightful owner if it isn't up to scratch. 

Looks promising for now tho, I have a 10yr old dell xps laptop which does everything I need, and this unit is slightly higher spec

---

### Post by MAFoElffen on 2021-08-19
If you do keep itt... Keep the second drive and buy a USB 2-1/2" drive case on Amazon... Very inexpensive. Just throwing ideas out there. It could still have a use.

---

### Post by steve234 on 2021-08-20
Thanks, I already have one of those. I'm interested that this particular unit has an expresscard port. So I could load it up with A LOT of M2 storage if I wanted (tho at EC speed)

---

### Post by steve234 on 2021-08-20
Dropped in my Lububtu 18.04 SSD from my 'dead' lappy and everything works like a charm. Will do a fresh Lububtu 20.04 install or (shudder) Arch and see how I get on. 

Thanks very much for unblocking this for me and helping me get over the hurdles of understanding the basics

---

### Post by steve234 on 2021-08-20
Should also add that w10 boots in legacy mode, so I'm in familiar (MBR dual boot) territory

---

### Post by ubfan1 on 2021-08-20
With an expresscard slot, you can even hang a desktop GPU off an adapter, see the egpu.io site.  Worked great for my old Lenovo W520.

---

### Post by steve234 on 2021-08-20
Similar era machine the Lenovo W520 - I'll have to do some research on that site to see what's viable (and cheap)

---

### Post by not-published on 2021-08-25
Here's my advice.

BEFORE installing Ubunu and Windows 10, go into your bios and enable EFI.  Make sure you use GPT partition tables (likely automatic).  You should get a boot manager capable of booting either ubuntu or windows10 by menu selection if you do that.  The reason for GPT is for easier better booting. easier dual-boot (ie, win10 hogs 3 partitions), and so each installer can have their OWN EFI boot partion area (yes, two boot loaders, let them each thing they are the one and only).

Newer PC have BIOS BUILT-IN EFI BOOT MENU - you don't use grub or any boot loader.  You just pick which one you want in the bios as default or DEL to get a menu.  Grub not required perhaps not desired.

---

### Post by steve234 on 2021-08-27
Thanks, assuming I have UFEI in my bios (I don't recall that) W10 is already installed, is the risk of conversion to GPT worth it?

---

### Post by yancek on 2021-08-27
>  is the risk of conversion to GPT worth it?          

There are quite a number of sites that explain this process.  I"m not a windows user, so I would suggest that you do an online search for "converting drive to GPT in windows without data loss", make sure you include the without data loss part.  Depends upon your familiarity with windows.  If you don't see any reference to UEFI/EFI in your BIOS, I wouldn't make the change.

If you have a GPT partition, windows won't boot from it unless it is an EFI install.

---

### Post by steve234 on 2021-08-27
Thanks guys, so my bios supports UFEI and its enabled

I converted the drive to GPT using Win10s MBR2GPT.exe and ended up with a non-bootable system.

I'm currently booting to LUbubtu live so I can restore (dd) my (MBR-using) boot disk from backup.

I think I'll stick with legacy on this machine

---

### Post by steve234 on 2021-08-29
Thanks again for all your help, got up and running easily using legacy / mbr. Went for Arch as OS in the end, too many papercuts now Lububtu has gone qt.

Marked solved

---

