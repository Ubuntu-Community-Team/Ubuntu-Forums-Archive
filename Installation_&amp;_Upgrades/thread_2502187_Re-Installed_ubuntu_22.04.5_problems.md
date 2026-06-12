---
title: "Re-Installed ubuntu 22.04.5 problems"
date: 2024-11-04
forum: Installation &amp; Upgrades
---

### Post by jgw on 2024-11-04
My first problem is that of colors.  After I boot the colors hide most of everything (yellow, etc)  I found that if I goto settings and then call up colors I can change the colors so that its functional.  The problem is that its not sticking.  Given that its currently easy to read everything I can do it again but how do I make it so?

My second problem is booting.  I put ubuntu onto a ssd and its really works fine.  The problem is that the machine is a dell and i have to press f12 and then I get a list of boot options.  The one I use is the first one which is "Legacy Boot"  About 3 down it comes to the ssd which I choose and it boots right up.  What I would like to do is to not have to go through this every time I boot up.

Thoughts?

---

### Post by yancek on 2024-11-04
The f12 key on a Dell  you refer to is a 'one time boot option' and does not make any change.  That is by design.  You need to use another key to access the BIOS to make the change permanent.  You can do an online search for this including information on which specific Dell you are using as the key is not the same.  You could also search for the online manual for your specific Dell.  You would then need to move the one you refer to as the 3rd one down which you use to boot, to the top of the menu with whatever keys are used to do that on your Dell.  The link below to the Dell site explains the function of the f12 key on boot.

[https://www.dell.com/support/manuals/en-us/latitude-15-5500-laptop/latitude_5500_setupspecs/boot-menu?guid=guid-8fc0315f-0cbf-461a-996f-54a98f99d05a&lang=en-us](https://www.dell.com/support/manuals/en-us/latitude-15-5500-laptop/latitude_5500_setupspecs/boot-menu?guid=guid-8fc0315f-0cbf-461a-996f-54a98f99d05a&lang=en-us)

Is this an EFI install or a Legacy install?  Do you know what those terms mean?  If it is EFI capable, you should see references in the BIOS for EFI/UEFI.  There are a number of ways to determine this.  One is when you are booted into Ubuntu to run the command below to output information.  It won't change anything but it will output information if it is UEFI, namely you will see a directory named ubuntu.

```
sudo ls -l /boot/efi/EFI
```

---

### Post by jgw on 2024-11-05
Thank you for the response!

Here is the result of your suggestion:

sudo ls -l /boot/efi/EFI
[sudo] password for greg: 
total 8
drwx------ 2 root root 4096 Oct  6 09:27 BOOT
drwx------ 2 root root 4096 Oct  6 09:27 ubuntu

My other problem is that I am connected to wi-fi and also network connected yet I have no internet.

I now have an internet.  I have absolutely no idea why but I am a happy camper!  I also re-booted this system and now it seems to be booting up properly.  Again, I have no idea but they only thing I did was to run tye thing you told me to check and suddenly things are working!  I am going to reboot again right now to make sure.  thank you!

---

