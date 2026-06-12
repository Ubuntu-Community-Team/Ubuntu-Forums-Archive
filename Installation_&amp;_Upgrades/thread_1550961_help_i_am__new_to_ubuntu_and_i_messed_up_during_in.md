---
title: "help i am  new to ubuntu and i messed up during install"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by f6e9a on 2010-08-11
;)hi,
 
when i first tried to install ubuntu a blank screen would show up. but then i followed the advice in this thread [http://ubuntuforums.org/showthread.php?t=1463294&page=4](http://ubuntuforums.org/showthread.php?t=1463294&page=4)
and finally i was able to log in and try ubuntu and on its desktop it said install and soo i clicked it and ran through the install deleting my win xp pro from my computer.
but when i restarted i had the same blank screen problem. help plz
 
btw i have a dell latitude d 505 
 
new memeber,
 
f6e9a:o

---

### Post by jcolyn on 2010-08-11
According to specs this laptop originally shipped with 128MB ram. This would cause problems since Ubuntu needs 512MB minimum. If this is the case you'll need to add memory.

I could be wrong but my impression is the Intel Celeron M processors don't do well with Linux. Hopefully someone with experience with these processors will comment..

---

### Post by f6e9a on 2010-08-11
i just want to try it out soo if u could just tell me how to fix my problem with the blank screen plz thanks

---

### Post by f6e9a on 2010-08-11
> **jcolyn said:**
> According to specs this laptop originally shipped with 128MB ram. This would cause problems since Ubuntu needs 512MB minimum. If this is the case you'll need to add memory.
 
I could be wrong but my impression is the Intel Celeron M processors don't do well with Linux. Hopefully someone with experience with these processors will comment..
 
i just need to know how to get the screen working and not blank 
 
thanks anyway

---

### Post by mudguts on 2010-08-11
you have a way of hooking up an external monitor to test?
maybe it's pushing the resolution out too high for your display?

---

### Post by f6e9a on 2010-08-11
i have a vga cord 
and a tv 
u want me to try that ?

---

### Post by linux18 on 2010-08-11
Put the live cd in and reinstall, this time not rushing through the process, but jcolyn is right 128MB of ram can cause problems, but the minimum is 256 not 512 (512 is just 3 times faster) you may need to grab the xubuntu-10.04-alternate-i386.iso and in the worst case you may need to use my distro remix (see sig)

---

### Post by f6e9a on 2010-08-11
this is wut i did 
 
1.when i booted from the ubuntu cd i pressed space on the little keyboard and man
2.i selected english
3.i selected try ubuntu without changes
4.i pressed f6
5.i entered 'i915.modeset=1'(without '') at the end of command line
6.ubuntu loaded and i saw its desktop on the desktop it said install ubuntu
7.i clicked on the install thing
8.wiped out my win XP pro and installed ubuntu
9.on restart i had a blank screen after loading 
 
is there somehow i can do step 5 to be able to see things on my screen ?
 
thanks

---

### Post by f6e9a on 2010-08-11
> **linux18 said:**
> Put the live cd in and reinstall, this time not rushing through the process, but jcolyn is right 128MB of ram can cause problems, but the minimum is 256 not 512 (512 is just 3 times faster) you may need to grab the xubuntu-10.04-alternate-i386.iso and in the worst case you may need to use my distro remix (see sig)
 
 
sorry but i am really new to this 
 
can u maybe give me a step by step list  plz
 
thanks

---

### Post by linux18 on 2010-08-11
do you get any grub boot options on startup (hold shift key at bootup untill you see a menu)
if so choose recovery mode and drop to a root prompt

---

### Post by f6e9a on 2010-08-11
i got the menu do i add a command line(c) or press  (e)

---

### Post by f6e9a on 2010-08-11
i so get a menu i have recovery highlighted do i press c or e
 
c= command line 
e= edit something

---

### Post by f6e9a on 2010-08-11
> **linux18 said:**
> do you get any grub boot options on startup (hold shift key at bootup untill you see a menu)
if so choose recovery mode and drop to a root prompt
 
 
i got the menu do i press c or e ?

---

### Post by f6e9a on 2010-08-11
sorry i accidently posted 3 times :(

---

### Post by linux18 on 2010-08-11
if the menu lists ubuntu "recovery mode" choose that (press enter after highlighting it)
then you will be presented with another menu scroll down and choose root

---

### Post by f6e9a on 2010-08-11
ok done that next 
 
btw thanks

---

### Post by linux18 on 2010-08-11
type xinit at the prompt

you should get a white terminal and a black background

if you do, then type

metacity && gnome-panel && nm-applet

---

### Post by f6e9a on 2010-08-11
i type "x" or "xinit ?"

---

### Post by linux18 on 2010-08-11
"xinit"

---

### Post by f6e9a on 2010-08-11
my screen is black after i typed xinit at the bottom of my screen

---

### Post by linux18 on 2010-08-11
ok, looks like its an xorg problem.
reboot, and type:
 sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak && sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

then try xinit

---

### Post by f6e9a on 2010-08-11
type that where?

---

### Post by linux18 on 2010-08-11
type that in the prompt you typed xinit in

---

### Post by f6e9a on 2010-08-11
i did it says no suck file or directory 
 
i typed "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak && sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
"

---

### Post by f6e9a on 2010-08-11
r there spaces where i have a ^ thing 
 sudo^ mv^ /etc/X11/xorg.conf^ /etc/X11/xorg.conf.bak^ &&^ sudo mv^ /etc/X11/xorg.conf.failsafe^ /etc/X11/xorg.conf
"

---

### Post by linux18 on 2010-08-11
which of these commands produces output:
```
cat /etc/X11/xorg.conf 
cat /etc/X11/xorg.conf.failsafe
cat /etc/X11/xorg.conf.bak

```

---

### Post by f6e9a on 2010-08-11
r these 3 diff lines
 
1.sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
2.sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
3.xinit

---

### Post by linux18 on 2010-08-11
if you use && #1 and #2 are one line, but #3 is a different line

---

### Post by linux18 on 2010-08-11
> **f6e9a said:**
> r there spaces where i have a ^ thing 
 sudo^ mv^ /etc/X11/xorg.conf^ /etc/X11/xorg.conf.bak^ &&^ sudo mv^ /etc/X11/xorg.conf.failsafe^ /etc/X11/xorg.conf
"
yes there are spaces there

---

### Post by f6e9a on 2010-08-11
> **linux18 said:**
> which of these commands produces output:
```
cat /etc/X11/xorg.conf 
cat /etc/X11/xorg.conf.failsafe
cat /etc/X11/xorg.conf.bak

```
 
 
ok i have tried each line 1nce it still says no file or directory
 
line 1 cat /etc/X11/xorg.conf 
line 2 cat /etc/X11/xorg.conf.failsafe
line 3 cat /etc/X11/xorg.conf.bak
line 4 /etc/X11/xorg.conf 
line 5 /etc/X11/xorg.conf.failsafe
line 6 /etc/X11/xorg.conf.bak

---

### Post by linux18 on 2010-08-11
are you capitalizing the "X" in  '/etc/X11' if you are then it appears to be a failed install

---

### Post by f6e9a on 2010-08-11
i did put it in caps 
 
this is wut i wrote in the thing 
 
 [EMAIL="root@administrator-laptop"]root@administrator-laptop[/EMAIL]:~# /etc/X11/xorg.conf.bak
 
 [EMAIL="root@administrator-laptop"]root@administrator-laptop[/EMAIL]:~# cat /etc/X11/xorg.conf.bak
 
i tried them both

---

### Post by linux18 on 2010-08-11
if those files aren't there, you can't start the display. your installation probably failed at some point.
you might be able to rescue it if you have an internet connection available for your laptop.
if its an ethernet connection:
ifconfig eth0 up
dhclient eth0

---

### Post by f6e9a on 2010-08-11
i do have a internet connection but no brower coz ubuntu wiped out my disc
 
btw does ur version of ubuntu have the same interface could u just tell me the diffs i will probably install urs

---

### Post by linux18 on 2010-08-11
you don't need a browser, just plug in the ethernet cable and run these commands 
ifconfig eth0 up
dhclient eth0
sed -i '/cdrom/d' /etc/apt/sources.list
apt-get ubuntu-desktop

---

### Post by f6e9a on 2010-08-11
g2g brb

---

