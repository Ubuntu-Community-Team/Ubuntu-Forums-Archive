---
title: "Ubuntu fails to load grub/boot, apparently out of nowhere"
date: 2020-08-05
forum: Installation &amp; Upgrades
---

### Post by kvsikand on 2020-08-05
So today I started having an issue that I don't know the cause of. I may have updated a few packages yesterday, but I didn't think I did anything significant.

In any event, today when I boot my computer (which is an Alienware laptop running dual-boot Windows10 and Kubuntu 18.04, both drives encrypted with BitLocker & LUKS respectively, as my employer required it), it boots straight into the grub shell instead of giving me the grub menu.

Note that this isn't the grub rescue shell, its the normal grub shell. However, the `ls` command doesn't work! It says that it can't find the `.mod` file for ls. I've encountered boot issues on previous computers before, and usually using ls is the first step to find where to point grub to, but without it, I'm lost.
Note that when I type `exit` from the grub shell, it boots directly into windows.

I tried using boot-repair, and it seemed to fail, but created this pastebin dump, which has lots of errors, but I am not entirely sure how best to parse it. (As advised by the tool, I unlocked and mounted my encrypted ubuntu partition on the boot-repair live os before running the tool).
[https://paste.ubuntu.com/p/8sZ6pCwf6R/](https://paste.ubuntu.com/p/8sZ6pCwf6R/)

Any help would be greatly appreciated! Trying to get back to the state of booting into the grub menu so I can boot to either ubuntu or windows.

(Also please let me know if there's a better place to put boot questions, I'm new to the forums)

---

### Post by oldfred on 2020-08-05
Your Windows shows errors which often are from Windows hibernation or fast startup. But it could just be because it is encrypted. Then it cannot be mounted & shows errors. Probably can ignore all those.

> error: attempt to install to encrypted disk without cryptodisk enabled. 

It looks like you tried to reinstall grub, but it did not work as / was still encrypted. 
You have to both mount LVM and decrypt / so it can see fstab and update files.

---

### Post by kvsikand on 2020-08-05
Hmm, so I'm a little unclear on how to ensure this is the case. I am using the boot-repair tool, which appears to attempt to reinstall grub.

On first booting with the Boot-Repair live usb, the boot-repair program didn't have an "automatic repair" option, and I suspected this was because it couldnt find the drive. So, I opened the disks program from boot-repair, and saw that the linux drive was encrypted and not mounted. Therefore, I went ahead and unlocked it (to do so, I had to install ** libblockdev-crypto2** and run** systemctl restart udisks2.service**
Once that was done, the partition in question (partition 8, for me) appears to be unlocked.
Now, when I run boot-repair, the automatically repair option is there, so I go ahead and follow those steps. I'm not sure how/when anything gets mounted to `/`. Is that something I explicitly need to do before running the steps in boot-repair?

Edit: Upon re-running the above steps, boot-repair does actually give a message saying

You may want to retry after mounting your encrypted partitions so that the tool can verify their contents. ([https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory))
Are you sure you want to continue anyway?

so once I've decrypted the drive, how do I go about mounting it, and where do I mount it to?

---

### Post by oldfred on 2020-08-05
I do not use LVM, so do not know details. But saved a couple of links.
I think you only need the first commands that mount encrypted LVM.

How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup

---

