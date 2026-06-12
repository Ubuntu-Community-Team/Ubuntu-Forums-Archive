---
title: "Just updated from 8.04 to 12.04 and no internet &amp; don't understand 12.04-what to do?"
date: 2013-12-24
forum: Installation &amp; Upgrades
---

### Post by Fidelio1st on 2013-12-24
Computer: Dell Inspiron 1420 Intel Core 2 Duo T5550 (3GB, DDR2, 667mHz)

Running Dual Boot with Windows Vista and now Ubuntu 12.04

Firstly, I'm not very Linux/Ubuntu savvy -- once things work I get it, but I'm not good at installing things or editing files... i.e. I need very specific instructions.

I've been using Ubuntu 8.04 forever and love it -- I've had my computer for over 5 years and it runs just as fast today as when I got it. But since 8.04 isn't supported anymore and I was having small issues like video in Firefox, and Firefox not updating I figured it was time to update and I just figured the most recent would be best. So I updated to 10.4 then 12.04.

Now I cannot connect to the internet in 12.04. I believe I could in 10.4. I've restarted a couple times and it says upon restarting "Waiting for network configuration." When I go into System Settings / Network there is immediately a message that reads "The system network services are not compatible with this version."

I also don't understand 12.04, I don't know where Administration and the other drop down menu below it moved to, when I right click on a folder it doesn't give me the options 8.04 gave me.

I do like the look, the new menu bar and the workspace switcher.... so if I could somehow get the internet working and understand the basics and how it changed from 8.04, I would like to keep it.

Not sure if I can save 12.04, or if I should revert back to 10.4 and try that, and if so the best way to do that. I did back up all my files (not programs)... any advice would be much appreciated.

---

### Post by oldfred on 2013-12-24
I do not know networking issues well, mine has just worked. I started with 6.06 on this dual core, converted to 64 bit with 9.10 and only had issues as I remember with the older versions.

Run these and copy to another computer and upload.
lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Attach (via the paperclip in advanced edit menu) the abs-network.txt file which will be in your home folder.


