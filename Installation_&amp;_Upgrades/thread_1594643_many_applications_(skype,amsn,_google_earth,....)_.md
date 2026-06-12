---
title: "many applications (skype,amsn, google earth,....)  crashes GDM / gnome after upgrade"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by deeeed on 2010-10-12
Hi,

I just upgraded to ubuntu 10.10 and my system is now very unstable.
Everytime I want to launch skype or amsn (but I am sure a lot of other softwares causes the same problem) gdm restart.
The only logs I have from this crash is by redirecting the output of the program to a file:

> $ amsn &> crash.log
Xlib:  extension "RANDR" missing on display ":0.0".

(<unknown>:8208): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:8208): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:8208): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:8208): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:8208): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:8208): Gtk-WARNING **: Loading IM context type 'ibus' failed
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

I don't have any errors into the other log files..

Any idea what could cause this problem ?

---

### Post by cornejotux on 2010-10-15
Same problem here!!

---

### Post by Mitsune on 2010-10-22
Bump.
I am experiencing the same problems.
Hovering the cursor over the skype or minitube window after they just started instantly crashes gnome and it restarts and leaves me at the login prompt.
I have tried usb installs, different cds, x86 and x86_64 etc. but the problem is still there.

---

### Post by mörgæs on 2010-10-22
Does the machine work with 10.04?

---

### Post by Mitsune on 2010-10-23
I have previously been running 10.04 on this machine without this issue yes.
I have been looking through the log files and I have not found anything yet.
I'll induce it to crash like it does and have a look again.

---

### Post by utilitytrack on 2010-10-23
> **deeeed said:**
> I just upgraded to ubuntu 10.10 and my system is now very unstable.

What conclusion? You rushed with upgrades. Ubuntu 10.10 inherently are beta version, wich contains so many bugs that we will be several more years work to correct them. So I can advice you to use Ubuntu 9.10 or Debian 5.0.6 or Fedora 13 as much more stable software.

---

### Post by Mitsune on 2010-10-23
My computer is normally configured with a dual screen setup using xinerama.
When I turn this off, the problem is no longer there.
So I guess this works as a temporary fix for me.

---

### Post by lledurt on 2010-10-25
Same problem here.  It crashes randomly when a new window or tab is opened.  It always crashes when I open k3b.  I am also running xinerama but with 3 screens.  I think I am going to try to downgrade X.  I will let you know how it goes.

---

### Post by lledurt on 2010-10-25
I had success in downgrading X, but I truly don't know what I am doing so don't try this unless you think you can fix it if it breaks.

1.  I made a copy of /etc/apt/sources.list
2.  In /etc/sources/list I changed all maverick to lucid.
3.  I opened synaptic and searched for xorg and then removed xserver-xorg and a few other xorg stuff.  It selects a bunch more.  I noted everything that was not an x server stuff.  My only other thing was ubuntu-desktop.
4.  I then reinstalled xorg and it installed the older version of all the xserver stuff.
5.  I then reinstalled ubuntu-desktop, but synaptic couldn't find it. so I did it manually "sudo apt-get install ubuntu-desktop.
6.  I then replaced my original sources.list with the one I modified figuring if I broke it I could do an update/upgrade from a command line to fix it.  MAYBE!
7.  I reconfigured with a dpkg-reconfigure xserver-xorg.  It seamed to have a few errors but still worked.
8.  I rebooted the machine and it worked with the old xserver.
9.  Since it worked I went into synaptic and searched xorg again.  There was a ! in the boxes of all the xserver stuff that could be upgraded.  I highlighted each one of those and went under package and locked version.  This way it will not upgrade.  My plan is when it is fixed I will unlock then upgrade.

Again It worked for me so far, but if you know what you are doing please look at what I did and modify it.  I had to downgrade Nvidia on a different machine to make it work, and I used those instructions to come up with this plan for x.  Again I don't know why it worked but it is working so far.

---

### Post by mauroma@gmail.com on 2010-10-27
same problem for me after upgrading from 10.04 to 10.10, using twinview


here is the .xsession-errors:

