---
title: "the whole desktop environment is gone!"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by pesho318i on 2008-05-18
Hi :)

after some attempts to install compiz on my Ubuntu 6.06, now I lost all the gnome desktop environment! When I reboot, I only get a small terminal in the upper left corner of my screen. 

Please let me know how I could restore the gnome desktop environment.

Thanks!

---

### Post by overdrank on 2008-05-18
> **pesho318i said:**
> Hi :)

after some attempts to install compiz on my Ubuntu 6.06, now I lost all the gnome desktop environment! When I reboot, I only get a small terminal in the upper left corner of my screen. 

Please let me know how I could restore the gnome desktop environment.

Thanks!

Hi and welcome, I believe the support for compiz on dapper has been stopped long ago. Have you tried to reconfigure your xorg and it seems you are in the command prompt or recovery mode.

---

### Post by Mhurst1 on 2008-05-18
Did you try sudo apt-get install ubuntu-desktop?

---

### Post by aysiu on 2008-05-18
**Step 1**:
Log in

**Step 2**:
Type ```
sudo dpkg-reconfigure xserver-xorg
``` and answer the questions as best you can. If you don't know the answer, go with the default.

**Step 3**:
Type ```
sudo /etc/init.d/gdm restart
```

---

### Post by pesho318i on 2008-05-18
thank you for the hints!

I tried reconfiguring the xserver, but didn't help, I was back to the same point - a brown background and a nice looking command-line terminal taking 1/4 of the display in the upper left corner. By the way I think this is not exactly recovery mode!?

I also tried installing the ubuntu-desktop, but there are some unresolved dependencies, I don't know how to force the apt-get to also install the dependencies...

would appreciate a little more help :)
Thanks...

---

### Post by aysiu on 2008-05-18
Unresolved dependencies sounds as if you have conflicting repositories in your sources.list.

Try this: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo nano /etc/apt/sources.list
``` This will open your repositories list in a text editor called Nano.

Delete (Control-K) all of the lines except these: ```
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
``` Then save the file (Control-X, Y, Enter) and ```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by pesho318i on 2008-05-18
hmm, again I get unresolved dependencies:

Depends: 
gnome-app-install .....
gnome-applets...
gnome-btdownload.....
...
...
...
nautilus...

Should I search for the corresponding update-sites and add them manually to the update.list file, or there is an easier way to tackle it?

---

### Post by aysiu on 2008-05-18
You shouldn't run into those dependency errors with the sources.list I gave you.

Did you get any error messages when you ran ```
sudo apt-get update
``` perhaps?

---

### Post by pesho318i on 2008-05-18
no, the update procedure went fine.
I still get the "Depends: blabla" messages after running "sudo apt-get install --reinstall ubuntu-desktop"
In the end there is also something about Broken packages!?

By the way I had some problem with "locales". It used to give me a message of the sort: "Could not find locale xxx, resorting to default locale". Maybe this is the reason I get dependency/broken packages problems?

---

