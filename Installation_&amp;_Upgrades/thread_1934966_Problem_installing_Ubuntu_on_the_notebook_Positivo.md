---
title: "Problem installing Ubuntu on the notebook Positivo"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by brunocarletti on 2012-03-03
Guys, I'm new here on the forum and wanted your help. I'm trying to install Ubuntu on my notebook Positivo, as did the distribution of HD, 300 Gb left for windows 7  and 200 Gb Ubuntu. When I go to install ubuntu CD runs good, but when I put to install, go to is a black screen with blinking cursor, and not out of it, so I left about 10 minutes and nothing, anyone have any idea what may be?

specifications of my notebook:


Positivo E4121
Chipset : Intel Ibex Peak-M HM55, Intel Arrandale
Processor: Intel Core i3 M380, 2.53 GHz
memory : 4 GB DDR3
Type of Bios : Phoenix
(HD): Hitachi HTSS455050B9A300 ATA Device(500 GB, 5400 RPM, SATA-II)
Optical Driver: tsst corp CDDVDW TS-L633C ATA Device
Video : Intel (HD) Graphics, DirectX 11.0

---

### Post by lovinglinux on 2012-03-03
Bem vindo ao fórum.

Instead of clicking to install, click "Try Ubuntu" and let it load the desktop. Once the desktop is loaded, you will see an icon in the desktop to install Ubuntu. Click it and report if there is any change.

You should see a series of dialogs asking for various informations, including the installation location.

---

### Post by brunocarletti on 2012-03-03
I click in "Try Ubuntu", but don't happen nothing, it's the same problem!

---

### Post by lovinglinux on 2012-03-03
> **brunocarletti said:**
> I click in "Try Ubuntu", but don't happen nothing, it's the same problem!

So it could some hardware incompatibility or CD defect.

Is this a new computer? Does it have a recover partition that allows to re-install Windows? Can you afford losing the data on this machine?

I am asking this stuff, just to know how far we can go.

You could try Wubi, which allows you to install Ubuntu inside Windows, without messing with your partitions. If it doesn't work, then you can simply remove it through Windows uninstallation feature.

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

If Wubi works, then you could have success with the alternate CD, instead of the LiveCD. There are some special installation commands that could help solving the problem. Additionally, the alternate CD is recommended when cannot run the graphical environment. However, we need to be careful, because we don't even know yet if Ubuntu will run on your machine. So Wubi would be a good way to make sure of that.

---

### Post by brunocarletti on 2012-03-03
My computer have 1 year, i can't lise nothing, because i don't have one way to save all. I have partition, the windows I put 300 GB, and leave 200 GB to linux. 

I will install the wubi and write here the result. Thanks for now.

---

### Post by lovinglinux on 2012-03-03
> **brunocarletti said:**
> My computer have 1 year, i can't lise nothing, because i don't have one way to save all. I have partition, the windows I put 300 GB, and leave 200 GB to linux. 

I will install the wubi and write here the result. Thanks for now.

That's the safest way then. Let us know if you succeed or not.

---

### Post by brunocarletti on 2012-03-03
I try twice time install using Wubi, but it does not work again. When finish install, appers error: Invalid argument.
And say to me see the log in c:\users\bruno\appdata\local\temp\wubi-11.10-rev245.log
The log says:

PS: This i use the ubuntu for 64bits:

03-03 15:36 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 202, in copy_file
IOError: [Errno 22] Invalid argument
03-03 15:36 DEBUG  TaskList: # Cancelling tasklist
03-03 15:36 DEBUG  TaskList: New task check_iso

03-03 15:36 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 202, in copy_file
IOError: [Errno 22] Invalid argument
03-03 15:36 ERROR  TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 589, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 568, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
03-03 15:36 DEBUG  TaskList: # Cancelling tasklist
03-03 15:36 DEBUG  TaskList: # Finished tasklist


When I try install using the ubuntu to 32bits, appers other error, that say "WindowsBackend" object has no attribute "iso_path'":

The log of this:

03-03 15:48 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (c396dd0f97bd122691bdb92d7e68fde5 != f986020c265f7b9228169f9be7b65985)
None
03-03 15:48 DEBUG  TaskList: ### Finished check_iso
03-03 15:48 ERROR  TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 589, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 568, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
03-03 15:48 DEBUG  TaskList: # Cancelling tasklist
03-03 15:48 DEBUG  TaskList: # Finished tasklist
03-03 15:48 ERROR  root: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 589, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 568, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'

What i have to do now? :/

---

