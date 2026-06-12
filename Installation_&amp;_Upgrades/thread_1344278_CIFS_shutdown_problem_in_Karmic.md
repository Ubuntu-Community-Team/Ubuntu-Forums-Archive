---
title: "CIFS shutdown problem in Karmic"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by Ian Ferguson on 2009-12-02
Like many others, I've had problems shutting down or rebooting when I've got Samba shares mounted from fstab. Shutdown hangs and I get messages along the lines of:

"CIFS VFS: No response for cmd 50 mid[n]" (Where n varies)

I usually get two of these with different ns, followed by "Stopping Samba daemons" and some other things before it eventually shuts down.

When I had this problem in 9.04, I fixed it using the workaround in this link:

[http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/](http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/)

This was originally written for 7.10, and some of the numbers have changed, but I understand that the principal is to change the order in which events happen during shutdown so that the shares are unmounted before the network connection is closed.

Unfortunately, the problem has come back now that I've upgraded to 9.10, and the same fix hasn't worked, so I've been Googling, searching forums and reading the Debian Policy Manual ([http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)) to try and get a deeper insight into what's going on during shutdown.

When I do 

```
ls -la /etc/rc0.d
```I see a file:"K00umountnfs.sh -> ../init.d/umountnfs.sh" (The same for /etc/rc6.d)

If I understand correctly, this means that the first thing the shutdown routine does is to run the script "umountnfs.sh", which is in the "/etc/init.d/" directory, and this unmounts the shares.

I tested this by running the script manually with

```
sudo /etc/init.d/umountnfs.sh 
```This seemed to do what it's meant to do. The icons for the shares disappeared from the desktop, and after doing this, when I shut down in the normal way from the GUI, the shutdown went perfectly, with no hangups and no error messages.

What I don't understand is, why do I still have a problem when I shut down without running this script first, when it should run automatically before anything else? Am I missing something?:confused:

---

### Post by louieb on 2009-12-02
I'm still using CIFS in Jaunty and Hardy but found my CIFS shutdown fix here 

