---
title: "help with installing ubuntu 14.04"
date: 2014-07-07
forum: Installation &amp; Upgrades
---

### Post by st_micah on 2014-07-07
Hello i am having trouble with authenticating an image after i install ubuntu 14.04 on my laptop.

says failed to authenticate image then shuts off my laptop.

if anybody can assist me in this matter it would be helpful.

---

### Post by Bashing-om on 2014-07-07
st_micah; Hi ! Welcome to the forum.

OK, so the Image is no-good. Let's see why wherefore.

What did you download and from where ? (md5sum)
What means did you employ to "BURN" the .iso file as an "IMAGE" ? (burned slowly)
What Operating System are you using to make up that liveimage ? (Windows ?)
Are you "BURNING" to a DVD or USB ? (verify - "check disk for defects")

What results when you boot the liveDVD to "try ubuntu" mode ?

There must be 20 ways to make up a boot image, a bit of info as to what you are doing, and details of your end goal would sure help us to help you.
(I am comfortable with 1 of them)

We will get you booting 'buntu, one way or another.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by st_micah on 2014-07-07
where i downloaded from is [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)

i am using linux mint os to make a bootable usb.

i can boot via usb without installing.

again i can install the ubuntu but it says image failed to authenticate then shuts down my laptop whenever i power on.

---

### Post by Bashing-om on 2014-07-07
st_micah; Humm,

I am venturing into uncharted - for me - waters.

Are we talking "secure boot" and UEFI here ? .. maybe turn off secure boot in the EFI firmware ? see what results ?

[INDENT]a shot in my darkness
[/INDENT]

---

### Post by st_micah on 2014-07-07
i have no idea.........

---

### Post by grahammechanical on 2014-07-07
Which of those images did you download?

a) PC (Intel x86) desktop image
b) 64-bit (AMD64) desktop image

If you downloaded the PC (Intel x86) image then that is a 32 bit version of Ubuntu and it will not install on modern machines that have Secure boot enabled. Ubuntu 64 bit versions (AMD64) are able to install with secure boot enabled because they have Linux kernels that are signed and so meet the secure boot protocol.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by st_micah on 2014-07-07
64 bit amd image.

---

### Post by st_micah on 2014-07-09
i can't be the only person who has ran into this problem. i know somebody out there has at least some kind of answer???

---

### Post by yancek on 2014-07-09
I've never read anywhere about that error message so you may have a unique problem or perhaps I need to read more?  I wonder what image it is trying to authenticate after you have already installed the ubuntu system.

From the information you posted, you indicate that you have some version of Linux Mint on either your laptop or another computer and you are using some software available on Mint to create a bootable usb with Ubuntu 14.04 on it.  You indicate that the usb does boot and apparently the installation completes?  Do you get this message at the end of the installation?  or do you get it when you reboot?  before or after login?  Is your computer a 64bit capable machine?

---

### Post by st_micah on 2014-07-10
yes i get the message after it is installed. it says to restart to finish the installation when it boots it says the selected image failed to authenticate, please press enter.

when i do this my laptop shuts down.

and yes my system is 64 bit.

---

### Post by yancek on 2014-07-10
When you reboot, you remove the flash drive first and change the boot priority, correct?
Did you install the Ubuntu Grub bootloader to /dev/sda?

You could boot Mint or Ubuntu from the flash and run the bootinfoscript to get more information on boot files.  Just google 'bootinfoscript' and it will show the page in your browser.
Strange error for a system with only one other Linux distribution like Mint on it.

---

### Post by Bashing-om on 2014-07-10
st_micah; Yeah.

Real strange +10 on yancek's advise.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by st_micah on 2014-07-10
> **yancek said:**
> When you reboot, you remove the flash drive first and change the boot priority, correct?
Did you install the Ubuntu Grub bootloader to /dev/sda?

You could boot Mint or Ubuntu from the flash and run the bootinfoscript to get more information on boot files.  Just google 'bootinfoscript' and it will show the page in your browser.
Strange error for a system with only one other Linux distribution like Mint on it.


I was under the impression that when i installed ubuntu that the [COLOR=#000000]Ubuntu Grub bootloader to /dev/sda was with it????

and yes i remove the usb flash drive and change the boot order.

just out of curiousity could windows 8 be a problem? because i removed it and installed linux mint 17 cin.[/COLOR]

---

### Post by yancek on 2014-07-10
Windows 8 adds some complications to the mix.  First there is the Secure Boot, also using UEFI and GPT partitioning and Fastboot (or something similarly named).  I don't use any of these so wait for someone else to give advice.

---

