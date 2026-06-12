---
title: "unable to boot GUI automatically"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by h313 on 2011-07-11
I am using ubuntu 11.04 from its release.
A month ago, i installed gnome3, replacing unity.
I have a ATI 5470 graphics card and needed to uninstall its drivers to make gnome 3 work.
yesterday, after updating my Natty, i waz unable to boot.
it displayed the following message and stopped.

*Enabling additional executable binary formats binfmt-support [OK]
*Starting CUPS printing spooler/server [OK]
*Starting anac(h)ronistic cron [OK]
*Stopping anac(h)ronistic cron [OK]

i was able to boot through recovery mode using 'startx'
I have checked all updates, and update manager displays,"the system is up-to date"

So i reinstalled gnome 3, and the above message vanished.
But now the problem is, i cannot boot in gui directly.
Everytime, i have to login from command line and fire the startx command.
How can i solve this ?
and what was the problem for the above message ?

---

### Post by snoopy-2009 on 2011-08-22
sucks no one has responded to this......did u figure out this problem? im having the exact same prob.

im entirely lost to any solution to this... and my issues are exactly the same, down to the fglrx driver being incompatable with gnome3. 

ive tried numerous things in attempt to fix this, ive had normal boots after fresh install, and even some after gnome installed. 

what im unsure of, is what's actually causing this to start happening...

seems completely random.. at times i thought it was only after i copied in my home directory, but that doesnt seem to be the case at all times either (its done it a few times in the installation process BEFORE copying in my user folder.)  

other times it seems that it stalls from a problem after installing my apache2, php, etc packages...also there was a time i uninstalled all those packages, and reinstalled, and the problem went away for the time being. unsure what brought it back.....

i really dont know...

im hoping theres some cmd outputs someone on here will ask for, that could help narrow down this problem?

ive had 11.04 and gnome3 working perfectly on this system before, all same hardware. 


@ original poster:   did you figure out a solution? any advice?

---

### Post by garvinrick4 on 2011-08-22
> i was able to boot through recovery mode using 'startx'
I have checked all updates, and update manager displays,"the system is up-to date"Which are you using now gdm or lightdm.
Can you get into a tty and it just does not get to login screen?
```
sudo dpkg-reconfigure gdm
``` (or lightdm if both installed should choose one there)

Does:
```
sudo /etc/init.d/gdm restart 
```From a tty does it boot you.
Just seems like a:
GDM provides the equivalent of a "login:" prompt for X displays: it asks for a
 login and starts X sessions.
or a problem:
Provides: x-display-manager
Description: Display Manager
 LightDM is a X display manager that: 
 * Has a lightweight codebase

---

### Post by snoopy-2009 on 2011-08-23
hopefully not hijacking this thread... im in hopes our problems are identical, and i can provide equivalent information... 

nor do i know if the OP will even return to this thread? (which i hope he does, i could use his help too!)

ive wondered if its any possible hardware failure? maybe just shorting out /sometimes/ ? .. but at the same time i have much hope, since everything does seem to run properly, if i go around the halt.

i usually have the same messages the OP stated, before halting.

i CAN use any of the alternate tty's and login and do startx (or sudo startx if not in root).

gnome3 boots properly then, except for it WILL login as root, and i have the option of switching over to another user, (my primary) and it puts it on /another/ tty mod.

im nearly positive any problems i /am/ having after switching over to my primary user, is strictly only because i've booted incorrectly, this way.  --because, if and when i CAN boot properly, logging in only as my primary, (not root first then switch)  EVERYTHING runs exactly as I'm accustomed to. Correct privlages (w/o modifying anything), the network manager and sound options are on the correct user (otherwise theyre mixed between the two tty desktops, and are NOT correct--sound only works on one, etc..mess), everything runs smoothly if i can get it to boot to the login screen ON IT'S OWN. 

thats the only problem really... if i could determine what's causing it, i could fix it, replace it, whatever the case may be..  just NEED HELP determining what it is :P

...
...

anyway, with your advise, i ran :
sudo dpkg-reconfigure gdm[FONT=monospace]

which returned no errors, or prompts, nothing.

next i ran:[/FONT]
sudo /etc/init.d/gdm restart[FONT=monospace]
which returned:

[/FONT]rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm restart

[FONT=monospace]blah.. a few more lines, and mentioning:   start gdm   and  stop gdm 