I have a 4:3 monitor and have been so used to old menus, I revert. Try Unity, some do like it afer they try it for a while.
       [http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 


 Unity info
[http://unity.ubuntu.com/about/](http://unity.ubuntu.com/about/)
[http://www.omgubuntu.co.uk/2011/04/how-to-add-folder-quicklists-to-the-home-launcher-in-ubuntu-unity/](http://www.omgubuntu.co.uk/2011/04/how-to-add-folder-quicklists-to-the-home-launcher-in-ubuntu-unity/)
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

---

### Post by grahammechanical on 2013-12-24
I am a little confused. You had a connection to the router/hub and on to the internet in 8.04. And you used the internet to upgrade 8.04 to 10.04 and then onwards to 12.04. Is this correct? Then you should still have an valid connection to the router/hub as the upgrade process would give Network Manager the correct configuration.

I wonder if you are confusing connecting to a router/hub with connecting to a network. In the 12.04 top panel on the right there should be an icon for Network Manager. If your connection is through ethernet (wired) then the icon will look like two arrows going in the opposite direction (with a connection that is).

If Network Manager is not connected to the router either by wire or by wireless then the icon will look like an inverted cone. Click on that icon and see if Enable Networking and Enable Wireless are both enabled. You should also see any wireless access points that are in range. Is your access point among them?

There is one possibility that comes to mind. In the old days before Ubuntu used Network Manager another utility was used. Having more than one utility managing wireless connections causes conflict and stops Network Manager from working. You could try this command

```
cat /etc/network/interfaces
```

That will show you what is written in the interfaces file. With Network Manager you should see this

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



Anything else will stop Network Manager from doing its job. As will having another wireless manager installed at the same time as Network Manager.

Regards.

---

### Post by Fidelio1st on 2013-12-27
@ oldfred - thank you, I ran those and attached the files.

@ grahammechanical -- I ran that and attached the screenshot.  I'm just trying to connect to my home wireless router (and for it to work when I go out to cafes, etc.). Yes, in 8.04 it wireless worked fine, and it must have in 10.4 because I upgraded to 12.04, and then no internet. You will see in the attached screenshot that there is no icon for internet, nothing like you described.

The more I read, I don't want to revert back, I want to get 12.04 working... I have burnt the 12.04 Ubuntu disc -- as mentioned before, I have a dual boot with Windows Vista... will it cause problems if I reinstall 12.04 from the burnt DVD?

ANOTHER NEW PROBLEM I noticed -- I lost audio. I have no audio for video files. Also whenever Update Manager tries to update Firefox, an error comes up. I do have Firefox opening though (just no internet to use it)...

Once again, any help much appreciated.

---

### Post by mikewhatever on 2013-12-27
Can you run the **nm-applet** command in Terminal and post the output or a screenshot.
Also, please post the output of **dmesg | grep -e wlan0 -e iwl4965**.

---

### Post by Fidelio1st on 2013-12-27
Here you go:

---------------

fidelio1st@Fidelio1st-1420:~$ nm-applet

** (nm-applet:5551): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: applet now removed from the notification area

** (nm-applet:5551): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: Starting applet secret agent because GNOME Shell disappeared

** (nm-applet:5551): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files



^C** Message: PID 0 (we are 5551) sent signal 2, shutting down...


----

fidelio1st@Fidelio1st-1420:~$ dmesg | grep -e wlan0 -e iwl4965
[   30.689616] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   30.689621] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   30.690404] iwl4965 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   30.690443] iwl4965 0000:0c:00.0: setting latency timer to 64
[   30.690500] iwl4965 0000:0c:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   30.733643] iwl4965 0000:0c:00.0: device EEPROM VER=0x36, CALIB=0x5
[   30.764456] iwl4965 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   30.764648] iwl4965 0000:0c:00.0: irq 46 for MSI/MSI-X
[   31.159891] iwl4965 0000:0c:00.0: loaded firmware version 228.61.2.24
fidelio1st@Fidelio1st-1420:~$

---

### Post by mikewhatever on 2013-12-27
Looks like something is wrong with the network manager. Let's see if it is installed with **dpkg -l | grep network-manager**.

If it is, try **sudo service network-manager start**.

---

### Post by Bucky Ball on 2013-12-27
@Fidelio1st: Please post new threads with descriptive titles and in the appropriate forum sections for consequent problems to avoid confusion and increase your chances of help. Stick to the networking issue here, please, and post the audio issue (and any other consequent issues) in separate threads in appropriate sections. Thanks.

If you have all your personal files backed up I would suggest a clean install of 12.04, unless you fancy a steep learning curve unravelling what I would call a dog's breakfast. You have a lot of problems going on here and getting to the bottom of it may, or may not, be possible. How much time do you have? It will take an hour tops to install and dump your personal data back to the appropriate places. To sort this out ... anyone's guess. Good luck.

PS: One thing you could try is checking your Software Sources and making sure you have none of the 8.04 or 10.04 repositories still hanging around and enabled.

---

### Post by Fidelio1st on 2013-12-27
mikewhatever -- YOU ROCK!!!! That solved the internet, I'm back on. Thank you. 

Apologies to Bucky Ball/forum, posted audio problem here: [http://ubuntuforums.org/showthread.php?t=2195918](http://ubuntuforums.org/showthread.php?t=2195918)

mikewhatever, since you solved my internet, I'd love it if you have any input on the audio problem. Thanks.

---

### Post by Bucky Ball on 2013-12-27
All good. Great news! Please mark this thread as solved to help others by following the instructions in my signature link. ;)

---

### Post by mikewhatever on 2013-12-27
Wow, haven't expected it to work so well. Glad it id.

---

### Post by Fidelio1st on 2013-12-28
Unfortunately I realized this is not solved. Whenever I restart or shutdown then start again, I have no internet and I have to enter the sudo service network-manager start command. Sure it's easy enough to do, but I'd rather figure out how to get the network manager to start upon booting up. Thanks.

