---
title: "Ubuntu within window7 not displayed in booting OS list"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by sivaramapandianbtech on 2011-05-24
Hi,

I have installed Ubuntu 8 within window 7. But when system starts, it does not promote for OS selection. By Pressing F12 on booting, i came to OS selection, but windows 7 is only listed, not ubuntu. As per my friend help, i checked msconfig-->boot, but it also list windows 7 only.
The same ubuntu i have installed earlier within windows Xp. but in windows 7 it produce issue like this.

Can anyone please help me?

Thanks

---

### Post by zvacet on 2011-05-24
If you don´t see grub try press shift key.If that doesn´t work try to reinstall grub following [this]("https://help.ubuntu.com/community/Grub2#SIMPLEST - Copy GRUB 2 Files from the LiveCD") guide.

---

### Post by oldfred on 2011-05-24
If it is a wubi install inside windows, you do not want to install grub or grub2's bootloader to the MBR. Wubi boots with the windows boot loader.

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

If windows is missing wubi, I think you have to use BCDedit to add it.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by sivaramapandianbtech on 2011-05-25
Thanks for your reply. I will try and revert back.

---

### Post by sivaramapandianbtech on 2011-05-25
hi 
I just found the blow point in one of the site you gave.
***Windows Vista, XP, and 2000 are known to work with Wubi. Windows 98  should also work, but has not been thoroughly tested. Windows ME is not  supported. Linux is supported through [Lubi]("http://lubi.sourceforge.net/"). ***

Actually i have window 7 and i installed ubuntu within window7 using wubi only. So is it the reason for this issue?

---

### Post by oldfred on 2011-05-25
I have not used wubi, but we have seen many users with windows 7 with wubi. I just think you have to update windows BCD, in install is ok. BCD is same for Vista & Windows 7.

Download a liveCd and run this. It will show if you have wubi installed, but cannot parse windows's BCD to see if it is correct.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

