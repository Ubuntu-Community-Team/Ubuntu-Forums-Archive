---
title: "Install Ubuntu to dual boot with win7, bitlocker and TPM?"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by cub on 2010-10-18
I have searched and read threads about the Bitlocker, grub and TPM issues that might show up, but I can't draw any conclusions as some information contradict each other. To make sure I don't screw up my pc as thought I need to make a new post.

At work I'm supposed to run Windows 7 and encrypt the win-partition with Bitlocker. I have installed Windows, turned on the encryption and it ties into the TPM. But as I am moving over to the *nix department I want to run Ubuntu as dual boot to check everything rusn fine with all the systems I need.

Before I installed Windows I partioned the disk:

1,5 GB for system/bitlocker requirement
147 GB for Windows, C:
85 GB which is empty where I intend to install Ubuntu (not formated yet)

I boot into Windows with my bitlocker/TPM key on an USB-stick. Without the usb-stick the pc won't boot.

Now, before I try to install Ubuntu I want to make sure to do it the right so I don't mess up the Windows installation or won't be able to boot the pc at all.

There seem to be several "schools" to this. Some suggest I should have installed Ubuntu first, then Windows and then encrypt.
Some say, no worries just fire away and install since you are not planning to read the windows-partition from Ubuntu. Or an alternative, install but make sure to deactive the encryption during installation.
Some say, install but make sure grub is installed in (multiple choices) location.

Does someone have knowledge on the way to go here?

---

### Post by Mark Phelps on 2010-10-18
> **cub said:**
> ... At work I'm supposed to run Windows 7 and encrypt the win-partition with Bitlocker. 

THIS make me nervous ... is this a machine that your "work" provided you?  Or is this your own machine that you use at "work"?

Asking because, in all too many instances, messing with a work-provided machine is "grounds for termination".  Wouldn't want you to get fired as a side-effect of trying to experiment with Ubuntu.

Another thought: If it IS a work-provided machine, and you are moving to a Unix department at work, perhaps there are some Unix System Admins that know how to do what you want to do?

---

### Post by Dr. C on 2010-10-18
I am assuming that the OP either owns the computer or has the proper  permission from the computer's owner to do this. Here is a link from "the other side" that may help with this issue. It is with Vista but it should apply to 7 [http://blogs.technet.com/b/voy/archive/2006/10/13/building-a-dual-boot-system-with-windows-vista-bitlocker-protection-with-tpm-support.aspx]("http://blogs.technet.com/b/voy/archive/2006/10/13/building-a-dual-boot-system-with-windows-vista-bitlocker-protection-with-tpm-support.aspx") 

Essentially one places GRUB outside the MBR and uses the Windows boot loader to launch GRUB.

---

### Post by cub on 2010-10-19
> **Mark Phelps said:**
> THIS make me nervous ... is this a machine that your "work" provided you?  Or is this your own machine that you use at "work"?

Asking because, in all too many instances, messing with a work-provided machine is "grounds for termination".  Wouldn't want you to get fired as a side-effect of trying to experiment with Ubuntu.

Another thought: If it IS a work-provided machine, and you are moving to a Unix department at work, perhaps there are some Unix System Admins that know how to do what you want to do?
It's a work provided laptop. However everyone set up their own computers (unless you need help) and management thought that a dual boot was a good idea.
I have spoken with both the windows and unix people there but noone has tampered with both worlds and therefore don't know how to do in this situation. They all know how to do the windows or unix part, but not on the same pc and with encryption. Otherwise I have run dual boot for years.

---

### Post by cub on 2010-10-19
> **FineE said:**
> I am assuming that the OP either owns the computer or has the proper  permission from the computer's owner to do this. Here is a link from "the other side" that may help with this issue. It is with Vista but it should apply to 7 [http://blogs.technet.com/b/voy/archive/2006/10/13/building-a-dual-boot-system-with-windows-vista-bitlocker-protection-with-tpm-support.aspx]("http://blogs.technet.com/b/voy/archive/2006/10/13/building-a-dual-boot-system-with-windows-vista-bitlocker-protection-with-tpm-support.aspx") 

Essentially one places GRUB outside the MBR and uses the Windows boot loader to launch GRUB.
Yeah I found that article before as well. But it describes the installations the other way around, it installs Ubuntu first then windows and then TPM and Bitlocker. As my previous experience have been to install windows first and then ubuntu that's what I started out with.

---

