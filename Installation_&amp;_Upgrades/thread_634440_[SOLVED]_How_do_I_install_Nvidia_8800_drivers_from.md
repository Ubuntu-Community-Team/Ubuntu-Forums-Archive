---
title: "[SOLVED] How do I install Nvidia 8800 drivers from recovery?"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by Sicundercover on 2007-12-07
I managed to install Ubuntu 7.10 using the alternate disk but cant boot into desktop.

Ctrl-Alt-f1 thru f7 doesnt work.

I can get into recovery. What commands do I need to type to load the Linux Nvidia 8800 drivers in from cd.

This is the only thing I can figure from everything Ive read it seems like its just that the drivers arnt working with my card.

System specs:
AMD X2 5200+
8 Gigs Corsair XMS TwinX ddr2 800 (pc6400) RAM
BFG 8800GTX
AMD Crosshair Mobo

---

### Post by Pumalite on 2007-12-07
Configure your xserver and once IN the system get the proper drivers for your card:
sudo dpkg-reconfigure xserver-xorg

---

### Post by Sicundercover on 2007-12-07
How do I configure my Xserver from inside recovery?

Whats the command?

---

### Post by Pumalite on 2007-12-07
I gave it to you.

---

### Post by Sicundercover on 2007-12-07
So I gave this a shot

```
sudo dpkg-reconfigure xserver-xorg
```

Which let me reconfigure  but when it finished it just return me to the recovery text screen. So not knowing what to do I rebooted and tried to enter in through GRUB but no luck still a blank screen.

---

### Post by Pumalite on 2007-12-07
Try this:

For 8600-8800 GT

When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

---

### Post by Sicundercover on 2007-12-07
Ive already tried this.

when I run 
```
apt-get install nvidia-glx-new
```

I get a screen full of attempts and unresolved connections.

Thats why I downloaded the new drivers and put them on a disk.

Anyway to install it from the disk whilst in the recovery mode?

Also
```
sudo password
```

Returns a "command not found"

And
```
nvidia-xconfig
```

Also returns a "command not found".

---

### Post by Pumalite on 2007-12-07
If the commands were not found, I suspect your installation. Beyond that, the series of commands I gave you not always works. The fact is that 8800 cards have been a problem for a long time.
[http://ubuntuforums.org/showthread.php?t=605282&highlight=8800](http://ubuntuforums.org/showthread.php?t=605282&highlight=8800)

---

### Post by Sicundercover on 2007-12-07
Actually this is the third time Ive done this install in as many days suspecting the same thing.

I also had this problem with 7.04 and eventually gave up.

My hope was that there would be some solution for this come 7.10.

Oddly enough I have gotten Gentoo Linux to install without this problem.

---

### Post by Sicundercover on 2007-12-07
OK so Ive managed to get into the desktop.

I had to select the Ubuntu 7.10 at GRUB and hit "e" then select down one to "kernel" then hit "e" again and delete "splash quite" this got me into the Desktop. 

Ive also managed to activate the restricted drivers.

Couple more questions.

After I activated the restricted drivers I had to do a restart. I still had to go through the same process to get the desktop to boot. How can I change this?

Also how do I get into the Nvidia manager to configure X for dual screens?

Ive tried "sudo apt-get install envy" but I just get a return of
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envy"

What next?

---

### Post by Sicundercover on 2007-12-28
For me [Envy]("http://albertomilone.com/nvidia_scripts1.html") was my solution.

Just download it and all will be guided from there.

---

