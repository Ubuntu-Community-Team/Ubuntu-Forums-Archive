---
title: "Problem after updating graphics card"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by hussiniraq on 2012-04-24
hello ..

Problem after updating graphics card 
type nvidia

Black screen at logon

Try not attributed by Failsafex

Shows this error 

[IMG]http://www.linuxac.org/forum/attachment.php?attachmentid=16753&d=1335249544[/IMG]

me ubuntu 10.04

---

### Post by raja.genupula on 2012-04-24
Latest drivers of this are broken , i dont know are they fixed or not . so up to they gonna have a fix you better to run with old drivers which ran fine in your PC .

---

### Post by hussiniraq on 2012-04-24
> **raja.genupula said:**
> Latest drivers of this are broken , i dont know are they fixed or not . so up to they gonna have a fix you better to run with old drivers which ran fine in your PC .

What solution specification a new personal computer

---

### Post by hussiniraq on 2012-04-24
up up up

---

### Post by papibe on 2012-04-24
Hi hussiniraq.

Did you upgrade from an Nvidia card to a new one of the same brand? or your previous card was something different?

Regards.

---

### Post by hussiniraq on 2012-04-24
> **papibe said:**
> Hi hussiniraq.

Did you upgrade from an Nvidia card to a new one of the same brand? or your previous card was something different?

Regards.

Both the definition of withdrawal from a company official nvidia

:cry::cry::cry:

---

### Post by papibe on 2012-04-24
Could you post the result of this commands?
```
lspci | grep -i vga

sudo lshw -C display

apt-cache policy nvidia-current
```
Regards.

---

### Post by hussiniraq on 2012-04-24
> **papibe said:**
> Could you post the result of this commands?
```
lspci | grep -i vga

sudo lshw -C display

apt-cache policy nvidia-current
```
Regards.
lspci | grep -i vga
[IMG]http://im29.gulfup.com/2012-04-24/1335275883851.jpg[/IMG]

[IMG]http://im29.gulfup.com/2012-04-24/1335275898452.jpg[/IMG]

===================
sudo lshw -C display

[IMG]http://im29.gulfup.com/2012-04-24/1335275900413.jpg[/IMG]

==================
apt-cache policy nvidia-current
[IMG]http://im29.gulfup.com/2012-04-24/1335275901104.jpg[/IMG]

[IMG]http://im29.gulfup.com/2012-04-24/1335275903895.jpg[/IMG]


With you I am aware of the inauguration of Type Definition i386

---

### Post by hussiniraq on 2012-04-24
up up up
:cry::cry::cry::cry::cry:

---

### Post by papibe on 2012-04-24
Try this:

Backup your configuration file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then recreate the file:
```
sudo nvidia-xconfig
```
Then restart your machine to see if it is fixed.
Regards.

---

### Post by Cavsfan on 2012-04-24
If that doesn't fix it, you could install the latest nVidia driver as I have: 295.33.
I have a Geforce  9800GT. 

I created this thread after I installed the driver. It has a link on how to install the driver and another one to a HOWTO
in this forum for installing the new driver into a new kernel when one gets installed.

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1948062_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948062")

On the how to install the driver, you'll want to print out step 4 through 8 and enter **telinit 3** before logging in at step 6.

When a new kernel is about to be installed you will want to enter 
**sudo apt-get update && sudo apt-get upgrade**
and 
**sudo apt-get update && sudo apt-get dist-upgrade**
Then you can watch for the word "success" when the kernel is installed.

This a better way to get your update any way. Better than Update Mangler.

It seems a bit daunting but, it should go OK if you follow the instructions.

[COLOR="Blue"]EDIT: The latest driver is 295.40 which was added 2012.04.11. I am going to install that myself.[/COLOR]

---

### Post by hussiniraq on 2012-04-24
> **papibe said:**
> Try this:

Backup your configuration file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then recreate the file:
```
sudo nvidia-xconfig
```
Then restart your machine to see if it is fixed.
Regards.

The same problem
[IMG]http://www.iraqup.com/up/20120424/k6J6N-X3oy_53254706.jpg[/IMG]



This is an image when you login

[IMG]http://www.iraqup.com/up/20120424/3UlfV-1jQ1_660692493.jpg[/IMG]

---

### Post by Cavsfan on 2012-04-24
Did you see my post above? That has fixed several problems I have had in the past.

