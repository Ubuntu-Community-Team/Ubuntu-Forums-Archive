---
title: "Installation help on new HDD"
date: 2015-03-22
forum: Installation &amp; Upgrades
---

### Post by ricethins on 2015-03-22
I installed an additional new 3TB hdd in my workstation. I want to install Ubuntu in the new drive, but I dont want Ubuntu to take the entire drive. Every time I start the new installation, the installer wants to format and take the entire 3TB drive. I need that space for storage of images from Lightroom, so I cannot have it be inaccessible from the windows programs. What can I do to install the program in a smaller portion of this new HDD?

Thanks!

---

### Post by sudodus on 2015-03-22
0. To make it easier and safer, ***disconnect the other drive(s)***. Then you cannot touch it (them) by mistake, and the installation will be completely into the new drive 3TB drive.

1. Run a live session from the install USB/DVD drive ***'Try Ubuntu'***

2. Use ***gparted*** and edit partitions to get what you want.

- Create a GUID partition table, '**GPT**', via ***Device -- Create Partition Table***

*Edit*: You will need a very small partition for BIOS or a small partition partition for UEFI. See this link

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
and specifically
[https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29](https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29)

- A ***data*** partition with the NTFS file system will be available from Ubuntu and Windows. Give it the label **data**.

- A ***root*** partition with the ext4 file system and at least 20 GB, maybe 40 GB will last 'forever'. Give it for example the label **ubuntu-root**.

- A ***swap*** partition with a little more than the RAM (in Gibibytes) if you want to hibernate, otherwise 1 GB will be enough.

3. Start the installer, and at the partitioning window you should select ***Something else*** (which means manual partitioning). Now you can use the partitions that you created with gparted.

*Edit*: After the installation, connect the other drive(s) again. Boot into the new 3TB drive, and when running the installed Ubuntu system, run the following command in a terminal window

```
sudo update-grub
```

which will create an entry for Windows in the grub menu.

If you are running in UEFI mode, you might need ***Boot Repair ***to make the dual boot system work. See these links and links from them

[https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

