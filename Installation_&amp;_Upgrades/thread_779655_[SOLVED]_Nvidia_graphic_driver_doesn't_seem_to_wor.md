---
title: "[SOLVED] Nvidia graphic driver doesn't seem to work &amp;amp; cause 8000x600 resolution"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by cooltuyul on 2008-05-02
i believe i have a nvidia 7300le, im running ubuntu 8.04 64bit, ive tried evny (a nvidia/ati driver downloader) and it installed the driver (i believe nvidia-glx-dev). however, when i boot up the computer, i get a window saying "ubuntu will run on low graphics mode" and there is a configure, shut down, and continue button. when i press configure, i get a window showing two tabs: (i think) display and driver. when i press continue, it boots up normal - but in 800x 600 resolution! what's goin' on?! 

im just a newb trying to learn the ways of linux, so any help is appreciated

---

### Post by Pumalite on 2008-05-02
Go to the Nvidia site, download appropriate driver for your card (if there is one) and install it through a virtual Terminal. If you need guidance about Virtual Terminal installation, come back.

---

### Post by cooltuyul on 2008-05-03
ive downloaded it, and uh... what virtual terminal? is it the terminal under apps-> accesories->terminal? if so how do i install it?

---

### Post by cooltuyul on 2008-05-03
Would any of these on  this website work?
[http://packages.debian.org/nvidia-glx](http://packages.debian.org/nvidia-glx)

---

### Post by Pumalite on 2008-05-03
Tell me the exact name of the driver you downloaded.

---

### Post by cooltuyul on 2008-05-05
yeah itd be NVIDIA-Linux-x86_64-169.12-pkg2.run. however it didn't work so i downloaded envy and usedit. i expect it is the same driver. 
heres the weblink:
[http://www.nvidia.com/object/linux_display_amd64_169.12.html](http://www.nvidia.com/object/linux_display_amd64_169.12.html)

---

### Post by PmDematagoda on 2008-05-05
First move to a tty by pressing Ctrl+Alt+F1, then execute:-
```
sudo /etc/init.d/gdm stop
```
to kill the X-Server, then install the necessary prerequisites for the Nvidia installer with:-
```
sudo apt-get install build-essential
```

After that is completed run the installer with(make sure that it exists in the folder where you are executing the command from):-
```
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```

After installation and configuration is done, check if the driver works properly by executing:-
```
sudo /etc/init.d/gdm start
```

Edit:- I see that you've installed the nvidia-glx-new package, that will conflict with the Nvidia driver, so uninstall the package with:-
```
sudo apt-get remove --purge nvidia-glx-new
```
before running the installer.

---

### Post by HalloweenB on 2008-05-05
I'm having the same problem on a system I just built.  Running Hardy, and went through the process of installing the ...169.12... driver mentioned above.  After a successful install, the best display setting I can get is 800 X 600.

Abit NF-M2SV mobo with integrated GeForce 6100 + 405 chip
AMD X2 4800 processor
Hardy 8.04 64-bit

Is it the on-board graphics that could be limiting?  If I installed a newer NVIDIA graphics card (suggestions welcome) would it be automatically detected?

---

### Post by PmDematagoda on 2008-05-05
If the above steps did not help, then try doing this:-

1) Open a modules file for editing with:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```
and save the file.

3) Reconfigure the X-Server with:-
```
sudo dpkg-reconfigure xserver-xorg
```
or run:-
```
sudo nvidia-xconfig
```

Then reboot the PC and see if your Nvidia driver issues are now fixed.

---

### Post by Malcy on 2008-05-05
PmDematagoda, thanks for the advice, my system had a similar problem and is now back on the nvidia drivers at the right resolution. The strange thing is that if I run the hardware drivers app, it is completely empty, where it used to show the restricted drivers in use??

p.s. how do I view the hardware manager, that seems to have disappeared since moving to 8.04?

---

### Post by histolo2 on 2008-05-05
I have similiar issues but can't install the driver.... i did everything as u said but whenever u want to run:
```

sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```
it tells me:
```
sh: can't run NVIDIA-Linux-x86_64-169.12-pkg2.run
``` 
I am in the right directory and i typed the filename right (pretty sure about that)...
i tried to run this when xserver was running and it started working then told me to that xserver should be stopped... when i stop xserver it just give that error

Any ideas?

---

### Post by Pumalite on 2008-05-05
Maybe you have a 32 bit Ubuntu.

---

### Post by Malcy on 2008-05-05
Yeah, don't forget to download the right driver. I run 32bit Ubuntu and had to download the 32bit driver but that's no hassle.

---

### Post by histolo2 on 2008-05-05
no i got amd64

I read some docs on nvidia site and they said i should stop xserver+opengl apps (some of them still work after stopping x) how do i do that?... maybe thats the problem

---

### Post by Pumalite on 2008-05-05
Take a good look at post # 7

---

### Post by cooltuyul on 2008-05-05
how do you get out of tty and can i just use terminal?

---

### Post by histolo2 on 2008-05-05
> **Pumalite said:**
> Take a good look at post # 7

I did exactly what it says... no workie

---

### Post by cooltuyul on 2008-05-05
when i try to to run 
code:
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
it says sh: file cannot be run (or something of that nature)
ive also tried the other way but still...no cigar

---

### Post by Pumalite on 2008-05-05
Make sure you have build-essential installed:
sudo aptitude install build-essential
Let me know if it's a matter of permissions.

---

### Post by cooltuyul on 2008-05-06
so i entered in that code... now what?

---

### Post by starcannon on 2008-05-06
Need to make it executable

```
sudo chmod a+x ./NVIDIA*.run
```

Then you just do this, note you don't need the sh in front:

```
sudo ./NVIDIA*.run
```

The rest of the directions in post #7 will complete your install.

Side note I usually back up my old xorg.conf file before I install my NVIDIA*.run drivers, then delete the old xorg.conf and let Nvidia write a new one from scratch. If you choose to do this just be sure to back up the old xorg.conf first, it may be of use if you run into problems.

```
cp /etc/X11/xorg.conf /home/yourhome/xorg.conf.backup.txt
```

Then to restore it if you find your stuck at a command line at some point:
```
cp /home/yourhome/xorg.conf.backup.txt /etc/X11/xorg.conf
```

---

### Post by histolo2 on 2008-05-06
starcannon: i tried your method it started ok but then it told me that it didn't find preccompiled kernel interface, it tried it from some nvidia ftp but didn't find the right version and when i told it to try to install anyway it said the 2.6 kernel refuses to use this because the compiler is an old version (gcc 4.1) and not gcc 4.2.....

i'll say it again... i followed the instructions exactly as posted

---

### Post by PmDematagoda on 2008-05-06
> **histolo2 said:**
> starcannon: i tried your method it started ok but then it told me that it didn't find preccompiled kernel interface, it tried it from some nvidia ftp but didn't find the right version and when i told it to try to install anyway it said the 2.6 kernel refuses to use this because the compiler is an old version (gcc 4.1) and not gcc 4.2.....

i'll say it again... i followed the instructions exactly as posted

What version of Ubuntu do you use?

---

### Post by histolo2 on 2008-05-06
I use ubuntu 8.04 (amd64 architecture), i upgraded to the beta version before the oficial release (don't think it matters)

---

### Post by toadman on 2008-05-07
> **histolo2 said:**
> starcannon: i tried your method it started ok but then it told me that it didn't find preccompiled kernel interface, it tried it from some nvidia ftp but didn't find the right version and when i told it to try to install anyway it said the 2.6 kernel refuses to use this because the compiler is an old version (gcc 4.1) and not gcc 4.2.....

i'll say it again... i followed the instructions exactly as posted



I have the same exact problem using instructions from post#7 on 32 bit hardy that was upgraded from gutsy.:confused:

---

### Post by cooltuyul on 2008-05-08
i used the code: sudo aptitude install build-essential (from post#19). so.. what do i do now?

---

### Post by toadman on 2008-05-08
Everything sorted out.Thanks for everyones help here.The problem was I wasn't booting with the kernel that I thought I was.And the one I was booting with didn't have headers installed.Switched to proper kernel which had headers already installed and drivers installed no prob except for my login screen only working right on plain setting.

---

### Post by cooltuyul on 2008-05-09
man i, cant get anything working!

---

### Post by jimbo99 on 2008-05-09
You have to install libc6 (the dev files).  No I don't know the exact name of it.  You'll find it if you open synaptic and look for libc.

You can't have the gdm running so hence you have to run (whatever your preference is) the command:  

sudo /etc/init.d/gdm stop.

You don't need to change the execute permission of the .run file from nVidia.  You simply, in the terminal window, type:

sudo sh NVIDIA*.run 

(hopefully you only have one file that starts with that).

Let her rip.

Unfortunately though you are going to have many other issues even if you do get it up and running because, for some reason under Hardy Heron, they messed up running this sort of driver.  You may get it to run but when you reboot and come back at some future date you'll get the "can't detect your video card nor display) and it puts you into this crappy low res mode (but worse, there's no way to resolve the issue with that low res mode utility).

It's a failed experiment and should be removed totally and forever.

One final comment regarding those responding to you.  Some people issued far far to elaborate and unnecessarily complex commands.  Keep it simple stupid, is the general rule.  Keep in mind also, that is someone is giving you excessively detailed commands to change permissions, etc for something as simple as installing a video driver they are probably just writing this because they like to hear their own voice.  Again, keep it simple stupid is the best rule you can follow.

---

### Post by cooltuyul on 2008-05-09
are there any big computer repair stores around for linux regarding this issue? Because my head is spinning with codes!

---

### Post by cooltuyul on 2008-05-18
well, on my mobo (ECS Geforce6100PM-M2) i have an on board video chip (NVIDIA GeForce 6100/P-based. 2D/3D graphic engine). is it worth continuing this struggle for the video card, or should a find a driver for this onboard video chip.

---

### Post by histolo2 on 2008-06-10
hey guys i was looking around the net for a solution and found this thread:
[http://ubuntuforums.org/showthread.php?t=596875](http://ubuntuforums.org/showthread.php?t=596875)
looks promising, will update if it succeed (currently i'm not home)

---

### Post by cooltuyul on 2008-06-15
its fixed!!!  a new driver came out; my problem is resolved!

---