each of these methods (including the first--acts like it does the same thing, even with the returned message)  flashes the screen once, then returns to the tty screen i was running on.

im a slight noob with linux, been about 6 months on ubuntu. done quite a bit of reinstalling and tinkering, replacing hardware, etc on different machines, all of my systems (and my wifes') are all ubuntu, 4 in total. one running ubuntu server, i had ubuntu netbook on her's til 11.04. 
ANYWAY...rambling for nothing.. sorry..

point being, im not sure the difference between gdm or lightdm ? 

if i can answer any other questions, please ask, i can run any commands neccessary or requested... . i would really like to figure out what is causing this headache.

[/FONT]

---

### Post by snoopy-2009 on 2011-08-23
well...that just sucked.... quite ironic actually....i must explain..lol...

laptop froze just after i sent last reply.. i rebooted, booted properly!
came back on, started typing another msg (lost quite a bit of typing) 
began with "wow, im actually quite surprised i managed to send that last reply before it froze" 
typed somemore, eventually losing another message... lol.. i find humor in that, at least looking at it positively... lol


ANYWAY...point!

BOOTED PROPERLY! 
unsure if it will boot properly AGAIN or not.. will try after sending this.

BAD POINT:   desktop compeltely restarted after just a few minutes of running ONLY firefox... ?? hmmph!
another:  if it continues to boot properly, then i may not figure out whats wrong with my laptop until something else goes wrong!! :( lol

if theres any way for us to track this down, please help me figure it out! i can replace whatever needs fixing....(damn it see, now i dont know what i wrote in the last message, and the one i lost! FRUSTRATING! lol.. im sure someone out there can relate to this happening! :P )

---

### Post by garvinrick4 on 2011-08-23
```
im not sure the difference between gdm or lightdm ? 
```lightdm took over for gdm in oneiric but it can be installed in Natty.
```
rick@rick-HP:~$ aptitude show gdm
Package: gdm                             
State: not installed
Version: 3.0.4-0ubuntu9
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 2,081 k
Depends: libaccountsservice0 (>= 0.6.8), libc6 (>= 2.4), libcairo2 (>= 1.10.0),
         libcanberra-gtk3-0 (>= 0.25), libcanberra0 (>= 0.2), libdbus-1-3 (>=
         1.0.2), libdbus-glib-1-2 (>= 0.88), libfontconfig1 (>= 2.8.0),
         libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0
         (>= 2.27.4), libgtk-3-0 (>= 3.0.0), libpam0g (>= 0.99.7.1),
         libpango1.0-0 (>= 1.14.0), libupower-glib1 (>= 0.9.0), libwrap0 (>=
         7.6-4~), libx11-6, libxau6, libxdmcp6, libxrandr2 (>= 2:1.2.99.3),
         debconf (>= 0.5) | debconf-2.0, gconf2 (>= 2.28.1-2), upstart-job,
         adduser, libpam-modules (>= 0.72-1), libpam-runtime (>= 0.76-13.1),
         accountsservice (>= 0.6.12), gnome-session-bin, kbd | console-tools,
         udev (>= 166-0ubuntu4)
Recommends: xserver-xorg, metacity | x-window-manager, gnome-settings-daemon |
            xfconf
Suggests: libpam-gnome-keyring, locales, uswsusp, gnome-power-manager,
          gnome-mag, gnome-orca, gok
Breaks: usplash
[COLOR=Red]Provides: x-display-manager[/COLOR]
Description: GNOME Display Manager
 GDM provides the equivalent of a "login:" prompt for X displays: it asks for a
 login and starts X sessions. 
 
 It provides all the functionality of XDM, including XDMCP support for managing
 remote displays, and extends it with the ability to start X servers on demand. 
 
 The greeter is written using the GNOME libraries and hence looks like a GNOME
 application - even to the extent of supporting themes! 
 
 This package contains the next generation GDM, which was developed using the
 technologies on which GNOME 3 is based.


``````
rick@rick-HP:~$ aptitude show lightdm
Package: lightdm                         
New: yes
State: installed
Automatically installed: no
Version: 0.9.3-0ubuntu5
Priority: optional
Section: x11
Maintainer: Robert Ancell <robert.ancell@ubuntu.com>
Uncompressed Size: 389 k
Depends: debconf (>= 0.5) | debconf-2.0, upstart-job, libc6 (>= 2.4),
         libglib2.0-0 (>= 2.28.0), libpam0g (>= 0.99.7.1), libxcb1, libxdmcp6,
         libpam-runtime (>= 0.76-14), libpam-modules, adduser, dbus
PreDepends: dpkg (>= 1.15.7.2)
Recommends: xserver-xorg, unity-greeter | lightdm-greeter
Conflicts: liblightdm-gobject-0-0, liblightdm-qt-0-0
[COLOR=Red]Provides: x-display-manager[/COLOR]
Description: Display Manager
 LightDM is a X display manager that: 
 * Has a lightweight codebase 
 * Is standards compliant (PAM, ConsoleKit, etc) 
 * Has a well defined interface between the server and user interface 
 * Cross-desktop (greeters can be written in any toolkit)
Homepage: https://launchpad.net/lightdm



```

---

### Post by snoopy-2009 on 2011-08-23
bahhh..... definitely NOT fixed... lol... i can get it to boot maybe 1/7 times.... and seemingly it WILL NOT boot alone.. i HAVE TO be rapidly spamming shift-enter-f6   again... i have no idea what this does, or if it even invloves all three keys.. lol shift f6 seems to bring up grub earlier on.... this blows...

---

### Post by snoopy-2009 on 2011-08-23
unnecesary post.. mods plz delete. sorry.

---

### Post by snoopy-2009 on 2011-08-23
heres what i got...


```
elite@DESIGNbox:~$ sudo aptitude show gdm
Package: gdm                             
State: installed
Automatically installed: no
Version: 3.0.4-0ubuntu3~natty1
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 7,627 k
Depends: libaccountsservice0 (>= 0.6.8), libatk1.0-0 (>= 1.12.4), libattr1 (>=
         2.4.41-1), libc6 (>= 2.4), libcairo-gobject2 (>= 1.10.0), libcairo2 (>=
         1.10.0), libcanberra-gtk3-0 (>= 0.25), libcanberra0 (>= 0.2),
         libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libfontconfig1 (>=
         2.8.0), libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.31.1),
         libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.27.4), libgtk-3-0
         (>= 3.0.0), libpam0g (>= 0.99.7.1), libpango1.0-0 (>= 1.14.0),
         libselinux1 (>= 1.32), libupower-glib1 (>= 0.9.0), libwrap0 (>=
         7.6-4~), libx11-6, libxau6, libxdmcp6, libxklavier16 (>= 5.1),
         libxrandr2 (>= 2:1.2.99.3), debconf (>= 0.5) | debconf-2.0, gconf2 (>=
         2.28.1-2), upstart-job, adduser, libpam-modules (>= 0.72-1),
         libpam-runtime (>= 0.76-13.1), accountsservice (>= 0.6.12),
         gnome-session-bin, kbd | console-tools, udev (>= 166-0ubuntu4)
Recommends: xserver-xorg, metacity | x-window-manager, gnome-settings-daemon |
            xfconf
Suggests: locales, uswsusp, libpam-gnome-keyring, gnome-power-manager,
          gnome-orca, gok, gnome-mag
Breaks: usplash
Provides: x-display-manager
Description: GNOME Display Manager
 GDM provides the equivalent of a "login:" prompt for X displays: it asks for a
 login and starts X sessions. 
 
 It provides all the functionality of XDM, including XDMCP support for managing
 remote displays, and extends it with the ability to start X servers on demand. 
 
 The greeter is written using the GNOME libraries and hence looks like a GNOME
 application - even to the extent of supporting themes! 
 
 This package contains the next generation GDM, which was developed using the
 technologies on which GNOME is based.


```AND

```


elite@DESIGNbox:~$ aptitude show lightdm
Package: lightdm                         
State: not installed
Version: 0.2.3-0ubuntu2
Priority: optional
Section: universe/x11
Maintainer: Robert Ancell <robert.ancell@ubuntu.com>
Uncompressed Size: 258 k
Depends: debconf (>= 0.5) | debconf-2.0, upstart-job, libc6 (>= 2.4),
         libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libglib2.0-0 (>=
         2.22.0), libpam0g (>= 0.99.7.1), libxcb1, libxdmcp6, libpam-runtime (>=
         0.76-14), libpam-modules, adduser
Recommends: xserver-xorg, lightdm-theme-gnome | lightdm-theme-webkit
Provides: x-display-manager
Description: Display Manager
 LightDM is a X display manager that: 
 * Has a lightweight codebase 
 * Is standards compliant (PAM, ConsoleKit, etc) 
 * Has a well defined interface between the server and user interface 
 * Fully themeable (easiest with the webkit interface) 
 * Cross-desktop (greeters can be written in any toolkit)
Homepage: https://launchpad.net/lightdm




```


so im using gdm... good to know i guess.. but what does that tell me about why my laptops not booting properly ?

---

### Post by garvinrick4 on 2011-08-23
> so im using gdm... good to know i guess.
I was just showing you what you asked about not knowing difference
and or how to find out what a package is.

Usually when a system gets to a certain point and then will not boot
into X but can get to a tty it has something to do with gdm. Just trying to point OP in that direction.
OP had installed gnome3-team ppa most likely in Natty to get to run gnome-shell and is using that instead of Unity or Classic Gnome so is running a system that has different variables involved.

---

### Post by MAFoElffen on 2011-08-23
Yes "garvinrick4" is definitely on the right track... GDM on yours seems to be bonked.  Not the package itself, but how it's loading and when. 

Your kernel boots... then stpos without errors, where GDM should start.  GDM starts manually and boots, but not on it's own, where it should.

Just for info-- the Display Managers were changed to upstart services when we were testing 11.04 at about apha2.  LXDM came back in at late 11.10 pre-alpha and I'm still having bugs with that on 5 machines in present dev builds (but hopefully will be worked out soon!!!).  But yes, it's slated to be the default on 11.10. Using "aptitude" and synaptic is other's that on 11.10 we will have to "install" to continue to use, or adapt to what's there...

Back to this, if reconfigure didn't work.... Maybe the Display Manager for some reason still isn't in the startup lists to get loaded at startup, then "garvinrick4's" idea of installing LXDM or to re-install GDM would still be spot-on...
```

sudo apt-get remove --purge gdm
sudo apt-get install gdm

```would add it back in to those startup lists and solve your problem.  You'ld think that dpkg -reconfigure gdm would do that, but sometimes it doesn't with only one DM installed.  With 2 DM's, you can flip back and forth and it does hit those files each time.  (My test boxes are XDM, GDM, KDE and LXDM.)

Edit after a few hours sleep-- another idea I have on this is update the  startup image.  Theres bee a few X relaied problems that have been  solved by that in the past 2 weeks. (Going back to sleep.)

Just an idea... A couple minutes of time to reinstall the same package and confirm they are configured correctly, with fresh files. Hoping a different perspective helps..

---

### Post by snoopy-2009 on 2011-08-23
> **garvinrick4 said:**
> I was just showing you what you asked about not knowing difference
and or how to find out what a package is.

Usually when a system gets to a certain point and then will not boot
into X but can get to a tty it has something to do with gdm. Just trying to point OP in that direction.
OP had installed gnome3-team ppa most likely in Natty to get to run gnome-shell and is using that instead of Unity or Classic Gnome so is running a system that has different variables involved.

actually thats exactly my point... my problem seems identical to his. i too use gnome-shell. and have the same graphics card.. im almost wondering if we have the same laptop....lol... it was somewhat scary when i found this post, he mentioned everything the exact same way i would have. 110% same details that i know of. 

im not sure if OP abandoned this thread, he hasnt said anything back to our replies yet. i found it, and pretty much re-innitiated discussion on this problem, as mine is seemingly identical so far.

---

### Post by snoopy-2009 on 2011-08-23
so should i post a new thread of my own to ask for help? --even tho my problem appears to be exactly the same..but just in case its actually not, and variables /are/, in fact, different..?

i suppose i can, i just dont know if it's necessary or not.....

advice?

at times i have done a fresh install of 11.04, and still get the boot stop at same part.

--right now i have gnome-shell (g3) installed over ubuntu 11.04 amd64 on an HP Pavilion dv7.

 i CAN /Always/ switch to alt TTY module, and boot with startx, that works, but i get stuck booting startx with sudo permissions, so it initially logs me in AS root. 
i then can 'switch user', (and it will allow logging in as my primary user, on an additional TTY. --so i can actually switch between root@tty7 and user@tty8) 

- but theres a variety of permission issues; 
- if i can get the sound to play at all-- sound options only work on ONE desktop (& seperate volume controls?);
- network manager only displays on root desktop, etc..

BUT, IF and WHEN i /DO/ get it to trigger a normal boot, EVERYTHING works properly!

---

