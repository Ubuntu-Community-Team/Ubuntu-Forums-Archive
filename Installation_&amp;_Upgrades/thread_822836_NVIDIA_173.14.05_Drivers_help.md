---
title: "NVIDIA 173.14.05 Drivers help"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by RESID3NT on 2008-06-08
Hi there. I have a problem installing these drivers on Hardy, that I hope you guys can help me.


So, I do CTRL+ALT+F2 to go console, and then
sudo apt-get install build-essential to install libc
sudo /etc/init.d/gdm stop to stop X
sudo chmod +x NVIDIA-drivers 
sudo sh NVIDIA-drivers

So, no problem installing it, when I start X thorugh /etc/init.d/gdm start it goes to my resolution of 1440*900 in a LG L192WS. It even appears the NVIDIA logo when I start X.

But when I restart the computer, the first screen that appears is a "compatability screen" where I have to "select screen + card drivers". When I choose those, the screen goes black with a message saying (from the screen, not from the OS) "Out of synch"

Any ideas on this?
Thanks in advance.

EDIT: 
system info
Hardy32bits
asus8800gts
4GB Ram (only 3.2 detected)

---

### Post by Pumalite on 2008-06-08
Did you let the driver reconfigure your xorg.conf file?

---

### Post by RESID3NT on 2008-06-08
> **Pumalite said:**
> Did you let the driver reconfigure your xorg.conf file?
I didn't have that option.

---

### Post by Unix_Slayer on 2008-06-08
> **RESID3NT said:**
> I didn't have that option.

You must have other drivers installed on your system. The first thing you should have done is:

```
sudo apt-get remove nvidia*
```

Then follow your remaining steps.

[IMG]http://mysite.verizon.net/mgm_mgm/realnv.jpg[/IMG]

---

### Post by RESID3NT on 2008-06-08
> **Unix_Slayer said:**
> You must have other drivers installed on your system. The first thing you should have done is:

```
sudo apt-get remove nvidia*
```

Then follow your remaining steps.

Fresh install. Drivers from rep was not installed.

---

### Post by Pumalite on 2008-06-08
Then you didn't do it right. I assume you have build-essential:
Ctrl+Alt+F1
username
password
sudo /etc/inhit.d/gdm stop
password
sudo sh /path/to/driver/NVIDIA-Linux-xxxx.run
Accept the License
Let the driver compile the module into your kernel
Let the driver reconfigure your xorg.conf file
Then:
startx
Or:
sudo /etc/init.d/gdm start

---

### Post by RESID3NT on 2008-06-08
> **Pumalite said:**
> Then you didn't do it right. I assume you have build-essential:
Ctrl+Alt+F1
username
password
sudo /etc/inhit.d/gdm stop
password
sudo sh /path/to/driver/NVIDIA-Linux-xxxx.run
Accept the License
Let the driver compile the module into your kernel
Let the driver reconfigure your xorg.conf file
Then:
startx
Or:
sudo /etc/init.d/gdm start
What's the difference bwtween CTRL ALT F1 to F2?
Other than that I have don exactly it :|

---

### Post by Pumalite on 2008-06-08
Read carefully and you'll find the offer to reconfigure your xorg.conf file.

---

### Post by RESID3NT on 2008-06-08
> **Pumalite said:**
> Read carefully and you'll find the offer to reconfigure your xorg.conf file.
removed the driver


It still doesn't. But I've tried exactly the same thing with CTRL ALT F1 and "magically" (I'm guessing that it made all the difference), the driver worked after restart :)

However  nvidia-settings says:
Unable to load X Server Display Configuration page:

Failed to parse the following modeline of display device
0x00000002 'LG L192WS' connected to GPU-0 'GeForce 8800 GTS':

source=edid :: "nvidia-auto-select"  106.500  1440 1520 1672 1904  900 903 909 934  -HSync +VSync

Still something left to do.

I appreciate your tips, guys!

---

### Post by Pumalite on 2008-06-08
Configure your monitor in xorg.conf file with exact details.

---

### Post by RESID3NT on 2008-06-08
Will do. I-ll browse around this forum.

Thankz for the info.

---

### Post by Unix_Slayer on 2008-06-08
> **Pumalite said:**
> Then you didn't do it right. I assume you have build-essential:
Ctrl+Alt+F1
username
password
sudo /etc/inhit.d/gdm stop
password
sudo sh /path/to/driver/NVIDIA-Linux-xxxx.run
Accept the License
Let the driver compile the module into your kernel
Let the driver reconfigure your xorg.conf file
Then:
startx
Or:
sudo /etc/init.d/gdm start

Let the driver reconfigure your xorg.conf file
Then:

At this point you reboot.Don't start X up.

---

### Post by Pumalite on 2008-06-08
You can do either one

---

### Post by Unix_Slayer on 2008-06-08
> **RESID3NT said:**
> What's the difference bwtween CTRL ALT F1 to F2?
Other than that I have don exactly it :|

It's dropping to term from X11. I'm using KDE4. I used control+alt+backspace to drop to term to install the new driver. Then I  did

```
sudo shutdown -r 0
```

---

### Post by Unix_Slayer on 2008-06-08
> **RESID3NT said:**
> removed the driver


It still doesn't. But I've tried exactly the same thing with CTRL ALT F1 and "magically" (I'm guessing that it made all the difference), the driver worked after restart :)

However  nvidia-settings says:
Unable to load X Server Display Configuration page:



You might not have write access to it.  

```
sudo nvidia-settings
```

---

### Post by Unix_Slayer on 2008-06-08
> **Pumalite said:**
> You can do either one

Better to reboot, than being sorry.

---

