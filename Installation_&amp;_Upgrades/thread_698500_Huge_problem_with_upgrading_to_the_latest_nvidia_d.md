---
title: "Huge problem with upgrading to the latest nvidia driver"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by devix91 on 2008-02-16
I actually have 2 problems, one isn't that bad and the second one is really horrible.
   The not bad one is basically that every time i try to boot Ubuntu it ALWAYS first checks my hardrive, this happens even when i turn the PC off in a normal way, PLUS it takes at least 5 minutes. and after it is finished it reboots the PC and boots up again AND starts checking the hard drive again however once it is finished it doesn't reboot the PC but loads up the Linux. So it normally takes me like 20 minutes just to log in :D
   now the second problem is that i recently tried installing new nvidia driver, this is because in the synaptic the latest version of nvidia driver was not updated, and so i downloaded the driver from nvidia website, then tried installing it. The installation told me that i have to be in a command line and not running any other programs or something like that. And so i went to INIT 1. There i successfully installed the driver, then when the PC rebooted, i cried out loud :confused: because it automatically took me to this option box saying that i have to boot Linux in a low resolution mode, unfortunately when i press OK, so that the Linux would AT LEAST start in low res mode. The screen stayed black.
   At this very moment i have no idea about what to do :( erm... any suggestions ? Thank you for any response. Btw my Skype name is devix91, so if someone wanted to you could contact me there, since i am really desperate to get my Linux up and working again. Thank you

---

### Post by Partyboi2 on 2008-02-17
If you can get to a terminal when the screen goes blank (Ctrl+Alt+F2) reconfigure the xserver choosing nv as the video driver
```
sudo dpkg-reconfigure xserver-xorg
```then
```
startx
```hopefully this will allow you to get a working desktop.
If you can not get to a terminal try booting into recovery mode and reconfiguring the xserver from there.
What nvidia graphics card are you using?

---

### Post by devix91 on 2008-02-17
My graphics cards is NVIDIA GFORCE 8800GTS. And thank you for the tip, i am going to try it right now :) I really appreciate it.

---

### Post by zanak on 2008-02-17
hello, 
installing nvidia drivers is realy straithforward ! 
first download the driver from nvidia web site 
# wget [http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run)
(if you<r using the geforce 8800.)

then if you are allready using X, try to run , # telinit 3 ('cause you need to be in level 3 i gess)
then :

# chmod a+x DRIVER_PATH/Nvidia-wathever.xxx.x.run
# ./Nvidia-watherver.xxx.x.run

folow the instruction, and you'll get it  .

if for some reason it wont work, you can allways do 
sudo dpkg-reconfigure xserver-xorg

hope it helps

---

### Post by devix91 on 2008-02-17
Thank you zanak, I am really glad you tried to help me..... however everytime i type in "telinit 3" it takes me back to this message sayingthat it needs to run in low-res mode and when i click continue it takes me back to the blank screen, and then i simply cant do anything

---

### Post by Pumalite on 2008-02-17
Download appropriate driver from Nvidia.
Use a virtual Terminal:
Ctrl+Alt+F1
username
pasword
sudo /etc/init.d/gdm stop
sudo /path/to/driver/NVIDIA-Linux-x86-xxxx.run
Accept the license
Let the driver compile the module into your kernel
Let the driver reconfigure your xorg.conf file
Then: startx
Or:
sudo /etc/init.d/gdm start
Make sure you have build-essential installed
sudo aptitude install build-essential.

---

### Post by zanak on 2008-02-17
oh ok, so try telinit 1,
and then run the nvidia installer, it may tell you that you need to be in level 3, but it works good in level 1 to, so try that and let us know !

hope it helps

---

### Post by devix91 on 2008-02-17
Thank you for your help. Unfortunately I can't try it now, since My brother is on the PC now. I will have the time in about 30 mins. and i iwll tell you how it went after. By the way i know this is probably a really newbie-like quesiton but what exactly is the difference between INIT 1 and TELINIT 1. Thanks

EDIT -> Okay, i have just trid it, and it still doesn't work, after I installed the NVIDIA driver i made the Gnome Desktop Manager (GDM) Start and then i again got this window saying stuff about the low-res mode with the button (Configure, Quit, Start) If I click configure, then it no matter what i do doesnt find any of the hardware that i have anyway. If I click QUIT once again it takes me to the pitch black screen and finally the continue button does the same.
   Do you think that this problem could b caused because my Monitor is windscreen? and the linux can't find a suitable resolution and something goes wrong after that ? Thank you

---

### Post by devix91 on 2008-02-18
One more thing, If i type in startx and execute it, it gives me these errors, that it failed to initialize NVIDIA.

---

### Post by zanak on 2008-02-18
okey it seems strange !

have you installed the right driver for the nvidea ?  do you have build-essential installed ?

try to make an update then an upgrade (sudo apt-get update, then sudo apt-get upgrade)

---

### Post by devix91 on 2008-02-19
Thank you all :guitar:
   Unfortunately my linux won't even work in recovery mode now :lolflag:
So I am just going to completely reinstall my Ubuntu and stick to the drivers that I can download from the Synaptic Application Manager.
   Also I am sorry that you had to waste your time with helping me out even though it ended like this.
So thank you for your help :D cya

---

### Post by Whiffle on 2008-02-19
Sounds to me like the nvidia kernel module isn't loading...

try lsmod in a terminal (ctrl + alt +f2) and see if nvidia is listed there.  


Its also possible that its loading but loading the wrong one, which is why if you install the nvidia drivers wit hthe nvidia installer you have to remove any ubuntu nvidia packages

---

