---
title: "&quot;Your system is running in low-graphics mode'' after Ubuntu 12.04 LTS update"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by Chris . on 2012-04-29
Hello!
I own a Acer Aspire 5552 laptop, which has Ubuntu on it. And now i updated it to 12.04 LTS from 11.10. When i turn the laptop on, it says : Your system is running in low-graphics mode, Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.
I read about this on Ask Ubuntu already, and it suggested to got to Ctrl + Alt + F1 and reinstall my desktop, or install fglrx. Well, these things what I read on this site : [http://askubuntu.com/questions/125453/your-system-is-running-in-low-graphics-mode-with-an-ati-radeon-3200-graphics-car](http://askubuntu.com/questions/125453/your-system-is-running-in-low-graphics-mode-with-an-ati-radeon-3200-graphics-car)

Both of them don't work. And if I don't enter Terminal and just click OK (press Enter, because the mouse cursor isn't there) when it says you system is running in low-..., I get options, but i can't choose any of them, can't even click cancel or OK. My graphics card is ATI Mobility Radeon HD 4250. Help please! Thanks :)

---

### Post by Chris . on 2012-04-30
:bump:
Help, please!

---

### Post by Herman on 2012-04-30
Try booting into 'Recovery Mode' from your GRUB Menu, there is a menu in there which includes 'failsafeX - Run in failsafe graphic mode', or something like that depending on what exact version of Ubuntu you have. That will lead you to more menus and you can reset your graphics (get rid of your specific graphics card driver temporarily), and continue with a normal boot.
After that you can install a graphics card driver again or not, it's up to you.

Actually, in Precise Pangolin beta, my mouse and keyboard don't work in the text console either, to select 'Reconfigure Graphics', or 'OK', so I'm stuck too as I'm testing my own solution in reply to your question. I hope that's fixed in the final release, which I have downloaded but not had time to install yet.

Another way to do the same thing is to mount your operating system in another Ubuntu such as a Live CD and delete or (better idea) rename the /etc/X11/xorg.conf  as a backup of the same file.
Then perform a normal boot and if you want, re-install a graphics driver.

---

### Post by Chris . on 2012-05-09
The 'failsafeX - Run in failsafe graphic mode' didn't work, it still takes me to the same error place, and it doesn't give me any more menus.
Give me something else to try, please :(

---

### Post by Peter09 on 2012-05-09
Have you already done
 
```
sudo apt-get install fglrx
```
 
in recovery mode?
 
What sort of graphics card have you got?

---

### Post by ronaldbrijo on 2012-05-09
Hi,


I had the exact same problem and solved it by:

On my one pc i had to do a clean 11.10 install and before installing any other software do the upgrade. 

Another pc i just installed 12.04 direct...

---

### Post by Chris . on 2012-05-09
> **Peter09 said:**
> Have you already done
 
```
sudo apt-get install fglrx
```
 
in recovery mode?
 
What sort of graphics card have you got?

I did it, and this is what i got:
```
W: Not using locking for read only file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
```

I have a Ati Mobility Radeon HD 4250.
;)
Edit:
Now i tried the same thing when i just started the laptop, got the error and used Ctlr+Alt+F1 to go to the terminal, and entered the code there.
It loaded and stuff, downloaded and so on. But i can't really say what it says, because my laptop language is Estonian, not English, so you won't understand all of it.

    But i'll try to transalte the end of it:
The following files(or packs) made errors:
```
/var/cache/apt/archives/fglrx_2%3a8.960-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So that's it...help :(

---

### Post by Chris . on 2012-05-09
> **ronaldbrijo said:**
> Hi,


I had the exact same problem and solved it by:

On my one pc i had to do a clean 11.10 install and before installing any other software do the upgrade. 

Another pc i just installed 12.04 direct...

Could you explain more about what you did and how you did it ?
Because right now i didn't understand :)
Thanks!

---

### Post by Peter09 on 2012-05-09
Try doing
 
```
sudo apt-get purge fglrx
```
 
(I think thats the correct command).
This will get rid of any old fglrx files that might be interfering.
 
Once thats been done, install it again.
 
Then reboot.

---

### Post by Chris . on 2012-05-09
> **Peter09 said:**
> Try doing
 
```
sudo apt-get purge fglrx
```
 
(I think thats the correct command).
This will get rid of any old fglrx files that might be interfering.
 
Once thats been done, install it again.
 
Then reboot.

Okay, i tried it.
At first it says :
```
Reading package lists... Done
Building dependency tree
Reading state information... Done

```
And then comes Estonian language lines.
But if translated, it looks something like this:
Packet fglrx was not removed, because it has not been installed.

Then there is an english line:
You might want to run 'apt-get -f install' to correct these.

and some other stuff.

So yeah, that failed :(

---

### Post by Peter09 on 2012-05-09
might be worth doing the install again, might have cleared up some old files.

---

### Post by Chris . on 2012-05-09
> **Peter09 said:**
> might be worth doing the install again, might have cleared up some old files.

And how do i do that? 
Sorry for all the questions :(

---

### Post by Peter09 on 2012-05-09
```
sudo apt-get install fglrx
```

---

### Post by ronaldbrijo on 2012-05-10
Hi Chris, 

I downloaded 12.04 from the ubuntu site, burned to a cd and booted the pc from the cd to run the installer.

---

### Post by awam66 on 2012-05-10
Hello Chris
Try this: boot to recovery mode and you should get a menu and then choose "Fix Broken Packages" or you could drop to a root terminal and type ```
apt-get upgrade -f
```
HTH

---

### Post by Chris . on 2012-05-12
> **awam66 said:**
> Hello Chris
Try this: boot to recovery mode and you should get a menu and then choose "Fix Broken Packages" or you could drop to a root terminal and type ```
apt-get upgrade -f
```
HTH

Hey,
i chose the "Fix Broken Packages", it did it's thing, but i still get the same error, so that didn't fix it.
And when i enter the code you gave me in root terminal, i get this:
```
W: Not using locking for read only file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
```
:(

---

### Post by Chris . on 2012-05-12
> **ronaldbrijo said:**
> Hi Chris, 

I downloaded 12.04 from the ubuntu site, burned to a cd and booted the pc from the cd to run the installer.

Hi,
but if i do a clean install with a cd for 12.04, will my previous files will be lost?  I mean like my pictures, folders, music and other stuff i had on my laptop.

---

### Post by Chris . on 2012-05-13
:bump:
;)

---

### Post by Herman on 2012-05-13
> but if i do a clean install with a cd for 12.04, will my previous files  will be lost?  I mean like my pictures, folders, music and other stuff i  had on my laptop.     Only if you delete your existing Ubuntu partition.

You should make a backup copy of all your files and settings and store them all in some other media before you do any work on your computer's hard disk. Most people now have too much stuff to fit on DVDs, so either a USB flash memory stick or another hard drive will likely be needed, you can use a USB external hard drive if you want. I think that's what most people probably use these days.

If you want you should be able to resize your existing Ubuntu partition smaller to make room for your new Ubuntu installation and have two Ubuntus in the same hard disk. You can do that either with GParted in the Ubuntu CD or with the installer's partitioner during the installation process. Install a new Ubuntu beside your old one and then copy your files across. You still should make a files backup in another disk beforehand though, to be safe.

EDIT: Also, have you read this sticky:  			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") ?

---

### Post by Chris . on 2012-05-14
> **Herman said:**
> Only if you delete your existing Ubuntu partition.

You should make a backup copy of all your files and settings and store them all in some other media before you do any work on your computer's hard disk. Most people now have too much stuff to fit on DVDs, so either a USB flash memory stick or another hard drive will likely be needed, you can use a USB external hard drive if you want. I think that's what most people probably use these days.

If you want you should be able to resize your existing Ubuntu partition smaller to make room for your new Ubuntu installation and have two Ubuntus in the same hard disk. You can do that either with GParted in the Ubuntu CD or with the installer's partitioner during the installation process. Install a new Ubuntu beside your old one and then copy your files across. You still should make a files backup in another disk beforehand though, to be safe.

EDIT: Also, have you read this sticky:  			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") ?

Okay, thanks for anwsering, but could you give me a tutorial on how to do all this?
Sorry, but i'm not sure how to do it myself, and i want to follow a tutorial just to be safe ;)

---

### Post by matt_symes on 2012-05-14
Hi  


Try posting the output of you xorg log file. That may give clues as to what is happening.


```
cat /var/log/Xorg.0.log
```


Kind regards

---

### Post by Chris . on 2012-05-14
> **matt_symes said:**
> Hi  


Try posting the output of you xorg log file. That may give clues as to what is happening.


```
cat /var/log/Xorg.0.log
```


Kind regards

Okay, but how do i post it here?
I mean it is a lot of text going by fast, and then stopping.

I bet i sound stupid :D

---

### Post by matt_symes on 2012-05-14
Hi

In your case, i suspect the easiest way may be to use pastbin.


Open a terminal and type


```
sudo apt-get install pastebinit
```


Then type


```
cat /var/log/Xorg.0.log | pastebinit
```


This will give you output similar i(but not the same) to this.


```

matthew@Aspire;$cat /var/log/Xorg.0.log | pastebinit
http://paste.ubuntu.com/123456
```


Post the URL (which will look similar to this: [http://paste.ubuntu.com/123456](http://paste.ubuntu.com/123456)) back here.


Kind regards

---

### Post by Chris . on 2012-05-14
> **matt_symes said:**
> Hi

In your case, i suspect the easiest way may be to use pastbin.


Open a terminal and type


```
sudo apt-get install pastebinit
```


Then type


```
cat /var/log/Xorg.0.log | pastebinit
```


This will give you output similar i(but not the same) to this.


```

matthew@Aspire;$cat /var/log/Xorg.0.log | pastebinit
http://paste.ubuntu.com/123456
```


Post the URL (which will look similar to this: [http://paste.ubuntu.com/123456](http://paste.ubuntu.com/123456)) back here.


Kind regards

Okay, i tried the 
```
sudo apt-get install pastebinit
```
And i got this :
```
Reading package lists... Done
Reading state information... Done
You might want to run 'apt-get -f install- to correct these:

```
Then it was some text in my language, but it said something about Fglrx and Python-configobj.

So i couldn't install it.

---

### Post by matt_symes on 2012-05-14
Hi

Right then. I have had a better look at this thread.


It seems you have a couple of packages that are still causing the problem to your package manager.


fglrx is not installed correctly, therefore i suspect it is falling back to the vesa or frame buffer driver at 640x480. Hence your low resolution.


This was an upgrade that seems to have gone wrong ?


I find this interesting and needs to be examined.


> W: Not using locking for read only file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
e: tHe package lists or status file could not be parsed or opened.



Can you post the output of, from the terminal,


```
ls -l /var/lib/dpkg/lock /var/cache/apt/ /var/cache/
```


That is a small L after ls.


Copy and paste (hightlight text->right click->copy) the results back, from the terminal, into your next post.


Kind regards

---

### Post by Chris . on 2012-05-20
> **matt_symes said:**
> Hi

Right then. I have had a better look at this thread.


It seems you have a couple of packages that are still causing the problem to your package manager.


fglrx is not installed correctly, therefore i suspect it is falling back to the vesa or frame buffer driver at 640x480. Hence your low resolution.


This was an upgrade that seems to have gone wrong ?


I find this interesting and needs to be examined.






Can you post the output of, from the terminal,


```
ls -l /var/lib/dpkg/lock /var/cache/apt/ /var/cache/
```


That is a small L after ls.


Copy and paste (hightlight text->right click->copy) the results back, from the terminal, into your next post.


Kind regards


Hi again, sorry for the late respone, my internet is been acting weird.
So i tried the code you gave me but how am i supposed to copy the results from my laptop to my pc?
Anyway, i took a picture of it, it's in the attachments.

---

### Post by Chris . on 2012-05-20
/SOLVED.

It got anwsered on Askubuntu.com, and it worked, here is what i followed:

```
I had the same problem with an Acer Aspire 3810tg. I soved it by doing the following:

Do a normal boot

Press Ctrl-Alt-F1 on the "Your system is running in low-graphics mode" screen

Download the correct driver from http://support.amd.com/us/gpudownload/Pages/index.aspx, in my case (ATI Mobility Radeon HD 4330): wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run which should also cover your case (Mobility Radeon HD 4xxx Series)

chmod 755 amd-driver-installer-12-4-x86.x86_64.run to make the file executable

sudo ./amd-driver-installer-12-4-x86.x86_64.run and follow the standard steps

You might need to run: sudo aticonfig --initial, but that was not necessary for me.

In my case the driver installation finished with an error, but it still worked. I hope this helps.
```

---

### Post by Arundhati Mohan on 2012-05-22
See the link below: 

[http://askubuntu.com/questions/129776/how-do-i-fix-running-in-low-graphics-mode-ubuntu-12-04](http://askubuntu.com/questions/129776/how-do-i-fix-running-in-low-graphics-mode-ubuntu-12-04)


This might help :)

---

### Post by Arundhati Mohan on 2012-05-22
See this link

[http://askubuntu.com/questions/129776/how-do-i-fix-running-in-low-graphics-mode-ubuntu-12-04](http://askubuntu.com/questions/129776/how-do-i-fix-running-in-low-graphics-mode-ubuntu-12-04)

---

### Post by opsharma on 2012-07-11
i am running GTS 450 and have installed ubuntu through windows 7 using wubi. Getting the same error still. Can you please help.

---

### Post by ozboy08 on 2013-02-22
> **opsharma said:**
> i am running GTS 450 and have installed ubuntu through windows 7 using wubi. Getting the same error still. Can you please help.

G'day.  I have just fixed this problem after spending most of the day trying to figure out what was wrong.

Step 1:  When the computer is stuck at that low graphics mode screen, press CTRL + ALT + F1 to start the termnal.  Login using your username/password.  First thing to do is type in :
   lspci
At the bottom of the screen, it will show you the graphics cards.  How many are there ?  I had two (One for onboard and one for discrete)

See if you can type in :  NVIDIA smi.  If the drivers are installed correctly, you will be able to do this.  Again, this will show you how many graphics cards your system is seeing.

Step 2:  Since you are already in Terminal, please type in:
   sudo apt-get install nvidia-current
This will update your drivers.

Step 3:   If your system has an onboard VGA and a discrete one, go into your computers BIOS and disable the onboard one.

Step 4:   Reboot.

In may case, what was happening was that the computer used to get confused on which graphics to use.  Even though my motherboard automatically switches off the onboard graphics when a discrete one is installed, Ubuntu was still seeing it and causing issues.  A combination of Steps 1-3 above fixed it.

Good luck and hope this helps to solve your problem.

Keep well.

---

### Post by bogan on 2013-02-22
Hi!, **ozboy08,**

You Posted: > See if you can type in :  NVIDIA smi. Was this a typo?? 

I get "NVIDIA : command not found", same with 'sudo' and with 'nvidia'. 

**Edit:** 31/03/13: I found the correct command is: 'nvidia-smi', the file is in /usr/bin:```
~$ nvidia-smi
Sun Mar 31 17:49:21 2013       
+--------------------------------------------------------------------------------------+                       
| NVIDIA-SMI 4.304.51        Driver Version:  304.51                         |                       
|-----------------------------------------------+--------------------------------------+----------------------------------------+
| GPU  Name                                    |  Bus-Id                           Disp. |  Volatile Uncorr.         ECC    |
| Fan  Temp  Perf  Pwr:Usage/Cap   |  Memory-Usage                     | GPU-Util      Compute   M.       |
|============================+=======================+=========================|
|   0    GeForce GT 520                     | 0000:01:00.0                N/A   |                                        N/A    |
| 40%     32C    N/A      N/A  /   N/A   |  19%   196MB  /     1023MB  |                  N/A            Default   |
+----------------------------------------------+--------------------------------------+-----------------------------------------+
                                                                               
+----------------------------------------------+--------------------------------------+-----------------------------------------+
| Compute   processes :                                                                                                GPU Memory  |
|     GPU             PID    Process name                                                                            Usage           |
|==============================================================================|
|             0                     Not Supported                                                                                                 |
+---------------------------------------------------------------------------------------------------------------------------------+
~$ 
```Chao!, **bogan.**

Reason for edit: Correct cmd found & example added.

---

### Post by hotlife3 on 2013-03-31
hi all
       i am get a error, when i am try to remove libasound2(error is.your system is running in low-graphics mode.(your screen,graphics card and input device settings could not detceted,you will need to configure these youself.plz help me

---

### Post by bogan on 2013-03-31
Hi!, **Hotlife3**,

Please start a Thread of your own with details of your set up and what you are trying to do and where & when the error occurs, what version of ubuntu and how installed -wubi?? - a new install or upgrade??

[Edit: Post a link here].

Also please Post: ```
uname -ar
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```Chao!,** bogan.**

---

### Post by hotlife3 on 2013-03-31
> **bogan said:**
> Hi!, **Hotlife3**,

Please start a Thread of your own with details of your set up and what you are trying to do and where & when the error occurs, what version of ubuntu and how installed -wubi?? - a new install or upgrade??

[Edit: Post a link here].

Also please Post: ```
uname -ar
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```Chao!,** bogan.**

Hi 
     I am make upgrade but it work normally but when I try to install teamviwer
      Then I m get error in libasound2 after I am try to uninstall libasound2 after get this error
      Your system running low graphics, ,

---

### Post by Ron O on 2013-11-28
The simplest solution seems to be one that was on askubuntu.com   [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)   Remove the file /etc/X11/xorg.conf.failsafe. From the GUI rather than command line, open Nautilus as root and copy the file to a safe location as a precaution, then delete the original file using Shift-Delete rather than just Delete. This removes it without moving it to the system trash folder in which case the file can magically re-appear. But first find out how to put this file back in place from recovery mode if it creates a boot problem with your particular installation and/or graphics driver.

I am using 12.04 64 bit with Gnome fallback and the video driver for my ATI card that was supplied by Ubuntu, not the ATI proprietary driver, and this worked for me. If the problem re-appears, check to see if /etc/X11/xorg.conf.failsafe has come back (as it did for me once) and remove it again. I think the trash folder MAY have been the source for re-inserting this file, but it could have been done by an update. But I do know that when this file is gone, the boot error goes away. This was a tricky one to fix because the problem is intermittent when the failsafe file is in place- sometimes it boots OK and sometimes not. I just started with the simplest solution I found, and it seems to work. IMHO- If this is a legitimate fix, the powers that be at Canonical should consider removing this file since it can lock an inexperienced user out of their system forcing them to do a reinstall, after which the problem will re-appear. 

BTW- emptying the system trash folder is not as simple as selecting empty trash, even if you are root. You have to open Nautilus as root and go to root/.local/share/Trash/files and remove each file with a Shift Delete. If you use Shift Delete to begin with, the file never gets copied to the trash folder.

---

### Post by pouldney on 2014-05-06
I upgraded my acer laptop 1551 with Mobility Radeon HD 4200 display
     from 12.04 to 12.10
  After upgrade had "The system is running in low graphics mode"
     click ctrl alt F2
  sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
  These commands gave wallpaper only
sudo dpkg-reconfigure lightdm   (to make sure lightdm is used)
 then reboot

            This worked for me

---

