---
title: "[Ubuntu 16.04] huge Problems with nvidia drivers"
date: 2017-06-16
forum: Installation &amp; Upgrades
---

### Post by gfoxhound on 2017-06-16
Hello
Iam an old kubuntu user since 2008 exactly. Until Kubuntu 14.04 it was really perfect, for me at least. I decided to upgrade towards Ubuntu 16.04, and there is the big problem. Once I installed Ubuntu 16.04, as it is slow, I decided to switch from generic video driver, to Nvidia's driver, as I used to do before. It does not work.
I followed the script availlable here 
[https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics](https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics)
> 
[h=1]Now for the fix[/h]
[LIST=1]
[*]Log into your account in the TTY.
[*]Run sudo apt-get purge nvidia-*
[*]Run sudo add-apt-repository ppa:graphics-drivers/ppa and then sudo apt-get update.
[*]Run sudo apt-get install nvidia-375.
[*]Reboot and your graphics issue should be fixed.
[/LIST]
[FONT=inherit][COLOR=#111111][FONT=Ubuntu]If you run into problems afterward, you should ask a different question. (Refer to this question so that we know it isn't a duplicate.) However, there are a few other small fixes you can try out before you do.[/FONT][/COLOR]

[LIST]
[*][FONT=inherit]Reinstall Xorg[/FONT]

[LIST]
[*]Go back into the TTY and run sudo apt-get purge xorg-* xserver-xorg; sudo apt-get install xorg xserver-xorg; sudo dpkg-reconfigure xorg.
[/LIST]

[*][FONT=inherit]Reinstall your desktop environment[/FONT]

[LIST]
[*]If on Unity, run sudo apt-get purge ubuntu-desktop; sudo apt-get install ubuntu-desktop.
[*]If on GNOME run sudo apt-get purge ubuntu-gnome-desktop gnome-desktop-environment; sudo apt-get install ubuntu-gnome-desktop.
[*]If on MATE run sudo apt-get purge ubuntu-mate-desktop mate-desktop-environment; sudo apt-get install ubuntu-mate-desktop
[*]Each Ubuntu DE has its own package name. If you have KDE or something else, the name should be similar to the ones above.
[/LIST]

[*]Fresh reinstall
[LIST]
[*]It's not the most inviting option, but sometimes it's the best thing to do in cases like this.
[/LIST]
[/LIST]
[/FONT]
 

But the big problem, I was unable to connect into my account. Is it a workaround ? Does it exist a solution please ? Why did Ubuntu's team change things that worked perfectly before ? 
My computer's config: 
Notice it works perfectly before, no problems with Kubuntu/Ubuntu 14.04. No problem with Win 7, or Win XP. The only problem I have met, is with Ubuntu 16.04, 17.04.
> 
CPU Type : DualCore Intel Core 2 Duo E6300, 1866 MHz (7 x 267)
Motherboard Name : Intel Lemont DP965LT (3 PCI, 3 PCIE x1, 1 PCIE x16, 4 DDR2 DIMM, Audio, Gigabit LAN)
Motherboard Chipset : Intel Broadwater P965
System Memory : DIMM1: Kingston 1 GB DDR2800 DDR2 SDRAM (55518 @ 400 MHz) (44412 @ 266 MHz) (3339 @ 200 MHz)


Video Adapter : NVIDIA GeForce 7300 GS (Microsoft Corporation WDDM) (256 MB)
Video Adapter : NVIDIA GeForce 7300 GS (Microsoft Corporation WDDM) (256 MB) 3D
Accelerator : nVIDIA GeForce 7300 GS
Monitor Acer G226HQL [22" LCD] (LYLEE0128524)



---

### Post by Bashing-om on 2017-06-16
gfoxhound; Hello;

That card is old ... takes the 304 driver:
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Soon now to be no-longer-supported:
> 
The Linux 304.* legacy driver series is the last to support the NV4x and G7x GPUs and motherboard chipsets based on them. Support for new Linux kernels and X servers, as well as fixes for critical bugs, will be included in 304.* legacy releases through the end of 2017. 
See: [http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)


But for now we need to clean this system up and get the 304 driver installed.

post back:
```

dpkg -l | grep -i nvidia
lsmod | grep nvidia
lsmod | grep nouveau
ls -al /home/<username>/

```
 where "username" is your actual system username .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by gfoxhound on 2017-06-17
First of all thx for your quick answer and your help.
In spite of the fact that Iam java developper, Iam far to be an expert in unix area-the rare commands that I know are....mkdir, cp, mv, ls, but grep I don't remember, it is a while that I don't see this command. Sorry but nobody is perfect  :biggrin: -. Very far. What commands lines exactly should I write.
Moreover, I searched in nvidia website 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
I found this driver
[http://www.nvidia.com/download/driverResults.aspx/114718/en-us](http://www.nvidia.com/download/driverResults.aspx/114718/en-us)
is it correct ? However as I said U, in ubuntu 16.04, I reached the interface TY, I see username, and password, but I could not log in. If I download the driver, what should I do in this case ?

PS: Again thx for your help.

---

### Post by Bashing-om on 2017-06-17
gfoxhound; hey;

Hey. not to know is not a sin . None of us know it all . I just have a bit of experience with the nvidia driver .

What we want here is the 304 version driver.
Getting a driver from nvidia direct is the means of last resort . The driver in our repo is optimized for ubuntu .
It is available in our software repository:
```

apt list nvidia-304

```

OK, let's proceed and get this driver installed from the repository.
1st is the find out why you are not able to log into the system:
> 
 I see username, and password, but I could not log in.  I see username, and password, but I could not log in. 


Let's "presume" that "you" do not have the authority to access your desktop.
Verify authority :
At the grub boot menu -> advanced options -> recovery kernel -> root access .
Now what shows from terminal command:
```

ls -al .ICEauthority .Xauthority

```
show me this complete output - checked for typos .

Once we have access to the system as "you" we continue in the process to get the proper graphic's driver installed.
 

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by gfoxhound on 2017-06-17
Thx Bashing-om for your help, and your quick reactivity.
We are saturday night, nearly 23:00. I will do it tomorow sunday.
However let's resume what I must to do

First of all, I must to login with my username and passworth, by executing this fragment of code

```

ctrl+alt+f1
// login into terminal mode and must execute this code
ls -al .ICEauthority .Xauthority

```

Once it is done I must to follow these statements

```

dpkg -l | grep -i nvidia
lsmod | grep nvidia
lsmod | grep nouveau
ls -al /home/<username>/

```
and finish by 
```

apt list nvidia-304

```

Is it correct ?

---

### Post by Bashing-om on 2017-06-17
gfoxhound; Mostly Yes.

All we are doing here is attempting to activate a console interface ( ctl+alt+F1)
See what is on the system ;
see that the desired driver is available ( apt list nvidia-304)

then we do the actual install if all is clean and proper.

[INDENT][INDENT]leastways. that is my thoughts
[/INDENT][/INDENT]

---

### Post by gfoxhound on 2017-06-18
Hello.
I could not login again. I applied the scripts that I described above. It is still the login screen.

PS- I applied obviously **apt get update and upgrade**, else I don't know how to set up the driver nvidia -304

---

### Post by Bashing-om on 2017-06-18
gfoxhound; Hey;

Sorry, I am unable to establish a point of reference as to logging in.

so, in small steps. What results when at the login screen you attempt to activate a console interface with key combo ctl+alt+F1 ?

Once we have verified access to the system we continue - with the thought to check what is installed, clean up and then install the 304 driver from our repository .

[INDENT][INDENT]should be
[INDENT][INDENT][INDENT]no big deal
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mc4man on 2017-06-18
Just a thought - it seems login was fine before installing the 375 drivers so maybe remove, reboot & take from there, i.e. from tty 
sudo apt purge nvidia*

---

### Post by gfoxhound on 2017-06-18
To Bashing-OM
> 
[COLOR=#000000]Sorry, I am unable to establish a point of reference as to logging in.[/COLOR]

[COLOR=#000000]so, in small steps. What results when at the login screen you attempt to activate a console interface with key combo ctl+alt+F1 ?[/COLOR]

It runs.
I did all your scripts that U wrote.

> 

[COLOR=#000000]Once we have verified access to the system we continue - with the thought to check what is installed, clean up and then install the 304 driver from our repository .[/COLOR]

[COLOR=#000000]should be
no big deal





[/COLOR]
 
Once I've finished -with apt get update, and upgrade-, I reboot. I see the Login interface, at this step I could not login,-with ctrl +alt+f1 worked in anyway-, but the goal with is to connect with its powerful GUI.

---

### Post by Bashing-om on 2017-06-18
gfoxhound; Hummm ..

Rather than verifying what is ; how about we just take the shortest route to a probable resolution ?
In that F1 console - logged into the system, run terminal commands:
```

sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo ubuntu-drivers autoinstall

```

reboot to see the effect.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by gfoxhound on 2017-06-18
To mc4man
Thx for your help too.
As I said ctrl+alt+f1 had always worked since the begining, the login fails only in GUI. At this step what should I do ? Any suggestion ?

---

### Post by gfoxhound on 2017-06-18
To Bashing-OM.
I will do immediately, I will let U know.

---

### Post by gfoxhound on 2017-06-18
> 
sudo rm /etc/X11/xorg.conf

It does not find this file

---

### Post by Bashing-om on 2017-06-18
gfoxhound; Hey /

We can do this . Patience .

> 
 the login fails only in GUI. At this step what should I do ? Any suggestion ?


That be the reason we asked to see:
```

ls -al /home/<username>/

```
to know that "you" have the authority to access your desktop. 

A real short version:
```

ls -al .ICEauthority .Xauthority

```

Mine:
> 
sysop@x1604:~$ ls -al .ICEauthority .Xauthority
-rw------- 1 sysop sysop 10048 Jun 18 12:11 .ICEauthority
-rw------- 1 sysop sysop    50 Jun 18 12:11 .Xauthority
sysop@x1604:~$ 

where here I am "sysop"; your results should be similar .

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by gfoxhound on 2017-06-18
I could login now, and I can access to the GUI, but as I could not execute

> 
sudo rm /etc/X11/xorg.conf


The screen is bad, It seems that the screen is frozen. I can see all my previous icons, but could not do something. Maybe because of this xorg.conf

---

### Post by Bashing-om on 2017-06-18
gfoxhound; Hummm ..

It that file did not exist - and it is depreciated - then yeah can not remove it .  Generally, not having that xorg.conf file is normal.

At this point we need to see the result of terminal command:
```

sudo lshw -C display

```

See here that a driver is loaded and what the hardware is .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by gfoxhound on 2017-06-18
Well, I much to copy what I could, as I became lazy, normally I direct it into file, copy and past, this time i must do much efforts....;)

The result of the command :
```

sudo lshw -C display

```

```

-display 
description : VGA compatible controller
product : G72 [GeForce 7300 GS]
vendor : NVIDIA Corporation
physical id : 0
bus info : pci@000:01:00.0
version: a1
width: 64 bits
clock: 33 MHz
capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
configuration: driver=nvidia latency=0
resources : irq:16 memory:d1000000-d1ffffff memory:c0000000-cfffffff memory: d0000000-d0ffffff


```

In my view the driver was installed -U did a good job-, the question now, why does the screen freezes, once I log in.

---

### Post by Bashing-om on 2017-06-18
gfoxhound; Yukkie -
that the screen still freezes.

Let's see what got installed:
We do this the easy way and use a pastebin site;
```

sudo dpkg -l | grep -i nvidia | nc termbin.com 9999

```
the result is a URL pack in terminal . Pass that complete link back here .
The file has the output of the dpkg command - no sensitive information is included .

Depending, next we go looking at the log files . see what the system thinks .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by gfoxhound on 2017-06-19
after writing 

```

sudo dpkg -l | grep -i nvidia | nc termbin.com 9999

```

I obtain either  

[COLOR=#0000ff]**[http://termbin.com/8pyt](http://termbin.com/8pyt)**[/COLOR]

or 
[FONT=arial black][B][COLOR=#ff0000]http://termbin.com/i3ig[/COLOR]

[/B][/FONT]**???**[FONT=arial black][/FONT]

---

### Post by Bashing-om on 2017-06-19
gfoxhound; Well.

That too is all good .
Let's see if this is a problem in "your" account . 
At the login screen choose to activate the guest account . Is the GUI fully functional in the guest account ?

[INDENT][INDENT]still, sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by gfoxhound on 2017-06-21
> 
...login screen choose to activate the guest account ...

I logged as Guess, and it is the same behaviour. The screen freezes, impossible to do something, even I could see a screen error saying something like this "Ubuntu encountered internal error..."  when I wanted to see the detail, impossible, impossible to click OK in order to see at least what kind of error.

---

### Post by Bashing-om on 2017-06-21
gfoxhound; Well;

So we do have a system level problem .

What shows the log files ?
Execute:
```

cat /var/log/Xorg.0.log | nc termbin.com 9999
cat /var/log/gpu-manager.log | nc termbin.com 9999

```
And pass the resulting links back here .

see if we get any hints where the issues lies .

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by oldfred on 2019-08-07
If you can get grub menu and boot using recovery mode, it definitely is a graphics issue.
And if you can boot recovery mode, you do not need chroot, otherwise you do need the chroot.

This is what I did just to prove the autoinstall installs the nVidia drive also. Numbers are from my history, # is comment.


#Checked to see that I had installed nVidia, my old GT620 has about the same performance as far as my normal use. It showed 390.xx.
 1987  dkms status
 1988  sudo apt purge nvidia-*
# still showed it even though gone, which is normal
 1989  dkms status
# made sure system was up to date
 1990  sudo apt update
 1991  sudo apt upgrade
 1992  sudo apt autoremove
#Rebooted and now it showed nouveau driver as default. Was surprised I did not need nomodeset on reboot.
 1993  sudo lshw -c display
 1994  sudo ubuntu-drivers autoinstall
# rebooted again & then it showed 390.xx installed. The autoinstall picks best (not sure how) driver for your system. 
1995  sudo lshw -c display
 1996  dkms status


#If autoinstall not what you want you can specify any driver in this list. The ppa will add newer drivers to this list.
       # should show newest versions available in addition
ubuntu-drivers devices 

    
How do you specify which video card is default? Is that a setting in UEFI. My system has UEFI setting for internal Intel chip's video & nVidia card, but I do not think you can choose, there?

---

