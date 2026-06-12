---
title: "Can't install any sw"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by gigiotd on 2010-08-27
Yes, it could seem a strange subject, but I can't install anymore any sw.
I have ubuntu 9.10, worked well till yesterday, when I removed some sw from "ubuntu software center". 
Now I get the message that says the sw can't be removed/installed and the detail errors are:  "install archives() failed".

Can anyone help, please?
Thanks in advance!
Bye
Gigio

edit: this images shows the screen
edit2: same when trying to install a .deb package (error2.jpg)
edit3: catfish can be installed and removed! Not ALL sw can't be installed... only some.
[IMG]http://ubuntuforums.org/home/nicola/error.jpg[/IMG]

---

### Post by mörgæs on 2010-08-27
If you boot the machine and then run 

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

you should have a working system.

After that, can you install and uninstall through Synaptic?


I have never understood the idea behind Software Centre. Just use Synaptic and you will be safe.

---

### Post by ajgreeny on 2010-08-27
> **mörgæs said:**
> 
I have never understood the idea behind Software Centre. Just use Synaptic and you will be safe.
The software Centre is supposed to be a simplified and dumbed-down version of synaptic, as far as I can make out, but I suspect rather like you, I have never used it.  I have opened it up once or twice to see what all the fuss was about and quickly decided that now I know enough about the system, synaptic does everything needed, but a lot better, as it has every possible package listed, whereas the SC only has a limited range.

However for the new user, I think the SC is probably very helpful.

---

### Post by gigiotd on 2010-08-27
> **mörgæs said:**
> If you boot the machine and then run 
 
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
 
you should have a working system.
 
After that, can you install and uninstall through Synaptic?
 
 
I have never understood the idea behind Software Centre. Just use Synaptic and you will be safe.
 
well... now I have another problem. These commands let me advance from ubuntu 9.10 to 10.04!
When I boot, I don't have anymore the graphic interface!! Only command line interface (character) is shown... how can I get ubuntu desktop gnome?!?? Please help, I'm rather preoccuped!
Now I boot into vista partition and I'm writing from IE... :(
Thanks again.

---

### Post by mörgæs on 2010-08-27
> **gigiotd said:**
> well... now I have another problem. These commands let me advance from ubuntu 9.10 to 10.04!
When I boot, I don't have anymore the graphic interface!! Only command line interface (character) is shown... how can I get ubuntu desktop gnome?!?? Please help, I'm rather preoccuped!
Now I boot into vista partition and I'm writing from IE... :(
Thanks again.

No, the three commands shown upgrade the packages within a version, they do not jump to the next one. 

[https://help.ubuntu.com/10.04/serverguide/C/apt-get.html](https://help.ubuntu.com/10.04/serverguide/C/apt-get.html)

It is possible to upgrade to the next Ubuntu using apt-get, but I do not recommend it.

If you are on your way to 10.04 (and are you sure about that?), could it be because you pushed the 'upgrade' button in Synaptic?

---

### Post by gigiotd on 2010-08-27
> **mörgæs said:**
> No, the three commands shown upgrade the packages within a version, they do not jump to the next one. 
 
[https://help.ubuntu.com/10.04/serverguide/C/apt-get.html](https://help.ubuntu.com/10.04/serverguide/C/apt-get.html)
 
It is possible to upgrade to the next Ubuntu using apt-get, but I do not recommend it.
 
If you are on your way to 10.04 (and are you sure about that?), 
 
The prompt tells "ubuntu 10.04"... 
 
> **mörgæs said:**
> 
could it be because you pushed the 'upgrade' button in Synaptic?

 
No, I'm sure... only the 3 command where typed. Anyway, from many weeks I had the warning, in system upgrade notification, that I could upgrade to ubuntu 10.04: may be this time I accepted this?
 
Anyway I have newbie question: 
-how can I execute GUI?
-how can I run a browser from command line? 
- My connection is proxied: an authentication is required the first time I try to connect internet. How can I autenthicate if I don't have a browser?
 
Thanks for help

---

### Post by mörgæs on 2010-08-27
> **gigiotd said:**
> 
-how can I execute GUI?


Try typing **startx**.

---

### Post by gigiotd on 2010-08-27
> **mörgæs said:**
> Try typing **startx**.
 
Well, one step ahead: startx seems to load gui. I see mouse, but desktop is black.
If I press power on/off button, I can see for a while my old desktop photo but, it then shuts down as required.
Could it be that I have a laptop with external monitor and the gui is confusing monitor?
Anyway I tried the laptop with external monitor detached, with no luck... :(
Furthermore: 
-everytime I boot I get command line prompt... why it doesn't load gui as it always was used to do??
-grub prompts me many different boot options: many ubuntu-linux versions and the vista boot too. May be now I should not use the first choice as I always did? I tried second e third option, but I always get command line.
btw I'm sure the 3 commads above let me advance to ubuntu 10.04, the prompt says "ubuntu 10.04 LTS".
 
bYE

---

### Post by mörgæs on 2010-08-27
It sounds like a problem with the screen card. Please post the output from 

```
hwinfo --gfxcard
```

Another good test is finding out which Ubuntu versions your machine likes. It has been running 9.10 well, I presume. How does it behave with a 10.04 live CD?

---

### Post by gigiotd on 2010-08-27
> **mörgæs said:**
> It sounds like a problem with the screen card. Please post the output from 
 
```
hwinfo --gfxcard
```
 
Another good test is finding out which Ubuntu versions your machine likes. It has been running 9.10 well, I presume. How does it behave with a 10.04 live CD?
 
hwinfo --gfxcard
 shows video card details (Nvidia, etc.).
 
I tried to execute 
```

sudo apt-get install ubuntu-desktop

```
Now pc boots in GUI mode, but it can't recognize keyboard! I can't login, because it doesn't let me type password (username is the same I used in 9.10).
:(
When I boot I get a mounting error, something like error "mounting none on /dev"... any ideas?
Now graphic card is ok... what happens to my keyboard?
 
Thanks

---

### Post by mörgæs on 2010-08-27
It seems like there was a bunch of problems on this machine. The trouble in Software Centre was probably just the tip of the iceberg.

I would save my files and do a clean install of either 9.10 or 10.04 (if a live boot with this release works well). Trying to diagnose and correct the errors will probably take much longer than a reinstall.

Just remember to have wired internet access while installing, then it should work as a charm.

---

### Post by gigiotd on 2010-08-27
> **mörgæs said:**
> It seems like there was a bunch of problems on this machine. The trouble in Software Centre was probably just the tip of the iceberg.

I would save my files and do a clean install of either 9.10 or 10.04 (if a live boot with this release works well). Trying to diagnose and correct the errors will probably take much longer than a reinstall.

Just remember to have wired internet access while installing, then it should work as a charm.

I think you're right. Should I format or I try to install from live on the same partitions?
Thanks a lot for great help!!!

---

### Post by mörgæs on 2010-08-27
You are welcome.

If you want to give Ubuntu the whole disk space, just boot the live CD and let Ubuntu wipe the drive in the process.

If you want to keep Windows: Boot a live CD, and from that you can delete the Ubuntu partitions. When the installation begins, Ubuntu will put itself in the empty space.

Let us hear how it goes.

---

