---
title: "can't get past login before 10.10 goes into a loop"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by maddbaron on 2011-02-16
Hello, upgraded from 10.04 install went fine, system rebooted then problems. 
Can't get past login...only way to access is safe graphics mode. 
Everything is installed correctly, I even removed a plymouth theme from 10.04,
I disabled the login screen and told the system to log me in directly and it still doesn't work.

My configuration file looks fine and simple enough but I don't know what to look for. 

Can someone tell me how to view my boot process while in safe graphics mode so I can see why it hangs then goes into the loop or better yet how to skip the login splash/ plymouth splash altogether?

---

### Post by sikander3786 on 2011-02-16
Please post the output of these commands.

```
cat /etc/X11/xorg.conf
lspci | grep VGA
glxinfo |grep vendor
```

---

### Post by maddbaron on 2011-02-16
> **sikander3786 said:**
> Please post the output of these commands.

```
cat /etc/X11/xorg.conf
lspci | grep VGA
glxinfo |grep vendor
```


```

$ cat /etc/X11/xorg.conf
Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

$ lspci | grep VGA
01:05.0 [COLOR="Red"]VGA[/COLOR] compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
$ glxinfo |grep vendor
$ 
$ glxinfo |grep vendor



```

is something missing?

---

### Post by sikander3786 on 2011-02-16
Try reconfiguring your graphics. Press Ctrl + Alt + F1 at the login screen and login to tty1. Then,

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

---

### Post by maddbaron on 2011-02-16
> **sikander3786 said:**
> Try reconfiguring your graphics. Press Ctrl + Alt + F1 at the login screen and login to tty1. Then,

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

can i do this from terminal while in safe mode? I can't get to the login screen in enough time it reboots the screen within a second, does the drums then a second later does it again and again

---

### Post by maddbaron on 2011-02-16
> **sikander3786 said:**
> Try reconfiguring your graphics. Press Ctrl + Alt + F1 at the login screen and login to tty1. Then,

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

it said it cannot
```
 mv: cannot stat /etc/X11/xorg.conf no file or directory found 
```

if i press ctrl + atl + fl 3 times is freezes the constant reboot and lets me press my login then begins to show my desktop before it reverts to the reboot... 

I went into safe graphic mode and used terminal to access nautilus under sudo and went to the x11 folder...

I had something called foremostgui installed I removed it now but it still shows up. I created a new xorg.conf by going into the folder and copying one of the backups and then saving it to the folder. when I got to the second step is some inline error with foremostgui(i deleted it but it still says that) then it says warning something about karmic.  I figure I need to purge foremostgui since removing all files with synaptic didn't really remove everything, do you know how I can do that?

I also noticed after I ran the 1st command with the new xorg.conf it would turn that into a backup and leave no xorg.conf in the folder. 

my xorg is pretty messed up I think. 

 how can I create an xorg.conf that will remain active and not become a backup?

---

### Post by sikander3786 on 2011-02-16
Yes you can do those commands from your safe mode Terminal as well.

As the above mentioned command cat /etc/X11/xorg.conf resulted in an output, xorg.conf is present there. Make sure your didn't mis-type the command or change case or left un-necessary spaces. Or simply copy/paste the text from here to your Terminal. You need to do all of those commands one-by-one, each after the first one succeeds.

---

### Post by maddbaron on 2011-02-16
> **sikander3786 said:**
> Yes you can do those commands from your safe mode Terminal as well.

As the above mentioned command cat /etc/X11/xorg.conf resulted in an output, xorg.conf is present there. Make sure your didn't mis-type the command or change case or left un-necessary spaces. Or simply copy/paste the text from here to your Terminal. You need to do all of those commands one-by-one, each after the first one succeeds.

i successfully type the 1st code then after the 2nd code I get

```

:~$ sudo dpkg-reconfigure -phigh xserver-xorg
warning, in file '/var/lib/dpkg/available' near line 89998 package 'foremostgui':
 error in Version string '9.11.08_karmic': invalid character in version number

```

BUT I rebooted and now can load my desktop but everything is very static like. I checked the drivers and they are all working fine. 

Now I need to solve this problem.

Thank you for your help and the codes!

---

### Post by sikander3786 on 2011-02-16
> **maddbaron said:**
> i successfully type the 1st code then after the 2nd code I get

```

:~$ sudo dpkg-reconfigure -phigh xserver-xorg
warning, in file '/var/lib/dpkg/available' near line 89998 package 'foremostgui':
 error in Version string '9.11.08_karmic': invalid character in version number

```

BUT I rebooted and now can load my desktop but everything is very static like. I checked the drivers and they are all working fine. 

Now I need to solve this problem.

Thank you for your help and the codes!
Glad to know that one issue is sorted.

For the dpkg issue, try using this command.

```
sudo dpkg --clear-avail
```

And then to make sure that everything is ok and packages are not broken,

```
sudo apt-get install -f
sudo dpkg --configure -a
```

Good Luck!

---

### Post by maddbaron on 2011-02-16
> **sikander3786 said:**
> Glad to know that one issue is sorted.

For the dpkg issue, try using this command.

```
sudo dpkg --clear-avail
```

And then to make sure that everything is ok and packages are not broken,

```
sudo apt-get install -f
sudo dpkg --configure -a
```

Good Luck!

thanks will do, i think i found the second issue but not sure I have conflicting nvidia and ati drivers. my system is ati and i don't know where nvidia came from. gonna research more and see if removing them then reinstalling my ati drivers will resolve this new issue.

---

### Post by sikander3786 on 2011-02-16
Yes, remove both of the drives, both ATI and Nvidia. Reboot. Remove xorg.conf if it is present.

```
sudo rm /etc/X11/xorg.conf
```

And then re-install ATI drivers. That should do it nicely.

---

### Post by maddbaron on 2011-02-16
> **sikander3786 said:**
> Yes, remove both of the drives, both ATI and Nvidia. Reboot. Remove xorg.conf if it is present.

```
sudo rm /etc/X11/xorg.conf
```

And then re-install ATI drivers. That should do it nicely.


worked but didn't work... i removed all the drivers from synaptic and rebooted...stuttering screen gone! reinstalled the ati drivers. rebooted... stuttering is back!.. i removed them again just to stop the stuttering but my monitor has huge letters and everything is out of whack...

in the drivers part do I remove the fire GL driver and reboot and if so will the system reinstall the driver itself?

---

### Post by sikander3786 on 2011-02-17
Don't use Synaptic for driver installation. Instead, use the gtk-jockey under System > Administration > Hardware Drivers/Additional Drivers.

---

### Post by maddbaron on 2011-02-18
> **sikander3786 said:**
> Don't use Synaptic for driver installation. Instead, use the gtk-jockey under System > Administration > Hardware Drivers/Additional Drivers.

yeah when that didnt Work I used the wiki and rebuilt then reinstalled the drivers but now my screen has a huge black bar @ the bottom that has become a huge black screen...

this feels like an xorg issue but i dont know what to check

---

