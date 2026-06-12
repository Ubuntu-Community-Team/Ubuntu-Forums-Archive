---
title: "Xubuntu only working on nomodeset"
date: 2018-01-24
forum: Installation &amp; Upgrades
---

### Post by felipeaamacedo on 2018-01-24
Hello everyone, 

I recently tried to install Xubuntu on my HP Mini 110 1121br, but it turns that Xubuntu tries to initiate but it stays on that screen, with a sort of purple bar and mouse arrow on it, such as the picture bellow:

[IMG]https://photos.app.goo.gl/wbVKOWYkSPttapQF2[/IMG] [ATTACH=CONFIG]278305[/ATTACH]

I figured it was a graphics's driver issue, so I restarted the PC pressed Shift to get the grub menu, then pressed E, and switched from **quiet splash** to **nomodeset**, and it worked, I can now use Xubuntu. Thought I couldn't figure out how to install the graphic's driver, because it doesn't show up on the additional drivers app on xubuntu.

Is it a graphics driver problem, or not?:confused:

does someone knows how to fix it?

Laptop specs:

processor: **Intel Atom N270 1,60GHz**
RAM: **1GB 533GHz**
Graphics card: **Intel Graphics Media Accelerator 950**

Yes, it is an awful Netbook  :D

Thanks again for the community support, hopefully when I become more experienced on Ubuntu flavors I'll also contribute!

---

### Post by ubfan1 on 2018-01-24
Recovering Journal....  Clearing orphaned inode....  Looks like a disk problem.  Run fsck and from the smartmontools package, run smartctl -a  to get a disk report.

---

### Post by ajgreeny on 2018-01-24
Which version of Xubuntu?

Check that the **xserver-xorg-video-intel** package is installed as there was a problem at one time with it not being installed by default in some versions of Lubuntu, though I thought this was now overcome, but it may be worth checking.

EDIT:
Your netbook may also run better with Lubuntu rather than Xubuntu.
I am typing this on an old netbook of apparently identical spec as yours, but with Lubuntu 16.04, and whilst not exactly sprightly, it is pretty good when travelling just for email and browsing.

---

### Post by felipeaamacedo on 2018-01-26
Hello everyone, first thanks to reply my problem,

ubfan1, well I ran the disk to see if there were any problem, but there was none, I really think it is a graphic issue, something like what ajgreeny said.

By the way, ajgreeny, I followed your advice and installed Lubuntu 17.10, but it has the same issue. In order to try fixing it, I tried to install **xserver-xorg-video-intel**, by typing on the terminal:

[B]sudo apt-get update
sudo apt-get install xserver-xorg-video-intel

[/B]However I got this message[B]

Reading package lists... Done
Building dependency tree        
Reading state information... Done
xserver-xorg-video-intel is already the newest version (2:2.99.917+git20170309-0ubuntu1).
The following packages were automatically installed and are no longer required:
  guile-2.0-libs libgc1c2 libgsasl7 libkyotocabinet16v5 libmailutils5
  libmysqlclient20 libntlm0 mailutils-common mysql-common
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 124 not upgraded.[/B]

Does anybody knows how to install this package correctly?

Thanks again!

---

### Post by Bashing-om on 2018-01-26
felipeaamacedo; Hello -

As we have:
> 
0 upgraded, 0 newly installed, 0 to remove and 124 not upgraded.

Let's get this system fully updated and then see what the graphic's status is.
From terminal is the more expedient means to do this :
At the log in screen - key combo ctl+alt+F2 - to gain a console interface. Login here with user name and pass word ( no response to the screen when PW is entered ; enter the pass word blindly and hit the enter key ).

Here once logged in execute terminal commands:
```

sudo apt update
sudo apt full-upgrade

```
Any error(s) then post these results .

Re-boot to see the effect .
```

reboot

```

[INDENT][INDENT]let there be light
[/INDENT][/INDENT]

---

### Post by felipeaamacedo on 2018-01-28
Hello Bashing-om, I did what you said, but I've got no errors, and the the problem still persists.

Here is what I got after apt update, and apt full-upgrade
[B]All packages are up to date.
felipeaamacedo@felipeaamacedo:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

[/B]

---

### Post by Bashing-om on 2018-01-28
felipeaamacedo; Well ! - not

Let's clear the deck for action. What are the parameters passed to the kernel at boot time ?
```

cat /proc/cmdline

```
make sure that 'nomodeset' is not set.

What now does the gpu-manager relate as to the graphic's situation ?
```

cat /var/log/gpu-manager.log

```

Is there a driver loaded ?
```

sudo lshw -C display

```

From these we see where we go and what to do next.

[INDENT][INDENT]all in  the process
[/INDENT][/INDENT]

---

