---
title: "Desktop hangs after upgrade to 18.04 (32 bit)"
date: 2018-10-20
forum: Installation &amp; Upgrades
---

### Post by rob190 on 2018-10-20
I've been running 14.04 (32 bit) for several years. I recently upgraded to 16.04 without any problems. I've now upgraded to 18.04 but can't get the desktop to run. I still have access via ssh and everything else appears to be running ok (web server, ftp server, git etc.). The symptoms are variable, including:


[LIST]
[*]Spashscreen, then a cursor top left. No login. 
[*]Login prompt but entering details just causes it to return to the login screen. 
[*]Login prompt which appears to accept the login but then hangs with the background and cursor displayed but no response. 
[/LIST]
 
I've tried various display managers including gdm3, lightdm, kde. None seem to work.

It has a skylake CPU with integrated graphics. The driver appears to be there ok.

I haven't been able to run fsck, even from a live CD. It just says 'disk in use'. 

Note this is still a 32-bit system. I guess running Ubuntu in 32 bit mode is fairly uncommon these days and I'm beginning to suspect it's not been tested as much as 64 bit. It's going to be a serious amount of work to do a fresh install of 64 bit and transfer everything over so is there anything I can do to debug this? I can't see anything obvious in any of the log files but it's quite possible I'm looking in the wrong places. 

Rob.

---

### Post by rob190 on 2018-10-24
Update:

Ran fsck from Ubuntu live. No errors.

Built and installed everything from here: [https://01.org/linuxgraphics/documentation/build-guide-0](https://01.org/linuxgraphics/documentation/build-guide-0) (mesa drive etc.)

It now boots (intermittently) to the desktop but immediately reports an error 'Sorry Ubuntu has experienced an error..."

After a minute or so I also get the error: "A system problem has been detected" (or something very similar) followed by a blank screen.

Access from ssh is fine and everthing except the desktop is working properly as far as I can tell.

---

### Post by rob190 on 2018-10-26
Finally found the problem. Contrary to what I had understood, 18.04 defaults to Wayland, at least on 32 bit. 

I disabled Wayland by editing /etc/gdm3/custom.conf, changing

#WaylandEnable=false

to

WaylandEnable=false

On reboot, it displayed the boot log but didn't start the display manager. This is the first time I've been able to view the boot log so it seems Wayland was getting in there very early and corrupting something. There were various errors e.g. 'failed to start the snappy daemon' so I ran the following:

apt-get update'
dpkg --configure -a
apt-get dist-upgrade
apt-get -f install

and on reboot I now have a working desktop.

---

