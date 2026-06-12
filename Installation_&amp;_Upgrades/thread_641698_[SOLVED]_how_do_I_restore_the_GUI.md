---
title: "[SOLVED] how do I restore the GUI?"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by Inspirer on 2007-12-15
Hi,

Had a Kubuntu 7.10 installation that worked well,
I was messing around with packages that I shouldn't have... in order to install the kicker-taskbar-compiz.
long story short, apt uninstalled my kde.

Now I have no desktop, no internet, just a console.

I tried the following with the CD:
```

sudo apt-cdrom add
sudo apt-get install kubuntu-desktop
```

doesn't work.

Please help.

---

### Post by taurus on 2007-12-15
> **Inspirer said:**
> Hi,

Had a Kubuntu 7.10 installation that worked well,
I was messing around with packages that I shouldn't have... in order to install the kicker-taskbar-compiz.
long story short, apt uninstalled my kde.

Now I have no desktop, no internet, just a console.

I tried the following with the CD:
```

sudo apt-cdrom add
sudo apt-get install kubuntu-desktop
```

doesn't work.

Please help.

```

sudo apt-cdrom add
**sudo apt-get update**
sudo apt-get install kubuntu-desktop

```

---

### Post by Inspirer on 2007-12-15
I get this:

```
kubuntu-desktop has no installation candidate
```

I looked at the /etc/apt/sources.list and the CDROM **is** there.
did they change the name of the package?

---

### Post by Sef on 2007-12-15
> I looked at the /etc/apt/sources.list and the CDROM is there.

Does your CDROM look like this:

> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823)]/ gutsy main restricted


or this:

> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823)]/ gutsy main restricted


or are both of them there?

---

### Post by Inspirer on 2007-12-16
Copied from the sources.list file:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

```

I added both CDs.

I first tried with just the Kubuntu,
then I tried installing ubuntu-desktop with the Ubuntu CD.

Both failed the way described above.

Any other ideas? I really appreciate this.

---

### Post by PmDematagoda on 2007-12-16
Are you sure that you don't have internet?

Usually the internet is not linked to the DE and would still work without it.

---

### Post by Sef on 2007-12-16
> 

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

Try commenting out the second one and see if that works.  If not, then comment out the first one instead of the second.  To comment out put a # before the line.

Example with the second one commented out.

> 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

#deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

---

### Post by Inspirer on 2007-12-16
I'm connected through wireless, the driver is probably intact but I don't know how to connect the network 

a friend suggested the following:

```
sudo iwlist
sudo iwconfig <interface> essid <mynetwork>

```

Is that accurate?
Is that enough to have package access? (assuming my router gives DHCP)

what packages do I apt-get once I do have the connection?

---

### Post by Inspirer on 2007-12-16
> **Sef said:**
> Try commenting out the second one and see if that works.  If not, then comment out the first one instead of the second.  To comment out put a # before the line.

Example with the second one commented out.

I wish... but sadly, no.

---

### Post by PmDematagoda on 2007-12-16
Not sure about the instructions, but try:-

```
sudo /etc/init.d/networking start
```

to see if you can get the internet connection that way.

---

### Post by Inspirer on 2007-12-16
I'll try that.
But assuming that the network thing will get sorted out, 
is this command still supposed to work?

```
sudo apt-get kubuntu-desktop
```

or

```
sudo apt-get ubuntu-desktop
```

---

### Post by PmDematagoda on 2007-12-16
I think the command should be either:-

```
sudo aptitude install kubuntu-desktop
```
or
```
sudo aptitude install ubuntu-desktop
```

---

### Post by Inspirer on 2007-12-16
It's Alive!!!! :)

what it took was an internet connection.

I had to do

```
sudo iwconfig wlan0 essid any
sudo dhclient
sudo apt-get install ubuntu-desktop

```

then lot's of downloading and after that it worked.

I'm sure glad I didn't reinstall.

---

### Post by Sef on 2007-12-18
Glad you got it back up without reinstalling.   Please ask any more questions that you have.

---

