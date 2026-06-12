---
title: "update error: not all updates can be installed"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by sarikan on 2007-01-10
Hi there, 
I have just booted my laptop with ubuntu 6.10 and synaptics gave me the mentioned error in header: not all updates can be installed.
There are 3 updates, but linux restricted modules 2.6.17.10 is not selected, the others are linux restricted modules common, and xserver-xorg-core
I am using beryl with nvidia drivers so it may be related to that. Has anyone come across this problem? Synaptic offers me a distribution update, but I do not want to break things. What should I do?

Regards
Seref Arikan

---

### Post by geokok1981 on 2007-01-10
Same problem here. The update distro option fails so dont worry that is not the solution. 
I get two restricted modules versions: one for 386 (ticked) and one for generic (not possible to choose). Any clues???

I disabled any third party repos I had (beryl, seaofsouls, automatix) but problem still there. 
Any clues???

P.S. As u probably have guessed I have latest nvidia drivers, beryl, automatix installed.

---

### Post by sarikan on 2007-01-10
oh, I was about to try the distro update, but I'd better not try that, since it did not work out with you. This is kinda annoying; anyone else with this problem?

Regards
Seref Arikan

---

### Post by nkkromhof on 2007-01-10
I did manage to get my distro upgraded, and now my X is broken, doh!

Reconfiguring through dpkg-reconfigure -phigh -xserver-xorg did NOT fix it... looking around for ways to get my Edgy box working again now :-(

---

### Post by Zalbor on 2007-01-10
In mine, I imagine it can't work because I've installed nvidia drivers from lupine, and the restricted modules from the official repository don't support them. If I installed that, it would break X.

---

### Post by sarikan on 2007-01-10
that's what I was afraid of. the install process for beryl has not been that straightforward for me; I've tried this and that to get it working; but now users like us seem to have a problem. Is there a more experienced user who can provide us with input to get back to the "common" path with the others? (Without using beryl of course)
There are a lot of ubuntu users who also use beryl, is this a rare problem?

Regards
Seref Arikan

---

### Post by geokok1981 on 2007-01-10
Not sure that official nvidia drivers cause this cause others have installed them and had no problem updating today.....

---

### Post by arnieboy on 2007-01-10
The latest kernel update breaks the seerofsouls nvidia-glx package and synaptic will uninstall it in order to install the latest kernel updates from Ubuntu.
To avoid any breakages do this, 
```
sudo gedit /etc/apt/sources.list
```
or use **kwrite** instead of **gedit** on Kubuntu or **nano** if you prefer the command line.
and comment the following line:
> deb [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy contrib
by changing it to:
> #deb [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy contrib
now add the following line to the same file:
> deb [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) binary/
now save the file, close it
and do
```
sudo apt-get remove nvidia-glx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-glx

```
Now restart your computer.

---

### Post by reiki on 2007-01-10
I need to find a solution for this as well. Updater won't install the new restricted modules for generic (Edgy) and if I tell it to install them it says it's going to uninstall nvidia-glx. I have the nVidia 9629 drivers installed. It updated everything else, but not the generic restricted modules and until I know more I'm not letting it install them and remove the nvidia-glx package.

What gives?

Seems this got answered while I was typing... :)

---

### Post by geokok1981 on 2007-01-10
@arnieboy

Thanks, but after following your instructions I saw that Nvidia settings (gui in the applications menu) mentioned the previous version of drivers I had (9629) while your guide was supposed to install the latest (97xx). I run glxinfo and the result was bad.....

```
~$ glxinfo
name of display: :0.0
Error: API mismatch: the NVIDIA kernel module has the version 1.0-9629, but
this client has the version 1.0-9746.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
display: :0  screen: 0
direct rendering: No

```

---

### Post by arnieboy on 2007-01-10
> **geokok1981 said:**
> @arnieboy

Thanks, but after following your instructions I saw that Nvidia settings (gui in the applications menu) mentioned the previous version of drivers I had (9629) while your guide was supposed to install the latest (97xx). I run glxinfo and the result was bad.....

```
~$ glxinfo
name of display: :0.0
Error: API mismatch: the NVIDIA kernel module has the version 1.0-9629, but
this client has the version 1.0-9746.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
display: :0  screen: 0
direct rendering: No

```

restart the computer.

---

### Post by geokok1981 on 2007-01-10
> **arnieboy said:**
> restart the computer.

Just did that....well I guess part of me will always be a noob....but then again, what would u guys do without my questions, huh?

Thanks mate, everything works great here.

---

### Post by sarikan on 2007-01-11
Arnieboy: thanks a lot; everything is working just fine now :)

---

### Post by reiki on 2007-01-11
This worked great for me as well. One question. How do I install the key for 

deb [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) binary/

so that I don't get nastygrams about it being unauthenticated?

---

### Post by sarikan on 2007-01-11
Bad news; these new drivers seem to have a problem with my console. When I switch to another console with Alt+f2 etc, I get really nasty fonts, which looks like they have been erased or blurry. 
I do not use console that much; but having a nice console would not hurt. Any ideas about this one?
Regards

---

### Post by umattu on 2007-01-11
Guys check out this thread.  [http://www.ubuntuforums.org/showthread.php?t=335080&highlight=nvidia-kernel](http://www.ubuntuforums.org/showthread.php?t=335080&highlight=nvidia-kernel)

the problem has been addressed and should be fixed.;)

---

### Post by arnieboy on 2007-01-11
> **reiki said:**
> This worked great for me as well. One question. How do I install the key for 

deb [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) binary/

so that I don't get nastygrams about it being unauthenticated?

The repository is not GPG secured yet. You can request Alberto (tseliot) to make it GPG secured.

---

