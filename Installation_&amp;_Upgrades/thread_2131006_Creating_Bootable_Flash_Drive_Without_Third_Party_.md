---
title: "Creating Bootable Flash Drive Without Third Party Software"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by MamuMogambo on 2013-03-31
Ubuntu officially recommends YUMI. Problem is it creates a flash drive without that beautiful Ubuntu logo which I want to see when I install the flash drive in Windows (I usually get that logo when I simply extract the Ubuntu ISO contents into the flash drive). Moreover, I don't want to use a third party software at all. Is there any way that I can just extract the contents and make it bootable. I am open to all the suggestions[FONT=comic sans ms][SIZE=6]&#8203;[/SIZE][/FONT]

---

### Post by Cheesemill on 2013-03-31
> **MamuMogambo said:**
> Ubuntu officially recommends YUMI.[FONT=comic sans ms][SIZE=6]&#8203;[/SIZE][/FONT]
I'd be interested to know where you got that information from. The official Ubuntu documentation recommends using either 'Startup Disk Creator' from a Ubuntu machine or 'Universal USB Installer' from a Windows machine.

To answer your question, because the Ubuntu download is a hybrid ISO file you can use dd to create a bootable USB, this will be identical to booting from a burned DVD.
For example...
```
sudo dd bs=4MB if=ubuntu-12.04.2-desktop-amd64.iso of=/dev/sdd

```where /dev/sdd is your USB drive.

If you are after a Windows solution then you can use [Win32 Disk Imager]("http://sourceforge.net/projects/win32diskimager/") to achieve the same result.

---

### Post by MamuMogambo on 2013-03-31
Thanx for correcting me. Yes, I want a Windows solution but I don't want to use a third party software. If I simply extract the ISO and try to boot, I get the message BOOTMGR is missing. Is there any way that I could just extract the ISO and use CMD to make it bootable, like we do to make a bootable Windows flash drive

---

### Post by Cheesemill on 2013-03-31
Unfortunately Windows doesn't have an equivalent of the dd command, so you are going to have to install some piece of software to write the image to your USB stick.

You can do this with any piece of software that will do a bit by bit copy of an iso file to your USB drive, I just suggested Win32 Disk Imager as I've used it before in the past. Another option would be to install [cygwin]("http://www.cygwin.com/") on your Windows machine to give you access to the dd command.

