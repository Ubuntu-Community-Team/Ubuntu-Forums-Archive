---
title: "Eternal question, upgrade or clean install?"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by laserburn2 on 2018-04-27
Hi, 18.04 is upon us and I'm two minds about upgrading my 16.04 LTS or formatting and making a clean install.

1. Arguemens for upgrade:
   - no fuss, no downloading, installing and configuring games and apps from the begging, no moving stuff to backup and restoring them afterwards

2. Arguemens for clean install:
   - cleaning up the mess and god knows what remnants from the system. This might be even more important because during the life of my current 16.04 I've basically changed the whole guts of the system, switching from Phenom to Ryzen
   - Thinking on maybe giving up on BTRFS, after hardware upgrade system for unknown reason got a bad habit of writing a small amount of data on the disk every couple of seconds, possibly bad for my SSD
   - big change between the old Ubuntu and the new, end of Unity, etc., capacity for problems after upgrade

What's your opinion? I'd like to hear some personal experiences of 16.04 to 18.04 upgrade so far.

---

### Post by Autodave on 2018-04-27
Personally, I rarely have an upgrade work. I did 13 machines once: one worked fine, one took a little work to get it running, the other 11 all had to be re-installed.

---

### Post by Irihapeti on 2018-04-27
If your current OS is / has been heavily customised or altered, a fresh install is likely to be easier.

Whatever choice you make, do a backup first. It does wonders for the peace of mind. :)

---

### Post by laserburn2 on 2018-04-27
> **Autodave said:**
> Personally, I rarely have an upgrade work. I did 13 machines once: one worked fine, one took a little work to get it running, the other 11 all had to be re-installed.

Dist-upgrade used to be coin toss for me too in the past, but lately usually works well. But since 16.04 I've decided to stick to LTS and I've never before attempted LTS to LTS upgrade.

---

### Post by mörgæs on 2018-04-27
Third option: If 16.04 works well for your hardware just keep it running.

---

### Post by laserburn2 on 2018-04-27
> **mörgæs said:**
> Third option: If 16.04 works well for your hardware just keep it running.

A sound advice for sure, but I don't want to be one of those users stuck in the past. It's good to make an effort to adjust to something new once every two years.

---

### Post by mircsicz on 2018-04-27
I'm running dozen of server's I dist-upgrade since several generations of releases both on Ubuntu & Debian... On Workstations I never got happy enough to not start over with a fresh install...

---

### Post by oldfred on 2018-04-27
I only have desktop.
I used to upgrade from 6.06 to 9.04, and back then always had issues, usually with video.
The I did a clean install of 9.10 and will never do another upgrade.

Also clean install can be a test that your backup procedure is correct & includes all your data & configuration settings (if you really want them). I also export list of installed apps and have an install script to do about 75% of configuration of a new install.
But I install to another / (root) partition, so if I really miss something I can go back and get it.

---

### Post by deadflowr on 2018-04-27
You should be backing up anyway, regardless of choice.

---

### Post by laserburn2 on 2018-04-27
I usually give Canonical few weeks to fix all the bugs in the new releases, but since their track record was good lately and I had time to kill this weekend, I decided what the heck, let's do that clean install now. Aaaand I got a critical bug stopping the installation:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1766945](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1766945)

Kind of a big deal not to be spotted before final image went live. Not cool, Canonical.

---

### Post by oldfred on 2018-04-27
Not sure I would want installer to convert BIOS installs on MBR drives to UEFI with gpt partitioning automatically unless I did choose the erase entire drive.
Windows only boots from MBR with BIOS.
Windows only boots from UEFI with gpt.
So if you start converting from one boot mode to another you must also convert drive partitioning. Or vice versa. If you convert drive from MBR to gpt, you then need to totally reinstall everything.

---

### Post by laserburn2 on 2018-04-27
> **oldfred said:**
> Not sure I would want installer to convert BIOS installs on MBR drives to UEFI with gpt partitioning automatically unless I did choose the erase entire drive.
Windows only boots from MBR with BIOS.
Windows only boots from UEFI with gpt.
So if you start converting from one boot mode to another you must also convert drive partitioning. Or vice versa. If you convert drive from MBR to gpt, you then need to totally reinstall everything.

The thing is that I replaced old CPU and mobo while I still had Ubuntu 14.04 installation on SSD, so drive remained MBR. It is however super-stupid to force conversion and then only allow it in hands off mode where you can't decide on partition size, file system, etc. So I had to unhook my storage disk and let Ubuntu installer create 512 MB EFI partition and then clump everything else on ext4 /. Plus it's scary when installer throws you an error that it can't install grub right after it already formatted your perfectly functional system. 

And since my storage HDD had to be unplugged during installation, I had to edit /etc/fstab afterwards to put swap on one partition. Not sure what I'm supposed to do with /swapfile line in that case, I commented it out.

---

### Post by oldfred on 2018-04-27
New versions of Ubuntu do not create new swap partition, but use swap file.
If you have a swap partition and it finds it,  it will use it.

Some systems mix up drive order. Ubuntu's installer only installs grub to ESP on drive seen as sda. And if that is not the install drive, it will not then install grub correctly unless that drive has an ESP.

Anytime you have multiple drives or even multiple drives, better to manage partitions yourself. But you do need to know partition requirements.

---