---

### Post by mörgæs on 2013-12-28
As a side note: Now you have been struggling with this problem for a number of days. It might have been solved in 20 minutes with a fresh install of 12.04.3 (which would also have given you the ext4 file system).

---

### Post by Fidelio1st on 2013-12-28
So I believe audio has been solved by going to F6 in alsamixer and changing to HDA Intel. It's working now -- still need to test upon reboot and burning.

What's ext4 file system and what's the advantage of that?

---

### Post by Iowan on 2013-12-28
> **Fidelio1st said:**
> Unfortunately I realized this is not solved. Whenever I restart or shutdown then start again, I have no internet and I have to enter the sudo service network-manager start command. Sure it's easy enough to do, but I'd rather figure out how to get the network manager to start upon booting up. Thanks.


Do you have */lib/init/upstart-job* and /*etc/init.d/network-manager*?

---

### Post by Fidelio1st on 2013-12-28
How do I check? I put those in terminal but don't know if that's what you meant...

fidelio1st@Fidelio1st-1420:~$ /lib/init/upstart-job
Usage: upstart-job JOB COMMAND
fidelio1st@Fidelio1st-1420:~$ /etc/init.d/network-manager
Usage: /etc/init.d/network-manager COMMAND

---

### Post by Iowan on 2013-12-28
```
ls -al /etc/init.d
ls -al /lib/init
```

*/etc/init.d/network-manager* should be a link to */lib/init/upstart-job*

---

