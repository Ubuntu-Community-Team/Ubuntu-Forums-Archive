---
title: "Post-Kernel Update Woes"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by abzolutxero on 2007-02-12
Well, albeit a woe, this has given me an opportunity to learn alot about Ubuntu.... 

here it goes.  So i did the kernel upgrade without thinking much about it, as i didnt know to expect problems.  As soon as i did, xserver started giving me trouble.  I instantly started trying to fix it without consulting the forums, as i thought it was something else i did that broke it.  

Here is what i did...
- booted into recovery mode
- ran envy, attempted to re-install driver. RESULT- could not find NVIDIA-xconfig, still had xserver issues.
- uninstalled all that is nvidia INCLUDING linux-restricted-modules-2.6.17-10-generic RESULT- nothing but problems thusfar.
- i then followed the directions on [http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html) to install drivers fresh without ENVY, because envy hadnt worked at all. RESULT - it would not install NVIDIA-glx using the provided guide, 
- soo... i used aptitude instead of apt-get, and it resolved the problems for me... it warned me 4 times, and i accepted the warnings.  xserv still did not work.
- so, i ran wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run) , then sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run .  It then informed me it needed to compile the kernel, compiled it, and then configured xorg.conf for me
- AT LAST I FINALLY HAD MY DESKTOP BACK.
- i attempted to run update manager to catch any files that i inadvertently uninstalled, and it informed me that it had to do a distribution upgrade.  i clicked OK, thinking it would fix what i messed up... but it told me it could not do so because of "An unresolvable problem occurred while calculating the upgrade." 
- so i restarted my computer, only to find that xserver would not start again.  It informed me that the driver version for NVIDIA was 1.0-9746, however the NVIDIA kerneal was 1.0-7xxx.  I then reran the nvidia installer shell again, and once again i had my desktop back.  Now each time i restart my computer, i have to run that installer to get to my desktop.  I also attempted to reinstall linux-restricted-modules-2.6.17-10-generic but it told me that it was going to have to downgrade the NVIDIA-GLX to do so, which would put me back in a worse place! (i think)

So i am entirely confused as to what i did, what i need to do to fix it, and where i should go from here.  

Thanks for any responses, i know this is a long post....

---

### Post by IgnorantGuru on 2007-02-13
I hit this problem too - updated the kernel and X wouldn't start.  modprobe nvidia reports "error running install command for nvidia".

Solution for me was
```
sudo apt-get install linux-restricted-modules-2.6.17-11-386
```

However, if you've monkeyed around this may not work now.  You may want to uninstall/reinstall the nvidia driver.  Maybe

```
sudo apt-get install --reinstall nvidia-glx nvidia-kernel-common
```

---

### Post by abzolutxero on 2007-02-13
gonna try those out... thanks.

---

### Post by abzolutxero on 2007-02-13
grr... no dice on that one.  got the following error:

API mismatch:  the kernel module has the version 1.0-8776 but this x module has the version 1.9-9629.

how exactly do i either update that kernel module to 9628 or downgrade the x module to 8776?

---

### Post by visible on 2007-02-13
I had my xserver not start after the kernel update too.  Not sure where the post was but when the screen comes up telling you that xserver failed to start...etc. etc...
the post said to press F1 then run envy to install nvidia driver.  this rebuilds the driver for the new kernel.
evidently the video drivers are based on the particular kernel version that is installed and when it is upgraded it messes it all up and causes it to crash.  this worked for me.

---

### Post by IgnorantGuru on 2007-02-13
Well maybe someone else can give you a better answer, because I've never encountered that.  But here's what I would do...

First, I wouldn't try changing X versions.  Just use the most current version and kernel.

Second, I would remove all nvidia drivers and kernel modules.  Maybe

```
sudo apt-get remove nvidia-glx nvidia-kernel-common
```

Then I would use a package manager to see what linux restricted modules are installed and remove those.

Maybe do a reboot then.  Also, find out what kernel you're using  with

```
sudo uname -r
```

Then I would 
```
sudo apt-get install nvidia-glx nvidia-kernel-common
```

