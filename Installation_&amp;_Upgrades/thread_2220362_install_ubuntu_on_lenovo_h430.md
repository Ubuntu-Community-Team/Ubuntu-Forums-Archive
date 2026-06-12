---
title: "install ubuntu on lenovo h430"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by Pedro_Trivino on 2014-04-27
hi, first sorry for my english. i want to install ubuntu on my pc, a lenovo 430, ram 4gb and 1t hdd with windows 7. But I read that with some lenovo system there are some problems with uefi. I don't don't want exactly it mean and how i must install ubuntu. i wanna know if some ca help me or if there were any guide to follow.
thanks.

---

### Post by oldfred on 2014-04-27
Most Windows 7 systems are booting with BIOS even if hardware is newer and can boot with UEFI.

Windows only installs to boot with UEFI on gpt partitioned drives and one of first partitions with be an efi partition. With BIOS boot you have a 100MB (hidden) Boot partition and your main isntall. Most Windows 7 systems also use all 4 primary partitions, which is another issue.

Post this from terminal in Live installer:
sudo parted -l

With 4GB of RAM and a newer computer you will want the 64 bit version.
       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