---

### Post by hussiniraq on 2012-04-24
> **Cavsfan said:**
> Did you see my post above? That has fixed several problems I have had in the past.

no
Now I will snap the

---

### Post by Cavsfan on 2012-04-24
I just upgraded my driver to 295.40.
It gets easier once you have done it a few times. Now I will fix the other kernel as I mentioned in the 2nd post of that thread.

Just be sure to wait after you enter **telinit 3** as it takes a few seconds and then enter **login**.

---

### Post by Cavsfan on 2012-04-24
Edit: Make sure you add the script in the **HOWTO: Automatically update manually installed NVidia drivers after kernel updates**
Before you attempt the stuff below!

Also I have a text (gedit) document called **kernel cmds** with all of my kernels listed like this.
I keep only the last 2.

```
sudo apt-get purge linux-headers-2.6.32-39 linux-headers-2.6.32-39-generic linux-image-2.6.32-39-generic    - deleted
sudo apt-get install linux-headers-2.6.32-39 linux-headers-2.6.32-39-generic linux-image-2.6.32-39-generic

sudo apt-get purge linux-headers-2.6.32-40 linux-headers-2.6.32-40-generic linux-image-2.6.32-40-generic
sudo apt-get install linux-headers-2.6.32-40 linux-headers-2.6.32-40-generic linux-image-2.6.32-40-generic

sudo apt-get purge linux-headers-2.6.32-41 linux-headers-2.6.32-41-generic linux-image-2.6.32-41-generic
sudo apt-get install linux-headers-2.6.32-41 linux-headers-2.6.32-41-generic linux-image-2.6.32-41-generic linux-headers-generic linux-image-generic


Had to also install linux-headers-generic linux-image-generic after removing the latest kernel as it was removed when purged

```EDIT: This is to install the driver into the 2 kernels I have. The most recently installed kernel will be the one that is used at bootup, not the highest numbered one.
So, I have to remove and install 40 and then 41, so 41 is the current one.
Note that there are 2 additional files removed when you purge the current one, so make sure you install them after removing them.

---

### Post by Cavsfan on 2012-04-24
After you have installed the script **update-nvidia** as mentioned above, you can 
remove and re-install 1st the oldest kernel and then the newest kernel both before rebooting.

Then in the future you will just have to remove and replace the driver and update-nvidia files in /usr/src/
when you add a new driver.

---

### Post by hussiniraq on 2012-04-24
> **Cavsfan said:**
> Did you see my post above? That has fixed several problems I have had in the past.

[IMG]http://www.iraqup.com/up/20120424/PqGle-S615_965729942.jpg[/IMG]

???

---

### Post by hussiniraq on 2012-04-24
Tomorrow will try my Iraqi time now will go to sleep:p

---

### Post by Cavsfan on 2012-04-24
> **hussiniraq said:**
> Tomorrow will try my Iraqi time now will go to sleep:p

Good! Just make sure you read all the above comments. You should be good to go. I just updated the driver and my 2 kernels.

---

### Post by Cavsfan on 2012-04-24
You must spell the driver exactly as it is with capitals and everything or else it won't work as above.

---

### Post by hussiniraq on 2012-04-25
> **Cavsfan said:**
> You must spell the driver exactly as it is with capitals and everything or else it won't work as above.

Applied and when all things appear the work of Restart 

[IMG]http://www.iraqup.com/up/20120425/P1db1-8WAm_290351714.jpg[/IMG]

[IMG]http://www.iraqup.com/up/20120425/ispP7-R8P5_753407520.jpg[/IMG]

---

### Post by Cavsfan on 2012-04-25
If you went by those instructions, there was no need to restart.
When you enter **sudo service gdm start**- step 8, it takes you  to the login screen.

