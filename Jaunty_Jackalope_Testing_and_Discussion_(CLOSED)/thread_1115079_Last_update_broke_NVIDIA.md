---
title: "Last update broke NVIDIA"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by swoll1980 on 2009-04-03
This happen to anyone else? Any idea how to fix it?

---

### Post by lcohen999 on 2009-04-03
running fine here, updated this AM

---

### Post by jocheem67 on 2009-04-03
You've got to be more specific....

I did notice that the 180.44 --- the latest stable from nvidia --- installed...
On Jaunty that is.

You can try a 

>  sudo apt-get install nvidia-glx-new 

But that's a very general advice now.

---

### Post by swoll1980 on 2009-04-03
> **jocheem67 said:**
> You've got to be more specific....

I did notice that the 180.44 --- the latest stable from nvidia --- installed...
On Jaunty that is.

You can try a 



But that's a very general advice now.

Thanks for the advise. 
```
sudo apt-get install nvidia-glx-180
```
fixed the problem. I don't know what went wrong during the update that made me reinstall.

---

### Post by robfish on 2009-04-04
> **swoll1980 said:**
> This happen to anyone else? Any idea how to fix it?

Yes I have the same problem but have not been able to fix it yet.
[http://ubuntuforums.org/showthread.php?t=1114731&highlight=jaunty+nvidia](http://ubuntuforums.org/showthread.php?t=1114731&highlight=jaunty+nvidia)

I tried removing nvidia stuff with Synaptic then reinstalling with
sudo apt-get install nvidia-glx-180
but still no joy.
I cannot even find them using System > Hardware drivers now.

---

### Post by Yumi on 2009-04-04
Same problem as robfish reports here since last update. System - Administration - Hardware Drivers does not show the nvidia 180 driver which according to Synaptics is installed (and was before the update).

Sudo apt-get install nvidia-glx-180 results in:
nvidia-glx-180 is already the newest version.
nvidia-glx-180 set to manually installed.

Downloading from Nvidia and trying to install fails with some error like cannot identify the kernel/compile

Maybe related, in terminal I get:
sudo nautilus
** (nautilus:10821): WARNING **: Unable to add monitor: Operation not supported

Michael

---

### Post by robfish on 2009-04-04
I have found the problem on my machine.

The update included a kernel update but Grub was not updated correctly.
There was no Grub entry for the new kernel.
Fixed that and now nvidia drivers are working again.

---

### Post by Yumi on 2009-04-04
How do I fix this grub entry?

---

### Post by vandorjw on 2009-04-04
Whenever you do a kernel update you must re-install your nvidia or ATI drivers.

---

### Post by robfish on 2009-04-04
> **Yumi said:**
> How do I fix this grub entry?

sudo nano -w /boot/grub/menu.lst

Worked for me.
You could check which kernel is being used with
uname -r
You can check which kernel is installed with synaptic.

You should check that the required files are there (for Grub to point to)

---

### Post by Yumi on 2009-04-04
No, reinstalling the nvidia 180 driver from synaptics did not change anything. Still no driver in Hardware Drivers.

---

### Post by taavikko on 2009-04-04
> **cc7gir said:**
> Whenever you do a kernel update you must re-install your nvidia or ATI drivers.

Manually, no.
If installed via hardware-drivers, this thing called dkms builds it for kernel automatically.

Let's just check what you have installed.
```
dpkg -l nvidia-\*
```

and if nvidia is been built
```
dkms status
```
You can also use dkms to build it again, if its missing
for more info, see "man dkms"

---

### Post by Yumi on 2009-04-04
Output is as follows
```
dpkg -l nvidia-\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
pn  nvidia-173-ker <none>         (no description available)
pn  nvidia-173-mod <none>         (no description available)
pn  nvidia-177-ker <none>         (no description available)
pn  nvidia-177-mod <none>         (no description available)
ii  nvidia-180-ker 180.44-0ubuntu NVIDIA binary kernel module source
ii  nvidia-180-lib 180.44-0ubuntu Video Decode and Presentation API for Unix
pn  nvidia-180-mod <none>         (no description available)
un  nvidia-71-kern <none>         (no description available)
pn  nvidia-71-moda <none>         (no description available)
un  nvidia-96-kern <none>         (no description available)
pn  nvidia-96-moda <none>         (no description available)
rc  nvidia-common  0.2.9          Find obsolete NVIDIA drivers
rc  nvidia-glx     1:96.43.05+2.6 NVIDIA binary XFree86 4.x/X.Org driver
rc  nvidia-glx-173 173.14.16-0ubu NVIDIA binary Xorg driver
rc  nvidia-glx-177 177.82-0ubuntu NVIDIA binary Xorg driver
ii  nvidia-glx-180 180.44-0ubuntu NVIDIA binary Xorg driver
un  nvidia-glx-71  <none>         (no description available)
un  nvidia-glx-96  <none>         (no description available)
un  nvidia-glx-env <none>         (no description available)
un  nvidia-glx-leg <none>         (no description available)
un  nvidia-glx-leg <none>         (no description available)
rc  nvidia-glx-new 169.12+2.6.24. NVIDIA binary XFree86 4.x/X.Org 'new' driver
un  nvidia-glx-new <none>         (no description available)
un  nvidia-glx-src <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
ii  nvidia-kernel- 20080825+1ubun NVIDIA binary kernel module common files
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-legacy- <none>         (no description available)
un  nvidia-legacy- <none>         (no description available)
un  nvidia-new-ker <none>         (no description available)
un  nvidia-new-ker <none>         (no description available)
ii  nvidia-setting 180.25-0ubuntu Tool of configuring the NVIDIA graphics driv
pn  nvidia-xconfig <none>         (no description ava
```

```
dpkg -l nvidia-\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
pn  nvidia-173-ker <none>         (no description available)
pn  nvidia-173-mod <none>         (no description available)
pn  nvidia-177-ker <none>         (no description available)
pn  nvidia-177-mod <none>         (no description available)
ii  nvidia-180-ker 180.44-0ubuntu NVIDIA binary kernel module source
ii  nvidia-180-lib 180.44-0ubuntu Video Decode and Presentation API for Unix
pn  nvidia-180-mod <none>         (no description available)
un  nvidia-71-kern <none>         (no description available)
pn  nvidia-71-moda <none>         (no description available)
un  nvidia-96-kern <none>         (no description available)
pn  nvidia-96-moda <none>         (no description available)
rc  nvidia-common  0.2.9          Find obsolete NVIDIA drivers
rc  nvidia-glx     1:96.43.05+2.6 NVIDIA binary XFree86 4.x/X.Org driver
rc  nvidia-glx-173 173.14.16-0ubu NVIDIA binary Xorg driver
rc  nvidia-glx-177 177.82-0ubuntu NVIDIA binary Xorg driver
ii  nvidia-glx-180 180.44-0ubuntu NVIDIA binary Xorg driver
un  nvidia-glx-71  <none>         (no description available)
un  nvidia-glx-96  <none>         (no description available)
un  nvidia-glx-env <none>         (no description available)
un  nvidia-glx-leg <none>         (no description available)
un  nvidia-glx-leg <none>         (no description available)
rc  nvidia-glx-new 169.12+2.6.24. NVIDIA binary XFree86 4.x/X.Org 'new' driver
un  nvidia-glx-new <none>         (no description available)
un  nvidia-glx-src <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
ii  nvidia-kernel- 20080825+1ubun NVIDIA binary kernel module common files
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-legacy- <none>         (no description available)
un  nvidia-legacy- <none>         (no description available)
un  nvidia-new-ker <none>         (no description available)
un  nvidia-new-ker <none>         (no description available)
ii  nvidia-setting 180.25-0ubuntu Tool of configuring the NVIDIA graphics driv
pn  nvidia-xconfig <none>         (no description ava
```

Thanks for your assistance
Michael

---

### Post by taavikko on 2009-04-04
Remove the cruft via
```
sudo apt-get --purge autoremove && sudo apt-get clean
```

Then re-install nvidia
```
sudo apt-get --reinstall install nvidia-glx-180
```
If it doesn't pull modaliases pkg, install them separately,
```
sudo apt-get --reinstall install nvidia-180-modaliases
```

Then refresh jockeys database.
```
sudo jockey-gtk -u -c
```

Does it then display?
```
gksudo jockey-gtk
```

---

### Post by Yumi on 2009-04-04
Followed your instructions with paste & copy. Now luck, gksudo jockey-gtk still displays nothing.

Michael

---

### Post by eyefragment on 2009-04-04
Robfish's fix worked for me.  If you're attempting to install the nvidia drivers manually, and it's telling you something about missing the kernel-source file, check if the following two things match:

1)  The kernel version given by running "uname -r" in the terminal
2)  The kernel versions found in /usr/src

