---
title: "Cannot install Ubuntu"
date: 2020-04-22
forum: Installation &amp; Upgrades
---

### Post by arkturus2 on 2020-04-22
Hello everyone.

I am a new user of Linux, or at least I am trying to become one, but I am facing some issues when I want to install it on my laptop.
Everything goes well until I get some messages during the instalation process. 

I will list all my install process in case I am doing something wrong and maybe someone will help me to correct the error which I may have made:
         *I need to mention that I had Windows 10 on this laptop but at this moment I have no OS installed on it

1. I select install Ubuntu 19.10 from the desktop of Linux Live
2. Language 
3. I check all the options (e.g. "Complete install..., Download updates during installation, etc)
4. I edit myself the partitions: 
                                         a. The partition which I chose to be the host of the OS (the "C" equivalent in Windows) like this:
                                         -  Use as: I chose "Ext4 journaling file system
                                         -  Check "Format partition"
                                         -  Mount point: "/"
                                          
                                          b. I create an EFI System partition ( I do not know which option should I chose "Primary" or "Logical"  and then "Beginning of this space" or "End of this space", options
                                          c. The partition where I have my important documents (the "D" equivalent in Windows) which I do not want to format
                                         - Use as: :NTFS journaling file system
                                         - Not checked the Format box
                                         - Mount point: "/D"
5. Install now

After this step it gets weird for me because it is appearing an info popup which says: "The attempt to mount afile system with type vfat in SCSI3 (0,0,0), partition #1 (sda) at/boot/efi failed. You may resume partitioning from the partitioning menu. Here I have 2 options "Go back" and "Continue"

If I go back I do not know what I have to change in the partitioning process and if I press "Continue", after the hour format selection, the status bar it sais "Removing the conflict files of the OS" and in the instalation details screen it shows some messages that I do not understand. At this point the installation process stops...I waited for couple hours and it is in the same state.  I will attach a picture because I do not know if I made myself clear.[IMG]https://ibb.co/JvXB2dP[/IMG]

I am sorry for the long post but I really need some help because I do not want to turn back to Windows.

Thank you very much

[IMG]https://ibb.co/JvXB2dP[/IMG]https://ibb.co/JvXB2dP

---

### Post by oldfred on 2020-04-22
I normally partition in advance, so not sure what you see. But I still have to use Something Else to choose partitions.
Do you have two ESPs?

I might not try to mount NTFS partition during install. It used to not even offer that.
Not all that difficult to add to fstab later, just make sure not to overwrite it.

Are you using gpt partitioning?
Windows only installed in UEFI boot mode to gpt partitioned drive.
Ubuntu used to let you use MBR, but should not. Maybe they now require gpt?

Post this, enclosed in code tags, # icon in forum's advanced editor:
sudo parted -l

---

### Post by Impavidus on 2020-04-23
I have a number of comments, not directly related to your immediate problem.> **arkturus2 said:**
> 
1. I select install Ubuntu 19.10 from the desktop of Linux LiveUbuntu 20.04 LTS is supposed to be released today. You may prefer the longer support period (5 years versus 3 months left).
> 3. I check all the options (e.g. "Complete install..., Download updates during installation, etc)Does that include options for LVM and encryption? Those option have their use, but make things more complicated for beginners and aren't really necessary for the typical home user.
> b. I create an EFI System partition ( I do not know which option should I chose "Primary" or "Logical"  and then "Beginning of this space" or "End of this space", optionsPrimary and logical partitions apply to MBR (old-fashioned) partitioned hard drives. On GPT (modern) partitioned hard drives all partitions are primary, so this suggests that you use MBR partitioning. This in turn suggests your Windows was installed in legacy (old-fashioned) mode, not in UEFI (modern) mode. An EFI partition is only used in UEFI mode. So what is it? UEFI or legacy? GPT or MBR?
> c. The partition where I have my important documents (the "D" equivalent in Windows) which I do not want to format
                                         - Use as: :NTFS journaling file system
                                         - Not checked the Format box
                                         - Mount point: "/D"So you want to keep your original partition for documents. Ubuntu can read and write NTFS partitions, but cannot fix them if damaged. Linux tools to deal with NTFS partitions are very limited. After all, it's a proprietary Windows filesystem. If you no longer have Windows installed on your computer, it's best to avoid NTFS.

---