[COLOR=DarkRed]/etc/gdm/Xsession: Beginning session setup...
export DESKTOP_SESSION='gnome'
export DISPLAY=':0'
export GDMSESSION='gnome'
export GDM_KEYBOARD_LAYOUT='it'
export GDM_LANG='it_IT.utf8'
export GNOME_KEYRING_CONTROL='/tmp/keyring-huuX4r'
export GNOME_KEYRING_PID='2400'
export HOME='/home/mmazza'
export JAVA_HOME='/home/mmazza/XMauro/Programs/jdk1.6.0_14'
export LANG='it_IT.utf8'
export LANGUAGE='it_IT:it:en_GB:en'
export LD_LIBRARY_PATH='/home/mmazza/XMauro/Programs/instantclient_11_1'
export LOGNAME='mmazza'
export ORACLE_HOME='/home/mmazza/XMauro/Programs/instantclient_11_1'
export PATH='/home/mmazza/XMauro/Programs/jdk1.6.0_14/bin:/home/mmazza/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'
export PWD='/home/mmazza'
export SHELL='/bin/bash'
export SPEECHD_PORT='7560'
export USER='mmazza'
export USERNAME='mmazza'
export WINDOWPATH='7'
export XAUTHORITY='/var/run/gdm/auth-for-mmazza-UdL1Wc/database'
export XDG_SESSION_COOKIE='192f319259574f9c0c31e7134a133252-1288171866.302779-1545951386'
MainThread 2010/10/27 11:31:06.5266 (sabayon-apply): No profile for user 'mmazza' found
Non è stato trovato alcun profilo per l'utente «mmazza»
MainThread 2010/10/27 11:31:06.5268 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2010/10/27 11:31:06.5270 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 149, in <module>
    sys.exit (util.EXIT_CODE_NO_USER_PROFILE)
SystemExit: 3[/COLOR]

---

### Post by elmoosecapitan on 2010-10-29
Hey utilitytrack, has anyone mentioned how helpful you are, lately? 10.10 was released officially, i.e., taken off the beta list, on, well, what do you know, 10/10. Good job.


At any rate, I also have the same problem. Here is what I have been able to figure out: (i) I can force a crash by running rhythmbox for a few seconds, (ii) once the crash occurs I cannot run my terminal, (iii) /tmp seems to be related (it becomes read-only), and (iv) when I do a hard bood my disc checker finds errors but cannot do anything to corret the erros because /tmp cannot be found.

---

### Post by mörgæs on 2010-10-30
Utliltytrack has given the best advice: Stick to an older release. 

As all other releases, 10.10 was not finished by the release dates. If you read the release notes or the relevant pages in Launchpad you will see lots and lots of errors. Maybe these errors are important on your hardware, maybe they are not. Same goes for other operative systems.

11.04 will be released 28. of april 2011. Do you believe that this means that it is error free at that date? How should anyone be able to predict that? 

The only wise approach is to try a new release for a test and see if it works better than the old one on your particular hardware. If not then stay with the old one and try a few months later or skip the release entirely.

---

### Post by wkavinsky on 2010-11-22
First of, sorry for the archaeological exploits, but a quick Google and forum search still points to this post, hence bringing me here.

The problem was a typo in the xorg software (oops!).

There is a fix, it's been committed to the source (by someone other than me), but as of the 20th of November 2010, this patch has not been propagated down to the updates going to a clean installation of Maverick Meerkat.

Lacking anywhere else to post it (the linked bug reports require some data ploughing to get to the fix), these are the steps to fix it:

[QUOTE="Bug #650539"]Until the fix is released as an official Ubuntu update, Jared Bunting has it in his PPA at [https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539]("https://launchpad.net/%7Ejared-bunting/+archive/xorg-xserver-650539") (thx!).
You need xserver-xorg-core and xserver-common, so for 32 bit
1) Download
[https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539/+files/xserver-xorg-core_1.9.0-0ubuntu7%2Bbug650539%2B1_i386.deb]("https://launchpad.net/%7Ejared-bunting/+archive/xorg-xserver-650539/+files/xserver-xorg-core_1.9.0-0ubuntu7%2Bbug650539%2B1_i386.deb") and
[https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539/+files/xserver-common_1.9.0-0ubuntu7%2Bbug650539%2B1_all.deb]("https://launchpad.net/%7Ejared-bunting/+archive/xorg-xserver-650539/+files/xserver-common_1.9.0-0ubuntu7%2Bbug650539%2B1_all.deb")
2) Install
sudo dpkg -i xserver-xorg-core_1.9.0-0ubuntu7+bug650539+1_i386.deb xserver-common_1.9.0-0ubuntu7+bug650539+1_all.deb

3) Restart X Server: CTRL+ATL+BACKSPACE[/QUOTE]

[Full Source of fix]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539")

Possibly this could also be marked as closed/fixed?

---

### Post by lledurt on 2010-12-08
It took a while, but I figured out how to do this in 64bt

1. add ppa 
    sudo add-apt-repository ppa:jared-bunting/xorg-xserver-650539

2.  Open synaptic and make sure it was reloaded after the ppa was added.
3.  Search for xorg.
4.  There should be a green box with an up arrow in xserver-xorg-core Select to upgrade that.  There should be a window indicating that Xorg-server needs to be upgraded.  I selected ok.

5.  reboot or restart the gdm  
     sudo /etc/init.d/gdm restart.

Seems to work.

Good luck.

---