### Post by lovinglinux on 2012-03-03
I am not sure, but I think it could be an issue reading/writing to disk because of the IO error and the md5 error.

Download the beta version of Ubuntu 12.04, burn a CD and try to load the LiveCD, without installing.


[http://ubuntu.mirror.pop-sc.rnp.br/mirror/ubuntu-releases/precise/](http://ubuntu.mirror.pop-sc.rnp.br/mirror/ubuntu-releases/precise/)

---

### Post by lovinglinux on 2012-03-03
Moved to the Installation & Upgrades sub forum.

---

### Post by brunocarletti on 2012-03-03
Ok. Thanks for now, I will buy one CD to burning and try this again, if the problem continue, I return.

:D

---

### Post by lovinglinux on 2012-03-03
> **brunocarletti said:**
> Ok. Thanks for now, I will buy one CD to burning and try this again, if the problem continue, I return.

:D

Instead of doing that, try this:

Boot from the CD you have, when you see a small keyboard and a human at the bottom, hit "e", then select the language, then hit F6 to bring additional options and select "nomodeset", then  hit ESC. Then click the option to install Ubuntu.

---

### Post by epichacker1 on 2012-03-03
You should, again, try to get a new CD and install from there, there could be some problems with the files burned to your disc. If it works, you might want to try the something else option, click add, then set the size to about 204800 MB (there are 1024 MB in a GB). Then, select a root directory from the list (/), and finish installing. You may want to make another partition for swap space, which is what Ubuntu refers to if there is no more memory (RAM) available.
 
(Do not click New Partition Table it erases all partitions left for other OSes.)

---

### Post by brunocarletti on 2012-03-03
I have to download "Desktop CD" or "Server install CD"?

---

### Post by epichacker1 on 2012-03-03
For starting, get the Desktop one.

---

### Post by epichacker1 on 2012-03-03
(I would also get 64 bit)

---

### Post by lovinglinux on 2012-03-03
Have you tried the "nomodeset" suggestion?

After hitting "e" you can also test the CD to check if there is any error, instead of installing.

---

### Post by epichacker1 on 2012-03-03
Yes, that would be faster and more efficient than getting a new CD, and if the installation did not work properly.

---

### Post by brunocarletti on 2012-03-03
Yes, i tried 'nomodeset", and it not work. :/, I will download what you say to see what happens!, I don't try see in the Menu if CD have error, i will see this now and write here what appers. Thanks for now!

---

### Post by brunocarletti on 2012-03-03
I thing i go give up of this. I try do what you say, i put to see if have error in CD at the menu next choice the language, ad the same thing happens,  go to is a black screen with blinking cursor. I will download 12.04 BETA and try to see. Does you have other exit? Thanks for now.

---

### Post by lovinglinux on 2012-03-03
> **brunocarletti said:**
> I thing i go give up of this. I try do what you say, i put to see if have error in CD at the menu next choice the language, ad the same thing happens,  go to is a black screen with blinking cursor. I will download 12.04 BETA and try to see. Does you have other exit? Thanks for now.

Unfortunately no. But I am not an expert on the subject. To be honest, the main reason why your thread got my attention is because I am also from Brazil and I was curious about Positivo notebooks. I just bought a new notebook, but from Asus, because I was afraid of buying from Positivo or CCE.

Anyway, I suspect Ubuntu is not detecting the notebook hard drive properly. Perhaps you could try to load Ubuntu from an external disk, like a USB stick.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I have no experience with that either, but sounds like a possible workaround, if the problem is indeed the HD.

---

### Post by brunocarletti on 2012-03-03
I will try it, but, how I do to computer read from USB flash driver?

---

### Post by brunocarletti on 2012-03-03
Oh man,  Thanks very much!, I install the ubuntu in my pen driver and it's work very good!, I install the ubuntu 11.10 with anyone problem!, Thanks Very much! :D

---

### Post by lovinglinux on 2012-03-04
> **brunocarletti said:**
> Oh man,  Thanks very much!, I install the ubuntu in my pen driver and it's work very good!, I install the ubuntu 11.10 with anyone problem!, Thanks Very much! :D

Great. Now, install Gparted from Software Center and check if it can detect your hard drive. If yes, you could try to split your free partition in 3, creating a swap partition , one for the root of your system (/) and one for your personal files (/home). 3 Gb for swap should do it, 30 Gb for root should be more than enough and the rest for home. Format root and home partitions as ext4. Then try to install from the USB. Select  the manual partitioning method. Set the swap, root and home partitions accordingly in the installation setup.

---

