---
title: "Virtualbox issue after upgrade from 18.04 -&gt; 20.04"
date: 2021-04-06
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2021-04-06
I exported my VMs and removed Virtualbox before upgrading.  I used Software Updater to do the upgrade (see [https://ubuntuforums.org/showthread.php?t=2459924]("https://ubuntuforums.org/showthread.php?t=2459924")).  After the upgrade, I reinstalled Virtualbox.  I was going to import my VMs, but I found that they were already there.  I was able to boot into each one, even though I had not installed Extensions and updated Guest Additions.  After checking the VMs, I installed Extensions for the new release.  I also moved the current version of Guest Additionst to /usr/share/virtualbox.  Virtualbox will not recognize the new Guest Additions iso.  I removed the old iso, but Virtualbox will only show the old Guest Additions, and it is not found since it is not there.

Any ideas how to get Virtualbox to recognize the new Guest Additions iso and not the old one?

---

### Post by ajgreeny on 2021-04-06
You need to give us more information about your versions of VBox and the Guest Additions that you have at present; they must always be exactly the same version of each or you may have problems.

You have upgraded from 18.04 to 20.04 but we also need to know which kernel your new 20.04 is using as there are known problems for some VBox versions running on newer kernel versions. Command ***uname -a*** will show your current running kernel.

---

### Post by cscj01 on 2021-04-06
> **ajgreeny said:**
> You need to give us more information about your versions of VBox and the Guest Additions that you have at present; they must always be exactly the same version of each or you may have problems.

You have upgraded from 18.04 to 20.04 but we also need to know which kernel your new 20.04 is using as there are known problems for some VBox versions running on newer kernel versions. Command ***uname -a*** will show your current running kernel.

Kernel is 5.4.0-70-generic (x86_64)

Virtualbox is 6.1.16_Ubuntu r140961

Extensions and Guest Additions are both 6.1.16.

---

### Post by ajgreeny on 2021-04-07
Well, bang goes my thoughts on a possible solution for you as I don't think VBox 6.1.16 with the same version guest additions would suffer in that manner.

However, I never used the VBox packages from Ubuntu and always installed direct from Oracle using their repos, instructions for which can be found at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) in the ***Debian based Linux Distros*** section, withe the Extension package also direct from [https://download.virtualbox.org/virtualbox/6.1.18/Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.18/Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack)

I can't promise this will work as I no longer use VBox having moved to KVM/QEMU, but I didn't have problems when I clean installed from one version of Xubuntu to a newer one.  I do have a separate /home partition, however, so the hidden .virtualbox folder in my home folder was already available in the new OS.

Try updating the VBox package by using the Oracle repos as I mention above, download the extension package and double click it to install it in VBox itself then boot to one of your VMs and insert the new guest-additions from the VM's device menu item.

---

