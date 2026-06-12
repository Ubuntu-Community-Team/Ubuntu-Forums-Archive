---
title: "Freeze after partial install"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by jeff17237 on 2010-12-15
Today I tried to upgrade from 10.04 to 10.10.  It got through probably 50% of the install and then everything froze.  I had to hard restart the computer, but when I try to boot to ubuntu, it just gives me a prompt and acts as if everything is wrong.  I have tried a few things (sudo dpkg -configure -a; sudo dpkg -reconfigure; etc..) but it all seems to lead back to the prompt with no success.  Is there anyway to recover my upgrade?  Do I have to resort to a reinstall of ubuntu and lose all my data?

Thanks,
Jeff

---

### Post by sikander3786 on 2010-12-15
From the command line, bring up your internet.

```
dhclient eth0
```

Where eth0 is your network interface.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get install -f
```

---

### Post by jeff17237 on 2010-12-15
i am not able to try this because i have no access to internet through commandline (wpa2 enterprise wireless and browser authentication ethernet are only options).  do you think the same thing would be possible through a distro disk?

---

### Post by sikander3786 on 2010-12-15
Yes you can do them from a Live CD as well.

Follow the Section 'Why Chroot' here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I hope it isn't a Wubi install and if not, follow the C. Normal Installation sub-section there and then the Continue from A, B or C sub-section. Then do the above mentioned commands.

---

### Post by jeff17237 on 2010-12-16
mounted and did everything as listed.  here is the outcome of the commands:

```
root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@ubuntu:/# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

update worked fine and upgrade also did nothing.  the files from my regular ubuntu partition seem to be intact.  ill give a better description about what happens on start-up:

grub works perfect (windows partition boots fine as well).  Both ubuntu boots (normal and recovery) take me to the same place.  ubuntu acts like it loads fine until just after the purple screen.  i get the "Ubuntu 10.10" with the four dots underneath loading fine, but just after that (right when it should go to the login gui) the screen flashes and it goes to a ubuntu prompt instead.  it says "Welcome to Ubuntu!" and prompts a login.  I can login with normal user and pswd.  once i login it just stays the same black commandline.

---

### Post by jazzerit on 2010-12-16
what happens if you type:
startx

---

### Post by sikander3786 on 2010-12-16
So you are not missing any updates and there are no broken packages on your system. Strange.

Anyhow, you can try starting the X server using command in above post and post back the error here. If that doesn't work, from the command line try this command.

```
sudo service gdm start
```

And also let us know about your graphics card. Were any proprietary drivers installed?

```
lspci | grep VGA
```

```
cat /etc/X11/xorg.conf
```

You can do all of these commands from the same command line. No need to chroot for that.

---

### Post by jeff17237 on 2010-12-16
more screen flashing and several errors about Segmentation fault and server error ("cannot connect to server" "server aborted")

EDIT: to clarify, the download of all distro files finished completely.  also, ubuntu-desktop (according to aptitude) is fully installed and complete.

---

### Post by jeff17237 on 2010-12-16
it says gdm is already running?

my gfx card is an ATI radeon mobility HD 3670 (2GB memory) and the driver i was using for it was by ATI ("ATI Proprietary Driver").

let me know if you need more info from xorg.conf

---

### Post by sikander3786 on 2010-12-16
Try reconfiguring your graphics and see if that makes a difference.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo shutdown -r now
```

See if that makes a difference now.

---

### Post by jeff17237 on 2010-12-16
that worked!

im not sure how that was the only thing wrong when i interrupted an upgrade, but hey it works!  thank you so much sikander you are a lifesaver!

Jeff

---

### Post by sikander3786 on 2010-12-16
You are Welcome :-)

Glad to know it is all sorted now.

Happy Ubuntu-ing!

---

### Post by Placet on 2010-12-16
Hi, I am sorry to hijack a perfectly solved thread, but I experienced similar trouble after an interrupted upgrade (wifi gave up on me halfway, synaptic package manager became unresponsive, after that I rebooted, sound plays, background comes up but not the login dialog, I can fall back to prompt but no networking - only wifi available). I removed /etc/X11/xorg.conf, removed fglrx drivers for ati radeon hd6300 (integrated ?) graphics card, did the 'dpkg-reconfigure -phigh xserver-xorg', but I still get stuck at the purply screen, mouse works, but that's all. 

In the /var/log/Xorg.0.log there is the following:
(EE) Failed to load module "ati" (module does not exist,0)

(EE) VESA: Kernel mode setting driver in use, refusing to load

(then starts to load sub module fbdevhw, leading to)

(EE) FBDEV(0) FBIOPUTCMAP: Invalid argument
... (lots of times)
ends with FBDEV(0) DPMS enabled
(Sorry, no screenshots/copy-paste, dual booting all day)

I am not very versed in all of this, trying stuff like this all day, trying to work out how to fix stuff with a live CD, but I didn't get it to work. Would you have a clue how to get out of this mess? Thanks in advance!

---

### Post by sikander3786 on 2010-12-17
> **Placet said:**
> Hi, I am sorry to hijack a perfectly solved thread, but I experienced similar trouble after an interrupted upgrade (wifi gave up on me halfway, synaptic package manager became unresponsive, after that I rebooted, sound plays, background comes up but not the login dialog, I can fall back to prompt but no networking - only wifi available). I removed /etc/X11/xorg.conf, removed fglrx drivers for ati radeon hd6300 (integrated ?) graphics card, did the 'dpkg-reconfigure -phigh xserver-xorg', but I still get stuck at the purply screen, mouse works, but that's all. 

In the /var/log/Xorg.0.log there is the following:
(EE) Failed to load module "ati" (module does not exist,0)

(EE) VESA: Kernel mode setting driver in use, refusing to load

(then starts to load sub module fbdevhw, leading to)

(EE) FBDEV(0) FBIOPUTCMAP: Invalid argument
... (lots of times)
ends with FBDEV(0) DPMS enabled
(Sorry, no screenshots/copy-paste, dual booting all day)

I am not very versed in all of this, trying stuff like this all day, trying to work out how to fix stuff with a live CD, but I didn't get it to work. Would you have a clue how to get out of this mess? Thanks in advance!
Welcome to the forums :-)

Chroot following post # 4 from a Live CD/USB with internet enabled. Then follow the commands in post # 2.

If that doesn't solve the issue, it would be better to start a new thread under 'Installations & Upgrades' sub-forum as this one is marked Solved by the OP and not many people will be looking at this one.

If you start a new thread, include the output of the commands mentioned in post # 2.

Good Luck!

---

