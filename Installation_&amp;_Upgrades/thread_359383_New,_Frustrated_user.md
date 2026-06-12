---
title: "New, Frustrated user"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by HessiaNerd on 2007-02-11
Hello,

I recently converted to Linux and Ubuntu from many many years of MS and for the most part I am glad to make the change.  I am currently having trouble getting my display to go above 600x800.  I would guess that this is a driver issue, but when I go to the DEVICE MANAGER I see that ubuntu has successfully recognized my Nvidia GeForce FX 5900 Ultra.

After searching your forums I ran across this thread:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I was unclear about which was the "appropriate module for ...[my] kernel" I believe that I should use the [686]("http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel") 'kernel'(?) As I am intel based, but have been getting conflicting messages as to whether I should change from 'generic':

from the first link:
"...if you have a generic kernel image, the X will not work."

then I read this
> **mcduck said:**
> There is no more separate 686 kernel in 6.10, instead the generic kernel checks your CPU at boot time and then uses right optimizations automatically.
....

and now I dont know what to do.  Please help explain some of this to me.  I want to get the most out of my graphics card and CPU, even though they are a little aged, I thought I could do this by swiching to a Linux distro.  I have read a lot about ubuntu but I gotta say this is starting to put me off.

***Edit:

I forgot to mention that I added the 'NVidida binary X.Org driver', ran the **sudo nvidia-glx-config enable** command and came back with the following:
[I]
Error: unable to load nvidia kernel driver! Be sure to have installed the nvidia driver for your running kernel.
[/I]

what next???

---

### Post by Kateikyoushi on 2007-02-11
Most likely you are using the generic kernel but you can check it with the following command.

```
uname -a
```

---

### Post by tagra123 on 2007-02-11
You can usually increase the display resolution by editing your xorg.conf refresh rates and then editing the sizes.

You can do this by running the following commands.

First make a backup of your xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup-1

sudo dpkg-reconfigure xserver-xorg
```

then 

ctrl-alt-backspace  to restart the xserver. Rebooting the computer also works.

Answer the questions and pay special attention to the screen size section. I believe it will also allow you to enter the monitor refresh rates.  You can usually find refresh rate fo a particular monitor using google.

If something didn't work correctly or you want to undo the changes choose recovery from the boot options and at the prompt type:

```
sudo cp /etc/X11/xorg.conf.backup-1 /etc/X11/xorg.conf
```

reboot and it should be just it was the way before you started

---

### Post by Tanker Bob on 2007-02-11
The best way to do NVidia or ATI is with the Envy script.  It will ID your card, download, compile, install, and activate the latest driver for your card.  Download the .deb file from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html).  Be sure to read the instructions at the bottom of Alberto's page from which you download the file.  After completely reading the instructions,  open a terminal and navigate to where you stored the download and type:

```

sudo dpkg -i envy_0.8.1-0ubuntu6_all.deb
sudo envy

```

Then just follow the prompts.  All the right answers are usually "yes".  When the script completes, use the option to start your X-server.  You should be up and running.

---

### Post by HessiaNerd on 2007-02-12
When I run envy I get a menu to 1) Install Nvidia driver 2)Uninstall Nvidia Driver.... etc
I obviously chose 1... I get 2 or 3 lines of response which go by too fast to read, then my screen goes black...  there is a cursor and I can type but commands dont do anything...


its still sitting there all black

any suggestions?

---

### Post by kvonb on 2007-02-12
It looks from your first post that you installed the Ubuntu "official" drivers, while this should work, I would recommend installing the Nvidia binary drivers instead (which is exactly what the Envy thing does, or in your case tried to do).

What I suggest the problem is, is that you needed to remove all the Ubuntu "official" drivers first, I believe that is where you are having a conflict.

Here is a link to a page which should sort out your problem:

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

***NOTE**  On that page, **go straight down to STEP2/Option2.**

[B]**DISREGARD ANY OTHER INSTRUCTIONS ON THE ENTIRE PAGE**
[/B]
And please **follow the instructions EXACTLY as they are written**, **EXCEPT** the actual driver version line, ie the page deals with driver version NVIDIA-Linux-x86-1.0-9629-pkg1.run, when you see that line, type only: NV then press the <TAB> key to autocomplete the driver name with your current one, assuming that the driver you downloaded is in your current folder.  Do that wherever you see "NVIDIA-Linux-x86-1.0-9629-pkg1.run" in those instructions.

Hope that makes sense :).

That guide will have you remove all the old stuff and install the new driver.

Also please note that whenever there is a kernel update, you will have to re-install the Nvidia binary driver, ie go through those instructions again, or use the Envy script which should then work.

Good luck, regards, Kev :)

EDIT: Once you have successfully installed the driver, and you are back in X, look on the Menu under Applications->System Tools, there will be an Nvidia settings icon, you can change the resolution with that :).

---

### Post by DMorg on 2007-02-12
There are no NVidia drivers for Linux. You can, however, sign this petition to NVidia and there might just be a package sooner or later;

[http://www.petitiononline.com/nvfoss/petition.html](http://www.petitiononline.com/nvfoss/petition.html)

---

### Post by HessiaNerd on 2007-02-12
> **kvonb said:**
> 
And please **follow the instructions EXACTLY as they are written**, **EXCEPT** the actual driver version line, ie the page deals with driver version NVIDIA-Linux-x86-1.0-9629-pkg1.run, when you see that line, type only: NV then press the <TAB> key to autocomplete the driver name with your current one, assuming that the driver you downloaded is in your current folder. 

EDIT: Once you have successfully installed the driver, and you are back in X, look on the Menu under Applications->System Tools, there will be an Nvidia settings icon, you can change the resolution with that :).

OK... so when I get to the stop command 

*sudo /etc/init.d/gdm stop*

I get the same blank screen as before...

I restarted and it tried to move the the next command (moved the .run into home directory, default was desktop) it tells me that I have an X server running....

... after a quick search I found this:
> **Pollywoggy said:**
> ... If you are using kdm, the command to stop the X server is  'sudo /etc/init.d/kdm stop'  "stop" can be replaced with "restart" or "start" as needed.  If you use xdm or gdm, just put those in that command instead of kdm.

Stopping the X server will take you to a console.

well stopping didnt take me to a console... just a blank screen.  So I started in "recovery mode (the -11 generic version) and tried the sh NV[tab] again.

now it says "your are running in runlevel 1... cause problems... swich to runlevel 3 ('telinit 3')..."

this brings me to the familar login screen.  so I went to options in the lower right, chose 'failsafe terminal' 

again the sudo NV[tab]

again xserver is running

....:confused: 

again I am at a loss of what to do next

ps Sorry if my explanation is too long, but I have been documenting it with my laptop as I go along to help me out

any suggestions would be helpful

thanks for the help so far btw

---

### Post by kvonb on 2007-02-12
Yes, sometimes the X server won't stop!

Are you using KDE or gnome?  Either way, once you issue the "stop" command, press <CTRL><ALT<F1> which will switch you to the virtual terminal 1.

Now login with your standard username and password, and issue the stop command again:

```
sudo /etc/init.d/gdm stop
```

(or kdm stop, or both!)

I would then issue this command:

```
ps uax | grep X
```

note the case sensitivity.

Now that should spit out a few lines something like this:


```
root      4138  1.7  3.5  41856 36436 tty7     SLs+ 12:37   1:04 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
1001      7110  0.0  0.0   2804   764 pts/0    S+   13:38   0:00 grep X

