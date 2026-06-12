---
title: "Nvidia 8800GT display drivers"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by Timberwolf92 on 2007-12-23
so, I get my 8800GT (so excited) and when I boot up Ubuntu I get an error saying that it could not detect my graphics card correctly (or something like that) and will start in low graphics mode. Okay, I say.. and head on over to Nvidia.com, but I can't find the correct driver. Eventually my friend points me to the Synaptic package manager, where I download the nvidia-gtx-new package, and install... well, that brings everyone up to date. I've restarted... and nothing's happened. still the same low graphics mode, highest resolution is 800x600... any help out there?

---

### Post by PmDematagoda on 2007-12-23
Remove the nvidia-glx packages using:-
```

sudo apt-get remove nvidia-glx-new
```

Go [here]("http://www.nvidia.com/object/unix.html") to get the driver for Linux.

After you download it kill the GUI using:-

```
sudo /etc/init.d/gdm stop
```

Then navigate to where the installer is and execute it:-

```
sudo sh nameofinstaller
```

After it is installed reconfigure the X-Server using:-

```
sudo dpkg-reconfigure xserver-xorg
```

After the X-Server is reconfigured do:-

```
sudo /etc/init.d/gdm start
```

---

### Post by IanW on 2007-12-23
Note that Nvidia's latest driver (Version 169.07) WILL wind up your video card's fan to full throttle.
This is a known bug & Nvidia is already working on it.

---

### Post by Timberwolf92 on 2007-12-23
Alright... I tried to do exactly what you said, but I keep on getting the error "could not open NVIDIA-Linux-x86-169.07-pkg1.run" is there anyway I can get a different file instead of this .run? (sorry, total newbie here.)

---

### Post by PmDematagoda on 2007-12-23
Do:-

```
chmod +x NVIDIA-Linux-x86-169.07-pkg1.run
```

Then try:-

```
sudo sh NVIDIA-Linux-x86-169.07-pkg1.run
```

---

### Post by Timberwolf92 on 2007-12-23
another error. Could not open, No such file or directory when I typed in

chmod +x NVIDIA-Linux-x86-169.07-pkg1.run

---

### Post by PmDematagoda on 2007-12-23
Could you please post the result of:-

```
ls  <-- l being simple L not number 1
```
and 

also post where you downloaded the installer to.

---

### Post by Timberwolf92 on 2007-12-23
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos

downloaded to desktop

---

### Post by PmDematagoda on 2007-12-23
Ok, first move to Desktop using:-
```

cd Desktop
```
Then do:-
```

sudo sh NVIDIA-Linux-x86-169.07-pkg1.run
```

---

### Post by Timberwolf92 on 2007-12-23
alright, that starts it up, but then It says there is no precompiled kernel interface found, so I selected for it to try and download one from the NVIDIA FTP. it couldn't find one, so it said the installer would have to make one. Then I get an error saying I do not have the libc headers, and installation fails.

---

### Post by PmDematagoda on 2007-12-23
Ok, first things are first. Post the result of:-
```

uname -a
```
and
Install the build-essential packages:-
```

sudo apt-get install build-essential
```

After the build-essential is installed try installing the driver again, the uname -a output does not matter much in the driver install, but it would help me understand something.

---

### Post by Timberwolf92 on 2007-12-23
heres the uname 
Linux HAL-9000 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux


will try others now

---

### Post by PmDematagoda on 2007-12-23
You kernel 2.6.22 does not need to compile a kernel usually, do you have a stable internet connection?

---

### Post by Timberwolf92 on 2007-12-23
yes, SBC DSL
also, when I quit the GUI, when I type now, nothing happens.. Can't even re enable the console, I have to manual restart.

---

### Post by PmDematagoda on 2007-12-23
When you quit the GUI you can't type?

If you cannot do that, then switch to a tty by pressing Ctrl+Alt+F1, that should let you type, the same commands I gave previously can be used as well.

---

### Post by Timberwolf92 on 2007-12-23
Thanks! That did it!

---

### Post by Timberwolf92 on 2007-12-23
Update... now, whenever I reboot, it doesn't sense the driver, and goes back to low graphics mode. However, when I install again, it says that it's overwriting 169.07.. so it's there...

---

### Post by awilki01 on 2007-12-28
> **PmDematagoda said:**
> Remove the nvidia-glx packages using:-
```

sudo apt-get remove nvidia-glx-new
```

Go [here]("http://www.nvidia.com/object/unix.html") to get the driver for Linux.

After you download it kill the GUI using:-

```
sudo /etc/init.d/gdm stop
```

Then navigate to where the installer is and execute it:-

```
sudo sh nameofinstaller
```

After it is installed reconfigure the X-Server using:-

```
sudo dpkg-reconfigure xserver-xorg
```

After the X-Server is reconfigured do:-

```
sudo /etc/init.d/gdm start
```

I go through this exactly.  Is the xconfiguration supposed to be able to autodetect the new Nvidia driver installed?  It just comes up with a Nvidia Generic driver.  In any event, I restart GDM and things look great (but I'm not sure if the new driver is being used or not - is there a way to tell?)  When I reboot, I end up back in this low resolution mode again.

Any ideas?

EDIT:  I just found another post that referenced the following URL and did the trick for me:
[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html]("http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html")

The key difference between what has been discussed here is the edit of the /etc/default/linux-restricted-modules* file.  Go to the URL above and see....

---

### Post by cooltd825 on 2008-01-22
yeah, i had this exact same problem.  actually, i still have it.  i'm just glad i dual-boot with Vista just in case this kind of thing happens (i'm brand new to Linux, but i love it.  a lot more than Vista)

although it doesn't have the latest driver, i heard Envy doesn't have any of these problems.  would there be a way to download and install Envy through the terminal?  the GUI is basically useless right now because it just brings up a blank black screen.  once again, i've only been using Linux for a week so it could just be a totally wrong hunch.

---

### Post by Partyboi2 on 2008-01-22
Login to a terminal download the deb package
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu1_all.deb

```install the deb
```
sudo dpkg -i envy_0.9.10-0ubuntu1_all.deb
```then to start it via terminal
```
 sudo envy -t
```

---

### Post by linuxbrit on 2008-01-23
Hi,

When you get the proprietary drivers installed, you may still need to make a few mods - I found that I had to edit my /etc/X11/xorg.conf file, and insert the proper dimensions for my screen - in my case 1440x900 as otherwise, even with the correct driver, when I attempted to select the display size, I was still only offered 800x600 as the highest resolution!

:KS I also noted that for some reason the refresh defaulted to 50 which gave me very 'blurred' fonts with little definition. Selecting 56 gave me a great screen, which so far has remained stable. I've found this in Mandriva One 2008 as well as Ubuntu (7.10) so suspect this is a generic problem with the latest NVIDIA drivers across all distributions?

---

### Post by Timberwolf92 on 2008-01-24
Okay, I didn't post my results, so I guess it's my fault. Awilki01's solution did work, and everything is fine on my Ubuntu now. Now stop sending me private messages! :P

---

### Post by Travler on 2008-01-24
> **awilki01 said:**
> 

EDIT:  I just found another post that referenced the following URL and did the trick for me:
[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html]("http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html")

The key difference between what has been discussed here is the edit of the /etc/default/linux-restricted-modules* file.  Go to the URL above and see....

Yes!!:popcorn:  Thank you! after a month of trying 2 different distros, recompiling kernels, downloading from several different repositories, removing and reinstalling drivers and other assorted files because I was following several different methods of getting this driver to work...THIS DID IT!:KS:guitar:

Thanks!

---