### Post by cub on 2010-10-21
I suppose this is new ground for everyone then?

---

### Post by pwrstick on 2010-11-08
I watch in earnest as I am in a similar situation.  However, I followed the guide mentioned and am stuck with a Grub> prompt when I try to boot Ubuntu.

However, my dilemma should be yours as well.  If I understand things correctly Win7/Vista and the TPM chip keep a hash of the boot sector, so if you install Grub Bitlocker no workie.

Also, before this go around I did have Win7 installed, bitlocker on, then tried installing Ubuntu.  Bitlocker broke, I had to manually enter the key, turned Bitlocker off/on (force it to recreate everything), but the TPM chip doesn't appear to be happy with Bitlocker.

As a result I'm believing you cannot use Grub with Vista/Win7 if you want Bitlocker enabled.

---

### Post by pwrstick on 2010-11-08
OK man I think I got something for you to try if you're still working on this:

0: Take an image of your drive, just in case. Or use Win7 Backup to make a system image.
1: Turn off BitLocker on Win7 (decrypt the drive)
2: Install Ubuntu, and let it install GRUB (which will overwrite current MBR)
3: Follow [these instructions (link)]("http://blogs.technet.com/b/voy/archive/2006/10/13/how-to-use-windows-vista-s-boot-manager-to-boot-linux.aspx") now (and note the last user's comment to make this work with Win7 and not Vista)
4: Pop in a Win7 disc and use the command prompt to "bootrec /fixmbr" and "bootrec /fixboot" to have Windows take over the MBR
5: Now turn Bitlocker back on

I believe the key is that Windows has to have control of the MBR in order for the TPM and Win7 to jive (their hash values or whatever they use).  As long as it's Windows and not Grub I think this should work.  But that's what backing up is for :)

---

### Post by cybergnome on 2010-11-08
The straight-forward install using guided partitioning, should allow you to leave windows untouched, install Ubuntu, and it will replace the Win 7 bootloader with Grub 2 in the MBR.  Windows won't care what boot loader is used to boot it, as long as the call to the boot files is correct.

AFAIK, the Win 7 boot loader won't natively boot a Linux kernel, so if you restore the MBR with the Windows commands (one addresses the MBR and the other the primary partition), you will lose your grub, and will need to chain to another bootloader that can boot Linux.

It's mostly an aesthetic issue, IMO.

---

### Post by cub on 2010-11-09
I grew tired of finding the answers and right way to do it so I scrapped my Windows installation and reinstalled Ubuntu as the only OS. :)

---

### Post by cybergnome on 2010-11-09
After reconsidering, I am aware that there are applications (esp. security) that write to the MBR.  I can't say if the Win 7 encryption program is one of these, but that info should be readily available on the web.  If that's the case, then the procedure to follow is to install Win 7 and then write the MBR to a file for restore.  Install Ubuntu next, and then restore the MBR from your file.  You will then need to chain Grub2 to the Win 7 boot loader to be able to dual boot.  I believe the specifics about doing this are on the Ubuntu documents on the web under Grub2.

---

### Post by pwrstick on 2010-11-10
> **cybergnome said:**
> It's mostly an aesthetic issue, IMO.

I just want to follow up with a comment to this particular thought should someone else be researching Ubuntu and Windows7/Vista/Bitlocker.  If you want to use Vista/Win7 with Bitlocker, and dual boot Ubuntu (or whatever other OS), Windows *must *have control of the MBR.  GRUB cannot.  It is not an aesthetic issue.  My experience is with the TPM chip - I do not know if it matters without the TPM chip.

> During the startup process, the TPM releases the key that unlocks the encrypted partition only after comparing a hash of important operating system configuration values with a snapshot taken earlier. This verifies the integrity of the Windows startup process. The key is not released if the TPM detects that your Windows installation has been tampered with.
From [Windows Bitlocker FAQ.]("http://windows.microsoft.com/en-US/windows-vista/BitLocker-Drive-Encryption-Overview")

---

### Post by pwrstick on 2010-11-10
> **cybergnome said:**
> ...I believe the specifics about doing this are on the Ubuntu documents on the web under Grub2.

[Here is Microsoft's suggestion for dual booting Vista/Bitlocker with Linux.]("http://blogs.technet.com/b/voy/archive/2006/10/13/building-a-dual-boot-system-with-windows-vista-bitlocker-protection-with-tpm-support.aspx")  Note the comments at the link for using Win7.

---

