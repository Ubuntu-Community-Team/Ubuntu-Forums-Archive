---
title: "Please help me!  Can't install driver!"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by Maww16 on 2007-12-06
I have been trying to research this problem for 3 days straight now.  I am VERY new to linux and I LOVE ubuntu 7.10 

Here is my problem.  I have a Nvidia GeForce Go 7950 GTX laptop video card.  I have installed Ubuntu 7.10 on my computer.  I have downloaded this driver > NVIDIA-Linux-x86_64-1.0-9755-pkg2.run from the Nvidia site.  I have learned how to stop the X server to enter console by typing in Terminal "sudo init 1".  I then type "sudo sh /home/matthew/NVIDIA-Linux-x86_64-1.0-9755-pkg2.run". 
YAY this is the furthest I have gotten in days!  But wait.  It comes up with this error.

You appear to be running in runlevel 1; this may cause problems.  For example:  some distributions that use devfs do not run the devfs daemon in runlevel 1, making it difficult for 'nvidia-installer' to correctly setup the kernel module configuration files.  It is recommended that you quit installation now and switch to runlevel 3 ('telinit 3') before installing.

I then quit the installation do as it says...try to enter init 3.  I type "telinit3" or "sudo init 3" (they both did the same) and they took me to my login screen as if I had just turned on my computer.  I log in thinking its something different and open terminal.  I type in "sudo sh /home/matthew/NVIDIA-Linux-x86_64-1.0-9755-pkg2.run" again in terminal and it says I'm running X server.  So I know that error was incorrect...So i go all the way back and instead of canceling the installation I proceed in "init 2" like I started.  the next error occurs though:

No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?)

So I'm in the army and deployed to Iraq right now...and to pass the time I mess around with computers.  Right now it's very hard to get on the internet ON MY LAPTOP.  But I can use a thumb drive on one of the internet cafe's computers and get the necessary kernel...or can i?  If this will fix my problem can anyone PLEASE tell me where to find this kernel.  

If that WON'T fix my problem...I clicked NO and continued.  This comes up:

No precompiled kernel interface was found to match your kernel; this means that the installer will need to compile a new kernel interface.

I click OK!

This comes up:

ERROR:  You do not appear to have libc header files installed on your system.  Please install your distribution's libc development package.

The only thing I can do from here is click OK which closes the installation.  :-(  I am very frustrated.  If THIS is my problem...does anyone know the solution?  I have no clue what a "libc header file" is.  I am stuck here.

Any help would be greatly appreciated.  
-Maww

---

### Post by Schalken on 2007-12-06
You're lucky I bothered to read enough of that to realise it was a simple question of "How do I install NVidia drivers?"

Don't bother using the drivers on nvidia's website. They work, they are just a bit complciated to install, and you have to reinstall them after you update your kernel.

This page should give you what you need: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

To summarise, you need to enable "Proprietary drivers for devices (restricted)" under System > Administration > Software Sources, then install the NVidia driver either by going to System > Administration > Restricted Drivers Manager and enabling it, or by installing nvidia-glx-new in System > Administration > Synaptic Package Manager or executing the command "sudo apt-get install nvidia-glx-new" in a terminal.

---

### Post by Maww16 on 2007-12-06
I'm going to try that right now...thanks so much for responding quickly...I'll repost in a minute to say whether it works or not.

---

### Post by Maww16 on 2007-12-06
> **Schalken said:**
> You're lucky I bothered to read enough of that to realise it was a simple question of "How do I install NVidia drivers?"

Don't bother using the drivers on nvidia's website. They work, they are just a bit complciated to install, and you have to reinstall them after you update your kernel.

This page should give you what you need: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

To summarise, you need to enable "Proprietary drivers for devices (restricted)" under System > Administration > Software Sources, then install the NVidia driver either by going to System > Administration > Restricted Drivers Manager and enabling it, or by installing nvidia-glx-new in System > Administration > Synaptic Package Manager or executing the command "sudo apt-get install nvidia-glx-new" in a terminal.

I don't have Restricted Drivers Manager.  Amongst all my messing around I might have uninstalled it...accidentally.  How can it be reinstalled.  

Oh...the other 2 methods you told me to do didn't work.  Synaptic didn't even have nvidia-glx-new on the list and the command gave me the same error as Synaptic.

Anymore help would be GREATLY appreciated. 
-Maww

---

### Post by sdhog2002 on 2007-12-06
Try this:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Maww16 on 2007-12-06
> **sdhog2002 said:**
> Try this:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

As I said before I'm in Iraq and cannot get on the internet directly through my laptop.  I've been using a thumb drive with a internet cafe computer.  I need a solution that doesn't require a "Magical" program that connects to the internet.  Eventually I can try Envy but not now.
Thanks for the suggestion though...I'll use it later if nothing else works.

Anyone else?

---

### Post by Maww16 on 2007-12-06
I'm going to try a fresh start and reinstall ubuntu.  I'm apparently going to need to get my laptop on the internet. 
I'll post again after that's happened.

---

### Post by JangMunho on 2007-12-06
It seems that nvidia driver cannot install under init 1.
If you wanna get rid of X server and install the driver, you should just press Ctrl+Alt+F2, and use "sudo /etc/init.d/gdm stop" command to stop gnome instead of init command.

Init 1 is used when there is serous problem on your system and you must fix it without any unnecessary services. The driver installer may need init 3.

---

### Post by Maww16 on 2007-12-07
Problem SOLVED!
I was forced to reinstall ubuntu due to the fact that I had removed the Restricted Drivers Manager!
But that alone wouldn't have fixed my problem!
Lesson of the day:  If your video card doesn't work...FIRST enable Proprietary drivers for devices (restricted) in Software Sources found in SYSTEM > ADMINISTRATION menu.
Thank you Shalken!  My problem was in Software Sources!
Hope this helps someone else.

---

### Post by bbaalloonn on 2007-12-07
"Ctrl+Alt+F2"  AND "sudo /etc/init.d/gdm stop" 
that works for me to get rid of x server.
thanks JangMunho :)

i can enable desktop effect now, yay!!

here's how i install nvidia driver (NVIDIA-Linux-x86-100.14.19-pkg1.run) in my pc (os ubuntu 7.04):
1. download driver from nvidia website
2. open terminal type in "sudo /etc/init.d/gdm stop" (only black screen with text appeared)
3. press "Ctrl+Alt+F2"
4. type in " sudo sh/ home/bbaalloonn/Desktop/NVIDIA-Linux-x86-100.14.19-pkg1.run" (sudo sh/ *path and name of the driver downloaded before*)
5. then the programme will run itself, just click "yes" or "ok" or something like, when it asked for license agreement or download dependencies or starting computer in xserver
6. type in " sudo reboot" to reboot back to graphical screen

that's how i install nvidia driver, hopes it'll help

---