Also install linux-restricted-modules for your kernel version.

```
sudo nvidia-xconfig
```

to enable the driver.  Reboot and then examine /var/log/Xorg.0.log for messages/errors.

I've never had much problem with nvidia drivers so I can't think of much else off-hand.  In fact if all of that didn't work I would probably just backup my /home folder, /etc/X11/xorg.conf, and /etc/fstab, and reinstall Ubuntu.

Then I would get everything installed and configured EXCEPT the nvidia drivers.  Then backup the partition - howto here... [http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017](http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017)

Then install the nvidia drivers, experiment with different methods, and restore the partition to the pre-nvidia state as necessary.

Sounds like the long way but in my experience it's easier than trying to undo a funked system, unless you really know your stuff.

One other suggestion - if you haven't already, do an exhaustive google search on the error messages you're getting.  You can find some solutions that way.

Let me know how it goes.

---

### Post by IgnorantGuru on 2007-02-13
Also, in case it helps, after the kernel update and the new nvidia-glx installation, here are my version numbers...

nvidia-glx   1.0.8776+2.6.17.7-11.1
nvidia-kernel-common   20051028+1ubuntu7
linux-restricted-modules     2.6.17.7-11.1
(I have linux-restricted-modules-common and -386, both the same version number)
xserver-org     1:7.1.1ubuntu6.2

Not sure what you mean by "x module" - don't see a version number like the 1.9-9629 you mentioned.

---

### Post by abzolutxero on 2007-02-14
heh.. it was supposed to be 1.0-9629  oops.  that is the driver fresh off of NVIDIA's website.  however, when it said it was going to compile a kernel for my particular installation it came up with the 1.0-8776.  that was just the blue/red error message that reported when x failed to load.  

i will try those tips  when i get home... thanks guy.

i guess now that i think about it i dont exactly know how to do all of that... i have a few Q's

1- how do i just change the version of X  that i am running?

2- how do i run package manager from terminal?  bascially, when it fails to load X, i dont have any GUI or desktop manager running, so i am doing it all in text.  i'm not quite as versed without gui.

Thanks again.

---

### Post by IgnorantGuru on 2007-02-14
Ok now it makes a little more sense.  Sounds like you are trying to use the 9629 nvidia driver ("fresh off their website") with the kernel module made for the 8776 driver (from ubuntu repos).  Hence the "API mismatch: the kernel module has the version 1.0-8776 but this x module has the version 1.0-9629".  "X module" must be their term for the nvidia driver.

My suggestion is stick with the 8776 ubuntu package rather than the fresh one off their website.  (Or, if you don't want to do that, then you need to compile your own kernel module - not sure how to go about that, so you would need to research it.)  The current linux-restricted-modules-2.6.17-11 seems to have a kernel module for the 8776 driver - hence your conflict.

Not sure how to use a package manager from console either.  But you should be able to proceed without it.  I think you should:

1) remove all traces possible of the 9629 nvidia driver.  Since you used an installer to install it, I'm not sure how to remove it - you should research that.  Maybe the installer can remove it, or maybe dpkg can?  Or maybe apt-get will do it - but it didn't seem to.

2) Just for completeness, I would remove the kernel modules (linux-restricted-modules-2.6.17-11-386, and -generic, as well as nvidia-kernel-common.
```
apt-get remove nvidia-glx linux-restricted-modules-2.6.17-11-386 linux-restricted-modules-2.6.17-11-generic linux-restricted-modules-common nvidia-kernel-common
```

3) Finally, install
```
apt-get install nvidia-glx linux-restricted-modules-2.6.17-11-386 linux-restricted-modules-2.6.17-11-generic linux-restricted-modules-common nvidia-kernel-common
uname -r
```

That should install the 8776 driver and corresponding kernel module.  The uname -r should report 2.6.17-11 (generic, 386, or x64)

---

