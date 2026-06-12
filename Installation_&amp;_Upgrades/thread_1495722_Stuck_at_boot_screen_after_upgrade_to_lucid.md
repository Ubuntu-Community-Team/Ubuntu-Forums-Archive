---
title: "Stuck at boot screen after upgrade to lucid"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by kcn_viper on 2010-05-28
Hi All,

I did a clean upgrade to lucid 10.04 from Karmic 9.10. After the installation, the boot was stuck at the purple screen with red and white dots.
I did this on Dell XPS M1530 laptop and there was no problem in Karmic.

1. I found a temporary solution. After being stuck here, I simply go to tty1, login and startx. Now, I could work normally but if I go to tty1 and then to 'Ctrl-Alt-F7', I could still see the purple boot screen whereas 'Ctrl-Alt-F8' brings me to the normal GUI. How do I get rid of this purple boot screen ?

Searching on google suggested:
2. Remove 'quiet splash' and instead use 'nomodeset'. When I did this, I got the black screen with the messages during boot but it still got stuck. Importantly, there was no login prompt at tty1 or other ttys. Some messages towards the end where boot got stuck are below. Please help as I did like a fix to this.
-----start messages
udevd[429]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:30
 
udevd[429]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:32
 
/dev/sda9: clean, 259570/1224000 files, 1649804/4883752 blocks (check in 3 mounts)
/dev/sda8: clean, 151452/1525920 files, 3210148/6102684 blocks
init: ureadahead-other main process (1030) terminated with status 4 
init: ureadahead-other main process (1035) terminated with status 4 
/usr/local/bin/fusermount
Fuse filesystem already available.
Fuse control filesystem already available.
 * Starting AppArmor profiles       [180G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 [174G[ OK ]
 * Setting sensors limits       [180G  [174G[ OK ]
 * Starting BandwidthD bandwidthd       [180G  [174G[ OK ]
 [33m*[39;49m Speech-dispatcher configured for user sessions
 * Starting VirtualBox kernel modules       [180G  [174G[ OK ]
 * Starting the Winbind daemon winbind       [180G  [174G[ OK ]
 * Starting Common Unix Printing System: cupsd       [180G  [174G[ OK ]
 [33m*[39;49m PulseAudio configured for per-user sessions
 * Enabling additional executable binary formats binfmt-support       [180G  [174G[ OK ]
 * Starting web server apache2       [180G  [174G[ OK ]
 * Checking battery state...       [180G  [174G[ OK ]
----------end messages.

Thanks,
 kcn

---

### Post by ronparent on 2010-05-28
You might try getting to the recovery mode menu and runing dpkg (hightlight and return). This may update your install distro to sweep a known bug? Post on how you make out.

---

### Post by kcn_viper on 2010-05-28
Sorry I didn't quite get you. I can work normally after doing startx from tty1 for example. So, do I need to go to recovery to fix this by running dpkg ? How do I run dpkg from recovery ? Can you give me the exact command to run ?

One thing more: I have to login from tty1, startx and then give the keyring password to enable the network. How do I get the network to be connected automatically after boot - even before logging in ?

thanks,
 kcn

---

### Post by ronparent on 2010-05-28
i'm sorry, I don't have a good answer for you. You semm to be doing all the right things to patch around your particular glitch. I'm also unsure about how the dpkg  command is formed in the recovery mode menu except that when I ran it, inadvertently in experimentation, I was upgraded from the .21 kernel to the .22 along with a lengthy host of updates.

On the hunch that something is malfunction on your particular system in the last stage of booting, running dpkg in the recovery mode might update or upgrade to overwrite the troublesome factor in your install. For instance, early problems with how the splash parameter was acted upon did block proper startup of x within the boot routine. In other words, if a fix has been enacted in one of the updates, it is an easy, no pain try to make a fix - if you can boot into the recovery mode.

---

### Post by kcn_viper on 2010-06-02
bump !

I still have this issue. Is there anyone with a (likely) solution or should I file a bug ?

I did like to boot to the login prompt and then do startx but can't do that right now due to this problem.

thanks,
 kcn

---

### Post by Avionix on 2010-06-02
Hi I have the same problem, got the purple screen with the red and white dots but only after hitting certain keys otherwise I have the udevd[429]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:30
ecept it's for about 30 lines. I can not get a terminal up no matter what combinations of keys I press so I'm stuck.

This upgrade to Lucid has not gone well to say the least, anyone out there got any clues.

Steve:confused:

---

### Post by kcn_viper on 2010-06-09
Hi ronparent,

I tried booting to recovery and running dpkg but it fails because dpkg is not able to access the internet for the package updates. This is because lucid is connecting to internet only after I run 'startx' (starting the x windows) and the entering the keyring password. Only then the wireless network connects.

Is there a way to ensure wireless network is connected during boot itself ? I have posted a different thread for a fix for this issue:
[http://ubuntuforums.org/showthread.php?p=9436469#post9436469](http://ubuntuforums.org/showthread.php?p=9436469#post9436469)

Thanks in advance,
kcn

---

