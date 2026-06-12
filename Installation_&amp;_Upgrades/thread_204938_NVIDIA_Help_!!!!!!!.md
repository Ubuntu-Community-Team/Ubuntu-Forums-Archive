---
title: "NVIDIA Help !!!!!!!"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by Culuntu on 2006-06-27
Hi this is my second post in ubuntuforums, i hope that someone will answer :) 

well i've got a problem with the nvidia driver
i downloaded it from nvidia.com , it's on the desktop now

i open the terminal : 
```
cd /home/romeo/Desktop
dir
sudo sh NVIDIA-Linux-x86-1.0-8762-pkg1.run
```

ok it begin to install and i receive this message : 

```
You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING
         THE NVIDIA DRIVER in the README available on the Linux driver
         download page at www.nvidia.com.
```

i know this subject has been many times posted! i've read them all ! :-k 

this link for example : [http://www.nvnews.net/vbulletin/showthread.php?t=39480]("http://www.nvnews.net/vbulletin/showthread.php?t=39480")

i have id:2:initdefault: instead of id:5:initdefault: and i can't modify it! ](*,) 

this one : [http://www.nvnews.net/vbulletin/showthread.php?t=29254]("http://www.nvnews.net/vbulletin/showthread.php?t=29254")

i can't login as root!!! :evil: 

this one : [http://www.linuxquestions.org/questions/showthread.php?t=250213]("http://www.linuxquestions.org/questions/showthread.php?t=250213")

> if the former do this:
1. press ctrl+alt+f2
2. login as root
3. type "killall kdm (or gdm)" without the quotes. this will stop x from running and bring you to the command line
4. press ctrl+alt+f2 again
5. install the nvidia driver, making changes to your xf86config-4 file in /etc/X11
6. when that is done, type kdm or gdm to get your login manager running again and you can login.
if it worked right (the nvidia driver) you should see the nice nvidia logo splash screen before your login manager starts up

if the latter do this:
1. logout of kde or gnome. this should drop you to a command line and x will be shut down
2. type su and give the root password
3. install the nvidia driver, making changes to your xf86config-4 file in /etc/X11
4. type exit to get out of su mode
5. type startx
if it worked right (the nvidia driver) you should see the nice nvidia logo splash screen before your gui loads up   

i cannot type su and put the root password !! and i don't know how to login as root      ](*,) ](*,) 

so guyz please help me 
if this might help i have NVIDIA GeForce 4 MX 440 AGP 8X
of course i'm on 32 intel :-|

---

### Post by rai4shu2 on 2006-06-27
The method in this howto is a little easier:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by knn on 2006-06-27
> **Culuntu]Hi this is my second post in ubuntuforums, i hope that someone will answer :) 

well i've got a problem with the nvidia driver
i downloaded it from nvidia.com , it's on the desktop now

i open the terminal : 
```
cd /home/romeo/Desktop
dir
sudo sh NVIDIA-Linux-x86-1.0-8762-pkg1.run
```

ok it begin to install and i receive this message : 

```
You appear to be running an X server said:**
> http://www.nvnews.net/vbulletin/showthread.php?t=39480[/URL]

i have id:2:initdefault: instead of id:5:initdefault: and i can't modify it! ](*,) 

this one : [http://www.nvnews.net/vbulletin/showthread.php?t=29254]("http://www.nvnews.net/vbulletin/showthread.php?t=29254")

i can't login as root!!! :evil: 

this one : [http://www.linuxquestions.org/questions/showthread.php?t=250213]("http://www.linuxquestions.org/questions/showthread.php?t=250213")



i cannot type su and put the root password !! and i don't know how to login as root      ](*,) ](*,) 

so guyz please help me 
if this might help i have NVIDIA GeForce 4 MX 440 AGP 8X
of course i'm on 32 intel :-|

Okay, let's do this step by step
You should install nvidia drivers from synaptic (System/Administration). The newest drivers are there. Open synaptic and search for nvidia-glx, then mark it (just nvidia-glx, leave the other matches alone), and when the program asks you about dependencies, just click ok. After synaptic is finished, log out and press ctrl-alt-backspace. This will restart the graphical system, and when it starts you should have 3d acceleration.

You should also install the kernel that best fits your system. In your case this should be linux-image-686. Also install linux-restricted-modules-686 and linux-headers-686.

Logging in as root is disabled in Ubuntu by default for a good reason. Use sudo instead. [Read this]("https://help.ubuntu.com/community/RootSudo")

Using init commands: these have to be prepended by sudo, since they require admin privileges. init 1 is single user, only root is available. Don't use it, since you don't have the password. init 2, 3, 4, 5 are identical in Ubuntu, but init 2 is default. init 0 is shutdown (sudo init 0 will shut down the machine), init 6 is reboot (sudo init 6 will shut down the machine). You really don't have to use these. To shutdown the gui in Ubuntu from the console (there are six consoles, accesible by pressing ctrl-alt-f<x>, where x is 1-6, and the gui is accesible by pressing ctrl-atl-f7), type sudo /etc/init.d/gdm stop (in kubuntu replace gdm with kdm). To restart gdm, type sudo gdm (kdm for kubuntu).

---

### Post by Culuntu on 2006-06-28
thanks you knn and rai4shu2 !

i'm following the steps

so from now on i don't have to download from [www.nvidia.com?](www.nvidia.com?)

---

### Post by tseliot on 2006-06-28
Please, use my guide (Method 2) or my script:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by Culuntu on 2006-06-28
damn i have a big problem !!!

i read the how-to i did all the steps 

i didn't c the nvidia logo  , in addition to this , more than 3/4 of the screensavers can't be displayed!!!!

btw i have a 386 not a 686 because when i started to download i found out that all the files in synaptic end with 386 !

So could anyone help me !

---

### Post by Culuntu on 2006-06-28
tseliot i OWE YOU ONE!!!!!!  :mrgreen: :mrgreen: 

a billion thanks !!!! :) 

it now works thank u!

btw i used method 1 ;)

---