### Post by IgnorantGuru on 2007-02-14
I notice these uninstall directions from the first website you mentioned...
[http://albertomilone.com/latest_nvidia_udsf_edgy.html#HOW_TO_UNINSTALL_THE_DRIVER_.28FROM_METHOD_2.29](http://albertomilone.com/latest_nvidia_udsf_edgy.html#HOW_TO_UNINSTALL_THE_DRIVER_.28FROM_METHOD_2.29)

However, it looks like that will also remove the nvidia reference in xorg.conf.  So after you install nvidia-glx you'll want to add it back in - one way is
```
sudo nvidia-xconfig
```

---

### Post by abzolutxero on 2007-02-15
alright, tried the methods you proposed, and i started running into some really dumb errors.  when i tried to install nvidia-glx, it kept saying it needed me to re-install the 9629 driver.  which didnt want to do... so i worked with it for a little while, uninstalled all that was nvidia, and related, and resinstalled alot of it.  then when it came down to instlaling the driver, i installed using envy, which has seemed to have worked.  i am back into my desktop, restarted 3 times, no issiues except one....  i dont have sound.  i checked the device manager, it is installed... so then i checked with the sound properties,  and it detects it there too... but still no sound.  adjusted volume, and then still no sound.  i know sound works, because when i use  a live CD, it creates audio.

thanks once again for all of your help.   sorry if this one sounds  a little unorganized, i'm just on the verge of going to bed. 

later :)

---

### Post by IgnorantGuru on 2007-02-15
I use Kubuntu so it may be a little different.  But when I have sound issues I first go into System Settings and test the sound there, make sure it is enabled, etc.

That's probably a separate problem from the video - maybe the sound module isn't loading, is crashing, etc.  Maybe compare an lsmod from the liveCD to your installed one.  Also compare ps.
```
lsmod | grep snd
ps -Af
```

I haven't troubleshooted sound much in (k)ubuntu so I would suggest searching for similar topics.  (SUSE was HELL when it came to sound, but I have repressed those memories.)

---

### Post by abzolutxero on 2007-02-15
okay, i did both of those, and i compared the results.  both seem to be relatively similar, yet i have sound on the liverun and not on the permanent installation.

maybe a fresh set of eyes would help??

Live Run
```
ubuntu@ubuntu:~$ lsmod | grep snd
snd_intel8x0           34844  1
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

```

My Installation
```

abzolutxero@melchior-1:~$ lsmod | grep snd
snd_intel8x0           33436  1
snd_ac97_codec         96672  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            46080  0
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    55428  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
```

