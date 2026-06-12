---
title: "Still rt2800usb and rt2870sta wirelss driver conflict?"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by blackSP on 2010-04-13
I want to start testing Beta 2 on my main system (!) but I still cannot connect 'out of the box' to my ralink wifi dongle. In 9.04 I had to:

Add 'rt2800usb' to the /etc/modprobe.d/blacklist.conf
Add rt2870sta to /etc/modules at the bottom of the file
Add bcmwl-kernel-source from live CD


Do I still need to do this to get wireless to work under 10.04?
If so this is going to be a real ball breaker for Ubuntu I fear...


BTW, I know there's already conversations going on like [here]("http://ubuntuforums.org/showthread.php?t=1438175&highlight=wireless&page=4") but I can't get it to work yet...

---

### Post by blackSP on 2010-04-14
Anybody?

---

### Post by imcookie on 2010-04-14
you fail to mention what ralink chipset you have! Never mind, if you have this problem then this will fix it!

I have an rt2870, rt2870f(*if you have an alternative wireless chipset then google the chipset id with "ubuntu", "karmic"*). As far as wireless network card drivers goes Lucid Lynx has pretty much the same set up as Karmic Koala.


**My Solution (LIVE CD(usb) VERSION):**

**1/** Open a terminal:
```
Applications -> Accessories -> Terminal
```
[INDENT]*a window will open*[/INDENT]

**2/** Type:
```
sudo rmmod rt2800usb
```
[INDENT]*enter your root password*[/INDENT]

**3/** Detach your wireless dongle from your pc, wait a few seconds, then plug it back in.
[INDENT]*this will inhibit the alternative driver*[/INDENT]

**4/** Networks will now be usable(connectable) from the panel


**My Solution after installation:**

**1/** Open a terminal
```
Applications -> Accessories -> Terminal
```
[INDENT]*a window will open*[/INDENT]

**2/** Type:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
[INDENT]*enter your root password.*[/INDENT]
[INDENT]*this will open a text editor focused on the blacklist.conf a file dedicated to removing modules that conflict others*[/INDENT]

**3/** Scroll as far as you can to the bottom of the text and create a new line.

**4/** Type:
```
blacklist rt2800usb
```

**5/** Save the file.

**6/** Restart the pc.

**7/** *After reboot you should be able to select wireless access points and connect*

---

### Post by eltonw on 2010-04-15
> **blackSP said:**
> I want to start testing Beta 2 on my main system (!) but I still cannot connect 'out of the box' to my ralink wifi dongle. In 9.04 I had to:

Add 'rt2800usb' to the /etc/modprobe.d/blacklist.conf
Add rt2870sta to /etc/modules at the bottom of the file
Add bcmwl-kernel-source from live CD


Do I still need to do this to get wireless to work under 10.04?
If so this is going to be a real ball breaker for Ubuntu I fear...


BTW, I know there's already conversations going on like [here]("http://ubuntuforums.org/showthread.php?t=1438175&highlight=wireless&page=4") but I can't get it to work yet...

You may want to have a look here:
[http://ubuntuforums.org/showthread.php?p=9126299#post9126299]("http://ubuntuforums.org/showthread.php?p=9126299#post9126299")

and also ***here***:
[https://launchpad.net/+search?field.text=ralink]("https://launchpad.net/+search?field.text=ralink")
...perhaps the Launchpad forums might provide you with a solution.

HTH...

respectfully,

---

### Post by blackSP on 2010-04-16
How can I forget! But didn't I said that in my post? rt2870sta 

The dongle is a edimax ew-7711utn
So, if this is still to be fixed manually the critics are going to have a field day on this one. There was already critique on Karmic and still not fixed?

---

