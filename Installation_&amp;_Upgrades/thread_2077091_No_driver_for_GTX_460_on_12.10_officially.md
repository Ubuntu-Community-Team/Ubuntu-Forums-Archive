---
title: "No driver for GTX 460 on 12.10 officially"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by Drimux on 2012-10-27
Greetings, 

I've got a strange problem with a clean new installation of Ubuntu 12.10... 

Before that, the driver for my 460GTX appeared.

But now:
[IMG]http://image.noelshack.com/fichiers/2012/43/1351178028-capture-du-2012-10-25-17-03-13.png[/IMG]
Nothing!

But lspci *sees* my graphic card...
```
01:00.0 VGA compatible controller: NVIDIA Corporation GF104 [GeForce GTX 460] (rev a1)
```Damn..
So what to do?

I think, the better was install jockey-common and using ```
sudo jockey-text -e kmod:nvidia_current
``` but my resolution is low... so I use *nvidia x server* to change manually the resolution for a correct one, but I've got some errors : *MetaMode [a number] of Screen [a number]  does not have an active display device.* With Auto-fix, the resolution is fine... however it seems not to be a safe solution ; It's like a terrible regression. And I don't want to get some troubles later with that...

So? What do you suggest?


Thank you!
Regards.

---

### Post by Drimux on 2012-10-28
Little up
Sorry to disturb you for this.

---

### Post by Tobeus on 2012-11-14
Just a head's up:

I'm also using an nVidia GTX 460 and when I went to upgrade from 12.04 to 12.10 the updater told me that there was a lack of driver support in 12.10 for my hardware and that I would likely have slow/sluggish response using the built-in nouveau driver.  I upgraded anyway to see what I could break and had very little luck with any of the ppa nvidia drivers.

I downloaded the 3.10 beta drivers from nvidia's website.  After purging all the ppa nvidia drivers and stopping lightdm
```
sudo stop lightdm
```I was able to run the installer and follow the directions to install the video driver.  It had to install a file into /etc/modprobe.d/ in order to prevent the built-in nouveau drivers from loading, and then reboot first, but after I restarted the installer it finished without a hitch.  I rebooted and there was Unity staring at me.

Personally, I feel like 12.10 is still only half-baked for some nvidia users due to the Unity integration, so I might just go back to 12.04 for a while.  I just wish there was a better hardware compatibility list for this kind of thing that balanced Nvidia, Linux, Unity, and Ubuntu compatibility to find out what really works.

Good luck, and hope this helps a bit!

-Tobeus

---

### Post by zite83 on 2012-11-14
I've gotten my 580 GTX to work just fine with Ubuntu 12.10.

Go to Nvidia's website and download the right driver.

[IMG]http://i284.photobucket.com/albums/ll35/zite83/Ubuntu/460gtx.jpg[/IMG]

Once the file is finished downloading, set it to be executable.

Open up a terminal and do the following.

[PHP]sudo nano /etc/modprobe.d/blacklist.conf[/PHP]Insert this at the bottom.

[PHP]blacklist amd76x_edac  #this might not be required for x86 32 bit users.
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
[/PHP]Save and exit

Next type the following commands in terminal

[PHP]
sudo apt-get remove --purge nvidia*

sudo apt-get install build-essential

sudo apt-get install linux-headers-$(uname -r)
[/PHP]Logout and at the login screen ctrl+shift+f1

Log back in through the terminal

Type
[PHP]sudo service stop lightdm[/PHP]Navigate to your drivers and install by

[PHP]sudo ./NVIDIA-Linux-???.??.???.run[/PHP]It will ask for user agreement say yes.
It will then say install script failed, click yes and continue
It should start installing kernel modules
Next it will have a few config screens just say yes to all
Reboot

---

### Post by phoel on 2013-03-20
Thanks, very good, works also for the GTX 460 on 12.10, after trying all the standard methods described by Nvidia etc. that failed.
With the standard nouveau driver I had strange artifacts on my desktop.

I used the latest nvidia update NVIDIA-Linux-x86_64-310.40.run

For getting into the console use ctrl+alt+f1, not ctrl+shift+f1.
Use [FONT=courier new]sudo sh ./NVIDIA-Linux-x86_64-310.40.run[/FONT]

Bye

---

