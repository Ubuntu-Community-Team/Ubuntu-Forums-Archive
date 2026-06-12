---
title: "Blank Screen After Upgrading to Ubuntu 23.04"
date: 2023-06-15
forum: Installation &amp; Upgrades
---

### Post by tb75252 on 2023-06-15
Yesterday I upgraded to Ubuntu 23.04 (64-bit).  I had v. 22.10.
Now when I boot up the scrolling stops for a few seconds at the line that says:
***Started wpa_supplicant service*** (or something like that!)
and then the screen goes blank, except for the blinking cursor on the top-left corner.

What can I do to fix this issue?

---

### Post by Rubi1200 on 2023-06-16
Hi,

at the blank screen, blinking cursor use Ctrl+Alt+F3 to get to the TTY console. Login using username and password.

Then try the following commands in order:

```

sudo apt update
sudo dpkg --configure -a
sudo apt upgrade -y
```

If all goes well and there are no errors then

```
sudo reboot
```

---

### Post by tb75252 on 2023-06-16
> **Rubi1200 said:**
> Hi,

at the blank screen, blinking cursor use Ctrl+Alt+F3 to get to the TTY console. Login using username and password.

Then try the following commands in order:

```

sudo apt update
sudo dpkg --configure -a
sudo apt upgrade -y
```

If all goes well and there are no errors then

```
sudo reboot
```
Ran the three commands as instructed but I still get a blank screen with a blinking cursor when rebooting.
When running
```
sudo apt upgrade -y
```
the system tells me that the following packages have been kept back:
> gdm3
gir1.2-gdm-1.0
libgdm1
Maybe this has something to do with my problem...

---

### Post by ubfan1 on 2023-06-16
Try to force the issue, taking a look with dry-run first:
sudo apt -o APT::Get::Always-Include-Phased-Updates=true upgrade --dry-run

---

### Post by tb75252 on 2023-06-16
> **ubfan1 said:**
> Try to force the issue, taking a look with dry-run first:
sudo apt -o APT::Get::Always-Include-Phased-Updates=true upgrade --dry-run
Unfortunately I still get the blank screen with the blinking cursor.

---

### Post by ajgreeny on 2023-06-17
We need to see the output of that dry-run command;
Using dry-run means no changes were made but all was simulated to check what would actually happen.

Do it again and show us the output using Code-Tags please

---

### Post by TheFu on 2023-06-17
> **tb75252 said:**
> 
***Started wpa_supplicant service*** (or something like that!)


That's 99.99999% unrelated.  WPA supplicants are for wifi WPA stuff.  If you aren't running a laptop, then you can safely disable that. No server nor desktop should be using wifi.

---

### Post by tb75252 on 2023-06-17
> **ajgreeny said:**
> We need to see the output of that dry-run command;
Using dry-run means no changes were made but all was simulated to check what would actually happen.

Do it again and show us the output using Code-Tags please
Here we go:
```
Reading package lists...  Done
Building dependency tree...  Done
Reading state information...  Done
Calculating upgrade...  Done
The following packages will be upgraded:
    gdm3  gir1.2-gdm-1.0  libgdm1
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
Inst gdm3 [44.0-1ubuntu1] (44.0-1ubuntu2 Ubuntu:23.04/lunar-updates [amd64]) []
Inst libgdm1 [44.0-1ubuntu1] (44.0-1ubuntu2 Ubuntu:23.04/lunar-updates [amd64]) []
Inst gir1.2-gdm-1.0 [44.0-1ubuntu1] (44.0-1ubuntu2 Ubuntu:23.04/lunar-updates [amd64])
Conf gdm3 (44.0-1ubuntu2 Ubuntu:23.04/lunar-updates [amd64])
Conf libgdm1 (44.0-1ubuntu2 Ubuntu:23.04/lunar-updates [amd64])
Conf gir1.2-gdm-1.0 (44.00-1ubuntu2 Ubuntu:23.04/lunar-updated [amd64])

```

---

### Post by ubfan1 on 2023-06-17
Looks OK to me to run without the --dry-run.  gdm3 is still only 10% phased, so it'll probably be awhile if you wait.  I had a similar issue with the Nvidia driver having a piece held back, so the thing couldn't build, but just waiting a day fixed that problem for me.

---

### Post by tb75252 on 2023-06-18
> **ubfan1 said:**
> Looks OK to me to run without the --dry-run.  gdm3 is still only 10% phased, so it'll probably be awhile if you wait.  I had a similar issue with the Nvidia driver having a piece held back, so the thing couldn't build, but just waiting a day fixed that problem for me.
Unfortunately I still get the blank screen with the blinking cursor.
You did mention that you had problems with the Nvidia driver.  I did have Nvidia drivers installed in v. 22.10.  Could there be some incompatibility with such drivers in v. 23.04?

---

### Post by ubfan1 on 2023-06-18
What Nvidia driver are you running?  Anything with "-open" at the end of the name may have problems with some scripts thinking the name should end in a version number.  Try a virtual terminal (ctrl+alt+F3 etc.) and see if you can login.  From there you may check/reinstall the previous Nvidia driver.  I've only had problems with Nvidia drivers that once -- normally, things just work for me.

---

### Post by tb75252 on 2023-06-18
> **ubfan1 said:**
> What Nvidia driver are you running?  Anything with "-open" at the end of the name may have problems with some scripts thinking the name should end in a version number.  Try a virtual terminal (ctrl+alt+F3 etc.) and see if you can login.  From there you may check/reinstall the previous Nvidia driver.  I've only had problems with Nvidia drivers that once -- normally, things just work for me.
I ended up uninstalling the Nvidia driver with this command:
```
sudo apt-get remove --purge '^nvidia-.*'
```
I think that the problem is that I have an old Nvidia graphics card (GeForce GT 620) and that the v. 390 driver that was installed is not compatible with Ubuntu 23.04.  Because my graphics card is old, I cannot install a newer Nvidia driver.

---

