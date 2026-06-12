---
title: "How to fix the boot when all the files in /boot"
date: 2019-12-06
forum: Installation &amp; Upgrades
---

### Post by finznc on 2019-12-06
I'v set the /boot to a USB pendrive in the Ubuntu 18.04 installer so I can't boot Ubuntu without the USB. Just then the bootable USB isn't bootable simply because I have two partitions and one of which contains old ext4 signature so I fixed it in another computer with GParted. I want to make the USB bootable again, and my Ubuntu has already been booted and login the desktop, maybe files /boot has no modified, can fix the boot easier because I hear that just update the GRUB?

---

### Post by yancek on 2019-12-06
Your post isn't clear to me.  Are you using what is commonly referred to as a 'live' Linux/Ubuntu pendrive?  If that's the case how did you create it, did you create a persistent file or partition?  If you are using a 'live' pendrive no changes will be saved on reboot.  If it is persistent you may be able to save some data/files.  Or have you done a full install on the pendrive of Ubuntu?   I don't understand the part about not being able to boot because you have 2 partitions on the pendrive as I've done that countless times without it affecting the booting.

Another thought, have you just put the Ubuntu boot partition/files on the usb?  If you don't resolve this soon, you might be best off posting more details here by using the boot repair tool to gather information (use the 2nd option explained on the page and select Create BootInfo Summary option).  Also, answers to the above questions might help.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by finznc on 2019-12-07
> **yancek said:**
> Your post isn't clear to me.  Are you using what is commonly referred to as a 'live' Linux/Ubuntu pendrive?  If that's the case how did you create it, did you create a persistent file or partition?  If you are using a 'live' pendrive no changes will be saved on reboot.  If it is persistent you may be able to save some data/files.  Or have you done a full install on the pendrive of Ubuntu?   I don't understand the part about not being able to boot because you have 2 partitions on the pendrive as I've done that countless times without it affecting the booting.  Another thought, have you just put the Ubuntu boot partition/files on the usb?  If you don't resolve this soon, you might be best off posting more details here by using the boot repair tool to gather information (use the 2nd option explained on the page and select Create BootInfo Summary option).  Also, answers to the above questions might help.   [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)  My bad English makes you unclear. I installed the Ubuntu root to HDD, except setting /boot mount-point at a partition of the pendrvie. Can you fix the boot by just updating the GRUB?

---

### Post by The Cog on 2019-12-07
if you still have Linux running, you can just install grub ot the pen drive. If the pen drive is (for instance) /dev/sdc then the command would be:
```
sudo grub-install /dev/sdc
```
I *think* it should be as easy as that. But the only way to prove it is to try and boot from it - it's something I haven't tried.

---

### Post by yancek on 2019-12-07
If you haven't resolved this I think it would be best to download and run boot repair and post the output here.  Don't make any repairs but use the Create BootInfo Summary option and post the link here as there are a number of unanswered questions which can all be answered with boot repair.

During the installation, did you set a partition for the root filesystem on the hard drive?
During the installation, did you create a separate boot partition on the pendrive?
Did you select to install the Grub boot files to the boot partition?
Is this an EFI or Legacy system?
Is Ubuntu the only OS installed?
Are you now able to boot Ubuntu with the pendrive attached?
Do you boot Ubuntu "without" the pendrive?

---

### Post by finznc on 2019-12-09
[**[COLOR=#000000]yeah, yancek[/COLOR]**]("https://ubuntuforums.org/member.php?u=1928724") and [**[COLOR=#DD4814][B]The Cog**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=437760")

 99% right after doing

     sudo grub-install /dev/sdc 

The boot menu is shown in other one computer.

mine is busy right now, I will try later

---