Live Run
```
ubuntu@ubuntu:~$ ps -Af
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 01:47 ?        00:00:01 /sbin/init splash --
root         2     1  0 01:47 ?        00:00:00 [migration/0]
root         3     1  0 01:47 ?        00:00:00 [ksoftirqd/0]
root         4     1  0 01:47 ?        00:00:00 [watchdog/0]
root         5     1  0 01:47 ?        00:00:00 [events/0]
root         6     1  0 01:47 ?        00:00:00 [khelper]
root         7     1  0 01:47 ?        00:00:00 [kthread]
root         9     7  0 01:47 ?        00:00:00 [kblockd/0]
root        10     7  0 01:47 ?        00:00:00 [kacpid]
root        11     7  0 01:47 ?        00:00:00 [kacpi_notify]
root       136     7  0 01:47 ?        00:00:00 [kseriod]
root       169     7  0 01:47 ?        00:00:00 [pdflush]
root       170     7  0 01:47 ?        00:00:00 [pdflush]
root       171     1  0 01:47 ?        00:00:00 [kswapd0]
root       172     7  0 01:47 ?        00:00:00 [aio/0]
root      1656     7  0 01:47 ?        00:00:00 [ata/0]
root      1660     7  0 01:47 ?        00:00:00 [scsi_eh_0]
root      1661     7  0 01:47 ?        00:00:00 [scsi_eh_1]
root      1665     7  0 01:47 ?        00:00:00 [scsi_eh_2]
root      1666     7  0 01:47 ?        00:00:00 [scsi_eh_3]
root      1808     7  0 01:48 ?        00:00:00 [khubd]
root      1830     7  0 01:48 ?        00:00:00 [khpsbpkt]
root      1843     1  0 01:48 ?        00:00:00 [knodemgrd_0]
root      1949     1  0 01:48 ?        00:00:00 [loop0]
root      3591     1  0 01:50 ?        00:00:00 //sbin/logd
root      3708     1  0 01:50 ?        00:00:00 /sbin/udevd --daemon
root      4499     7  0 01:50 ?        00:00:00 [irda_sir_wq]
root      4554     7  0 01:50 ?        00:00:00 [shpchpd]
root      4577     7  0 01:50 ?        00:00:00 [kpsmoused]
daemon    5156     1  0 01:50 ?        00:00:00 /sbin/portmap
root      5314     1  0 01:50 tty6     00:00:00 /bin/login -f      
root      5317     1  0 01:50 tty5     00:00:00 /bin/login -f      
root      5320     1  0 01:50 tty4     00:00:00 /bin/login -f      
root      5323     1  0 01:50 tty3     00:00:00 /bin/login -f      
root      5326     1  0 01:50 tty2     00:00:00 /bin/login -f      
root      5329     1  0 01:50 tty1     00:00:00 /bin/login -f      
ubuntu    5339  5329  0 01:50 tty1     00:00:00 -bash
ubuntu    5340  5320  0 01:50 tty4     00:00:00 -bash
ubuntu    5343  5314  0 01:50 tty6     00:00:00 -bash
ubuntu    5344  5323  0 01:50 tty3     00:00:00 -bash
ubuntu    5347  5317  0 01:50 tty5     00:00:00 -bash
ubuntu    5348  5326  0 01:50 tty2     00:00:00 -bash
root      5654     1  0 01:50 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events
root      5743     1  0 01:50 ?        00:00:00 /sbin/syslogd
root      5769     1  0 01:50 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/r
klog      5771     1  0 01:50 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
root      5843     1  0 01:50 ?        00:00:00 /usr/sbin/gdm
root      5844  5843  0 01:50 ?        00:00:00 /usr/sbin/gdm
root      5877  5844  1 01:50 tty7     00:00:13 /usr/X11R6/bin/X :0 -br -audit 0 -au
cupsys    5887     1  0 01:50 ?        00:00:00 /usr/sbin/cupsd
root      5908     1  0 01:51 ?        00:00:00 /usr/sbin/hpiod
hplip     5913     1  0 01:51 ?        00:00:00 python /usr/sbin/hpssd
root      5970     1  0 01:51 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
ubuntu    5983  5844  0 01:51 ?        00:00:01 x-session-manager
mysql     6070  5970  0 01:51 ?        00:00:00 /usr/sbin/mysqld --basedir=/usr --da
root      6071  5970  0 01:51 ?        00:00:00 logger -p daemon.err -t mysqld_safe
ubuntu    6140  5983  0 01:51 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-lau
ubuntu    6143     1  0 01:51 ?        00:00:00 /usr/bin/dbus-launch --exit-with-ses
ubuntu    6159     1  0 01:51 ?        00:00:00 /usr/bin/dbus-daemon --fork --print-
ubuntu    6175     1  0 01:51 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 5
ubuntu    6192     1  0 01:51 ?        00:00:00 /usr/bin/gnome-keyring-daemon
ubuntu    6195     1  0 01:51 ?        00:00:00 /usr/lib/control-center/gnome-settin
clamav    6305     1  0 01:51 ?        00:00:00 /usr/bin/freshclam -p /var/run/clama
103       6321     1  0 01:51 ?        00:00:00 /usr/bin/dbus-daemon --system
106       6337     1  0 01:51 ?        00:00:01 /usr/sbin/hald
root      6338  6337  0 01:51 ?        00:00:00 hald-runner
106       6344  6338  0 01:51 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
106       6351  6338  0 01:51 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
106       6354  6338  0 01:51 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
106       6366  6338  0 01:51 ?        00:00:00 /usr/lib/hal/hald-addon-storage
106       6368  6338  0 01:51 ?        00:00:00 /usr/lib/hal/hald-addon-storage
root      6391     1  0 01:51 ?        00:00:00 /usr/sbin/dhcdbd --system
root      6413     1  0 01:52 ?        00:00:00 /usr/sbin/NetworkManager --pid-file
ubuntu    6418     1  0 01:52 ?        00:00:00 /bin/sh -c /usr/bin/esd -terminate -
ubuntu    6419  6418  0 01:52 ?        00:00:00 /usr/bin/esd -terminate -nobeeps -as
root      6432     1  0 01:52 ?        00:00:00 /usr/sbin/NetworkManagerDispatcher -
dhcp      6449  6391  0 01:52 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/dhcp3
ubuntu    6473     1  0 01:52 ?        00:00:00 /usr/bin/metacity --sm-client-id=def
ubuntu    6507     1  1 01:52 ?        00:00:06 gnome-panel --sm-client-id default1
ubuntu    6512     1  0 01:52 ?        00:00:00 gnome-screensaver
root      6513     1  0 01:52 ?        00:00:00 perl /usr/share/system-tools-backend
ubuntu    6529     1  0 01:52 ?        00:00:01 nautilus --no-default-window --sm-cl
ubuntu    6539     1  0 01:52 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-ac
ubuntu    6563     1  0 01:52 ?        00:00:00 gnome-volume-manager --sm-client-id
114       6566     1  0 01:52 ?        00:00:00 /usr/sbin/exim4 -bd -q30m
ubuntu    6603     1  0 01:52 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-dae
ubuntu    6606     1  0 01:52 ?        00:00:00 /usr/lib/evolution/2.8/evolution-ala
ubuntu    6611     1  0 01:52 ?        00:00:00 /usr/lib/gnome-applets/trashapplet -
ubuntu    6626     1  0 01:52 ?        00:00:01 beagled --debug /usr/lib/beagle/Beag
ubuntu    6632     1  0 01:52 ?        00:00:00 nm-applet --sm-disable
root      6638     1  0 01:52 ?        00:00:00 /usr/sbin/hddtemp -d -l 127.0.0.1 -p
ubuntu    6682     1  0 01:52 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapping-
ubuntu    6696     1  0 01:52 ?        00:00:00 gnome-cups-icon --sm-client-id defau
ubuntu    6703     1  0 01:52 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2
ubuntu    6706     1  0 01:52 ?        00:00:00 gnome-power-manager
root      6755     7  0 01:53 ?        00:00:00 [nfsd4]
root      6756     1  0 01:53 ?        00:00:00 [nfsd]
root      6757     1  0 01:53 ?        00:00:00 [nfsd]
root      6758     1  0 01:53 ?        00:00:00 [nfsd]
root      6759     1  0 01:53 ?        00:00:00 [lockd]
root      6760     7  0 01:53 ?        00:00:00 [rpciod/0]
root      6761     1  0 01:53 ?        00:00:00 [nfsd]
root      6762     1  0 01:53 ?        00:00:00 [nfsd]
root      6763     1  0 01:53 ?        00:00:00 [nfsd]
root      6764     1  0 01:53 ?        00:00:00 [nfsd]
root      6765     1  0 01:53 ?        00:00:00 [nfsd]
root      6769     1  0 01:53 ?        00:00:00 /usr/sbin/rpc.mountd
root      6788     7  0 01:53 ?        00:00:00 [ondemand]
root      6804     1  0 01:53 ?        00:00:00 /usr/sbin/nmbd -D
ubuntu    6807     1  0 01:53 ?        00:00:02 gnome-terminal
root      6810     1  0 01:53 ?        00:00:00 /usr/sbin/smbd -D
root      6811  6810  0 01:53 ?        00:00:00 /usr/sbin/smbd -D
root      6829     1  0 01:53 ?        00:00:00 /usr/sbin/sshd
statd     6892     1  0 01:53 ?        00:00:00 /sbin/rpc.statd
root      6910     1  0 01:53 ?        00:00:00 /usr/sbin/hcid -x
root      6916     1  0 01:53 ?        00:00:00 /usr/sbin/sdpd
root      6927     1  0 01:53 ?        00:00:00 [krfcommd]
daemon    6945     1  0 01:53 ?        00:00:00 /usr/sbin/atd
root      6958     1  0 01:53 ?        00:00:00 /usr/sbin/cron
root      7005     1  0 01:53 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  7006  7005  0 01:53 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  7007  7005  0 01:53 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  7009  7005  0 01:53 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
ubuntu    7129  6807  0 01:53 ?        00:00:00 gnome-pty-helper
ubuntu    7132  6807  0 01:53 pts/0    00:00:00 bash
ubuntu    7182     1  0 01:54 ?        00:00:01 beagled-helper --debug /usr/lib/beag
ubuntu    7316     1 13 01:59 ?        00:00:24 /usr/lib/firefox/firefox-bin
ubuntu    7412  7132  0 02:02 pts/0    00:00:00 ps -Af
```

