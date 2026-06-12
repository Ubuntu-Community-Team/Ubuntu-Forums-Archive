---
title: "Error installing ubuntu-22.04.3-live-server, stops at &quot;installing kernel&quot;"
date: 2023-10-21
forum: Installation &amp; Upgrades
---

### Post by xadro on 2023-10-21
Hi Everyone,
i've been tryint to install various versions of the ubuntu server image on my Fujitsu Futro S520 ThinClient(4gb), but it always fails at the step "installing kernel", this is my error log :[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292896&stc=1[/IMG]
I have tried to use older Versions of the server image. different USB Ports and played around in the BIOS settings. Nothing's worked so far and i am quite out of ideas why it would keep crashing at that point.

[https://paste.ubuntu.com/p/vvxCtPFhtb/](https://paste.ubuntu.com/p/vvxCtPFhtb/) System Info

---

### Post by MAFoElffen on 2023-10-21
Let's see what the sytem looks like from this report: [UbuntuForums 'system-info]("https://github.com/UbuntuForums/system-info")' Script...

You can run it from the Server Edition Installer Live USB after you get past the language and keyboard panels, select the "Help" button, then go to the system prompt...
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details

```
Choose to upload the report to a pastebin. Please post the URL of where it uploads to...

---

### Post by xadro on 2023-10-22
Managed to get that to work :D 
[https://paste.ubuntu.com/p/vvxCtPFhtb/](https://paste.ubuntu.com/p/vvxCtPFhtb/) here it is :)

---

### Post by MAFoElffen on 2023-10-22
A couple things...

First off your system is UEFI, but the BIOS boot mode was probable set to boot as either Hybrid or Legacy. IT booted as Legacy and the installer was trying to install as a Legacy boot system. The BIOS needs to be set to BIOS Boot mode of UEFI only... But that is not caused the crash.

For storage, you have a 4GB NAND Drive, with the installation options you probably selected Standard install > Erase all with LVM2... which when it created the volumes, partitioned the disk as this:
```

sda                         3.7G                                                                                                               4GB NANDrive
|_sda1                        1M                                                                                                               
|_sda2                      1.8G ext4                                                                                                          
|_sda3                      1.9G LVM2_member                                                                                                   

```
The partition table is GPT, so sda1 is bios_boot (1M), sda2 is a /boot partition (1.8G), and sd2 is your root partition (1.9G)...

If you look at the LVM details section... In all subsections of that, when you look for the free space left, there is 0.

You ran out of room = The disk was full. It failed during an APT process of trying to install the kernel because the disk was full.

1.9GB is not enough room for standard ubuntu-server. ubuntu-server-minimal might possibly fit in 1 G, if nothing else is installed... 1.75 with a few other packages. But be fore-warned it still needs some room left over after that to do APT update processes. That means it needs working room to download packages, then it extracts those packages to install them. It also needs room left over just to boot, for the initramfs image to un-compress during the boot process. That takes some storage space to do that. Rule of thumb is leave about 20% storage free for that to work. Understood?

It takes some maintenance to run a minimal system. If you get it installed within that space, you will need to keep an eye on your storage stat's so you do not fill up your disk space.

Here are three options for you:

1) Setup your BIOS to boot as UFEI only. In the install options, install as Ubuntu Server Minimal. Choose manual as the partition method. Cretae an EFI boot partition of 750MiB and set it as the boot partition. Create a partition with the rest of the space as mounted as "/" (the root system partition)... That will work out to about 3.25GiB. That should give you some head room to install ubuntu-minimal with a few services. If you get it installed and check how much room is left over, you might possible be able to (then) install ubuntu-server. It needs about 2.5GiB + 500MiB free to work. It would install easier like that because of less packages involved at one time. Notice I said "might".

2) Install the Ubuntu Server pre-installed image, which would mean removing the NAND drive and temporarily attaching it to another computer to extract the image onto the drive. Once written, then extend the root partition to the extent of the drive. RE: [https://ubuntuforums.org/showthread.php?t=2474692](https://ubuntuforums.org/showthread.php?t=2474692), with this image: [https://cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/jammy-preinstalled-server-amd64.img.xz](https://cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/jammy-preinstalled-server-amd64.img.xz)

3) Install a larger SATA SSD or NAND drive to install the system to. You might have to watch how much power your PSU provides with this option. It is a minimal device.

---

