---
title: "Installing Ubuntu MATE 14.04.2 on Lenovo G40-45 (A8-6410)"
date: 2015-05-19
forum: Installation &amp; Upgrades
---

### Post by ajack on 2015-05-19
Hi all,

I just purchased a Lenovo G40 laptop and not wanting to use the Windows 8.1 that came pre-installed, I switched the BIOS to legacy mode and I installed the first half of the hard disk with Windows 7 Professional (x64).  That was the easy part.

I then decided to install Ubuntu MATE 14.04.2 (LTS).  The funny thing is I selected not to install Ubuntu on the entire hdd and the installer didn't have the option to install Ubuntu into the largest free space.

I manually created an ext4 partition, a swap partition and a 1MB BIOS partition and pretty much left everything else to default.

My problem now is whenever I restart my computer, instead of getting the grub screen, I get a grayish white screen and after a few seconds, the computer starts into Ubuntu.  I do not get to see the usual grub screen and if I want to boot into Windows, have to boot directly into Windows partition when I hit the F12 key for boot options.

Can anybody help or have similar experience as myself?  Please feel free to ask me any question or additional information you may need to help me with this problem.

Thanks in advance.

---

### Post by ajgreeny on 2015-05-19
See Boot-Repair in my signature and follow the info there to run it and produce the Report.  You will get a pastebin URL which you can paste back here and someone will hopefully be able to help you more.  Do not carry out the default repair at this stage, just get the report.

---

### Post by ajack on 2015-05-19
[http://paste.ubuntu.com/11224620/](http://paste.ubuntu.com/11224620/)

---

### Post by ubfan1 on 2015-05-19
Well, for BIOS mode, you need to have the boot flag on the Windows 7 partition, not the EFI partition (which somehow got installed).  Not sure how the BIOS/UEFI boot setups interfere with each other.

---

### Post by ajack on 2015-05-19
> **ubfan1 said:**
> Well, for BIOS mode, you need to have the boot flag on the Windows 7 partition, not the EFI partition (which somehow got installed).  Not sure how the BIOS/UEFI boot setups interfere with each other.

So how do I go about fixing this?

---

### Post by Vladlenin5000 on 2015-05-19
Running a live session will let you open GParted. From there you can manage your partitions by right-clicking in the one you need to add the boot flag to.

---

### Post by ajack on 2015-05-20
Problem solved, there was a GPT partition instead of an MBR on the hard disk. Deleted all partitions and got gparted to write a new msdos partition effectively deleting the GPT and replacing it with an MBR. Thanks to all for your assistance. UEFI and GPT are new to me. My bad (and I've been using Linux since 2005)... :/

---

