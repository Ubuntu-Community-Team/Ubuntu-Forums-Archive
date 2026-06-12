---
title: "Want to go to linux mint."
date: 2017-05-28
forum: MINT
---

### Post by omrthaq on 2017-05-28
Hello,

today i wanted to go to linux mint because its a bit easier for me.
But, I spend like 6 hours to fix this problem.
I made a bootable USB with Unetbootin and restarted my PC. 
But everytime , every stick and even my HDD brings me to the grub menu.
I really need help here. Else ill start raging to much [IMG]https://ubuntuforums.org/images/icons/icon8.png[/IMG].

Thanks

---

### Post by howefield on 2017-05-28
Thread moved to the "*MINT*" forum.

---

### Post by yancek on 2017-05-28
It isn't clear whether your problem is booting the Mint usb or if you completed the install and cannot now boot the installed Mint from the harddrive.  You will need to clarify that.
If you are unable to boot the Mint usb, are you sure you have it set to first boot priority in the BIOS?
Did you verify the download of the Mint iso before putting it on the flash drive with unetbootin?
Have you tried booting the Mint flash on another computer to see if it works?

You don't mention having any other OS on the machine, do you?  If so, what?

---

### Post by ajgreeny on 2017-05-28
Are you using a machine with BIOS or UEFI as this may affect your ability to boot the USB, depending on how you made the USB.

Is the grub menu the usual one you see when booting your current Ubuntu or the boot menu you see if booting a live USB in UEFI mode offering to either boot the live Mint OS or install Mint?

---

### Post by omrthaq on 2017-05-29
yancek.

1.I setted USB 1. Place but it just skips that and boots to the grub menu
2.I loaded the ISO from [https://linuxmint.com/](https://linuxmint.com/) 
3.I dont have a PC ready. But VirtualBox detects it.

---

### Post by omrthaq on 2017-05-29
ajgreeny.

I tryed Windows UEFI mode + Other OS (not uefi).
And its the usual grub menu ( like this [https://i.stack.imgur.com/MEloE.jpg](https://i.stack.imgur.com/MEloE.jpg) but with some .efi files that wornt work !NOT MY SOURCE!)

---

### Post by yancek on 2017-05-29
So to clarify, do you now have some 'unknown' version of windows actually installed on this computer and functioning/
You are trying to install Mint from a usb and it fails?
On some systems, you need to set the boot priority for a usb under the HDD listing and if the name of the usb shows, select it.  Don't know why it would be getting you a Grub menu if it is not the Mint boot usb.  You don't mention having any system with Grub installed?

---

### Post by omrthaq on 2017-06-01
Hello,

I solved the problem. I must sadly format my SSD and then install windows and linux mint in dualboot.

I dont know what happened

Omrtha

---

