---
title: "How do you create a bootable Windows 8 USB from Ubuntu?"
date: 2014-07-31
forum: Installation &amp; Upgrades
---

### Post by zuffazen on 2014-07-31
I have tried several tutorials, including ones like this - [http://www.plop.at/en/winusbinstall.html](http://www.plop.at/en/winusbinstall.html)

Nothing works, the usb will not boot from any of my computers which include BIOS and UEFI.

Tutorials that say to use winusb will not work because I the site that hosted winusb is no longer maintained.

I have stack overflow methods but it still will not boot.

I would just create the usb stick from Windows but my windows machine needs repair.

---

### Post by Mark Phelps on 2014-07-31
Not sure what you mean by "bootable Windows 8 USB".  

If you mean a LiveUSB of Windows 8, that you can use much the same as you use LiveUSBs of Linux distros, that can't be done.  Win8 does support something they call WindowsToGo, but that is only the Enterprise edition of Windows 8 and is not LEGALLY available to individuals.

If you mean a USB INSTALLER of Windows 8, as in, a USB stick containing the windows installer, that tutorial should work, so I have to ask, WHAT are you using as the source for the Win8 installer? Win8 install DVD? Downloaded Win8 ISO file?

---

### Post by zuffazen on 2014-07-31
I'm not sure how you don't understand what a bootable usb stick with windows 8 is. If you referred to my link in the post you would see the process I am referring to - [http://www.plop.at/en/winusbinstall.html](http://www.plop.at/en/winusbinstall.html)

It is possible to do it as there are many discussions out there. I have a backup of my own iso and legal key that I paid money for when I bought my computer. I have installed Windows to my box using a bootable usb stick that I've created in Windows. Windows has a tool that they made just so you can do this, [http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool](http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool) so I'm not sure what you are on about.

I need to make USB stick, that I can boot from, that has the Windows 8 installed so I can re-install windows 8 on my computer. It's not complicated at all from Windows but it's a huge hassle to do this from Linux. How do I do this, the tutorials I have referenced DO NOT WORK.

---

### Post by uRock on 2014-07-31
You may want to try the advice given here. [http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu](http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu)

Which version of Ubuntu are you using for this?

If all else fails, burn your ISO to disk.

---

### Post by zuffazen on 2014-07-31
> **uRock said:**
> You may want to try the advice given here. [http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu](http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu)

Which version of Ubuntu are you using for this?

If all else fails, burn your ISO to disk.

I have tried this already. WinUSB is no longer maintained and the package doesn't exist. UNetbootin no longer allows you to 'select from all drives' meaning you can't select the usb via /dev/sdb1 anymore. Neither of these work.

---

### Post by uRock on 2014-07-31
Did you try the dd command offered in that link?

---

### Post by zuffazen on 2014-07-31
> **uRock said:**
> Did you try the dd command offered in that link?

dd is the incorrect method for doing a windows usb as it formats the drive.

Also I tried it.

---

### Post by uRock on 2014-07-31
What version of Ubuntu are you using? I just installed WinUSB by following the instructions on the page I linked.

---

### Post by Vladlenin5000 on 2014-07-31
> **zuffazen said:**
> (...) I have a backup of my own iso and legal key that I paid money for when I bought my computer. (...)

Still not clear enough (to me, at least) what you want to do... And your intended use is of utmost importance due to strict rules in this forum (let me add strict & necessary). Two options:

1. Have you bought a **generic Windows 8 license***? If so you're allowed to install and use it in whatever computer you want and later transfer to other computer provided you delete the first installation, ie, you can't use the same license in more than one machine at same time.

2. Was the Windows 8 preinstalled (**OEM license***)? If so you're allowed to reinstall as many times you need/want _in the exact same computer where it came and no other_.



* License of use, NOT ownership.


**PS - I will strongly recommend the mods to close your thread if you are attempting to use an OEM license in a different computer.**

---

### Post by zuffazen on 2014-07-31
> **uRock said:**
> What version of Ubuntu are you using? I just installed WinUSB by following the instructions on the page I linked.

Is yours launching a command lind or a gui version?

---

### Post by zuffazen on 2014-07-31
> **Vladlenin5000 said:**
> Still not clear enough (to me, at least) what you want to do... And your intended use is of utmost importance due to strict rules in this forum (let me add strict & necessary). Two options:

1. Have you bought a **generic Windows 8 license***? If so you're allowed to install and use it in whatever computer you want and later transfer to other computer provided you delete the first installation, ie, you can't use the same license in more than one machine at same time.

2. Was the Windows 8 preinstalled (**OEM license***)? If so you're allowed to reinstall as many times you need/want _in the exact same computer where it came and no other_.



* License of use, NOT ownership.


**PS - I will strongly recommend the mods to close your thread if you are attempting to use an OEM license in a different computer.**

I'm reinstalling windows to the same computer

---

### Post by uRock on 2014-07-31
Gui

---

### Post by uRock on 2014-07-31
> **zuffazen said:**
> dd is the incorrect method for doing a windows usb as it formats the drive.

Also I tried it.

For the record, WinUSB formats the external drive as well. I don't think you can get out of doing that.

---

### Post by zuffazen on 2014-07-31
> **uRock said:**
> For the record, WinUSB formats the external drive as well. I don't think you can get out of doing that.

dd won't format it correctly and add the mbr IIRC. 

I have the CLI version of WinUSB not sure how that happened.

---

### Post by uRock on 2014-07-31
I ran the following commands they had listed.```
sudo add-apt-repository ppa:colingille/freshlight
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/colingille-freshlight-trusty.list"
sudo apt-get update
sudo apt-get install winusb

```

---

### Post by uRock on 2014-07-31
Tested from beginning to end. I used it to put Windows 8.1 Professional on a USB and install it on my Netbook.

Let us know if you get it working.

---

### Post by zuffazen on 2014-08-01
> **uRock said:**
> Tested from beginning to end. I used it to put Windows 8.1 Professional on a USB and install it on my Netbook.

Let us know if you get it working.



Hi I did get it working, I did not see the Ubuntu 14.02 instructions on that post, I followed the wrong instructions.
I got Windows installed to a USB and it boots from my laptop. I will post later if it works on my desktop as well, which is where I need it to install.

My one question is what is the sed command doing that is making this work for Ubuntu 14?

---

### Post by oldfred on 2014-08-01
The ppa must not have a trusty version. And if 14.04 all your sources will refer to trusty. So you edit just that only line for the ppa to be the older version. If newer version comes along you should edit it back.

And if upgrading Ubuntu in future you must comment out or delete the ppa, as that will confuse update and cause it to not complete.

View Sources:
cat /etc/apt/sources.list

 # Edit Sources
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksu gedit /etc/apt/sources.list

---

