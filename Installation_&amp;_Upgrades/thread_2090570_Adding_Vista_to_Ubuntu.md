---
title: "Adding Vista to Ubuntu"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by kvalenza on 2012-12-02
I just purchased a used Dell Latitude D620 computer with Ubuntu 12.04 already installed. There are no partitions. It just installs Ubuntu.  I would like to add a partition so that I can dual boot Windows Vista. Is there any way to do this?

I am already familiar with how to set Ubuntu up for dual booting when installing on a Windows machine, but I have never made a partition from Ubuntu so that it can dual boot Windows.

Can anyone give me any step by step instructions on how to do this?

---

### Post by oldfred on 2012-12-02
I would think most would say use XP or Windows 7 as Vista was the worst of the versions.

Windows will only install, boot directly from, or repair boot of a primary NTFS partition with the boot flag. So sda1 thru sda4 will work. Gparted creates a XP type NTFS partition, so newer installs may need it reformated or will reformat to the newer NTFS. The main difference is the PBR or partition boot sector and which boot loader to use, ntldr for XP or bootmgr for newer versions.
       [URL="https://help.ubuntu.com/community/WindowsDualBoot"]
[/URL]
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
    
       [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by NM5TF on 2012-12-02
> **kvalenza said:**
> I just purchased a used Dell Latitude D620 computer with Ubuntu 12.04 already installed. There are no partitions. It just installs Ubuntu.  I would like to add a partition so that I can dual boot Windows Vista. Is there any way to do this?

I am already familiar with how to set Ubuntu up for dual booting when installing on a Windows machine, but I have never made a partition from Ubuntu so that it can dual boot Windows.

Can anyone give me any step by step instructions on how to do this?

have you considered installing your WIN OS into a Virtual Machine???

I use Ubuntu 12.04 as my main OS, but also have WIN XP running in Virtual
Box....it certainly boots faster than a stand alone WIN OS ever did, and
retains all the WIN functuality of a stand alone install...

Tommy

---

