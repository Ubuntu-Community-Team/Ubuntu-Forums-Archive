---
title: "still can't boot after upgrade to Oneiric"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by ivotedforkodos on 2012-01-15
After several days of effort, I still cannot boot reliably into Oneiric, after upgrading. Here is where I'm at:

1. If I try to boot the 3.0.0.14-generic kernel, it always hangs on the blank screen (not black, but the purplish color)
2. If I try to boot into recovery mode, one of two things happens:
 2a. It hangs after saying something about "firewire_ohci...". At this point the machine is completely unresponsive. That is, the kernel does not appear to be loaded. 
 2b. If I can make it to the recovery menu, and I select "remount", "grub", and then "resume", then it will boot. However, if I merely select "resume" at the first menu, then it will hang after saying :
```
SP5100 TCO timer: mmio address 0xb8fe00 already in use
```
Again, at this point the machine is completely unresponsive. I found [this thread]("http://ubuntuforums.org/showthread.php?t=1874905"), but given the other issues, I don't think the TCO timer actually has much to do with the problem. 

Similar behavior occurs if I try the 2.6.38-13 kernel, although the specific point at which the boot fails are not exactly the same. 

I do have an Nvidia graphics card, but right now I am not using any of their drivers. Also, my xorg.conf file has been deleted. I've attached kern.log. 

I am getting sort of desperate, so if anyone can help me figure this out, I'd really appreciate it. I'm almost out of my depth here...

Thanks.

---

### Post by ivotedforkodos on 2012-01-15
> **ivotedforkodos said:**
>  I've attached kern.log.

Forgot the attachment.

---

### Post by ivotedforkodos on 2012-01-16
UPDATE: Even booting in recovery mode is now problematic. 

Can anyone help me solve this problem??

---

### Post by mörgæs on 2012-01-16
There is some advice in the link in my signature.

---

### Post by ivotedforkodos on 2012-01-16
> **mörgæs said:**
> There is some advice in the link in my signature.

Thanks, I read through some of this. Here is an update:

If I try to boot normally, it just hangs on the purple screen right away. There is no disk activity. However, if I hit "e" at the grub menu, and make NO CHANGES, but just continue with Ctrl-x, then the system boots normally!

I tried with "nomodeset" and "acpi_osi=\"Linux\"" and neither seemed to make a difference. 

What could be causing this behavior??

---

### Post by drs305 on 2012-01-16
> **ivotedforkodos said:**
> However, if I hit "e" at the grub menu, and make NO CHANGES, but just continue with Ctrl-x, then the system boots normally!

Perhaps you need a short delay to ensure the partition/drive is accessible. To see if this might be the problem, boot, then open /etc/default/grub, and add the 'rootdelay' kernel option.
```

gksu gedit /etc/default/grub &
```

Add this to the existing entries in the GRUB_CMDLINE_LINUX_DEFAULT= line. You can try various settings (seconds):
> rootdelay=10

Save the file, then run "sudo update-grub".

---

### Post by ivotedforkodos on 2012-01-16
> **drs305 said:**
> Perhaps you need a short delay to ensure the partition/drive is accessible. To see if this might be the problem, boot, then open /etc/default/grub, and add the 'rootdelay' kernel option.
```

gksu gedit /etc/default/grub &
```

Add this to the existing entries in the GRUB_CMDLINE_LINUX_DEFAULT= line. You can try various settings (seconds):


Save the file, then run "sudo update-grub".

That did not seem to work. And in fact, the previous trick of "editing" grub without actually doing anything doesn't seem to work reliably either. 

I do think some sort of timing issue may be at fault here, however. Whatever is happening, the system tries to boot (you can hear the HD cranking away and the activity light is blinking), and then it just stops cold, and there is no activity. 

Any other ideas?

---

### Post by ivotedforkodos on 2012-01-16
> **ivotedforkodos said:**
> That did not seem to work. And in fact, the previous trick of "editing" grub without actually doing anything doesn't seem to work reliably either. 

I do think some sort of timing issue may be at fault here, however. Whatever is happening, the system tries to boot (you can hear the HD cranking away and the activity light is blinking), and then it just stops cold, and there is no activity. 

Any other ideas?

What else can I do to diagnose this problem?

---

### Post by ivotedforkodos on 2012-01-16
It looked like the UUID of the swap partition did not match. I tried to fix it, but now I can't boot AT ALL!! :confused:

...losing patience here...

---

### Post by ivotedforkodos on 2012-01-17
...managed to boot in recovery mode...

Does this syslog look weird?