Thread also has some fixed to try for Karmic too.
[Mount samba shares with utf8 encoding using cifs - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=288534&highlight=samba")

---

### Post by Velophile on 2009-12-03
From the thread already quoted above:

[http://ubuntuforums.org/showpost.php?p=8420370&postcount=1170](http://ubuntuforums.org/showpost.php?p=8420370&postcount=1170)

[URL="http://ubuntuforums.org/showpost.php?p=8375663&postcount=1159"]
"Are you using WPA encryption on your wireless, and are you using NetworkManager to manage your wireless connection?"[/URL]

This combination appears to be causing the problem though I don't have a solution or any ideas on how to investigate.

---

### Post by Ian Ferguson on 2009-12-03
> **Velophile said:**
> From the thread already quoted above:

[http://ubuntuforums.org/showpost.php?p=8420370&postcount=1170](http://ubuntuforums.org/showpost.php?p=8420370&postcount=1170)

[URL="http://ubuntuforums.org/showpost.php?p=8375663&postcount=1159"]
"Are you using WPA encryption on your wireless, and are you using NetworkManager to manage your wireless connection?"[/URL]

This combination appears to be causing the problem though I don't have a solution or any ideas on how to investigate.

I'm still working through this long thread, and I'll post when I find an solution.

I'm using a WPA2-encrypted wireless connection controlled by Network Manager, but I've just tried an experiment connecting to my network through an Ethernet cable, and I still had the same problem, so I don't think that can be the cause.

---

### Post by Ian Ferguson on 2009-12-05
Thanks, louieb and Velophile. I still haven't found a solution, but I've been doing some digging and found out some things that may help diagnose the problem. To sum up:

After trying various fixes, my /etc/rc0.d directory now looks like this:

```
total 20
drwxr-xr-x   2 root root  4096 2009-12-05 01:48 .
drwxr-xr-x 150 root root 12288 2009-12-05 01:55 ..
lrwxrwxrwx   1 root root    22 2009-12-05 01:48 K15umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx   1 root root    16 2009-10-14 20:31 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx   1 root root    15 2009-10-14 20:31 K19samba -> ../init.d/samba
lrwxrwxrwx   1 root root    26 2009-11-08 14:01 K20clamav-freshclam -> ../init.d/clamav-freshclam
lrwxrwxrwx   1 root root    15 2009-10-14 20:31 K20exim4 -> ../init.d/exim4
lrwxrwxrwx   1 root root    20 2009-11-29 21:46 K20kerneloops -> ../init.d/kerneloops
lrwxrwxrwx   1 root root    17 2009-10-14 20:31 K20winbind -> ../init.d/winbind
lrwxrwxrwx   1 root root    20 2009-10-14 20:31 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx   1 root root    20 2009-10-14 20:31 K50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx   1 root root    21 2009-10-14 20:31 K99laptop-mode -> ../init.d/laptop-mode
-rw-r--r--   1 root root   353 2009-09-07 19:58 README
lrwxrwxrwx   1 root root    41 2009-10-14 20:31 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx   1 root root    29 2009-11-29 21:35 S10unattended-upgrades -> ../init.d/unattended-upgrades
lrwxrwxrwx   1 root root    22 2009-10-14 20:31 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx   1 root root    18 2009-10-14 20:31 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx   1 root root    17 2009-10-14 20:31 S30urandom -> ../init.d/urandom
lrwxrwxrwx   1 root root    20 2009-11-29 21:33 S35networking -> ../init.d/networking
lrwxrwxrwx   1 root root    18 2009-10-14 20:25 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx   1 root root    20 2009-10-14 20:31 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx   1 root root    14 2009-10-14 20:31 S90halt -> ../init.d/halt
```(rc6.d is the same except for the last line, which is S90reboot)

umountnfs.sh is still the first init.d script to be called.

When I run this script manually, it works, and I get a clean shutdown.

When I look at syslog for the time I shut down or reboot, I see repeated instances of the lines:

```
Dec  5 09:04:21 Fergubuntu kernel: [   60.247288]  CIFS VFS: Error connecting to socket. Aborting operation
Dec  5 09:04:21 Fergubuntu kernel: [   60.247300]  CIFS VFS: cifs_mount failed w/return code = -101
```So it looks like something is still preventing the unmount from working when it runs in the normal shutdown sequence. Is there anything that runs when I hit "Shut Down" before entering the rc0.d or rc6.d sequence?

I don't get a "Server not responding" message, as I did when I had a similar problem in Jaunty. The messages start with two instances of "No response for cmd 50 mids [n]". The cmd is always 50, but the mids is different every time.

I normally connect to my Samba server by means of a WPA encrypted wireless network, but I get the same problem when I use a wired connection.

It makes no difference whether I shut down or reboot from the GUI or from the terminal using "sudo shutdown -h (or -r) now".

This problem has only occurred since I upgraded to Karmic. The problem I had in Jaunty was due to the fact that wpa-ifupdown closed the network connection before umountnfs.sh tried to unmount the shares and I fixed it by changing the priority of umountnfs.sh.

Can anyone suggest anything else I might try to get to the bottom of this?

---

### Post by Ian Ferguson on 2009-12-06
I found a fix [here]("http://ubuntuforums.org/showthread.php?p=8451352#post8451352").:D

---

### Post by Velophile on 2009-12-07
Thanks Ian, I'll give that a go later, looks like it should do the job.

Makes me wonder if the problem is caused by network manager stopping when the gnome session ends, before the rc scripts run the machine shutdown.  In which case you'd have no network and the rc scripts umount'ing of CIFS would error and have to timeout.

---

### Post by Velophile on 2009-12-07
Once I'd corrected the typo in my script it worked fine for me too....thanks for the tip-off Ian.

---

