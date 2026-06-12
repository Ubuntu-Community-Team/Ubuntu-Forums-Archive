---
title: "Already Installed GUI ubuntu-desktop, how to run?"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by WhiteCross on 2008-04-06
Hi

Im really new to Linux, and ive read many guides here
but I may not seem to find any that will guide me on how to
run the ubuntu-desktop GUI on my server 7.10 after i have
successfully installed it..

Pls help me how to run the installed GUI.

many thanks!

---

### Post by tamoneya on 2008-04-06
```
startx
```

---

### Post by WhiteCross on 2008-04-06
Hi,

but it says "-bash: startx: command not found"

:(

wait, it says install xinit

but when i installed it and run "startx", here's the output on my screen

X: cannot stat etc/X11/X (No such file or directory), aborting. giving up
xinit : Connection refused (errno 111): unable to connect to X server
xinit : No such process (errno 3): Server error.

---

### Post by warp99 on 2008-04-06
With a server install the GUI is not installed. You have to add it after installation. You have to run the following:

```
sudo apt-get install ubuntu-desktop linux-386
```

This will install a complete ubuntu-desktop with a desktop kernel since the server kernel does not include certain modules for mice and other desktop stuff. You can run the desktop kernel with the server applications without any problems.

---

### Post by WhiteCross on 2008-04-06
> **warp99 said:**
> With a server install the GUI is not installed. You have to add it after installation. You have to run the following:

```
sudo apt-get install ubuntu-desktop linux-386
```

This will install a complete ubuntu-desktop with a desktop kernel since the server kernel does not include certain modules for mice and other desktop stuff. You can run the desktop kernel with the server applications without any problems.

i'd tried it sir, but now it says:

E: Couldn't find package ubuntu-desktop

---

### Post by warp99 on 2008-04-06
Do you have an internet connection? If not please make sure you have the install disc in your CD rom.

---

### Post by WhiteCross on 2008-04-06
> **warp99 said:**
> Do you have an internet connection? If not please make sure you have the install disc in your CD rom.

yes sir i have internet connection because when i configure

sudo apt-get update

it is updating

but when i use 

sudo apt-get install ubuntu-desktop linux-386

thats where the error occurs..

i also installed xinit,

it is successful but when i "startx"

xauth: error in locking authority file /home/myname/.Xauthority       msg output..

---

### Post by warp99 on 2008-04-06
Try the following:

```
cat /etc/apt/sources.list
```

and please post the results to this thread.

---

### Post by WhiteCross on 2008-04-06
> **warp99 said:**
> Try the following:

```
cat /etc/apt/sources.list
```

and please post the results to this thread.

u r a big help sir, tnx for the time... here's the output

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsby-backports main restricted universe multiverse
deb-src http ://ph.archive.ubuntu.com/ubuntu/ gutsby-backports main restricted universe multiverse

## uncomment the following two lines to add software from Canonical's
## 'partner' repository This software is not part of Ubuntu, but is
## offered by Canonicall and respetive vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.comubuntu](http://archive.canonical.comubuntu) gutsy partner
# deb-src [http://archive.canonical.comubuntu](http://archive.canonical.comubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by warp99 on 2008-04-06
I've attached a correct sources.list with all of the repositories enabled to download the packages you will need. Please download the file, change to the directory of the file, and do the following:

```
sudo cp sources.txt /etc/apt/sources.list
```
then
```
sudo apt-get update
```
and finally
```
sudo apt-get install ubuntu-desktop linux-386
```

Please install the desktop kernel or certain desktop functions will not work. If you installed the 64-bit Ubuntu OS then replace 'linux-386' with 'linux-generic'. After you've installed the packages use the command 'startx' to bring up the desktop.

---

### Post by WhiteCross on 2008-04-06
@WARP

uuummm.. i installed ubuntu to a VMWare..

where shud i put the source.txt so that the ubuntu will recognize it?

i'm so sorry for all the trouble.. i was raised using MSWin...

this is really my 1st time using Linux..

i havent had enough sleep since yesterday..

---

### Post by warp99 on 2008-04-06
If you have network shares turned on in the vmware image you can transfer the file that way. If you can't do that then just open the /etc/apt/sources.list file with the following command:

```
sudo pico /etc/apt/sources.list
```

Delete the contents of the file and just type the contents in from the sources.txt file since there are only about 8-10 lines of information and save the file. The lines beginning with 'deb-src' can be ignored if you want since they are only for source code, not packages. Hope this helps.

---

### Post by WhiteCross on 2008-04-06
I followed all your instructions..
sad to say it still have an output of

E:Couldn't find package : ubuntu-desktop

so tired... maybe linux is not for me..

:confused:

---

### Post by WhiteCross on 2008-04-06
wait wait mr.Warp!

ire-installed ubuntu server 7.10

now i managed to install the ubuntu-desktop linux-386

i dont want to make any harsh actions..

after installing, what shud i do?

startx?

or do i need to install other package?

pls pls help..

so excited to use diff OS!

---

### Post by warp99 on 2008-04-06
Just reboot to load the new kernel and type 'startx' at the command prompt and everything should be fine.

---

### Post by WhiteCross on 2008-04-06
Thanks so much mr.Warp! :popcorn:

you rock! :guitar:

its running ok now.
thanks thanks thanks!

---

