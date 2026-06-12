---
title: "gparted won't resize NVMe disk (unable to create partition to install ubuntu)"
date: 2023-12-09
forum: Installation &amp; Upgrades
---

### Post by jessel on 2023-12-09
Hi,

I would like to install ubuntu 22.04 on a new laptop. The laptop comes with windows 11 and I'd like to create a dual boot system if possible.

The laptop is asus vivobook 14", its 16 gb of ram and 512 gb ssd and comes with windows 11 pre-installed.

On my first attempt to install ubuntu (from a 22.04 live disc usb that I downloaded) there was an error about bitlocker. I did not capture an image of this error but basically it said that the service needed to be disabled from within windows. At this point I registered my copy of windows, and I was able to go into the settings and disable disc encryption but it showed that bitlocker was a service available if I upgraded my windows subscription. I'm not likely to upgrade windows 11. I likely won't use windows at all but for now I'd like to keep it if possible.

After disabling the disc encryption service and subsequent attempts to install ubuntu I see warnings within gparted "unable to read the contents of this file system"... and it will not allow a resizing.

I tried a gparted live-cd and it makes no difference, essentially I get the same warning.

I suspect that there is a simple solution to this and I apologize if I've overlooked something obvious but I have searched the forums and likely I just don't know what the correct search term is.

Thanks,

Jesse

---

### Post by TheFu on 2023-12-09
Getting Bitlocker to co-exist with a dual boot environment isn't trivial. I don't know if it is even possible. It is completely outside my skill.

What you can do is to use a hypervisor and run Ubuntu in a virtual machine under MS-Windows.  Then the virtual storage will be encrypted by bitlocker already.

Of course, you can go a different direction and wipe the MS-Windows install, install Ubuntu on the full drive, selecting full-drive encryption, then under Linux, load a hypervisor and install MS-Windows into that.  I don't know how the MSFT licensing works.  That's one of the nice reasons to use most Linux distros is that there aren't any license keys.

I use LUKS encryption on my portable devices.  I've run a few VMs under that, but not MS-Windows.  I've never used Bitlocker or any encryption provided by MSFT.

Lastly, if you do use encryption, it is absolutely critical to have excellent backups for any data.  Good encryption doesn't allow data recovery efforts to work if the encryption becomes corrupted for any reason.  There are lots of physical issues with storage that can make encrypted data/stuff completely inaccessible.

---

### Post by tea for one on 2023-12-09
Turn off Bitlocker (if installed)
Do not have any drives encrypted during Ubuntu installation process
Disable Fast Start Up i.e. Windows is not hibernating
Some Windows updates turn on hibernation automatically
Windows will have  an EFI partition (needed by Ubuntu later)

Boot into Windows 11 and use Windows (Disk Management) tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run

When you have free space, boot Ubuntu installer in UEFI mode

---

### Post by yancek on 2023-12-09
I agree you should shrink the largest partition using windows Disk Management tool and reboot windows to verify it works.  Probably run chkdsk also.

Your problem using Gparted may be due also to hibernation as Linux won't mount a hibernated partition due to the risk of data loss.  You can turn it off in your windows Power Settings and there are countless sites explaining how to do this available.  Remember that windows may turn hibernation back on during some updates and will not notify the user or ask if the user wants this.  This should not be a problem in ordinary use but if you are trying to access a windows partition while booted into Ubuntu, it probably won't work if hibernation is on whether it is the system or a windows data partition.

---

### Post by jessel on 2023-12-09
Thanks very much for the responses. This was very helpful. I have no need or desire for encrypted discs, so I followed guidelines as suggested (used the windows disk tool and then disabled the fast start). From that point installation went smoothly.

I can now boot either windows or ubuntu!

Thanks again!

Jesse

---

### Post by MAFoElffen on 2023-12-11
We are responsible for the status of "our own threads" here. We decide on our own if something is solved to our satisfaction.

Since you say this is "Solved"... You are responsible to use the "Thread Tools" link in the upper right of the first page of a thread, to use the "Mark as Solved" link. This helps others to find solved threads, to help answer with their own questions. No being marked, that help members to find threads that are still open and searching for help... You can see where that helps, right?

---

