---
title: "xserver-xorg upgrade errors"
date: 2009-06-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by descendent87 on 2009-06-30
Just got the following errors while upgrading:
```
libglu1-xorg-dev x11-common xlibmesa-gl-dev xserver-xorg xserver-xorg-input-all xserver-xorg-video-all
```

```
Preparing to replace x11-common 1:7.4~5ubuntu21 (using .../x11-common_1%3a7.4+3ubuntu1_all.deb) ...
Unpacking replacement x11-common ...
Preparing to replace libglu1-xorg-dev 1:7.4~5ubuntu21 (using .../libglu1-xorg-dev_1%3a7.4+3ubuntu1_all.deb) ...
Unpacking replacement libglu1-xorg-dev ...
Preparing to replace xlibmesa-gl-dev 1:7.4~5ubuntu21 (using .../xlibmesa-gl-dev_1%3a7.4+3ubuntu1_all.deb) ...
Unpacking replacement xlibmesa-gl-dev ...
Preparing to replace xserver-xorg-video-all 1:7.4~5ubuntu21 (using .../xserver-xorg-video-all_1%3a7.4+3ubuntu1_amd64.deb) ...
Unpacking replacement xserver-xorg-video-all ...
Preparing to replace xserver-xorg-input-all 1:7.4~5ubuntu21 (using .../xserver-xorg-input-all_1%3a7.4+3ubuntu1_amd64.deb) ...
Unpacking replacement xserver-xorg-input-all ...
Preparing to replace xserver-xorg 1:7.4~5ubuntu21 (using .../xserver-xorg_1%3a7.4+3ubuntu1_amd64.deb) ...
Unpacking replacement xserver-xorg ...
dpkg: error processing /var/cache/apt/archives/xserver-xorg_1%3a7.4+3ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/hal/debian-setup-keyboard', which is also in package hal
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xorg_1%3a7.4+3ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by paul_in_london on 2009-06-30
Yeah, I'm seeing this too on i386...

---

### Post by zika on 2009-06-30
```
zika@zika-desktop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  xserver-xorg 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/29.1kB of archives. After unpacking 426kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 151190 files and directories currently installed.)
Preparing to replace xserver-xorg 1:7.4~5ubuntu21 (using .../xserver-xorg_1%3a7.4+3ubuntu1_amd64.deb) ...
Unpacking replacement xserver-xorg ...
dpkg: error processing /var/cache/apt/archives/xserver-xorg_1%3a7.4+3ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/hal/debian-setup-keyboard', which is also in package hal
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xorg_1%3a7.4+3ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

---

### Post by psyke83 on 2009-06-30
Relax, people. An [update]("https://lists.ubuntu.com/archives/karmic-changes/2009-June/003422.html") to hal is probably still waiting to be built, and the new xserver depends on the changes in the newer hal package. Don't force any partial upgrades, the problem will resolve itself.

---

### Post by paul_in_london on 2009-06-30
Resolved by the latest set of updates.

---

### Post by Regenweald on 2009-06-30
Sudo aptitude safe-upgrade always :)

---

### Post by descendent87 on 2009-06-30
> **paul_in_london said:**
> Resolved by the latest set of updates.

yeah fixed for me too

---

### Post by tepsipakki on 2009-06-30
HEADS UP:

you'll be disappointed once you restart your session, since gdm is looking for the wrong X (/usr/X11R6/bin/X is no more).. sorry for the trouble, there is a new gdm coming up soon where the path is fixed to /usr/bin/X.

in the meantime, hold your upgrades for a while...

---

### Post by descendent87 on 2009-06-30
is it the same for kdm?

---

### Post by wayne_cat on 2009-06-30
I still get the error and gdm does not start after a reboot.