### Post by Fidelio1st on 2013-12-28
```
fidelio1st@Fidelio1st-1420:~$ ls -al /etc/init.d
total 320
drwxr-xr-x   2 root root  4096 Dec 24 09:01 .
drwxr-xr-x 188 root root 12288 Dec 28 08:23 ..
lrwxrwxrwx   1 root root    21 Dec  8  2011 acpid -> /lib/init/upstart-job
-rwxr-xr-x   1 root root   652 Jul  9  2010 acpi-support
lrwxrwxrwx   1 root root    21 Mar 28  2013 alsa-restore -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Mar 28  2013 alsa-store -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Jun 20  2010 anacron -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  1663 Nov  3  2009 apmd
-rwxr-xr-x   1 root root  4596 Sep 25  2012 apparmor
lrwxrwxrwx   1 root root    21 Oct 24 05:42 apport -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Oct 25  2011 atd -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Dec 12 14:02 avahi-daemon -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Nov 25  2011 binfmt-support -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Mar 21  2012 bluetooth -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  2444 Jul 26  2012 bootlogd
-rwxr-xr-x   1 root root  2125 Mar  1  2011 brltty
-rwxr-xr-x   1 root root  6355 May 30  2007 console-screen.sh
lrwxrwxrwx   1 root root    21 Dec 24 07:53 console-setup -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Jun 19  2012 cron -> /lib/init/upstart-job
-rwxr-xr-x   1 root root   922 Mar  8  2012 cryptdisks
-rwxr-xr-x   1 root root   871 Mar  8  2012 cryptdisks-early
lrwxrwxrwx   1 root root    21 Apr 13  2012 cryptdisks-enable -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Apr 13  2012 cryptdisks-udev -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 May 13  2013 cups -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  3095 Dec  4  2012 cups.dpkg-remove
lrwxrwxrwx   1 root root    21 Jun 13  2013 dbus -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  1506 Oct 23  2007 dhcdbd
lrwxrwxrwx   1 root root    21 Nov 26 11:42 dmesg -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  1242 Dec 13  2011 dns-clean
lrwxrwxrwx   1 root root    21 May  9  2013 failsafe-x -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  1523 Feb  6  2011 fancontrol
lrwxrwxrwx   1 root root    21 Mar 14  2012 friendly-recovery -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Apr 11  2013 gdm -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  1105 Jan 20  2012 grub-common
-rwxr-xr-x   1 root root  1329 Jan 20  2012 halt
lrwxrwxrwx   1 root root    21 May 26  2011 hostname -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  3576 Apr 10  2008 hotkey-setup
lrwxrwxrwx   1 root root    21 Mar 29  2012 hwclock -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Mar 29  2012 hwclock-save -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  4521 Apr 14  2008 hwclock.sh.dpkg-obsolete
lrwxrwxrwx   1 root root    21 Feb  3  2012 irqbalance -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  1893 Apr 19  2010 kerneloops
-rwxr-xr-x   1 root root  1293 Jan 20  2012 killprocs
-rwxr-xr-x   1 root root  1729 Nov 23  2007 klogd
-rwxr-xr-x   1 root root  3202 Oct 16 02:33 landscape-client
-rwxr-xr-x   1 root root  2308 Dec 11  2007 laptop-mode
-rw-r--r--   1 root root     0 Dec 24 01:30 .legacy-bootordering
lrwxrwxrwx   1 root root    21 Jul 19 17:41 lightdm -> /lib/init/upstart-job
-rwxr-xr-x   1 root root   869 Feb  6  2011 lm-sensors
lrwxrwxrwx   1 root root    21 Mar 24  2012 modemmanager -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Nov 20  2011 module-init-tools -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  2797 Feb 13  2012 networking
lrwxrwxrwx   1 root root    21 Sep 19 13:00 network-interface -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Sep 19 13:00 network-interface-container -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Sep 19 13:00 network-interface-security -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Jun 27  2013 network-manager -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Dec  9 10:54 nmbd -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  1116 Aug 25  2008 nvidia-kernel
-rwxr-xr-x   1 root root   882 Jan 20  2012 ondemand
lrwxrwxrwx   1 root root    21 Sep 12  2012 passwd -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 May 16  2013 plymouth -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 May 16  2013 plymouth-log -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 May 16  2013 plymouth-ready -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 May 16  2013 plymouth-splash -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 May 16  2013 plymouth-stop -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 May 16  2013 plymouth-upstart-bridge -> /lib/init/upstart-job
-rwxr-xr-x   1 root root   665 Mar  6  2010 policykit
-rwxr-xr-x   1 root root  4803 Mar 18  2009 powernowd
-rwxr-xr-x   1 root root   177 Mar  8  2008 powernowd.early
-rwxr-xr-x   1 root root   561 Feb  4  2011 pppd-dns
-rwxr-xr-x   1 root root  4988 Jan  7  2012 privoxy
lrwxrwxrwx   1 root root    21 Oct 28 11:32 procps -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  2180 Sep 26 02:10 pulseaudio
-rwxr-xr-x   1 root root  8635 Jul 26  2012 rc
-rwxr-xr-x   1 root root   801 Jan 20  2012 rc.local
-rwxr-xr-x   1 root root   117 Jul 26  2012 rcS
-rwxr-xr-x   1 root root  1492 Apr 21  2008 readahead
-rwxr-xr-x   1 root root  1957 Apr 21  2008 readahead-desktop
-rw-r--r--   1 root root  2427 Jul 26  2012 README
-rwxr-xr-x   1 root root   639 Jan 20  2012 reboot
lrwxrwxrwx   1 root root    21 Sep  8  2012 resolvconf -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Mar 22  2012 rfkill-restore -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Mar 22  2012 rfkill-store -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  4395 Nov  8  2011 rsync
lrwxrwxrwx   1 root root    21 Nov 26 11:42 rsyslog -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  2344 Dec  4  2011 saned
lrwxrwxrwx   1 root root    21 Jun  6  2011 screen-cleanup -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  4321 Jul 26  2012 sendsigs
lrwxrwxrwx   1 root root    21 Dec 24 07:53 setvtrgb -> /lib/init/upstart-job
-rwxr-xr-x   1 root root   590 Jan 20  2012 single
-rw-r--r--   1 root root  4304 Jul 26  2012 skeleton
lrwxrwxrwx   1 root root    21 Dec  9 10:54 smbd -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  2107 May 15  2011 speech-dispatcher
-rwxr-xr-x   1 root root   567 Jul 26  2012 stop-bootlogd
-rwxr-xr-x   1 root root  1143 Jul 26  2012 stop-bootlogd-single
-rwxr-xr-x   1 root root   864 Apr 21  2008 stop-readahead
-rwxr-xr-x   1 root root   700 May 23  2012 sudo
-rwxr-xr-x   1 root root  3343 Nov 23  2007 sysklogd
-rwxr-xr-x   1 root root  4569 Dec 19  2011 tor
lrwxrwxrwx   1 root root    21 Jul 19 17:24 udev -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Jul 19 17:24 udev-fallback-graphics -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Jul 19 17:24 udev-finish -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Jul 19 17:24 udevmonitor -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Jul 19 17:24 udevtrigger -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 Apr  5  2012 ufw -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  2800 Jul 26  2012 umountfs
-rwxr-xr-x   1 root root  2211 Jul 26  2012 umountnfs.sh
-rwxr-xr-x   1 root root  2926 Jul 26  2012 umountroot
-rwxr-xr-x   1 root root  1039 Nov  9  2011 unattended-upgrades
-rwxr-xr-x   1 root root  1985 Jul 26  2012 urandom
-rwxr-xr-x   1 root root  2814 Oct 15  2007 usplash
-rwxr-xr-x   1 root root 11460 Feb 17  2011 vboxdrv
-rwxr-xr-x   1 root root  8131 Feb 17  2011 vboxweb-service
-rwxr-xr-x   1 root root  4065 Feb 15  2012 virtuoso-nepomuk
lrwxrwxrwx   1 root root    21 Aug  1 03:20 whoopsie -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  1342 Apr 11  2012 winbind
-rwxr-xr-x   1 root root  2666 Mar 22  2012 x11-common
-rwxr-xr-x   1 root root   568 Mar 29  2008 xserver-xorg-input-wacom
```
```

fidelio1st@Fidelio1st-1420:~$ ls -al /lib/init
total 36
drwxr-xr-x  2 root root  4096 Dec 24 09:14 .
drwxr-xr-x 23 root root 12288 Dec 24 09:11 ..
-rwxr-xr-x  1 root root  1060 Jan 18  2013 apparmor-profile-load
-rw-r--r--  1 root root  1812 Jan 29  2013 fstab
lrwxrwxrwx  1 root root     4 Dec 24 09:14 rw -> /run
-rw-r--r--  1 root root  2847 Jul 26  2012 splash-functions-base
-rwxr-xr-x  1 root root  3444 Jan 18  2013 upstart-job
-rw-r--r--  1 root root  1229 Jul 26  2012 vars.sh
fidelio1st@Fidelio1st-1420:~$
```

---

### Post by Iowan on 2013-12-28
OK, the files are there... so much for that  idea...

---

### Post by Fidelio1st on 2013-12-29
It seems like all I need to do is add the Network Manager to start upon reboot -- so how do I add that to the startup programs?

---

### Post by Bucky Ball on 2013-12-29
In Settings>Session & Startup>Application Autostart>Try enabling just 'Network' rather than 'Network Manager' and see how that goes.

---

### Post by Fidelio1st on 2013-12-30
[ATTACH=CONFIG]249024[/ATTACH]

Please see screenshot... under "System Settings" I do not see an option for "Sessions and Startup". I'm unsure how to access any other settings...

---

### Post by Bucky Ball on 2013-12-30
Me either and not in a position to boot Ubuntu in a VM at the mo to have a look for it, but I imagine it, or something similar to it, is around somewhere ...

---

### Post by mikewhatever on 2013-12-30
You can launch the Startup Applications thing from the Dash, just search for session or startup. That said, I am not sure what you'd add there. The network manager service should be started under a special user by an upstart job. Maybe you can try reinstalling the network manager, which will hopefully solve its loading problem. To do that, enable the wireless, then run:
```

sudo apt-get --reinstall install network-manager network-manager-gnome

```

---