Here is what you were supposed to do:
1) Download Newest Nvidia drivers from [[color=blue]_here._[/COLOR]](http://www.nvidia.com/Download/index.aspx?lang=en-us)
2) Open module blacklist as admin
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
Add these lines and save:
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```

3) Uninstall any previously installed Nvidia drivers:
```
sudo apt-get --purge remove nvidia-*
```

4) Reboot your computer

5) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
   (or if you have done this before and just want to install a newer driver, go into recovery mode and select exit to console)

6) Enter this to stop the x server and wait a minute or so for it to work:
```
telinit 3
```
6) Login and cd to the directory where you saved your file

7)Install drivers

```
sudo sh NVIDIA-Linux-x86_64-295.40.run
```
You will be asked several questions and you want to answer "yes" for each one.
(use the tab key to move the  selection)

8 ) Start GDM
```
sudo service gdm start
```

You will be taken to your normal login screen. Mission accomplished.

Then make sure you perform the steps in 
HOWTO: Automatically update manually installed NVidia drivers after kernel updates.
This was written by **sdennie** from this forum.

If you have done this before, you will just need to start at step 4.

---

### Post by hussiniraq on 2012-04-25
> **Cavsfan said:**
> If you went by those instructions, there was no need to restart.
When you enter **sudo service gdm start**- step 8, it takes you  to the login screen.

Here is what you were supposed to do:
1) Download Newest Nvidia drivers from [[color=blue]_here._[/COLOR]](http://www.nvidia.com/Download/index.aspx?lang=en-us)
2) Open module blacklist as admin
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
Add these lines and save:
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```

3) Uninstall any previously installed Nvidia drivers:
```
sudo apt-get --purge remove nvidia-*
```

4) Reboot your computer

5) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
   (or if you have done this before and just want to install a newer driver, go into recovery mode and select exit to console)

6) Enter this to stop the x server and wait a minute or so for it to work:
```
telinit 3
```
6) Login and cd to the directory where you saved your file

7)Install drivers

```
sudo sh NVIDIA-Linux-x86_64-295.40.run
```
You will be asked several questions and you want to answer "yes" for each one.
(use the tab key to move the  selection)

8 ) Start GDM
```
sudo service gdm start
```

You will be taken to your normal login screen. Mission accomplished.

Then make sure you perform the steps in 
HOWTO: Automatically update manually installed NVidia drivers after kernel updates.
This was written by **sdennie** from this forum.

If you have done this before, you will just need to start at step 4.

[IMG]http://im26.gulfup.com/2012-04-25/1335345632941.jpg[/IMG]

[IMG]http://im26.gulfup.com/2012-04-25/1335345632482.jpg[/IMG]

---

### Post by Cavsfan on 2012-04-25
I cannot read very much of that screenshot. Maybe you need to do a clean install of Ubuntu.
That would be my choice if you cannot accomplish the steps mentioned.

---

### Post by hussiniraq on 2012-04-25
> **Cavsfan said:**
> I cannot read very much of that screenshot. Maybe you need to do a clean install of Ubuntu.
That would be my choice if you cannot accomplish the steps mentioned.

Will re-install it again, but if the definition of new graphics card will be a problem due Aiza What solution do you think

---

### Post by Cavsfan on 2012-04-25
> **hussiniraq said:**
> Will re-install it again, but if the definition of new graphics card will be a problem due Aiza What solution do you think

Whatever nVidia card you have should not be a problem unless you are installing an older beta version of Ubuntu.

---

### Post by hussiniraq on 2012-04-25
> **Cavsfan said:**
> Whatever nVidia card you have should not be a problem unless you are installing an older beta version of Ubuntu.

I am now again you Ptthbt

I have a question i686 Does that mean 64

Now my own card designer on 64

---

### Post by Cavsfan on 2012-04-25
> **hussiniraq said:**
> 
I have a question i686 Does that mean 64

Now my own card designer on 64

Not sure what you are asking. 
It asks you when you download the driver and you should select from Linux 32 bit or Linux 64 bit.

The "_64" denotes it is the 64 bit version.

It depends on your machine.

---

### Post by hussiniraq on 2012-04-25
> **Cavsfan said:**
> Not sure what you are asking. 
It asks you when you download the driver and you should select from Linux 32 bit or Linux 64 bit.

The "_64" denotes it is the 64 bit version.

It depends on your machine.

How do I know that two or system that you install is 64 or 32

---

### Post by Cavsfan on 2012-04-25
> **hussiniraq said:**
> How do I know that two or system that you install is 64 or 32


In a terminal enter 
```
getconf LONG_BIT
```It will return 32 or 64.

---

### Post by hussiniraq on 2012-04-25
> **Cavsfan said:**
> In a terminal enter 
```
getconf LONG_BIT
```It will return 32 or 64.

Thank Tapetk me thank you again

---

