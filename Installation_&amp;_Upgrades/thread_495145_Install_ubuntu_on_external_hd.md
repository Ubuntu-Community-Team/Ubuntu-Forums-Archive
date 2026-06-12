---
title: "Install ubuntu on external hd?"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by Onay on 2007-07-07
I'm new to the whole idea of Linux and specifically ubuntu, but I find it quite intriguing. But I have a few questions concerning installation.

I tried the live cd, but I find it to limit such things as advanced graphical displays, and I believe that to get the nVidia driver working ubuntu needs to be installed. I do not want to dual boot, install a virtual machine, or anything that affects the original hard drive I am running Windows XP on. 

I have external hard drive that connects to my computer via usb, and I want to install ubuntu 7.04 on it. Do I click install and it gives me an option of which drive I can install it on? To install to an external HD do I need to boot the live cd first? If I do sucessfully complete the installation, can I easily boot ubuntu on the external HD through the BIOS settings?

I've already searched a bit and I couldn't find a quite direct or user friendly enough answer for me, so pardon me if this is already posted somewhere. Thanks for help ahead of time.

---

### Post by Megaqwerty on 2007-07-07
I wrote this up for a friend so that they could install Dapper on their External USB Drive, it should be basically the same for Feisty:

Make sure the external drive is unmounted. Before plugging it in, go to **System>Preferences>Removable Drives and Media** and uncheck everything in the **Storage** tab.

1. Just like normal, click on the installer, go through it as usual until you get to the partitioning part. **MAKE SURE YOU CHOOSE THE USB DRIVE**.
a) Now Partition the drive
2. Let it install until it gets to the GRUB bootloader stage. Here, you will be asked if you want to load GRUB to the MBR of the internal hard drive. Select No, and then specify in the next screen "/dev/sda" or whatever Linux device was assigned to your drive.

3. Now complete the installation BUT: **DON'T SELECT "CONTINUE TO REBOOT THE SYSTEM"**. We still have some work to do.

4. Go into the terminal, and run these commands:

```
sudo mount -t proc /target/proc
sudo chroot /target
sudo nano /etc/mkinitramfs/modules

```5. After the last command, Text should fill the terminal window. You now must scroll to the bottom of the page (Using the arrow keys or the page down key) and add the following to the document:
```

ehci-hcd
usb-storage
scsi_mod
sd_mod

```Add these as well if you end up using Firewire instead of USB:
```

ieee1394
ohci1394
sbp2

```Now do Ctrl+x then y to accept the changes.

6. Now to set up initrd so it will wait a bit before trying to boot (so the USB drive has time to be detected and configured).

```
sudo nano /etc/mkinitramfs/initramfs.conf
```At the top of the page, put:

```
WAIT=10
```Ten seconds should be enough, but feel free to change the value as needed.

7. Now you need to re-create the initrd file:

```
sudo mkinitramfs -o /boot/initrd.img-`uname -r` /lib/modules/`uname -r`
```THE FINAL STEP:

8.  Update GRUB.

```
sudo nano /boot/menu.lst
```Now you need to find the lines that refer to the GRUB root device. It may look something like this:

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)
```Change the last line to go to hd0 instead:

```
## default grub root device
##e.g. groot=(hd0,0)
# groot=(hd0,0)
```Now we need to change all the references to hd0 in the section with the Ubuntu Kernels. So they each look something like this:
(What I changed is in bold)
```

