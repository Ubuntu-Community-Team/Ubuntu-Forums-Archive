---
title: "Installing Ubuntu Server 22.04.01 fails"
date: 2024-02-08
forum: Installation &amp; Upgrades
---

### Post by functiondj on 2024-02-08
Hi, i'm trying to install the recommended Ubuntu Server 22.04.01 on my metal home server.

It's a new ATX tower with consumer hardware, including a Ryzen 5600, an ASRock B550 mainboard and 2x16GB of Samsung ECC memory.

I've briefly run Proxmox VE on it but ran into issues with hardware passthrough (IOMMU) so i've decided to run Ubuntu Server directly and later install cockpit-project.org for web management.

Unfortunately the installation fails and the log is a huge wall of text that doesn't tell me anything as a newb. I don't know what to look for. The failure happens a couple seconds after confirming the installation configuration (the point of no return) when the installer appears to start writing to the disk and i'm prompted to configure my default user name and password, computer name, etc.

Steps i've taken in an attempt to fix the installation failing:
- verify downloaded ISO with SHA256 (valid)
- used a different brand, known-good USB on a USB port on the back (i.e. not a PC case port)
- updated the mainboard BIOS to the latest version (using USB flashing)
- disconnect all devices from the mainboard not essential for installation (SAS HBA, other directly connected SATA drives, extra NICs)
- reset UEFI to default settings

I've decided to simply upload all the generated log/crash data to a GitHub remote repository in addition to attaching a ZIP file here (identical contents).
This allows browsing the files without downloading: [https://github.com/FunctionDJ/ubuntu-server-install-logs-2024-02-08](https://github.com/FunctionDJ/ubuntu-server-install-logs-2024-02-08)

Any advice / help is much appreciated, thanks a lot :)

---

### Post by functiondj on 2024-02-08
Looking at the files for a bit (pls keep in mind i barely know anything about Linux or Ubuntu under the hood) these couple of lines and words seem to occur often throughout the various logs:

```

 Running command ['dmsetup', 'splitname', 'pve-data', '-c', '--noheadings', '--separator', '=', '-o', 'vg_name,lv_name'] with allowed return codes [0] (capture=True)
 Wiping lvm logical volume: /dev/pve/data
 Running command ['wipefs', '--all', '--force', '/dev/pve/data'] with allowed return codes [0] (capture=False)
 wipefs: error: /dev/pve/data: probing initialization failed: No such file or directory

```

Maybe the installer fails at wiping my existing installation? "pve" happens to be a common abbreviation for "Proxmox VE" which is still present on the disk i'm trying to install on top of.

---

### Post by SeijiSensei on 2024-02-09
Boot from an installation medium, choose "Try Ubuntu", then use fdisk to repartition the drive as a single volume.
```

$ sudo fdisk /dev/sda
use the "d" command to delete any existing partitions
use the "n" command to create a new partition; hit Enter to make it span the entire drive
use the "w" command to write the changes to the device
use the "q" command to quit.

```
Now run the Ubuntu installer from the icon on the desktop.

/dev/sda is usually the identifier for the first "hard drive." Since there are more names in use these days, you can use the command "sudo fdisk -l" first to have it scan all the devices and list their names and any partitions they have.

---

### Post by functiondj on 2024-02-10
Even though fdisk threw a couple of warnings and errors at me the partitions were successfully removed after a reboot and i was able to install Ubuntu Server!
Thanks a lot :)

---

### Post by MAFoElffen on 2024-02-10
Welcome to Ubuntu!

Glad that you foud an answer to your problem. Please use the "Thread Tools" link in the upper right & select to mark your thread as "Solved". We are responsible for the thread we start, to confirm that you reached a solution that to your problem.

---

### Post by functiondj on 2024-02-13
@MAFoElffen Thanks for letting me know. I looked for a "solved" button or similar for a brief moment but didn't see one, so i just changed the thread title. I've marked the thread as solved the right way and will change the title back again.

---