```

bbaumer@ubuntu-gigantica:~$ tail -50 /var/log/syslog
Jan 17 04:41:39 ubuntu-gigantica rtkit-daemon[2634]: Successfully made thread 2632 of process 2632 (n/a) owned by '120' high priority at nice level -11.
Jan 17 04:41:39 ubuntu-gigantica rtkit-daemon[2634]: Supervising 1 threads of 1 processes of 1 users.
Jan 16 23:41:39 ubuntu-gigantica kernel: [   58.946088] EXT4-fs (sda5): re-mounted. Opts: user_xattr,commit=0
Jan 17 04:41:39 ubuntu-gigantica rtkit-daemon[2634]: Successfully made thread 2655 of process 2632 (n/a) owned by '120' RT at priority 5.
Jan 17 04:41:39 ubuntu-gigantica rtkit-daemon[2634]: Supervising 2 threads of 1 processes of 1 users.
Jan 17 04:41:40 ubuntu-gigantica rtkit-daemon[2634]: Successfully made thread 2658 of process 2632 (n/a) owned by '120' RT at priority 5.
Jan 17 04:41:40 ubuntu-gigantica rtkit-daemon[2634]: Supervising 3 threads of 1 processes of 1 users.
Jan 17 04:41:40 ubuntu-gigantica rtkit-daemon[2634]: Successfully made thread 2659 of process 2632 (n/a) owned by '120' RT at priority 5.
Jan 17 04:41:40 ubuntu-gigantica rtkit-daemon[2634]: Supervising 4 threads of 1 processes of 1 users.
Jan 16 23:41:41 ubuntu-gigantica gnome-session[2682]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
Jan 17 04:41:42 ubuntu-gigantica rtkit-daemon[2634]: Successfully made thread 2766 of process 2766 (n/a) owned by '1000' high priority at nice level -11.
Jan 17 04:41:42 ubuntu-gigantica rtkit-daemon[2634]: Supervising 5 threads of 2 processes of 2 users.
Jan 16 23:41:42 ubuntu-gigantica dbus[1608]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jan 16 23:41:42 ubuntu-gigantica dbus[1608]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jan 17 04:41:43 ubuntu-gigantica rtkit-daemon[2634]: Successfully made thread 2848 of process 2766 (n/a) owned by '1000' RT at priority 5.
Jan 17 04:41:43 ubuntu-gigantica rtkit-daemon[2634]: Supervising 6 threads of 2 processes of 2 users.
Jan 17 04:41:43 ubuntu-gigantica rtkit-daemon[2634]: Successfully made thread 2849 of process 2766 (n/a) owned by '1000' RT at priority 5.
Jan 17 04:41:43 ubuntu-gigantica rtkit-daemon[2634]: Supervising 7 threads of 2 processes of 2 users.
Jan 17 04:41:43 ubuntu-gigantica rtkit-daemon[2634]: Successfully made thread 2880 of process 2880 (n/a) owned by '1000' high priority at nice level -11.
Jan 17 04:41:43 ubuntu-gigantica rtkit-daemon[2634]: Supervising 8 threads of 3 processes of 2 users.
Jan 16 23:41:43 ubuntu-gigantica pulseaudio[2880]: [pulseaudio] pid.c: Daemon already running.
Jan 16 23:41:43 ubuntu-gigantica kernel: [   63.156726] ISO 9660 Extensions: Microsoft Joliet Level 3
Jan 16 23:41:43 ubuntu-gigantica kernel: [   63.336664] ISO 9660 Extensions: RRIP_1991A
Jan 16 23:41:45 ubuntu-gigantica goa[3016]: goa-daemon version 3.2.1 starting [main.c:112, main()]
Jan 16 23:41:46 ubuntu-gigantica kernel: [   65.736120] wlan0: no IPv6 routers present
Jan 16 23:41:46 ubuntu-gigantica kernel: [   66.102056] CE: hpet increased min_delta_ns to 67879 nsec
Jan 16 23:41:47 ubuntu-gigantica kernel: [   66.626764] init: tty1 main process (1989) terminated with status 1
Jan 16 23:41:47 ubuntu-gigantica kernel: [   66.626789] init: tty1 main process ended, respawning
Jan 16 23:41:56 ubuntu-gigantica ntpdate[2387]: adjust time server 204.9.54.119 offset 0.392161 sec
Jan 16 23:41:56 ubuntu-gigantica ntpd[3156]: ntpd 4.2.6p2@1.2194 Fri Sep  2 18:42:25 UTC 2011 (1)
Jan 16 23:41:56 ubuntu-gigantica ntpd[3157]: proto: precision = 0.104 usec
Jan 16 23:41:56 ubuntu-gigantica ntpd[3157]: ntp_io: estimated max descriptors: 2144, initial socket boundary: 16
Jan 16 23:41:56 ubuntu-gigantica ntpd[3157]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Jan 16 23:41:56 ubuntu-gigantica ntpd[3157]: Listen and drop on 1 v6wildcard :: UDP 123
Jan 16 23:41:56 ubuntu-gigantica ntpd[3157]: Listen normally on 2 lo 127.0.0.1 UDP 123
Jan 16 23:41:56 ubuntu-gigantica ntpd[3157]: Listen normally on 3 wlan0 192.168.1.104 UDP 123
Jan 16 23:41:56 ubuntu-gigantica ntpd[3157]: Listen normally on 4 wlan0 fe80::6ef0:49ff:fec5:97bb UDP 123
Jan 16 23:41:56 ubuntu-gigantica ntpd[3157]: Listen normally on 5 lo ::1 UDP 123
Jan 16 23:42:04 ubuntu-gigantica ntpd_intres[1842]: parent died before we finished, exiting
Jan 16 23:42:43 ubuntu-gigantica dbus[1608]: [system] Activating service name='org.debian.apt' (using servicehelper)
Jan 16 23:42:44 ubuntu-gigantica AptDaemon: INFO: Initializing daemon
Jan 16 23:42:44 ubuntu-gigantica dbus[1608]: [system] Successfully activated service 'org.debian.apt'
Jan 16 23:42:44 ubuntu-gigantica AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Jan 16 23:42:44 ubuntu-gigantica AptDaemon.Trans: INFO: Simulate was called
Jan 16 23:42:44 ubuntu-gigantica AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/08732486779c4d0d83d21418d689b133
Jan 16 23:42:46 ubuntu-gigantica AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Jan 16 23:47:44 ubuntu-gigantica AptDaemon: INFO: Quitting due to inactivity
Jan 16 23:47:44 ubuntu-gigantica AptDaemon: INFO: Quitting was requested
Jan 16 23:56:52 ubuntu-gigantica kernel: [  972.102161] show_signal_msg: 36 callbacks suppressed
Jan 16 23:56:52 ubuntu-gigantica kernel: [  972.102172] indicator-weath[2796]: segfault at 14 ip 00007f9880134895 sp 00007fff447eb260 error 4 in libdbusmenu-glib.so.4.0.5[7f988012c000+17000]
```

