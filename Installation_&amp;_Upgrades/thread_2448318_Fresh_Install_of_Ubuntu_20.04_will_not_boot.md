---
title: "Fresh Install of Ubuntu 20.04 will not boot"
date: 2020-08-05
forum: Installation &amp; Upgrades
---

### Post by tacodos on 2020-08-05
I have been humbled to the dust, and now I have to make my first forum post. Its been a few days and I can't get this working.

My latptop was running windows 7 and one day started running real slow, so I took that as a sign to switch to full-time ubuntu. I tried installing the default ubuntu, but then it would not boot after I restarted. I thought maybe switching flavors would help (and I wanted to anyway afterwards) so I switched to Ubuntu-Mate. Same problem, so I dug around some more.

I have tried most things posted about how to fix Ubuntu not booting.

I had to reformat my disk because no partitions were even detected during the first install, so now it is currently MBR.

My computer is a DELL XPS L521X, with BIOS version A04. Not UEFI I believe. There aren't options for "secure boot" and all that, just where to boot from (in terms of boot options).

I booted a live session and ran boot-repair. I will paste the error below.
I currently only have 2 partitions, as the default set up made for me. A FAT16 boot one and then an ex4 one. Both have /mnt/boot as mount points..

I have tried a reinstall once of Ubuntu Mate and had the same problems. Before the reinstall, I tried reinstalling grub but then it booted just to grub, and didn't detect the operating system.

This could have something to do with RAID which I don't know much about, or an outdated BIOS, bad partitions...
Currently it just says no bootable disk when I try and boot without the flash drive.
Its got to be something simple, but I just keep missing it. Thanks in advance. I will be happy to provide more output if needed.

(I prefer not reinstalling if possible, it has taken hours even when I don't download upgrades.)

Last thing, after my last attempt at boot repair my live session won't detect any WiFi connections. I even plugged in ethernet and couldn't get it. If anyone knows common problems or tricks to solve that, it will probably be necessary to do any fixes.

[https://paste.ubuntu.com/p/bhGgkzcnth/](https://paste.ubuntu.com/p/bhGgkzcnth/)

---

### Post by tacodos on 2020-08-05
I got internet connection back.

---

### Post by oldfred on 2020-08-05
While Windows 7 systems were normally BIOS/MBR, Intel i-series chips were on newer systems that were UEFI. So it may be an early UEFI, but then would need BIOS/UEFI update.

Older Dell seem to make it difficult to update BIOS from anything but Windows as it normally offers an .exe that will not run in Linux.
[https://www.dell.com/support/article/en-vi/sln171755/update-the-dell-bios-in-a-linux-or-ubuntu-environment?lang=en](https://www.dell.com/support/article/en-vi/sln171755/update-the-dell-bios-in-a-linux-or-ubuntu-environment?lang=en)


Do you have RAID or Intel RST on? It is trying to mount /dev/mapper which is either RAID or LVM. And that is confusing everything. Check your BIOS settings for drives, should be AHCI, not RAID nor Intel RST.

---

### Post by pbear42 on 2020-08-05
Agreed, the RAID question is critical. * tacodos*, please boot a live session (same as you used to install), set up an internet connection, open Firefox, log into the Forum, and navigate to this thread.  Then, open Terminal (Ctrl-Shift-T) and run the following two commands (per [NixCP]("https://nixcp.com/find-out-raid-controller-type-and-model-on-linux/")):
```
sudo lshw | grep raid -I
lspci | grep -i raid 
```
In Terminal, select Edit > Select All, then Edit > Copy.  Switch back to Firefox and paste the clipboard into your next reply, preferably enclosing the output in code tags (the # button).
If this doesn't answer the question, I'm going to suggest installing inxi and getting the answer that way, sudo apt install inxi, then inxi -SMR (which I know works).

---

