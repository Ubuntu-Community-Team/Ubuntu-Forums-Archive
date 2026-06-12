---
title: "Ubuntu OS Installation"
date: 2017-03-16
forum: Installation &amp; Upgrades
---

### Post by michelbevan on 2017-03-16
How can I install Ubuntu OS on my Desktop PC? I'm trying to install it on my Desktop PC but I can't. My PC configure is Core i3, 4th Generation, 4GB Ram, 500 GB Hard Disk Drive.

---

### Post by howefield on 2017-03-16
An idea of what is failing for you might be helpful. Where have you gotten stuck in the installation process, have you even gotten as far as creating the Live media to install from ?

---

### Post by cmcanulty on 2017-03-16
How are you trying to install it? From a CD, USB, over windows, alongside windows? This can surely be fixed, just need a few more details.

---

### Post by michelbevan on 2017-03-16
> **cmcanulty said:**
> How are you trying to install it? From a CD, USB, over windows, alongside windows? This can surely be fixed, just need a few more details.

  I'm trying to install from a DVD. Of course alongside Windows.

---

### Post by cmcanulty on 2017-03-17
Possibly you have to set your bios to boot from the DVD. You power the PC on while tapping one of the F keys. Usually F2, F10, or F12. Right at power on most PCs tell you the boot option key but it is fast so as soon as you see that be ready to hit an F key. You can also do it by trying the F keys and see which one works.

---

### Post by michelbevan on 2017-03-18
Yes, bios have been set to boot from the DVD. But still, I got the same problem. Could you please tell me in details for installation, so that I can Install it properly. Thanks!

---

### Post by cmcanulty on 2017-03-18
OK no problem. Please tell me which install screen you start getting trouble on. Just describe what it says and I will help. Or do you not even get to any install screen?

---

### Post by RobGoss on 2017-03-18
Hello and welcome, Please tell us the methods you have taken in detail to install Ubuntu what have you tried

Are you able to boot into the Live desktop or are you getting some sort of error message

Do you have a **USB drive **you can use to install Ubuntu in some cases if not all I feel they are much more reliable

---

### Post by cmcanulty on 2017-03-18
Yes I forgot to mention that. A few times I had trouble installing ubuntu from install option on usb or dvd but it installed fine when I selected try ubuntu, then when I got to a desktop select the install option and it worked. The issue may be a modset quirk which seems to sometimes go away when you install from a live desktop.

---

### Post by michelbevan on 2017-03-21
Yes, I'm not getting to any install screen. And does not show any error message. I don't have any USB Drive, if you can confirm me that, I can able to install with USB drive, then I will purchase it as soon as I can.
Thanks & Regards

---

### Post by jsc12345 on 2017-03-21
Okay, so, here's the idea: 
1. Use [https://unetbootin.github.io/]("http://[URL")]Unetbootin[/url] to create a bootable USB with the Ubuntu ISO
2. Hold Shift while clicking the restart button to boot into Advanced Startup. 
3.Click "boot from external disk"
4. Et Voilà! You should see the Ubuntu Boot Screen!
This assumes you use a Windows computer. On a Mac, make the bootable USB, restart the computer and spam F12 while on the boot screen to bring up the boot menu.

---

### Post by oldfred on 2017-03-21
Some have better luck with DVD and others with flash drives.
I stopped using CD/DVD years ago as many times I burned a coaster(bad burn). Always use slowest speed to insure good burn.
Flash drives are reusable, so if an issue you can redo it. And then when new Ubuntu LTS comes out, you can update it for the new version.

If an i3, you Windows is probably Windows 8 or 10 and booting in UEFI boot mode.
Then you really want to install in Ubuntu in UEFI boot mode, not the 35 year old BIOS/CSM boot mode.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by RobGoss on 2017-03-21
> **michelbevan said:**
> Yes, I'm not getting to any install screen. And does not show any error message. I don't have any USB Drive, if you can confirm me that, I can able to install with USB drive, then I will purchase it as soon as I can.
Thanks & Regards

I cannot guarantee that the USB will work on your machine that would premature of me to say  

They cost next to nothing you can probably pick up a 16.GB for about 10 bucks 

It seems to me that you need to make the correct changes within your BIOS to boot from the DVD, otherwise try a USB dive

---

### Post by michelbevan on 2017-03-22
Hello Cmcnulty, how are you today? How is going on?  I'm waiting for your valuable instruction. 

[COLOR=#000000]**cmcanulty**[/COLOR]

---

### Post by cmcanulty on 2017-04-14
if you have a usb with the iso file on it then boot your computer while the usb is plugged into it and hit f2 or f8 while it powers on. Or look as it boots and it will say which f key it the boot key then look for a boot tab and select the usb to boot from

---

