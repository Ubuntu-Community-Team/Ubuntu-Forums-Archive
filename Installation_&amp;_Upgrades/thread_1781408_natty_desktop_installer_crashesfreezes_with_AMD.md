---
title: "natty desktop installer crashes/freezes with AMD"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by jmborr on 2011-06-13
Trying to install ubuntu 11.04 drove me nuts until I found this [page ]("http://halffull.org/2008/10/25/how-to-fix-an-ubuntu-crash/").

My system is an ASUS moderboard with an AMD chipset. The solution came when I entered the BIOS and disabled the cool&quiet feature for the chipset.

After installation, I have to keep cool&quiet disabled in order to run ubuntu. Re-enabling cool&quiet results in ramdon restarts or freezing :(

I hope this serves of help to anyone in a similar predicament.

---

### Post by jmborr on 2011-06-13
I have dual boot, and I don't want the grub startup menu to vanish after a few seconds, I want it to stay.

First, don't waste your time installing the startup-manager application
```
sudo apt-get install startupmanager
```
which I did. this application does not allow you to deactivate the timeout.

Instead:
```
cd sudo vi /etc/default/grub
```
set variable **GRUB_TIMEOUT** to **-1** and exit. Then...
```
sudo update-grub
```

and voila! A new /boot/grub/grub.cfg file is generated with **timeout=-1**

---

### Post by jmborr on 2011-06-13
This thread is becoming a log of my ubuntu install :p

The onboard sound was not detected by ALSA. First, we find the sound device:

```
*sudo aplay -l*

**** List of PLAYBACK Hardware Devices ****
card 0: M5455 [ALi M5455], device 0: Intel ICH [ALi M5455]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Amazingly, a search in this forum for "ALi M5455" resulted in a [thread]("http://http://ubuntuforums.org/showthread.php?t=317061") with the correct solution, which I reproduce here:

```
*sudo gedit /etc/modprobe.d/alsa-base.conf*
```

We comment this line:

```
#options snd-intel8x0m index=-2
```

and after that line we add this:

```
options snd-intel8x0 buggy_semaphore=1
```

Then reboot the computer.
sweet :guitar:

---

### Post by jmborr on 2011-06-14
My Xorg session uses a big fraction of CPU power. It may be that the graphics card is not helping because of the nvidia drivers have not been installed. Commands:
```
lsmod | grep nvidia
lsmod | grep nv
```
results in no output

The nvidia drivers are located in [this page.]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

My system (video card PNY Verto GeForce FX 5500 with linux 32-Bit) requires driver NVIDIA-Linux-x86-173.14.30-pkg1.run

Add executable permissions:
```
chmod a+x NVIDIA-Linux-x86-173.14.30-pkg1.run
```

Log-out and then login in a "recovery console" session.

Stop the X-server:
```
sudo /etc/init.d/gdm stop
```

Bring the loging prompt by pressing Ctrl+Alt+F1 and login, then install the driver
```
sudo ./NVIDIA-Linux-x86-173.14.30-pkg1.run
```

The installer informed me I had to disable 'Nouveau'. The installer prompted this message:

"*The modprobe configuration file to disable Nouveau, /etc/modprobe.d/nvidia-installer-disable-nouveau.conf, has been written. For some distributions this may be sufficient to disable Nouveau; other distributions may require modification of the ramdisk. Please **reboot** your system and attempt NVIDIA driver installation again. Note if you later wish to re-eenale Nouveau, you will need to **delete** the file /etc/modprobe.d/nvidia-installer-disable-nouveau.conf.*"

and this message:

"*Error: installation has failed. Please see this file '/var/log/nvidia-installer.log" for details. You may find suggestions in the README file availabe on the Linux driver download page at [www.nvidia.com](www.nvidia.com)*"

I rebooted the computer
```
sudo shutdown -r now
```

Again:
- login in the 'recovery console' session, kill the X-server
```
sudo /etc/init.d/gdm stop
```
- bring the login prompt, login, and re-issue the command to start the installer ```
sudo /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
```

The installer built the kernel, and I accepted all suggestions in the installation processes.

After installation finished, I rebooted the computer (may be not necessary)

Check:
```
lsmod | grep nvidia
*nvidia    7098106 nvidia*
```

---

### Post by jmborr on 2011-06-14
I don't like my files in /tmp being removed every time I reboot the computer. The solution turned out to be very simple:

1- edit file /etc/default/rcS
2- change value of TMPTIME to -1

For more info on this file:
```
man rcS
```

---

### Post by jmborr on 2011-07-15
Yesterday I was offered some updates and accepted them all, as I routinely do (sigh!). I briefly saw one of the updates was a kernel update.

Today the computer would not run to level 5. As it turned out, the nvidia module could not be loaded. Then I remembered the kernel update, and the fact that my nvidia modules were compiled against the old kernel: aaaarrrgggg!!!!

I crossed my fingers and reinstalled the nvidia drivers (see my previous post on installing). The trick worked! I almost did not believe it that my assessment of the problem turned out to be correct :guitar:.

---

