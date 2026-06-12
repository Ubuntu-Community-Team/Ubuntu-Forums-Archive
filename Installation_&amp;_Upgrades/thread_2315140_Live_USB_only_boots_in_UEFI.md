---
title: "Live USB only boots in UEFI"
date: 2016-02-26
forum: Installation &amp; Upgrades
---

### Post by awsumatt on 2016-02-26
[SIZE=2][FONT=arial]I have a 5 year old Toshiba Satellite L745. I wanted to install Ubuntu on it. It only has legacy BIOS and no UEFI and when attempting to boot from more than 1 flash drive (that were both tested on my desktop machine that does have UEFI) I received the error: "Missing operating system". I've installed it several different ways (ddrescue, startup disk creator, gnome disk utility) and it won't work. The only thing I can get to boot is MATE and that is what is on it right now, but if I could,  I'd prefer Ubuntu or Kubuntu. I've done a lot of googling and still can't seem to find the answer, so if anyone has any ideas, it would be appreciated.

[COLOR=#212121]Ok, I solved it and here's how: [/COLOR]
[COLOR=#212121]So basically I managed to get a Syslinux error when trying to boot instead of just a "missing operating system" when I used the Startup Disk creator. This obviously lead me to believe it was a problem with syslinux. I also knew that Ubuntu MATE *would* boot. So what I did was took two partitions on an external hard drive (you can do this with a single flash drive too) and, using the Startup Disk Creator, installed Kubuntu on one and MATE on the other. Then I went into the **syslinux** folder on the Kubuntu partition and copied all the **.cfg** files and pictures (**.pcx**, **.jpg**, **.png**) and put them in a folder on another hard drive. Once those were safe, I deleted the **syslinux** and **boot** folders. Then, I went to the MATE partition and copied those two folders from the MATE partition to the Kubuntu partition. Lastly, I copied the **.cfg** files and pictures and replaced the ones in the **syslinux** folder that I had just pasted on the Kubuntu partition. I got the gfxboot-com32-whatever (solution for that [here]("http://askubuntu.com/a/543284/371656")[/COLOR][COLOR=#212121]) and then it booted right up![/COLOR][/FONT][/SIZE]

---

### Post by oldfred on 2016-02-26
Are you sure it is BIOS?
Most 2nd gen Intel chips had UEFI, but Windows 7 may have been installed in CSM/BIOS/Legacy boot mode.
Have you updated video BIOS which sounds like UEFI to latest version?
[http://support.toshiba.com/support/viewContentDetail?contentId=3464812](http://support.toshiba.com/support/viewContentDetail?contentId=3464812)

And have you set UEFI/BIOS to boot in BIOS mode? And is UEFI, then you may get two boot options for flash drive installer. UEFI:flash drive and just flash drive which is BIOS boot.

---

### Post by awsumatt on 2016-02-27
It's BIOS. Link you sent me was for a different model.

---

### Post by grahammechanical on 2016-02-27
> The only thing I can get to boot is MATE

How? What did you do? My BIOS motherboard sees a USB memory stick with an OS on as an external USB hard drive. I have to go to the Boot options section of the BIOS settings utility and change what drive is being booted from and make sure that External USB is at the top of the list.

This is a different setting from boot priority. 

Regards

---

### Post by awsumatt on 2016-02-27
> **grahammechanical said:**
> How? What did you do? My BIOS motherboard sees a USB memory stick with an OS on as an external USB hard drive. I have to go to the Boot options section of the BIOS settings utility and change what drive is being booted from and make sure that External USB is at the top of the list.

This is a different setting from boot priority. 

Regards

Personally on my laptop, pressing F12 when I boot up (a.k.a. spamming it while it turns on) brings me into a boot menu which lists the bootable devices and you can select the USB from there. I'm assuming because Ubuntu MATE is used often on older computers because of how lightweight it is, they made sure everything worked for legacy BIOS. I hope this clears something up, I wasn't quite sure how to answer your question.

---

