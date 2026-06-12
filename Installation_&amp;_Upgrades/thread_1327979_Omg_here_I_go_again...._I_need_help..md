---
title: "Omg here I go again.... I need help."
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by Justin2240 on 2009-11-16
Ok here's the deal. I have _**Linux Ubuntu 8.10 Server 64x**_ and I'm having an issue. Whenever I install all the updates for the operating system and tell Linux to activate the driver for my_** 2 ATI 4830 graphics cards**_ and reboot for it to finish activation it boots up _**NOT**_ into the _**DESKTOP**_ but into a **_black screen_** that ask for my _**LOG IN**_ and my _**PASSWORD.**_ I type in my log in name and my password and it just gives me a _**SUDO**_ command line and still **_doesn't_** bring me to my **_desktop._** If anyone has any ideas on what I should do it would be most appreciated. Thank you for all your time on reading this and please do forgive me for the bold and underline words. I just don't want there to be any mix up on communication here.

---

### Post by earthpigg on 2009-11-16
what happens if you type

```
xinit
```
or
```
startx
```
?

---

### Post by Justin2240 on 2009-11-16
I don't know lol. Let me find out real quick and then give you a good detail on what it does.

---

### Post by Justin2240 on 2009-11-16
Ok here we go..... It tells me the build date and operating system. Then it gives me a log file: "/ete/x11/Xorg.conf". Then it gives me this

(WW) fglrx: No matching device section for instance (BusID PCI: 0@1:0:0)
(WW) fglrx: No matching device section for instance (BusID PCI: 0@1:0:1)
(WW) fglrx: No matching device section for instance (BusID PCI: 0@2:0:0)
(WW) fglrx: No matching device section for instance (BusID PCI: 0@2:0:1)

(EE) No devices detected.
Fatal Server Error:
No screens found
giving up 
xinit connection refused (error 111): unable to connect to X server
xinit no su process (errno3): server error


And that's all she wrote man..... So what do you think?

---

### Post by Justin2240 on 2009-11-16
Hey guys I haven't really got a reply back about my recent post can anyone plz help me here?? I would really appreciate it. I really want to find out what is causing my installation of Ubuntu to be acting weird like this.

---

### Post by earthpigg on 2009-11-16
have you tried uninstalling and reinstalling X?

---

### Post by Justin2240 on 2009-11-17
I don't know what "X" is the only thing I know about linux is the synaptic package manager installing linux and some of the updates. Sorry I'm a bit of a noob when it comes to Linux. If you mean the entire operating system then yes I have. It only seems to do this whenever I tell it to do all the updates and then tell it to install the driver for my GPU's.

---

### Post by ElSlunko on 2009-11-17
Have you tried booting in recovery mode? Perhaps reinstalling ubuntu-desktop might get your gui back.

sudo apt-get install ubuntu-desktop

---

### Post by Justin2240 on 2009-11-17
No I haven't tried booting in recovery mode.... but then again I don't know how. Do I have to have the disc in the cd-rom drive to do that?? Also I will try the command that you gave me I hope it will work.

---

### Post by Justin2240 on 2009-11-17
Ok this is what happens when I type in "sudo apt-get install ubuntu-desktop."

Reading package list... done
Building Dependency tree
Reading state information... done
Ubuntu-descktop is already the newest version
0 upgrade, 0 newly installed, 0 to remove and 0 not upgraded

---

### Post by Justin2240 on 2009-11-18
So anymore suggestions before I just give up on this thing?? I really want to see if I can get it working.

---

### Post by earthpigg on 2009-11-18
honestly? i've never had X break on me, so never been forced to learn to fix it...

---

### Post by Robertjm on 2009-11-20
Try:

sudo apt-get install --reinstall ubuntu-desktop

> **Justin2240 said:**
> Ok this is what happens when I type in "sudo apt-get install ubuntu-desktop."

Reading package list... done
Building Dependency tree
Reading state information... done
Ubuntu-descktop is already the newest version
0 upgrade, 0 newly installed, 0 to remove and 0 not upgraded

---

### Post by gamerteck on 2009-12-09
I don't think re-installing Ubuntu will do anything, from the logs posted it's an "X"org thing.

Try reconfiguring X
```
sudo dpkg-reconfigure xserver-xorg
```
Then reboot.
If you still only get into the terminal then delete the xorg.conf file.
```
sudo rm -i /etc/X11/xorg.conf
```
reboot.

---

