---
title: "Feist and Gutsy not working with ATI X1400"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by nabeelfa on 2007-09-28
I posted this issue here: [http://ubuntuforums.org/showthread.php?t=560861](http://ubuntuforums.org/showthread.php?t=560861)
I am working now on Kubuntu Dapper live CD and viewing the Forums with its browser, I faced an issue with the Feisty, and a professional friend tried really hard to help me with my major issue with the Feisty. The ATI Mobility Radeon X1400 is not working with the Feisty Distro!!, and they Kubuntu forum recommended me to use the Alpha distro of Gutsy and uptill today its not working at all!!! the Live CD is not launching at all!!! tried all the support messages and not working!!!. I just need to notify the developers of the new distro before the last and final release to be on the distro line!!! this is really bad point and a disappointing issue!!

---

### Post by Pumalite on 2007-09-28
Ask ATI. They should be supporting Linux. And all of you future linux users: vote with your pocket, buy only NVIDIA.

---

### Post by nabeelfa on 2007-09-29
> **Pumalite said:**
> Ask ATI. They should be supporting Linux. And all of you future linux users: vote with your pocket, but only NVIDIA.

Well, ATI already supporting Linux cuz it worked on Dapper - the older distro - so I think the problem is within the developer of the Feisty & Gutsy.......

---

### Post by Pumalite on 2007-09-29
Lets see how you do with this:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by nabeelfa on 2007-09-30
> **Pumalite said:**
> Lets see how you do with this:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

OK, but why the developers didn't add it from the begining?? they should do it as per as the old version - Dapper - and it works great on the Dapper......

---

### Post by Pumalite on 2007-09-30
Good. You read my link.

---

### Post by nabeelfa on 2007-10-01
> **Pumalite said:**
> Good. You read my link.

at the above mentioned website there is Notes:
"The above drivers support English only. 
The display driver requires POSIX shared memory to be enabled on the system. 
Kernel Source package is no longer required if Kernel Header package is installed."
 What is Kernel Source package is no longer required if Kernel Header package is installed????

---

### Post by nabeelfa on 2007-10-02
This is a solution from [http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/](http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/) 
and I listed it on [http://kubuntuforums.net/forums/index.php?topic=3086249](http://kubuntuforums.net/forums/index.php?topic=3086249)

[I]Many people are having problems installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards. This is caused by this bug that unfortunately could not fixed before the release of Ubuntu 7.04.

This quick guide will get Feisty installed and X.org 7.2 up and running.

Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu. 
Start text mode installer and install Ubuntu/Kubuntu. 
Finish Install and reboot. 
Update package list and upgrade any packages needed.
sudo apt-get update
sudo apt-get dist-upgrade 
Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx 
Update loaded modules.
sudo depmod -a 
Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv 
Reboot 
Ubuntu 7.04 should now boot into GDM/KDM.[/I]

worked for me !!!!!!!!!!!

---

### Post by MozartlovesUbun2 on 2007-10-24
how to install gutsy on a ati x1400 pc?

are there any step by step guides

---

### Post by NOSintake on 2007-10-24
i would like to know the same

---

### Post by Pumalite on 2007-10-24
Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
Start text mode installer and install Ubuntu/Kubuntu.
Finish Install and reboot.
Update package list and upgrade any packages needed.
sudo apt-get update
sudo apt-get dist-upgrade
Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx
Update loaded modules.
sudo depmod -a
Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot
Ubuntu 7.10 should now boot into GDM/KDM.

---

### Post by NOSintake on 2007-10-24
well, i got it working, but when i go to get compiz working, it says the "composite extension is not available"

---

### Post by joop! on 2007-10-25
> **NOSintake said:**
> well, i got it working, but when i go to get compiz working, it says the "composite extension is not available"


install xgl (libglitz-glx1, libglitz1 & xserver-xgl)

That should do

---

### Post by diskotek on 2007-10-26
i also would like to know about gutsy and ati x*** cards.
the one for feisty fawn works flawless but not for gutsy (as i tried).

---

### Post by diskotek on 2007-10-28
> **diskotek said:**
> i also would like to know about gutsy and ati x*** cards.
the one for feisty fawn works flawless but not for gutsy (as i tried).

i'm still dealing with gutsy!, and well stil looking for a solution.. i didn't quit yet (however i re-installed feisty)...

---

### Post by jack handy on 2007-10-28
will the new driver be added to the update manager someday so that i dont have to mess up my systems by installing them manually?

---

### Post by [@lex] on 2007-10-31
I have ubuntu 7.10, on a Dell Inspirion 6400, Intel Core 2 Duo T7200, 2 GB RAM, 120 GB HDD, Radeon x1400 video card.

Same problem, the OS works, but I can't change the resolution or graphics effects intenisty, not mentioning the lack of support for wireless LAN.

I tried to install this driver:

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

and this driver:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

(I think they are the same thing, but, just to be sure)

After I download the driver and try to install it, the following text appears in gedit:

"Could not open the file /home/alexandru/Desktop/…-8.42.3-x86.x86_64(2).run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
"

Regarding character coding, I have the following options:

1. Current Locale (UTF-8 )
2. Western (ISO-8859-15)
3. Add or Remove (with which, I can add various different character coding)

As a result, which character coding I should use ?

I really want to see some compiz fusion graphic capabilities.

Thanks in advance,

Alex

---

### Post by amd-64 on 2008-01-01
> **'[@lex] said:**
> 
After I download the driver and try to install it, the following text appears in gedit:

"Could not open the file /home/alexandru/Desktop/…-8.42.3-x86.x86_64(2).run.


The driver is downloaded as a bin file that needs to have executable flag in order to install to install. 

sudo chmod a+x /home/alexandru/Desktop/…-8.42.3-x86.x86_64(2).run

and then run the file from the command line
/home/alexandru/Desktop/…-8.42.3-x86.x86_64(2).run

---