title        Ubuntu, kernel 2.6.17-11-386
root        (**hd0,0**)
kernel        /boot/vmlinuz-2.6.17-11-386 root=/dev/sda1 ro quiet splash
initrd        /boot/initrd.img-2.6.17-11-386
boot
```If Ubuntu has detected and configured Windows already, and you want to be able to choose it as well, repeat the same changes to the root config option for Windows, only change hd0 to hd1. Then save your changes (Ctrl+x then y).

Now you can type exit in the terminal, and allow the machine to reboot. It should be working now, feel free to post if something in here is unclear.

---

### Post by Onay on 2007-07-08
Wow, thanks for the excellent guide. It worked out near perfectly for me. I still have other questions regarding my wireless card, a D-link usb acceptor, but I think this is the wrong forum for that. Thanks again for all the help.

---

### Post by Megaqwerty on 2007-07-08
I'm glad it helped. Please click on "Thread Tools" and change this thread to "Solved" so that others with this question can find the answer easier.

-Megaqwerty

---

### Post by nikRbokR on 2008-02-18
> **Megaqwerty said:**
> I wrote this up for a friend so that they could install Dapper on their External USB Drive, it should be basically the same for Feisty:

Make sure the external drive is unmounted. Before plugging it in, go to **System>Preferences>Removable Drives and Media** and uncheck everything in the **Storage** tab.

1. Just like normal, click on the installer, go through it as usual until you get to the partitioning part. **MAKE SURE YOU CHOOSE THE USB DRIVE**.
a) Now Partition the drive
2. Let it install until it gets to the GRUB bootloader stage. Here, you will be asked if you want to load GRUB to the MBR of the internal hard drive. Select No, and then specify in the next screen "/dev/sda" or whatever Linux device was assigned to your drive.

3. Now complete the installation BUT: **DON'T SELECT "CONTINUE TO REBOOT THE SYSTEM"**. We still have some work to do.

4. Go into the terminal, and run these commands:

```
sudo mount -t proc /target/proc
sudo chroot /target
sudo nano /etc/mkinitramfs/modules

```5. After the last command, Text should fill the terminal window. You now must scroll to the bottom of the page (Using the arrow keys or the page down key) and add the following to the document:
```

ehci-hcd
usb-storage
scsi_mod
sd_mod

```Add these as well if you end up using Firewire instead of USB:
```

ieee1394
ohci1394
sbp2

```Now do Ctrl+x then y to accept the changes.

6. Now to set up initrd so it will wait a bit before trying to boot (so the USB drive has time to be detected and configured).

```
sudo nano /etc/mkinitramfs/initramfs.conf
```At the top of the page, put:

```
WAIT=10
```Ten seconds should be enough, but feel free to change the value as needed.

7. Now you need to re-create the initrd file:

```
sudo mkinitramfs -o /boot/initrd.img-`uname -r` /lib/modules/`uname -r`
```THE FINAL STEP:

8.  Update GRUB.

```
sudo nano /boot/menu.lst
```Now you need to find the lines that refer to the GRUB root device. It may look something like this:

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)
```Change the last line to go to hd0 instead:

```
## default grub root device
##e.g. groot=(hd0,0)
# groot=(hd0,0)
```Now we need to change all the references to hd0 in the section with the Ubuntu Kernels. So they each look something like this:
(What I changed is in bold)
```

title        Ubuntu, kernel 2.6.17-11-386
root        (**hd0,0**)
kernel        /boot/vmlinuz-2.6.17-11-386 root=/dev/sda1 ro quiet splash
initrd        /boot/initrd.img-2.6.17-11-386
boot
```If Ubuntu has detected and configured Windows already, and you want to be able to choose it as well, repeat the same changes to the root config option for Windows, only change hd0 to hd1. Then save your changes (Ctrl+x then y).

Now you can type exit in the terminal, and allow the machine to reboot. It should be working now, feel free to post if something in here is unclear.

Thanks a bunch for this guide.  However, on my laptop, it automatically ejects the Text-Based Installer CD for Gutsy.  Should I leave it out when I do that sudo ..... stuff?

*I'm new... so sry if my ? sounds stupid ;)

---

### Post by Megaqwerty on 2008-02-18
That's alright, it's a valid question. I haven't tried using the text-based installer before, so I'm not sure. When it ejects your CD, does it leave you at a command prompt? If so, these steps should still apply.

Hope that helps,

Megaqwerty

---

### Post by nikRbokR on 2008-02-19
So this guide you've given is for Live CD?  That's good, I'm much more comfortable with that.

Does it work for 7.10?

---