[COLOR=Red]edit: [[COLOR=#76482C]**tepsipakki**[/COLOR]]("http://ubuntuforums.org/member.php?u=367778") posted the solution while I was typing my answer. [/COLOR]

---

### Post by afv on 2009-06-30
> **wayne_cat said:**
> I still get the error and gdm does not start after a reboot.

[COLOR=Red]edit: [[COLOR=#76482C]**tepsipakki**[/COLOR]]("http://ubuntuforums.org/member.php?u=367778") posted the solution while I was typing my answer. [/COLOR]


You can also login at tty and do "startx".

---

### Post by wayne_cat on 2009-06-30
> **afv said:**
> You can also login at tty and do "startx".

Thanks ...  worked ... had to remove (temporary) gdm from /etc/X11/default-display-manager.

---

### Post by tepsipakki on 2009-06-30
> **descendent87 said:**
> is it the same for kdm?

Not as far as I can tell.

---

### Post by tjeremiah on 2009-06-30
I get this when try to start```
 Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?
```

I hit yes and receieve this 
```
Warning : Could not generate /etc/x11/xorg.conf.failsafe for vesa driver
```

Anyway I read throughout the thread and "start x" seems to allow me to continue.

---

### Post by DougieFresh4U on 2009-06-30
I seem to be getting the 'starting in low graphics mode' meesege. Then it goes on to tell me it's due to 'AIGLX' and something about rendering. I can not login to anything other than .30.9, I installed the .31 kernel earlier today and had the 'xorg' update that failed and was presented with all this mees upon reboot.
Any idea what this 'AIGLX' issue is? And how to correct it?
Thanks
[B]
EDIT: GDM update seems to have allowed me to boot with out all the drama![/B]

---

### Post by alphacrucis2 on 2009-06-30
An update horribly broke X for me. Have just run another update and some new x-server packages installed. All seems to be well again.

---

### Post by wayne_cat on 2009-06-30
> **alphacrucis2 said:**
> An update horribly broke X for me. Have just run another update and some new x-server packages installed. All seems to be well again.

Are you using gdm/kdm on your system? I get an error with gdm

---

### Post by tjeremiah on 2009-06-30
did an update and all appears to be well. Thank God.

---

### Post by Starks on 2009-07-01
Synaptics touchpad is borked.

---

### Post by jppr on 2009-07-01
> **starks said:**
> synaptics touchpad is borked.

+1

---

### Post by ghindo on 2009-07-01
> **Starks said:**
> Synaptics touchpad is borked.Did you file a bug report?

---

### Post by Starks on 2009-07-01
No need.

I had to reinstall xserver-xorg-video-synaptics

---

### Post by paul_in_london on 2009-07-01
The subsequent gdm update that came through last night fixed it again for me as well.

Don't know what things are like today yet though :)

---

### Post by schmolch on 2009-07-01
I was able to upgrade now but when i start X i only get some white lines.

---

### Post by ghindo on 2009-07-01
> **schmolch said:**
> I was able to upgrade now but when i start X i only get some white lines.Visions, dreams of passion!

---

### Post by descendent87 on 2009-07-01
> **ghindo said:**
> Visions, dreams of passion!

:lolflag:

---

### Post by drfox on 2009-07-01
startx doesn't work for me now that I've updated to the 2.6.31-1 kernel. I have to escape into grub2 and select 2.6.30-10-generic in order to get my desktop.

HTH

Larry

---

### Post by Aries K on 2009-07-02
It's gotten worse for me after the updates. Now it doesn't even boot me into a non-graphics mode to open up a terminal so I can upgrade or startx. So now it just gets stuck on the screen where it shows "Hardware abstraction layer" with "Fail" on it. Can't startx or anything. :(

---

### Post by Peter09 on 2009-07-02
Yes, when I boot I get a pretty? green a white striped screen, I get this in normal and recovery mode. I have to boot against the older kernel to get in.

---

### Post by fabrixx on 2009-07-02
There is a similar bug

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/394288](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/394288)

old:
[https://bugs.launchpad.net/baltix/+source/xserver-xorg-video-vesa/+bug/174434](https://bugs.launchpad.net/baltix/+source/xserver-xorg-video-vesa/+bug/174434)

---

### Post by Cloud79 on 2009-07-02
I reinstalled the earlier broken xserver-xorg update. Then later in failsafe i installed the newer fixed version. I had to restart dbus and hal for this to work. 

The problem is, now i can't get into X at all. Just get graphicgarbage all over the screen. No mousepointer, keyboard stop working and so on. How do i fix this? I have tried with the vesa and radeon driver but i get the same thing. Seems to be x that is the problem after my messy updates. Help! :)

---

### Post by MacUntu on 2009-07-02
> **Cloud79 said:**
> The problem is, now i can't get into X at all. Just get graphicgarbage all over the screen. No mousepointer, keyboard stop working and so on. How do i fix this? I have tried with the vesa and radeon driver but i get the same thing. Seems to be x that is the problem after my messy updates. Help! :)

Just an idea: what's the output of ```
ls -l /dev/null
```?

---

### Post by fabrixx on 2009-07-02
Problem solved:

Add to [I]/etc/gdm/gdm.conf-custom the following:

[/I]```
[server-Standard]
command=/usr/bin/Xorg
```

(delete /usr/X11R6/bin/X if you have it at that place)

Bye ;)

---