Just extracting the files from the iso file to the USB drive won't work, as it won't be a bit-perfect copy (the bootloader won't be written to your USB).
Also Windows doesn't come with software for extracting an iso file anyway, so you would still need 3rd party software.

---

### Post by MamuMogambo on 2013-03-31
I am OK with using certain softwares like PowerISO cause I use it frequently. I just don't want a software that I won't be using much.
Here's the solution I have in mind:
Use DiskPart:
Diskpart
List Disk
Select Disk "Whatever"
Clean
Create Partition Primary
Select Partition 1
Active
Assign
And then format the drive to Fat32
Finally extract the ISO

---

### Post by steeldriver on 2013-03-31
oops n/m

---

### Post by MamuMogambo on 2013-03-31
> **MamuMogambo said:**
> I am OK with using certain softwares like PowerISO cause I use it frequently. I just don't want a software that I won't be using much.
Here's the solution I have in mind:
Use DiskPart:
Diskpart
List Disk
Select Disk "Whatever"
Clean
Create Partition Primary
Select Partition 1
Active
Assign
And then format the drive to Fat32
Finally extract the ISO
Well, this didn't work

---

### Post by Cheesemill on 2013-03-31
> **MamuMogambo said:**
> I am OK with using certain softwares like PowerISO cause I use it frequently. I just don't want a software that I won't be using much.
Here's the solution I have in mind:
Use DiskPart:
Diskpart
List Disk
Select Disk "Whatever"
Clean
Create Partition Primary
Select Partition 1
Active
Assign
And then format the drive to Fat32
Finally extract the ISO
That isn't going to work.

As I said earlier you need a piece of software that can do an ***exact*** bit-perfect copy of the iso file to your USB stick.
Just extracting the files from the iso isn't sufficient, as this doesn't copy any of the required bootloader code from the iso file.

If you want a bootable USB that's identical to a burnt DVD then you need to either use dd from a Linux machine, or use one of the [Windows applications]("https://www.google.co.uk/search?q=dd+for+windows") that replicates the functionality of dd.

---

### Post by MamuMogambo on 2013-03-31
> **Cheesemill said:**
> That isn't going to work.

As I said earlier you need a piece of software that can do an ***exact*** bit-perfect copy of the iso file to your USB stick.
Just extracting the files from the iso isn't sufficient, as this doesn't copy any of the required bootloader code from the iso file.

If you want a bootable USB that's identical to a burnt DVD then you need to either use dd from a Linux machine, or use one of the [Windows applications]("https://www.google.co.uk/search?q=dd+for+windows") that replicates the functionality of dd.
Can you please tell me how to use dd in linux to create bootable usb. I am okay with it as far as it retains that Ubuntu logo beside my USB drive

---

### Post by Cheesemill on 2013-03-31
I gave you the command in my first post....
```
sudo dd bs=4MB if=ubuntu-12.04.2-desktop-amd64.iso of=/dev/sdd
```

Where if= is the input file (your Ubuntu iso) and of= is your output device.
Be very careful that you specify the correct output device, as a typo here could lead to you writing the image over your hard drive by mistake.

If you are unsure as to which device is your USB drive you can use the following command to list details of all of the devices attached to your system...
```
sudo lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE
```

If you take a look at my example you can see that /dev/sdd is my 8GB USB drive.
```
rob@raring:~/ISOs/Linux/Ubuntu/Precise$ sudo lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE
NAME                FSTYPE      LABEL                    MOUNTPOINT                            SIZE
sda                                                                                           59.6G
&#9492;&#9472;sda1              LVM2_member                                                               59.6G
  &#9500;&#9472;ssd-root (dm-0) ext4                                 /                                      14G
  &#9492;&#9472;ssd-home (dm-1) ext4                                 /home                                  14G
sdb                                                                                          298.1G
&#9492;&#9472;sdb1              ext4        data                     /mnt/data                           298.1G
sdc                                                                                          931.5G
&#9500;&#9472;sdc1              ext4        emulation                /mnt/emulation                      869.1G
&#9500;&#9472;sdc2              ntfs        WIN7                                                          54.4G
&#9492;&#9472;sdc3              swap                                 [SWAP]                                  8G
sdd                 iso9660     Ubuntu-GNOME 13.04 amd64                                       7.5G
&#9500;&#9472;sdd1              iso9660     Ubuntu-GNOME 13.04 amd64 /media/rob/Ubuntu-GNOME 13.04 amd64   942M
&#9492;&#9472;sdd2              vfat                                                                       2.2M

```

---

### Post by MamuMogambo on 2013-03-31
> **Cheesemill said:**
> I gave you the command in my first post....
```
sudo dd bs=4MB if=ubuntu-12.04.2-desktop-amd64.iso of=/dev/sdd
```

Where if= is the input file (your Ubuntu iso) and of= is your output device.
Be very careful that you specify the correct output device, as a typo here could lead to you writing the image over your hard drive by mistake.

If you are unsure as to which device is your USB drive you can use the following command to list details of all of the devices attached to your system...
```
sudo lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE
```

If you take a look at my example you can see that /dev/sdd is my 8GB USB drive.
```
rob@raring:~/ISOs/Linux/Ubuntu/Precise$ sudo lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE
NAME                FSTYPE      LABEL                    MOUNTPOINT                            SIZE
sda                                                                                           59.6G
&#9492;&#9472;sda1              LVM2_member                                                               59.6G
  &#9500;&#9472;ssd-root (dm-0) ext4                                 /                                      14G
  &#9492;&#9472;ssd-home (dm-1) ext4                                 /home                                  14G
sdb                                                                                          298.1G
&#9492;&#9472;sdb1              ext4        data                     /mnt/data                           298.1G
sdc                                                                                          931.5G
&#9500;&#9472;sdc1              ext4        emulation                /mnt/emulation                      869.1G
&#9500;&#9472;sdc2              ntfs        WIN7                                                          54.4G
&#9492;&#9472;sdc3              swap                                 [SWAP]                                  8G
sdd                 iso9660     Ubuntu-GNOME 13.04 amd64                                       7.5G
&#9500;&#9472;sdd1              iso9660     Ubuntu-GNOME 13.04 amd64 /media/rob/Ubuntu-GNOME 13.04 amd64   942M
&#9492;&#9472;sdd2              vfat                                                                       2.2M

```
I created a bootable usb with startup disk creator in ubuntu. It worked. Thanx Cheesemill for all the help. I will also try DD command

---

