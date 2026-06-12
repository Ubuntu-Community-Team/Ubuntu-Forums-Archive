---
title: "Ubuntu Black scren"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by Danlatch on 2008-03-27
Ok
Compaq Persario laptop F557US
1.8 MHz Processor Mobile Sempron 3500+
90 Gib HD all  Ubuntu 6.10
VRAM 32 MB
32 bit Operating system
Nvidia "pure video" graphics
Windows Vista Basic came with the computer but is gone now.

This disc is "Ubuntu" version 6.10 that came with the Ubuntu Linux for Dummies book by Paul S. Sery.

The Live disc will run if I select the 1024x whatever 16 bit graphics  but won't if I let it boot on its own.

The computer will not finish booting form the hard drive after I did the install.  It goes through the splash screen with the logo and then goes black with no CD or HD action.
I can't seem to find how to adjust the display settings with the command line as I am a total noob.

QUESTION:  How do I adjust the display proprieties from the command line for Ubuntu 6.10

---

### Post by lawentzel on 2008-03-27
Does it get you to your login screen?  If so, you can select to boot to terminal I think.  If not, booting off of the CD you got, should have an option to drop to a terminal prompt.  Then you will want to type the following:

sudo dpkg-reconfigure xserver-xorg

It will ask you for your password.  Enter it.  At that point, you should be able to select a lower resolution to boot up to.  The black screen is due to one of two things.  Linux is setting your screen resolution too high, or it is setting it to a frequency your monitor can't handle.  So, take a look at these two things.  I found this answer by looking up "x-server Ubuntu" on Google.  X-Server is the "Windows" environment which Linux runs.  (Unix and Mac uses it as well.)

Good Luck.

---

### Post by Danlatch on 2008-03-27
OK!  Up and ready to go.  Thanks.  Have not touched a command line since the days of DOS.

I am now a recovering Windows user and it feels good.  It will need some work as all my printer/scanner and wireless stuff needs to be brought on board but it is good to have that Vista thing gone.

:)

---

### Post by Danlatch on 2008-03-28
Hmmm....
I did as instructed and  I thought the issue was done.  Now I restart this morning and black screen again.

When I did the "install nvidia-glx-new" command it told me that it could not get the driver so I did "nvidia-glx" and that it found.  I set the screen resolution to the 50Hz 1024x768 and did the reboot.

I can get the command line but the GNOME just won't start.

Thanks for taking the time.

-a noob

---

### Post by Danlatch on 2008-03-29
OK see if this can be done.  I am on the live desktop with the Nvidia driver on the "desktop"

I can't install it becase I cant be 'root' in this mode.

so I have tried . . .

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo apt-get install Nvidia-linux-x86-169.12-pkg.run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Nvidia-linux-x86-169.12-pkg.run
ubuntu@ubuntu:~$ sudo install Nvidia-linux-x86-169.12-pkg.run
install: missing destination file operand after `Nvidia-linux-x86-169.12-pkg.run


I am missing something?

---

### Post by PmDematagoda on 2008-03-29
Actually apt-get is only used to install packages on repositories not binary files on the hard drive.

What you need to do is:-

1) First kill the X-Server with:-
```
sudo /etc/init.d/gdm stop
```

2) Uninstall the nvidia package:-
```
sudo apt-get remove --purge nvidia-glx
```

3) Run the Nvidia installer by:-

1. Moving to the Desktop directory:-
```
cd ~/Desktop
```

2. Executing the installer:-
```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```

---

### Post by Danlatch on 2008-03-30
OK here is the result . . . 

```

ubuntu@ubuntu:~$ sudo /etc/init.d/gdm stop
 * Stopping GNOME Display Manager...                                     [ ok ] 
ubuntu@ubuntu:~$ sudo apt-get remove --purge nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ cd ~/Desktop
ubuntu@ubuntu:~/Desktop$ sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 169.12............................................................................................................................................................................................................................................................................................

```
This pops up in another screen:
```

ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com.

```
then it gives me the prompt again
```

ubuntu@ubuntu:~/Desktop$ 

```
:confused:
After this I think my next project should be a basic Unix course. Thanks for the help everybody.
Edit: Running from "Live" CD, If I should be using the command line from the installed version please let me know.

---

### Post by Danlatch on 2008-03-30
OK I got the Nvidia-glx out by using the command line on the installed version.
The Nvidia driver is on a USB key I have plugged in.
I am now at a
Root@willer-laptop:~#

---

### Post by Danlatch on 2008-03-30
Any suggestions?  I'm going to have to reinstall Vista if I cant get it up and running soon.  Would Fedora Core have the same issues?:confused:

---

### Post by PmDematagoda on 2008-03-30
> **Danlatch said:**
> Any suggestions?  I'm going to have to reinstall Vista if I cant get it up and running soon.  Would Fedora Core have the same issues?:confused:

First boot Ubuntu in Recovery Mode, that can help.

And then navigate into the USB drive through the /media folder, you should be able to see the folder that corresponds to the USB's name, move into that and then execute the Nvidia driver installer.

---

### Post by Danlatch on 2008-04-01
Thanks for the effort.  It just won't work and now it is not even booting in recovery mode.  Next computer I get I will have it built around a Linux OS but for now I need to get back up and running so I can do my work at home.  I'll play with the live CD until I figure out what I am doing.  I think a "teach yourself" this in 21 days book is in order.

Again, thanks for the help and all the best.  One of these days school children will be amazed to discover that there was a time when Microsoft wasn't a soft drink company.  ;)

---

### Post by PmDematagoda on 2008-04-02
If you are still willing to try, could you please provide some specifics as to where Ubuntu stops booting up through Recovery Mode?

---

### Post by jecker on 2008-04-09
Also post this log file /var/log/Xorg.0.log

---

