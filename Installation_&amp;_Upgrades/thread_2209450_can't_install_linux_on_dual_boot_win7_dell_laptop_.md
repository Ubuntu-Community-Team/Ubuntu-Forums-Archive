---
title: "can't install linux on dual boot win7 dell laptop - recovery media error"
date: 2014-03-05
forum: Installation &amp; Upgrades
---

### Post by tasos2 on 2014-03-05
Hello,


 i bought a Dell Inspiron 15R laptop with Linux Ubuntu pre-installed. I  did a format and installed Win7 only and now i want to dual boot with  linux.

 
I created a bootable usb stick but the problem is that when i boot  from the usb, the ubuntu logo starts normally and then i got a message  about Recovery Media which says that there is an error that "The recovery media  tool only functions on Dell and Alienware systems" and then there is  only the "Quit" button to press.

 How can i install linux on my machine avoiding this message?
Did you have any similar problem?

 
Thank you in advance

---

### Post by oldfred on 2014-03-05
Why install the recovery?

Just install Ubuntu 13.10. One user posted that 13.10 now  includes all of  sputnik which were the Dell specific updates to 12.04 or before.

Do you want to dual boot?
When you installed Windows did you convert from UEFI to BIOS boot? 

Post this from live installer:
sudo parted -l

---

### Post by tasos2 on 2014-03-09
I don't want to install recovery, that's the problem!
I want to dual boot with windows7 and linux.
I switched t legacy boot and i disabled secure boot but the same..

I can not run this command because i cannot enter in the linux desktop from the usb.
I just put inand boot from it, and then (after the ubuntu logo) i get this message..

---

### Post by oldfred on 2014-03-09
Is Windows 7 in Legacy boot mode or UEFI?
Was this a Windows 8 system you converted to Windows 7?
If you installed Windows 7 it would convert a gpt drive to MBR incorrectly and you have to use fixparts to correct the Windows errors.

If Ubuntu flash drive correctly downloaded and installed to flash drive you should have two boot options from UEFI/BIOS menu. If only BIOS then it should boot.

Confirm that download was correct.
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

What tool did you use to create bootable flash drive. Some seem to have better luck with one or the other.
      
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

   Usb installer from Windows
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

   Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

 
    
But some just have issues with one USB port (try all) or cannot boot from a USB3 port and USB2 works. 
Some also have issues with certain brands of flash drives.

  Installation/FromUSBStick - with lots of details on various USB drive issues by  sudodus
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

---

### Post by tasos2 on 2014-03-09
In the beginning it was linux and i format and installed windows 7. Now i want to have a dual boot.
I created the usb with the "universal USB installer". I'll try with another one and i will download the latest 12.04 version of ubuntu but,
from my experience, i don't think the problem is with the linux iso etc
I think it's a dell problem..

---

### Post by oldfred on 2014-03-09
Some systems have settings in UEFI/BIOS to lock hard drive, or security settings. You need to change those if you have them.
Someone posted this on a Dell:
  Dell security software on Windows 7 ties in with the BIOS cannot write to drive

---

### Post by tasos2 on 2014-03-09
If you mean security boot it is already disabled..
i'll try to find other options..

---