If they don't match, your boot menu has probably been screwed up one way or another (in my case, I told the package manager not to update my menu.lst, thinking that I liked my menu.lst as it was right now and not realizing that without doing the update, I would be running the wrong version of the kernel!  Perhaps this should be made more clear for those of us who don't know the linux boot process?  I'm not sure where to make that suggestion...).  Check to see if you have a more recent version of the kernel listed under /boot (in my case, I was running 2.6.27-7-generic, but there was a 2.6.28-11-generic listed in my /boot folder), and update your grub (sudo emacs /boot/grub/menu.lst) to use the newer kernel (not including the title line, there are two lines that you need to change).  Then reboot and install the nvidia drivers using whatever method you'd like.

That fixed my drivers, at least.

---

### Post by jocheem67 on 2009-04-04
One should review it's sources I think, cause just maybe the people with problems with their drivers installed from 'proposed' and 'backports'....
It would be safer to not add those.

---

### Post by robfish on 2009-04-04
Thanks taavikko.

Your instructions (changed slightly) got my GUI for System > Hardware Drivers working again.

I did......
sudo apt-get --reinstall install nvidia-180-modaliases
sudo apt-get --reinstall install jockey-kde
jockey-kde -u -c (this line did not work with sudo)
jockey-kde

---

### Post by robfish on 2009-04-04
> **Yumi said:**
> Followed your instructions with paste & copy. Now luck, gksudo jockey-gtk still displays nothing.

