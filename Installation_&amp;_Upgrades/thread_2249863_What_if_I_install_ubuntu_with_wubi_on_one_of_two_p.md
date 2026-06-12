---
title: "What if I install ubuntu with wubi on one of two partitions of my second harddrive?"
date: 2014-10-25
forum: Installation &amp; Upgrades
---

### Post by mind-mind on 2014-10-25
At first sorry for my bad english usually i dont speak english. 

Ok, i have two partitions on my second harddrive. What would happen? Because BIOS is only able to see physical harddrives. Can i install it anyways? And will the GRUB bootloader work? And i install Ubuntu 13.04 because 14.04.1 isnt working. And another question: schould i install 12.04 instead of 13.04 because of the long term support?

---

### Post by Elfy on 2014-10-25
First - forget about 13.04 if you are intending to install that now - you'll get no support it is end of life - [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

If you're going to install 12.04 you'll get a couple of years before that goes end of life.

You're no longer talking about wubi in the post - I hope that is your intention.

---

### Post by westie457 on 2014-10-25
Hello mind-mind and welcome to Ubuntu Forums.

A couple of things in your request will not receive very much support because they are either EOL (End of Life- 13.04) or being phased out - Wubi.
Things would probably be much better for you if you were to do proper installation of 12.04 which is supported until April 2017 and/or a dual-boot with whichever operative system you already use.

If you let us know some specs of your machine

Processor speed
Amount of RAM
Graphics card
Current OS

We will be able to offer choices and guidance.

In the meantime do not install via Wubi and do not install 13.04.

---

### Post by mind-mind on 2014-10-25
CPU: Intel i7-4770k
RAM: 16GB DDR3
GPU: NVIDIA GTX 760 (sadly 192 bit :c)
OS: Windows 8.1

---

### Post by Elfy on 2014-10-25
well - windows 8.1 is one of the reasons that the ubuntu devs are wanting to pull wubi, so as I intimated and westie457 bluntly said - forget about wubi :)

I would look at WHY 14.04 doesn't work for you.


Check out [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Make sure that if you only get the option to Erase disk and install Ubuntu that you stop.

[COLOR="#FF0000"]This WILL erase the WHOLE disk - including windows.[/COLOR]

---

### Post by coffeecat on 2014-10-25
Another thing to add to what has already been posted. If your machine came with Windows 8.1 it will almost certainly have a UEFI BIOS and you will need to boot up the Ubuntu installation medium in UEFI mode. If you don't, Ubuntu will be installed in legacy mode and this will cause you problems. Although fixable, it will be something you will want to avoid.

Here is a useful Ubuntu wiki page on UEFI:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mind-mind on 2014-10-25
Ok i used the universal usb tool to extract the 12.04 iso to an usb stick. but my bios doesent detect the usb stick. what i can do? I dont have fastboot and secureboot is on other os

---

### Post by mind-mind on 2014-10-25
The problem on 14.04 is that if i start it, there comes the boot screen and after a couple of minutes the 5 points get orange and it stays and nothing happens. No problem on BIOS

---

### Post by Elfy on 2014-10-25
> **mind-mind said:**
> Ok i used the universal usb tool to extract the 12.04 iso to an usb stick. but my bios doesent detect the usb stick. what i can do? I dont have fastboot and secureboot is on other os

Look for a boot option when the machine is booting - might be F12 or something like that.

If not you'll have to change the boot options to allow for it - might be Del - again look when it's booting.

---

### Post by Elfy on 2014-10-25
> **mind-mind said:**
> The problem on 14.04 is that if i start it, there comes the boot screen and after a couple of minutes the 5 points get orange and it stays and nothing happens. No problem on BIOS

Try booting the live session with nomodeset

[https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options](https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options)

---

