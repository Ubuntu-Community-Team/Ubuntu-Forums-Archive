---
title: "Cannot boot Ubuntu 22.04 LTS 'error: file `/boot/` not found."
date: 2023-05-07
forum: Installation &amp; Upgrades
---

### Post by no-never-ever on 2023-05-07
I have been using Ubuntu for over a year now. I tried to reset Ubuntu with a fresh install, but I believe I made a mistake and now I cannot boot.

I'll try to keep it short: 
Ubuntu 22.04 LTS was the only OS on my system before this. I created a live USB in Ubuntu and booted it successfully.

In the prompt where I am asked how to install Ubuntu, I selected the wrong option by mistake (I wanted to erase the disk, but I chose to keep home directory and reinstall). I selected 'back' on the prompt where it asked for my time zone. I was then able to choose the option I wanted, but the system kept returning an error- which I did not think to document- preventing the install from proceeding. So, I restarted.

Now, every time I start the computer, it prints [FONT=Courier New][SIZE=3]error: file `/boot/` not found[/SIZE][/FONT] before going straight to GRUB. I tried doing the install again to no avail. 

Checking BIOS/UFEI settings reveal that **a)** the computer could not detect a bootable OS and **b)** Windows Boot Manager was missing from the boot sequence.

I'm hoping boot-repair will help, but I don't know if this is a problem that it can fix. 
Generated diagnosis here: [https://paste.ubuntu.com/p/fctxp9sG27/](https://paste.ubuntu.com/p/fctxp9sG27/)

I hope to receive a response as soon as possible. Thank you all.


**_EDIT: 5-8-23_**
Thank you all so much for your feedback!!! I am now able to boot into Ubuntu! It was actually kind of a fluke...

The underlying issue was that I created a UEFI Ubuntu install, but kept trying to boot it in BIOS mode. I stood up painstakingly trying to create a new UFEI-only live USB to solve this but, no matter what, I could not boot into any USB in UEFI mode, only BIOS.

Then, I went into the BIOS settings --> Advanced Boot Options and unticked the option **Legacy Option ROMs Enabled**, which ensures I can only boot into UEFI mode. After that, I tried booting the Ubuntu again from the boot menu (pressing F12), and it worked! \\:D/

I didn't think anything was going to happen because I had already tried booting Ubuntu from the boot menu, which didn't work. I guess I figured I had nothing else to lose at that point. Then again, the first time I tried, Legacy Option ROMs Enabled was ticked. I don't know if unticking it is the reason why I can boot now, but I'm happy either way! :grin:

---

### Post by ajgreeny on 2023-05-07
I assume from your comment near the end of your post that this installation was meant to be a dual boot with Windows and that now you can't boot either Windows or Ubuntu.
Then I noticed your comment about the Windows Boot Manager being missing!
Why do you expect or want that if this is a sole install of Ubuntu with no Windows on the machine?

---

### Post by jeremy31 on 2023-05-07
Can you use the BIOS boot loader to select a different option to boot Ubuntu?  From what I see in the Boot Repair info is a mixed install of BIOS/UEFI as it shows grub installed to the MBR and there is a 1MB partition that would be needed for BIOS boot on a GPT drive but there are also some files for Ubuntu in the EFI System Partition

---

### Post by no-never-ever on 2023-05-07
> Then I noticed your comment about the Windows Boot Manager being missing!
Why do you expect or want that if this is a sole install of Ubuntu with no Windows on the machine?         

I wasn't expecting/wanting it to happen at all!

Included that detail because I thought it might help narrow down what the issue could be, and if boot-repair could do anything about it.
I know what the boot-manager is supposed to do, so I was worried that I had lost some kind of functionality I needed to boot into any OS. If I don't need it to boot into Ubuntu, then I can at least be sure that's not the problem.

For the record, I did try booting into Ubuntu from the boot menu (pressing F12 at startup), but the computer still returned an error that there was no bootable OS. Maybe I have a broken installation?

---

### Post by no-never-ever on 2023-05-07
> Can you use the BIOS boot loader to select a different option to boot Ubuntu?

I can, and I already tried. It still says that there is no bootable OS.

> ...I see in the Boot Repair info is a mixed install of BIOS/UEFI as it  shows grub installed to the MBR and there is a 1MB partition that would  be needed for BIOS boot on a GPT drive but there are also some files for  Ubuntu in the EFI System Partition 

Okay, so what does all of this mean? Is there something wrong with this setup? Do I need to use something like Gparted to fix it?
I'm really not an expert on all of this...

---

### Post by oldfred on 2023-05-07
Systems since Microsoft required UEFI/gpt in 2012 are UEFI based. But old BIOS mode could still be used, booting from MBR.
You have grub installed to MBR for BIOS boot, but also have grub installed in ESP - efi system partition for UEFI boot. 
Only one grub install can be most current and working version.

Your fstab shows mount of ESP, line 185, so current install is UEFI.
Make sure you have UEFI as default boot mode for your installed system.
Trying to boot in BIOS mode will use grub in MBR, which is an old grub and will just give error message.

UEFI also does not delete entries, so you still have an old UEFI boot entry for Windows.
You can remove that with efibootmgr. See:
man efibootmgr
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B

Since UEFI system & UEFI install, you want to always boot in UEFI mode.
Installed systems boot from mode set in UEFI settings, often UEFI, BIOS/CSM/Legacy or some sort of combination which may confuse it. Use UEFI only  or UEFI setting.

But booting USB flash drive for install or repairs has two boot options. One clearly UEFI as UEFI xxxx and other xxxx which is BIOS mode. Only choose to boot in UEFI mode or you will try to convert system to old BIOS mode.

---

### Post by no-never-ever on 2023-05-07
Ah, so the problem was that I was booting into BIOS mode, and I need to reinstall/boot in UEFI mode...

Thanks for the info! I'll give that a try and see how it goes. :smile:


> **oldfred said:**
> UEFI also does not delete entries, so you still have an old UEFI boot entry for Windows.
You can remove that with efibootmgr.

Is it absolutely necessary to delete the entry? Like, would not doing so create any pre-installation problems?
I mean, I'll still give it a whirl, but I'd prefer to try it after installation so I can make backups and all...

---

### Post by yancek on 2023-05-08
>  Is it absolutely necessary to delete the entry? Like, would not doing so create any pre-installation problems?

No, it wont't.  It will just show the windows entry in the BIOS boot options and obviously, selecting it there will do nothing since you don't have windows installed.

---