Michael

Yumi, I think you now need to clarify a few things for us.

Did you check what is the latest kernel you have installed?
Did you check/correct grub so it points to the correct kernel?
Have you checked that nvidia is enabled in /etc/X11/xorg.conf ?
Are you getting as far as Gnome or KDE working?

Once you have booted into the correct kernel but only have a terminal I suggest the following:-

sudo apt-get --purge autoremove && sudo apt-get clean
sudo apt-get --reinstall install nvidia-glx-180
sudo apt-get --reinstall install nvidia-180-modaliases
sudo nano -w /etc/X11/xorg.conf (check nvidia is enabled)
sudo reboot

Then to get hardware device GUI working again:-
(for Gnome)...
sudo apt-get --reinstall install jockey-kde
jockey-gtk -u -c (this line did not work for me with sudo)
jockey-gtk

(for KDE)
sudo apt-get --reinstall install jockey-kde
jockey-kde -u -c (this line did not work for me with sudo)
jockey-kde

---

### Post by Yumi on 2009-04-05
Puuh:-) at last it is working for me again as well. We even had another kernel update today I noticed.

In the end it was quite easy.

1. As you alerted me to the kernel version, I noticed that the grub menu booted into 2.6.28-8 while after the update installed is 2.6.28-11-40.

Altered the Grub menu manually and a restart booted into the right kernel. Nvidia driver was visible again in System - Administration - Hardware Drivers and enabled.

2. Renamed my backup version of /etc/X11/xorg.conf.5 to xorg.conf and another restart got my display working properly again.

Thanks a lot for all your help. I learned a lot going through all the suggestions.

Michael

---

### Post by robfish on 2009-04-06
> **Yumi said:**
> 2. Renamed my backup version of /etc/X11/menu.lst to xorg.conf and another restart got my display working properly again.

Not sure what you mean by this but nice that you are going well again.

---

### Post by Yumi on 2009-04-06
Sorry robfish. Was a long day. I corrected the post. Thanks again for pointing me in the right direction.

Michael

---

### Post by Irishpolyglot on 2009-04-09
I'm glad this thread was pointed out to me!! I thought I had somehow broken my computer. Sadly I'm still stuck - I enthusiastically applied the code provided above and it actually made things worse!! I got a host of new errors, had no options at boot up or access to the GUI (like I do now) and the file system was riddled with errors; automatically scanning itself on boot up. Even reinstalling the OS (currently 9.04 beta) wasn't possible until I formatted the drive. So I'm back to square one. I'll admit that I tried a few things mentioned above ( sudo apt-get install nvidia-glx-180 , sudo apt-get --reinstall install nvidia-180-modaliases , jockey-kde -u -c ...), so maybe the combination messed things up.

Basically, I'm on 9.04 beta (but I was on 8.10 when the problem started) and I **can** access the GUI of Ubuntu, but only because I reinstalled the operating system. Even the installation CD won't load correctly unless I go to "mode" options and select "safe graphics". Back in the fresh install I **do** have access to the 180 hardware driver in Hardware Drivers through System->Administration, but activating it and rebooting give me the black screen after the Ubuntu loading screen and Ctrl+Alt+F1/F7/Backspace or any other combination doesn't do anything for me. The result is the same with previous versions of the hardware driver (173 and 96 are in the list) too.

The only way to get out of it if I apply the driver is to run xfix by selecting recovery mode from grub. So I can access everything, but in the lowest resolution since drivers aren't applied; obviously this limits what I can do.

I'm on a Dell Inspiron 9400 with nVidia Geforce Go 7800. Any help hugely appreciated! I've been without a useful computer all week...

---

### Post by Irishpolyglot on 2009-04-10
It's working now; I had to select recovery mode at grub - it didn't give me the usual selection screen; it went straight into scanning the drive, then on reboot it scanned the drived AGAIN with the Ubuntu loading screen. Then I was shown a list of things to fix (selecting 'y' for each) and now everything seems to be working.
If the driver crashes again I'll start a new thread since my problem seems different to the one here, even if the cause is the same.

---

