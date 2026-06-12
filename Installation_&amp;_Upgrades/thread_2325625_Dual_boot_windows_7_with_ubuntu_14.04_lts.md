---
title: "Dual boot windows 7 with ubuntu 14.04 lts"
date: 2016-05-24
forum: Installation &amp; Upgrades
---

### Post by fin4 on 2016-05-24
I just install Ubuntu 14.04 lts on W7 using my hp(nokia) as flashdisk ,when I running boot order first than stuck long, how this, whether I have waiting or what? please helpme I want dual boot?

---

### Post by QIII on 2016-05-24
Hello!

Your post is almost impossible to understand.  Is English your first language?  If not, let me know what is and I will try to get you directed to where you can get help in your native tongue.  

We would love to help, but if there is a language barrier we may not do much more that cause you frustration.

Cheers!

---

### Post by fin4 on 2016-05-24
Yes, 
how make dual boot 32bit windows 7 with ubuntu 14.04,but using flashdisk hp device as flashdisk it. It is can?

---

### Post by yancek on 2016-05-24
If you already have windows 7 installed and want to install Ubuntu 14.04, first did you download Ubuntu from the official site?  Did you verify the download of the iso file was good by doing an md5 checksum?  How did you get the Ubuntu iso file on the flash drive, which software did you use to do this?  Or have you actually gone through the installation process andare now unable to boot?

---

### Post by grahammechanical on 2016-05-24
When we install Ubuntu to dual boot with Windows we see a boot menu that lists both Ubuntu and Windows bootloader. That menu will stay on the screen for 10 seconds and then load the operating system that is at the top of the menu. Ubuntu is usually at the top of the menu. We can cancel the 10 second delay by selecting an operating system to load and then pressing Enter. Ubuntu should load in less than 20 seconds. 

Do you see a boot menu? At the top it will have the word Grub. What happens when you select Windows to load? Does it load? What happens when you select Ubuntu to load? Does it load?

Do you want to use a Nokia phone as a storage device to put the Ubuntu  installer on? I do not think that is possible. We can Drag and Drop  files from a phone onto a desktop operating system but that is not the  way to install Ubuntu onto the desktop machine to dual boot with  Windows.

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

[http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Ubuntu 14.04 is supported until April 2019. The latest release of Ubuntu is 16.04 (supported until April 2021). That is why the instructions mention Ubuntu 16.04 and not 14.04 but the instructions apply to both Ubuntu 16.04 and 14.04.

Regards.

---

### Post by oldfred on 2016-05-24
Almost all Windows 7 systems use all 4 primary partitions.
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360) 

Only use Windows own disk tools to shrink the main NTFS partition, but not to create new partitions.
And reboot into Windows immediately so it can run chkdks.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) 
      
 Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by fin4 on 2016-05-24
[COLOR=#000000]At the top it will have the word Grub.  >> nothing. but I select f9->boot menu->usb HHD

What happens when you select Windows to load?  >> normal

Does it load? >> yes it is,

What happens when you select Ubuntu to load?the first it's normal like os windows7 loading select menu try ubuntu,install ubunut...help less more like that

 Does it load? yes it is, but after I select install ubuntu on menu ubuntu,than it's loading so long. "this problem,why ask here"

[/COLOR][COLOR=#000000]Do you want to use a Nokia phone as a storage device to put the Ubuntu installer on? I do not think that is possible. We can Drag and Drop files from a phone onto a desktop operating system but that is not the way to install Ubuntu onto the desktop machine to dual boot with Windows. >>the  last there is someone  here that my mean, what my ask "[/COLOR][COLOR=#000000]use a Nokia phone as a storage device to put the Ubuntu installer on", yes ,my phone use as bootable UUI/rufus,


Regards[/COLOR]

---

### Post by fin4 on 2016-05-24
> **grahammechanical said:**
> When we install Ubuntu to dual boot with Windows we see a boot menu that lists both Ubuntu and Windows bootloader. That menu will stay on the screen for 10 seconds and then load the operating system that is at the top of the menu. Ubuntu is usually at the top of the menu. We can cancel the 10 second delay by selecting an operating system to load and then pressing Enter. Ubuntu should load in less than 20 seconds. 

Do you see a boot menu? At the top it will have the word Grub. What happens when you select Windows to load? Does it load? What happens when you select Ubuntu to load? Does it load?

Do you want to use a Nokia phone as a storage device to put the Ubuntu  installer on? I do not think that is possible. We can Drag and Drop  files from a phone onto a desktop operating system but that is not the  way to install Ubuntu onto the desktop machine to dual boot with  Windows.

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

[http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Ubuntu 14.04 is supported until April 2019. The latest release of Ubuntu is 16.04 (supported until April 2021). That is why the instructions mention Ubuntu 16.04 and not 14.04 but the instructions apply to both Ubuntu 16.04 and 14.04.

Regards.


[COLOR=#000000][COLOR=#000000]At the top it will have the word Grub. >> nothing. but I select f9->boot menu->usb HHD

What happens when you select Windows to load? >> normal

Does it load? >> yes it is,

What happens when you select Ubuntu to load?the first it's normal like os windows7 loading select menu try ubuntu,install ubunut...help less more like that

Does it load? yes it is, but after I select install ubuntu on menu ubuntu,than it's loading so long. "this problem,why ask here"

[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]Do you want to use a Nokia phone as a storage device to put the Ubuntu installer on? I do not think that is possible. We can Drag and Drop files from a phone onto a desktop operating system but that is not the way to install Ubuntu onto the desktop machine to dual boot with Windows. >>the last there is someone here that my mean, what my ask "[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]use a Nokia phone as a storage device to put the Ubuntu installer on", yes ,my phone use as bootable UUI/rufus,


Regards[/COLOR][/COLOR]

---