The rtkit-daemon appears to be using a different time than the rest of the system. Could this have caused the segfault on the weather indicator? Could this be the cause of a larger issue? How do I fix it?

---

### Post by ivotedforkodos on 2012-01-17
Is my swap parition working?

It seems like it is:
```
bbaumer@ubuntu-gigantica:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda2                               partition	3999740	0	-1
bbaumer@ubuntu-gigantica:~$ sudo blkid
/dev/sda1: LABEL="windowsxp" UUID="37A6A0607B5C126B" TYPE="ntfs" 
/dev/sda2: UUID="5d7c43b5-b430-48af-93d6-b8b629b24613" TYPE="swap" 
/dev/sda3: LABEL="Ubuntu64" UUID="7c24b275-b81c-4bd5-a701-e49581336054" TYPE="ext4" 
/dev/sda5: LABEL="Home" UUID="145319cb-a7a5-4983-874f-6f8e8716ffd8" TYPE="ext4" 
/dev/sdb1: LABEL="windows7" UUID="3D0B1E91308B2ECA" TYPE="ntfs" 
```

Except the boot log shows an error:
```
bbaumer@ubuntu-gigantica:~$ cat /var/log/boot.log | grep swap
swapon: /dev/disk/by-uuid/5d7c43b5-b430-48af-93d6-b8b629b24613: swapon failed: Device or resource busy
mountall: swapon /dev/disk/by-uuid/5d7c43b5-b430-48af-93d6-b8b629b24613 [982] terminated with status 255
mountall: Problem activating swap: /dev/disk/by-uuid/5d7c43b5-b430-48af-93d6-b8b629b24613
```

---

### Post by drs305 on 2012-01-17
> **ivotedforkodos said:**
> Is my swap parition working?

You can check with the following command:
```
free -m

```

Here's what mine returns:
>              total       used       free     shared    buffers     cached
Mem:          3961       3716        244          0        536       1221
-/+ buffers/cache:       1957       2003
Swap:         4039         15       4024

The swap line should not have all zeros.

---

### Post by reinhha1 on 2012-04-29
I seem to experience the same problem after upgrading to 12.04.....

I cannot boot either from a CD:

Hardware: ACER TravelMate 8210

---

### Post by luissil on 2012-06-18
> **reinhha1 said:**
> I seem to experience the same problem after upgrading to 12.04.....

I cannot boot either from a CD:

Hardware: ACER TravelMate 8210

Same problem here...
I think the problem begins after kernel update.. 
First sytem reboot...
Then can't boot either selecting normal kernel or recovery mode...

Only shows "sp5100 tco timer... mmio alredy in use..."

---

