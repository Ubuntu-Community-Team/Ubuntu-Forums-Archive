---
title: "Ubuntu 14.04 install problem. Black screen and blinking cursor"
date: 2016-01-10
forum: Installation &amp; Upgrades
---

### Post by donistiv on 2016-01-10
Hi all,

I tried to get one of my computers converted to ubuntu but the installation failed miserably and I cannot access anything.
Since I did not want to have windows, I selected to put ubuntu over the whole hard disk. At the end it said it failed to install grub and I should put it somewhere. I said put it on the whole disc. Then I rebooted the system and I am left with nothing.

There is NO windows (which is what I wanted but...)
I CANNOT get into ubuntu (which is not what I wanted). I am not sure it is even installed, but I do not know how to check
I CANNOT get into the live usb no matter how high it is in the BIOS boot sequence.
With everything I try I am met with a black screen and a blinking _.

The usb has installed ubuntu on a different machine and I do not think it is the problem.

My computer DOES NOT have UEFI. It is a Dell Optiplex 745.

I have searched google, but it seems most help relies on getting to a point where you can access the terminal... I cant even see ubuntu.

Edit: doing F12 and selecting usb drive manually results in a freeze up.

Where should I go from here?

---

### Post by yancek on 2016-01-10
Since you are not using UEFI, the default for Device for bootloader installation would have been /dev/sda.  That would have put the Grub boot code in the MBR.  You inability to access the BIOS is totally unrelated to whatever operating system you have installed on your hard drive(s) as that code is on chips on the mother board.  If you can't boot the hard drive or a flash drive or DVD, there really isn't any way to get more info or make changes.  Could you post more info on the age of the computer, cpu, RAM and other hardware?

---

### Post by donistiv on 2016-01-10
Hey,

I can access the BIOS, but I cannot start anything with it.

Previous software was Windows XP
I do not remember when I got it.
Core 2 duo
3 GB RAM
160 GB hard drive

---

### Post by Bucky Ball on 2016-01-11
Let's start at the beginning. Boot from the Ubuntu install media> choose 'Try Ubuntu' when you get to the options> when at a desktop, launch Gparted. Have a look around there and see what you can see. Any NTFS partitions marked 'Windows' anything? Perhaps take a screenshot of that and post here. 

You could also open a terminal and paste in this command:

```
sudo blkid
```

Hit enter and post the output here between code tags (see the last link in my signature).

Also, and perhaps firstly, try Boot Repair. You can select from the 'Advanced' tab to install grub to sda. Do that and reboot. There is also a function there to create a bootinfo output. Run that and post the link here also, thanks.

---

### Post by donistiv on 2016-01-11
Hi buckey,

I cannot get to ubuntu.

---

### Post by v3.xx on 2016-01-11
Bucky Ball is asking you to use the live installer (your usb) to get into your computer.  Is this what your trying?

---

### Post by Bucky Ball on 2016-01-11
> **v3.xx said:**
> Bucky Ball is asking you to use the live installer (your usb) to get into your computer.  Is this what your trying?

+1. Ubuntu should work ok on that hardware but you might want to try something lighter, Xubuntu or Lubuntu perhaps, for a speedier experience (or even a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD")). :)

* Just read your first post. Try the F12 key at boot to get you to a boot device menu then try the USB. Your machine might use a different key. Check.

How did you create the USB? If there are problems with booting the USB the BIOS will skip right past it and boot the hard drive. That might be your issue there.

---

### Post by donistiv on 2016-01-11
V3,

Yes it does not boot into the usb.

Buckley,

I moved usb up and tried usb. I tried everything that's why I am here.

The usb is fine. It worked before.

---

### Post by oldfred on 2016-01-11
A few systems promote USB flash drive to sda. Grub defaults install to sda and then corrupts flash drive.
Best to check if flash drive is still ok.

---

### Post by donistiv on 2016-01-11
oldfred,

I can assure you the usb has all files in it

---

### Post by oldfred on 2016-01-11
But an install of grub to sda, would overwrite the MBR. Installer uses syslinux, a Windows type boot loader. So files would be intact, but MBR may not be. Then system would not boot.
Otherwise it is some setting in BIOS, that you have to enable to allow USB boot. A BIOS update resets to defaults so if you did that it could mean you need to review BIOS settings again.

Also what video card/chip do you have. You may need nomodeset.
Do you get accessibility screen or tiny icons of keyboard & human at bottom of screen when booting flash drive?

---

### Post by donistiv on 2016-01-11
oldfred,

I use the motherboard video.

No I do not see anything when booting from the flash drive

---

### Post by donistiv on 2016-01-11
Hey all,

I still do not know what happened when I was installing from the USB but I really wanted to get this project done so I decided to make a dvd disc and install from there.

That worked which is good. 

Steps:
f12 > cd rom boot > if it doesnt work then shut down and retry more than once (what happened to me)

Thank you all

---

