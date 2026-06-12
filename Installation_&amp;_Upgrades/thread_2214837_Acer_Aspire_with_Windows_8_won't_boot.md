---
title: "Acer Aspire with Windows 8 won't boot"
date: 2014-04-03
forum: Installation &amp; Upgrades
---

### Post by Sophicidal on 2014-04-03
Howdy. I have the Acer Aspire V5-123. A rather weak machine that doesn't benefit from Windows 8 even in the slightest.

I just bought a new external DVD ROM to install this because USB boot was being difficult and I chalked that up to my usb stick being a cheap . So I put in my Ubuntu disc and I get the same message, something along the lines of "system doesn't support USB boot" and even when I clicked the "help me install from CD" option on WUBI I got a black screen with white letters. 

I've been working on this for about a month and I'm no closer to figuring it out than when I started. Thank you.

---

### Post by su:bhatta on 2014-04-03
Hi and welcome to the Forums.

Wubi is not under current development  and it is not advisable to run it.
Did your Acer come with pre installed Windows8? 
If so, chances are it has a UEFI boot.


Read these threads and see if that helps:

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://askubuntu.com/questions/374931/install-ubuntu-in-uefi-mode-unable-to-boot-from-usb](http://askubuntu.com/questions/374931/install-ubuntu-in-uefi-mode-unable-to-boot-from-usb)

You can then go for a dual boot.

---

### Post by Sophicidal on 2014-04-03
It is a UEFI boot. 
I can't even start running it with LIVEUSB or LIVECD. This laptop didn't come with a dvdrom so I had to get an external one.
I've disabled secureboot and fast startup and have tried to boot it over and over again, each time I do however I get the same message. "Does not support USB boot" or something like that. I'm sorry if there's something I'm missing but I'm really frustrated.

---

### Post by Sophicidal on 2014-04-03
Bump.

---

### Post by su:bhatta on 2014-04-03
I am sorry, but I don't have an UEFI system and not conversant with it, please wait till someone with experience in the same responds.

I could only provide you the links which might help you resolve the issue.

---

### Post by Sophicidal on 2014-04-03
> **bhattabhishek said:**
> I am sorry, but I don't have an UEFI system and not conversant with it, please wait till someone with experience in the same responds.

I could only provide you the links which might help you resolve the issue.

Thank you either way. :)

---

### Post by oldfred on 2014-04-03
Some have reported that in addition to turning off secure boot they have settings in UEFI/BIOS for USB ports and must enable them for system to boot from USB.

Almost all of my flash drives are the Microcenter house brand. I find them behind counter when checking out and they were cheaper every time I went to store. And now they have USB3 flash drives that even with my USB2 ports are about 10% faster. Or I have a lot of flash drives and they all have worked.

 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)

---

### Post by Sophicidal on 2014-04-03
Nothing I plug in is even shown in the boot menu, so I can't get very far at all.

---

### Post by oldfred on 2014-04-03
Then the issue is either a bad download, check with md5sum or incorrect install to flash or DVD. In some cases certain ports may not work, have you tried a different port? And some have had issues with some brands of flash drives.

You do have to use DVD now as install image is too large for CD, but install process is otherwise the same.
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

      
 [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM

      [/URL]
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

      
  Installation/FromUSBStick - with lots of details on various USB drive issues by  sudodus
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

     
    [URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]

---

### Post by ubfan1 on 2014-04-03
Some machines give additional boot options after setting the supervisor password.  Might try that.

---

### Post by Sophicidal on 2014-04-03
I just tested my 12.10 dvd on another computer and it worked swimmingly. 

I'll get another USB stick tomorrow and test it out.

---

### Post by Sophicidal on 2014-04-03
> **ubfan1 said:**
> Some machines give additional boot options after setting the supervisor password.  Might try that.

Thank you, I had to do that to disable secure boot to begin with. It doesn't really offer much after that.

---

### Post by Sophicidal on 2014-04-04
Nope. It's still not doing anything even with the new USB stick. Should I upload pictures?

---

### Post by oldfred on 2014-04-04
Is it starting to boot, or does UEFI/BIOS not show any bootable device?

---

### Post by Sophicidal on 2014-04-04
[http://imgur.com/a/OaSPn](http://imgur.com/a/OaSPn)

It doesn't even show up. There's everything on my BIOS, and within the "use a device" function on W8.

The "EFI USB DEVICE" function brings me to the screen where it says there's no boot function.

---

### Post by oldfred on 2014-04-04
It looks like it is not seeing a boot able device.
First link in post #7 says they just moved USB hard drive to first boot choice & it worked.

With my old BIOS system, I had many USB boot options and none of them worked for my flash drive. But if I chose to boot hard drive then it opens another window on which hard drives and flash drive then is a choice.
But flash drive must be bootable and plugged in when rebooting.

---