```

That indicates that X is still running, so issue this command:

```
sudo kill -9 4138
```

That should get rid of it.  The number "4138" is taken from the line above, just after "root".  Yours will be different, just use the number that the command above spits out, that is the process number of the X server that is running.

Now try going through the driver instructions again from where you are in that VT.

I hope that makes sense :).

If you still get stuck, I'm quite sure you can do all that from runlevel 1, if you first issue the command:

```
bash
```

Which will (or rather, should) load the bash terminal, rather than the basic "sh" that is default in runlevel 1.

Please post back here if you run into problems, I will try my best to help you as soon as possible.

Regards, Kev :)

---

### Post by lojic on 2007-02-13
> **DMorg said:**
> There are no NVidia drivers for Linux. You can, however, sign this petition to NVidia and there might just be a package sooner or later;

[http://www.petitiononline.com/nvfoss/petition.html](http://www.petitiononline.com/nvfoss/petition.html)
signed it dude - thx

---

### Post by HessiaNerd on 2007-02-13
> **kvonb said:**
> Yes, sometimes the X server won't stop!

Are you using KDE or gnome?  Either way, once you issue the "stop" command, press <CTRL><ALT<F1> which will switch you to the virtual terminal 1.

Now login with your standard username and password, and issue the stop command again:

```
sudo /etc/init.d/gdm stop
```

(or kdm stop, or both!)

I would then issue this command:

```
ps uax | grep X
```

note the case sensitivity.

Now that should spit out a few lines something like this:


```
root      4138  1.7  3.5  41856 36436 tty7     SLs+ 12:37   1:04 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
1001      7110  0.0  0.0   2804   764 pts/0    S+   13:38   0:00 grep X

```

That indicates that X is still running, so issue this command:

```
sudo kill -9 4138
```

That should get rid of it.  The number "4138" is taken from the line above, just after "root".  Yours will be different, just use the number that the command above spits out, that is the process number of the X server that is running.

Now try going through the driver instructions again from where you are in that VT.

I hope that makes sense :).

If you still get stuck, I'm quite sure you can do all that from runlevel 1, if you first issue the command:

```
bash
```

Which will (or rather, should) load the bash terminal, rather than the basic "sh" that is default in runlevel 1.

Please post back here if you run into problems, I will try my best to help you as soon as possible.

Regards, Kev :)

Uhh... I dont really understand the difference between bash and sh(ell)...  but I ended up getting to work by editing my default-display-manager file located at /etc/X11/ to contain only
'false'
as opposed to 
/usr/sbin/gdm      (Im using gnome)

thanks to [this]("http://ubuntu.wordpress.com/2006/01/22/booting-in-to-the-command-prompt/") article...

from there everything worked fine....

thanks again for your help.... 

Im sure Ill need it again soon...  I got lots of hardware to try to configure for this box...

---

### Post by hardyn on 2007-02-13
> **DMorg said:**
> There are no NVidia drivers for Linux. You can, however, sign this petition to NVidia and there might just be a package sooner or later;

[http://www.petitiononline.com/nvfoss/petition.html](http://www.petitiononline.com/nvfoss/petition.html)


there IS an nvidia driver for linux, there is not an official OSS driver for nvidia.

nvidia-glx is the CSS driver for linux, and is a little better than ATI attempt

---

