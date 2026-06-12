---
title: "RaspberryPi 4 USB Boot (No SD Card)"
date: 2020-09-06
forum: Installation &amp; Upgrades
---

### Post by jsciamms on 2020-09-06
I have gotten the RaspberryPi to boot Ubuntu server without the need of an SD card.  I originally posted this in the RaspberryPi Fourms ([https://www.raspberrypi.org/forums/viewtopic.php?f=131&t=278791](https://www.raspberrypi.org/forums/viewtopic.php?f=131&t=278791)), but figured that this information should also be put here.

I also have a link to an image that will work, as long as you have the updated EEPROM (See step 3).  Here is the link:
[https://mega.nz/file/yQVGxYKQ#Sv9ZutsMbfXiWlAohrdivKqaj5Fxzj4Ywj59tzbQDmE](https://mega.nz/file/yQVGxYKQ#Sv9ZutsMbfXiWlAohrdivKqaj5Fxzj4Ywj59tzbQDmE)

So Here are the steps:

1) Download the Ubuntu image for raspberry pi 4 form the Ubuntu official website.

2) Flash the image to a USB drive (USB 3.0 SSD or UBS flash drive).

3) Download the updated firmware files from the raspberry pi github site [https://github.com/raspberrypi/firmware/tree/master/boot](https://github.com/raspberrypi/firmware/tree/master/boot). Copy all *.dat and *.elf files to the Ubuntu boot partition. (Overwrite the files that were previously there).
NOTE: You must have MSD Booting EEPROM flashed onto your RPI4, or else this will not work!!! See: [https://www.raspberrypi.org/documentation/hardware/raspberrypi/bcm2711_bootloader_config.md#usbmassstorageboot](https://www.raspberrypi.org/documentation/hardware/raspberrypi/bcm2711_bootloader_config.md#usbmassstorageboot)
Note: As of August 2020, you may not need to perform step 3. It has been reported that the current Ubuntu image contains the correct firmware files. I will leave this step here in case it does help someone. Be aware that it may not be necessary, but does not hurt to do anyway.

4) Decompress vmlinuz on the boot partition

```
zcat vmlinuz > vmlinux
```

5) Update the config.txt as follows for the [pi4] section:

```
[pi4]
max_framebuffers=2
dtoverlay=vc4-fkms-v3d
boot_delay
kernel=vmlinux
initramfs initrd.img followkernel
```

6) Add a new script to the boot partition called auto_decompress_kernel with the following:

```
#!/bin/bash -e

#Set Variables
BTPATH=/boot/firmware
CKPATH=$BTPATH/vmlinuz
DKPATH=$BTPATH/vmlinux

#Check if compression needs to be done.
if [ -e $BTPATH/check.md5 ]; then
    if md5sum --status --ignore-missing -c $BTPATH/check.md5; then
    echo -e "\e[32mFiles have not changed, Decompression not needed\e[0m"
    exit 0
    else echo -e "\e[31mHash failed, kernel will be compressed\e[0m"
    fi
fi

#Backup the old decompressed kernel
mv $DKPATH $DKPATH.bak

if [ ! $? == 0 ]; then
    echo -e "\e[31mDECOMPRESSED KERNEL BACKUP FAILED!\e[0m"
    exit 1
else     echo -e "\e[32mDecompressed kernel backup was successful\e[0m"
fi

#Decompress the new kernel
echo "Decompressing kernel: "$CKPATH".............."

zcat $CKPATH > $DKPATH

if [ ! $? == 0 ]; then
    echo -e "\e[31mKERNEL FAILED TO DECOMPRESS!\e[0m"
    exit 1
else
    echo -e "\e[32mKernel Decompressed Succesfully\e[0m"
fi

#Hash the new kernel for checking
md5sum $CKPATH $DKPATH > $BTPATH/check.md5

if [ ! $? == 0 ]; then
    echo -e "\e[31mMD5 GENERATION FAILED!\e[0m"
    else echo -e "\e[32mMD5 generated Succesfully\e[0m"
fi

#Exit
exit 0
```

7) Create a script in the /etc/apt/apt.conf.d/ directory and call it 999_decompress_rpi_kernel. The script should contain the following:

```
DPkg::Post-Invoke {"/bin/bash /boot/firmware/auto_decompress_kernel"; };
```

9) Make the script executable

```
sudo chmod +x 999_decompress_rpi_kernel
```

Steps 7 and 8 can be done before first boot if you can mount the root file system on your computer, if you cannot, you can do them after you boot up the pi and log on to ubuntu for the first time. I recommend that you do it before first boot, but if you cannot, once you have the files in the correct place, please run the script auto_decompress_kernel from the /boot/firmware directory. If you do not, and you cannot boot after a restart, you will need to manually decompress your kernel again before this script will actually work (step 3).

10) Enjoy Ubuntu on the RPI4 without hassle [IMG]https://www.raspberrypi.org/forums/images/smilies/icon_e_biggrin.gif[/IMG]

---

### Post by m-hewitt on 2021-01-02
I have followed these instructions, but have not found them to be successful.  Two immediate issues are that the vmlinux image is no longer compressed (and that is a n easy fix) but more significant is that after updating the pi 4's EEPROM, booting will still only complete with an SD card in place, otherwise an 'SD: Card not found" error results.  The updated firmware is from 11th December 2020, version 000138a1: are there different instructions for this firmware version?

---

### Post by TheFu on 2021-01-02
The release notes for 20.10 Ubuntu related to r-pi v4 devices says that only Pis with 4G of RAM or more are supported.  They say less may work if the OS is stripped down.  [https://discourse.ubuntu.com/t/groovy-gorilla-release-notes/15533](https://discourse.ubuntu.com/t/groovy-gorilla-release-notes/15533)

I don't have a r-pi v4.  Santa brought me something different, but still nice, this year.

---

### Post by m-hewitt on 2021-01-02
My test here is for Ubuntu 20.04 with an 8G Rpi 4B.

---

### Post by TheFu on 2021-01-02
> **m-hewitt said:**
> My test here is for Ubuntu 20.04 with an 8G Rpi 4B.
That's a good data point.  This thread is for jsciamms, so his answers take priority.

---