My Installation
```
abzolutxero@melchior-1:~$ ps -Af
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 21:03 ?        00:00:01 /sbin/init splash
root         2     1  0 21:03 ?        00:00:00 [ksoftirqd/0]
root         3     1  0 21:03 ?        00:00:00 [watchdog/0]
root         4     1  0 21:03 ?        00:00:00 [events/0]
root         5     1  0 21:03 ?        00:00:00 [khelper]
root         6     1  0 21:03 ?        00:00:00 [kthread]
root         8     6  0 21:03 ?        00:00:00 [kblockd/0]
root         9     6  0 21:03 ?        00:00:00 [kacpid]
root        10     6  0 21:03 ?        00:00:00 [kacpi_notify]
root       135     6  0 21:03 ?        00:00:00 [kseriod]
root       168     6  0 21:03 ?        00:00:00 [pdflush]
root       169     6  0 21:03 ?        00:00:00 [pdflush]
root       170     1  0 21:03 ?        00:00:00 [kswapd0]
root       171     6  0 21:03 ?        00:00:00 [aio/0]
root      1633     6  0 21:03 ?        00:00:00 [ata/0]
root      1634     6  0 21:03 ?        00:00:00 [scsi_eh_0]
root      1635     6  0 21:03 ?        00:00:00 [scsi_eh_1]
root      1643     6  0 21:03 ?        00:00:00 [scsi_eh_2]
root      1644     6  0 21:03 ?        00:00:00 [scsi_eh_3]
root      1780     6  0 21:03 ?        00:00:00 [khubd]
root      1795     6  0 21:03 ?        00:00:00 [khpsbpkt]
root      1815     1  0 21:03 ?        00:00:00 [knodemgrd_0]
root      1855     6  0 21:03 ?        00:00:00 [kjournald]
root      1934     1  0 21:03 ?        00:00:00 //sbin/logd
root      2082     1  0 21:03 ?        00:00:00 /sbin/udevd --daemon
root      2826     6  0 21:03 ?        00:00:00 [shpchpd]
root      2951     6  0 21:03 ?        00:00:00 [kpsmoused]
root      3028     6  0 21:03 ?        00:00:00 [irda_sir_wq]
daemon    3462     1  0 21:03 ?        00:00:00 /sbin/portmap
root      3631     1  0 21:03 tty1     00:00:00 /sbin/getty 38400 tty1
root      3632     1  0 21:03 tty2     00:00:00 /sbin/getty 38400 tty2
root      3633     1  0 21:03 tty3     00:00:00 /sbin/getty 38400 tty3
root      3634     1  0 21:03 tty4     00:00:00 /sbin/getty 38400 tty4
root      3635     1  0 21:03 tty5     00:00:00 /sbin/getty 38400 tty5
root      3636     1  0 21:03 tty6     00:00:00 /sbin/getty 38400 tty6
root      3828     1  0 21:03 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/eve
root      3910     1  0 21:03 ?        00:00:00 /sbin/syslogd
root      3936     1  0 21:03 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /v
klog      3938     1  0 21:03 ?        00:00:00 /sbin/klogd -P /var/run/klogd/km
root      4010     1  0 21:03 ?        00:00:00 /usr/sbin/gdm
root      4011  4010  0 21:03 ?        00:00:00 /usr/sbin/gdm
root      4035  4011  0 21:03 tty7     00:00:07 /usr/X11R6/bin/X :0 -br -audit 0
cupsys    4044     1  0 21:03 ?        00:00:00 /usr/sbin/cupsd
root      4065     1  0 21:03 ?        00:00:00 /usr/sbin/hpiod
hplip     4068     1  0 21:03 ?        00:00:00 python /usr/sbin/hpssd
root      4126     1  0 21:03 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     4190  4126  0 21:03 ?        00:00:00 /usr/sbin/mysqld --basedir=/usr
root      4191  4126  0 21:03 ?        00:00:00 logger -p daemon.err -t mysqld_s
clamav    4347     1  0 21:03 ?        00:00:00 /usr/bin/freshclam -p /var/run/c
103       4363     1  0 21:03 ?        00:00:00 /usr/bin/dbus-daemon --system
106       4378     1  0 21:03 ?        00:00:01 /usr/sbin/hald
root      4379  4378  0 21:03 ?        00:00:00 hald-runner
106       4385  4379  0 21:03 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
106       4396  4379  0 21:03 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
106       4399  4379  0 21:03 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
106       4409  4379  0 21:03 ?        00:00:00 /usr/lib/hal/hald-addon-storage
106       4411  4379  0 21:04 ?        00:00:00 /usr/lib/hal/hald-addon-storage
root      4428     1  0 21:04 ?        00:00:00 /usr/sbin/dhcdbd --system
root      4445     1  0 21:04 ?        00:00:00 /usr/sbin/NetworkManager --pid-f
root      4460     1  0 21:04 ?        00:00:00 /usr/sbin/NetworkManagerDispatch
root      4476     1  0 21:04 ?        00:00:00 perl /usr/share/system-tools-bac
114       4531     1  0 21:04 ?        00:00:00 /usr/sbin/exim4 -bd -q30m
root      4610     1  0 21:04 ?        00:00:00 /usr/sbin/hddtemp -d -l 127.0.0.
root      4658     6  0 21:04 ?        00:00:00 [nfsd4]
root      4659     1  0 21:04 ?        00:00:00 [nfsd]
root      4660     1  0 21:04 ?        00:00:00 [nfsd]
root      4661     1  0 21:04 ?        00:00:00 [nfsd]
root      4662     1  0 21:04 ?        00:00:00 [nfsd]
root      4663     1  0 21:04 ?        00:00:00 [lockd]
root      4664     6  0 21:04 ?        00:00:00 [rpciod/0]
root      4665     1  0 21:04 ?        00:00:00 [nfsd]
root      4666     1  0 21:04 ?        00:00:00 [nfsd]
root      4667     1  0 21:04 ?        00:00:00 [nfsd]
root      4668     1  0 21:04 ?        00:00:00 [nfsd]
root      4672     1  0 21:04 ?        00:00:00 /usr/sbin/rpc.mountd
root      4687     6  0 21:04 ?        00:00:00 [ondemand]
dhcp      4702  4428  0 21:04 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/d
root      4708     1  0 21:04 ?        00:00:00 /usr/sbin/nmbd -D
root      4710     1  0 21:04 ?        00:00:00 /usr/sbin/smbd -D
root      4718  4710  0 21:04 ?        00:00:00 /usr/sbin/smbd -D
root      4729     1  0 21:04 ?        00:00:00 /usr/sbin/sshd
statd     4797     1  0 21:04 ?        00:00:00 /sbin/rpc.statd
root      4813     1  0 21:04 ?        00:00:00 /usr/sbin/hcid -x
root      4817     1  0 21:04 ?        00:00:00 /usr/sbin/sdpd
root      4830     1  0 21:04 ?        00:00:00 [krfcommd]
ntp       4849     1  0 21:04 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.
root      4881  4849  0 21:04 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.
daemon    4882     1  0 21:04 ?        00:00:00 /usr/sbin/atd
root      4895     1  0 21:04 ?        00:00:00 /usr/sbin/cron
root      4940     1  0 21:04 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  4941  4940  0 21:04 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  4942  4940  0 21:04 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  4944  4940  0 21:04 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
1000      5121  4011  0 21:17 ?        00:00:00 x-session-manager
1000      5158  5121  0 21:17 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus
1000      5161     1  0 21:17 ?        00:00:00 /usr/bin/dbus-launch --exit-with
1000      5162     1  0 21:17 ?        00:00:00 /usr/bin/dbus-daemon --fork --pr
1000      5164     1  0 21:17 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 5
1000      5167     1  0 21:17 ?        00:00:00 /usr/bin/gnome-keyring-daemon
1000      5170     1  0 21:17 ?        00:00:00 /usr/lib/control-center/gnome-se
1000      5179     1  0 21:17 ?        00:00:00 /bin/sh -c /usr/bin/esd -termina
1000      5180  5179  0 21:17 ?        00:00:00 /usr/bin/esd -terminate -nobeeps
1000      5187     1  0 21:17 ?        00:00:00 /usr/lib/bonobo-activation/bonob
1000      5192     1  0 21:17 ?        00:00:01 /usr/lib/vino/vino-server --oaf-
1000      5194     1  0 21:17 ?        00:00:00 /usr/bin/metacity --sm-client-id
1000      5200     1  1 21:17 ?        00:00:02 gnome-panel --sm-client-id defau
1000      5202     1  0 21:17 ?        00:00:01 nautilus --no-default-window --s
1000      5206     1  0 21:17 ?        00:00:00 gnome-volume-manager --sm-client
1000      5216     1  0 21:17 ?        00:00:00 update-notifier
1000      5219     1  0 21:17 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs
1000      5221     1  0 21:17 ?        00:00:00 /usr/lib/evolution/2.8/evolution
1000      5231     1  0 21:17 ?        00:00:01 beagled --debug /usr/lib/beagle/
1000      5234     1  0 21:17 ?        00:00:00 nm-applet --sm-disable
1000      5241     1  0 21:17 ?        00:00:00 gnome-cups-icon --sm-client-id d
1000      5245     1  0 21:17 ?        00:00:00 gnome-power-manager
1000      5261     1  0 21:17 ?        00:00:00 /usr/lib/evolution/evolution-dat
1000      5270     1  0 21:17 ?        00:00:00 /usr/lib/evolution/2.8/evolution
1000      5272     1  0 21:17 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapp
1000      5286     1  0 21:17 ?        00:00:00 /usr/lib/gnome-applets/trashappl
1000      5319     1  0 21:17 ?        00:00:00 /usr/lib/gnome-applets/mixer_app
1000      5337     1  0 21:17 ?        00:00:00 gnome-screensaver
1000      5343     1  0 21:17 ?        00:00:01 gnome-terminal
1000      5345  5343  0 21:17 ?        00:00:00 gnome-pty-helper
1000      5346  5343  0 21:17 pts/0    00:00:00 bash
1000      5398     1 11 21:18 ?        00:00:11 /usr/lib/firefox/firefox-bin
1000      5418  5398  0 21:18 ?        00:00:00 [netstat] <defunct>
```

---

### Post by IgnorantGuru on 2007-02-15
Sound modules appear to be loaded, so it must be something else.

I've been seeing this problem reported a lot today, so I suggest you look through some of the "my sound isn't working" threads and see how those discussions are going.  This person, for example, reports the same problem...
[http://www.ubuntuforums.org/showthread.php?t=362198](http://www.ubuntuforums.org/showthread.php?t=362198)

---

### Post by IgnorantGuru on 2007-02-15
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by abzolutxero on 2007-02-16
i've been so wrapped up into the problems i've been having, it didn't even occur to me that this could be a separate problem.

i'll search through the forums, and look at those threads, and let you know where it gets me. 


Thanks again for your help thusfar!!

---

