---
title: "Fail on upgrade to 11.10 - need help to chroot fix"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by bag123 on 2011-10-20
Good day to you all.

I am having some difficulty with an upgrade to 11.10 on an Acer Aspire One (ZG5 - AOA-110).  I've had difficulties before but this is particularly bad, and I could do with some help to try and sort out my mess.

I chose to upgrade the netbook, and not to reinstall.  However, the upgrade hung, completely blanked the screen and I needed to use the magic sys-req system to unblock and to reboot.  On booting, the computer hangs and will not get to the command line.

This isn't particularly a big issue, I have chrooted into broken systems (many!) times before and just used a combination of "sudo dpkg -a --configure" and "sudo apt-get update" to keep going and fix the issue.  And this is what I am trying to do now.

I have booted into a LiveCD/USB version of Ubuntu 11.10.  I have opened a command line and mounted my netbook's root partition, and chrooted into it.  I can now quite happily poke around the innards of my broken filesystem.  This time, however, whilst trying to use the time-honoured fix-it commands, I've hit a bigger problem.  

Using "sudo dpkg -a --configure" complains of too many errors, and dumps back to the command line at what I presume to be mid-way through, and "sudo apt-get update" returns errors about not being able to resolve addresses.  Error shown is:

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
```

although this is only one of a long stream of them that I get.

From the command line (inside the chroot system) I have tried pinging an address.  Pinging my gateway router works fine - no problems, and returns pings in less than 2ms.  Pinging an internet address (say, Yahoo!) returns that the address is not resolved.  And yet, surfing from the same netbook using the LiveCD/USB (outside the chroot system) works fine, as does surfing from other computers/devices in the house that connect through the same router. 

I currently see this as a two-step problem.

1.  Fix the network issues to ensure connectivity from inside the chroot system.
2.  Use the usual commands to fix and update/upgrade the system inside the chroot, reboot and cross my fingers...

So then, to step 1...  

Please can people help me to understand the issues here.  Obviously, the hardware is working (since I can connect to the internet and surf using the same netbook but outside the chroot system).
Ping obviously still works - since I am able to ping my gateway router from inside the chroot system - but I do not understand why it doesn't work when I try to ping somewhere on the internet.  What systems/programs could be in use to ping outside my home network that are not in use when inside my home network?  Am I barking up the wrong tree here?  Is this just a red herring?
And once I have worked this out, and got internet connectivity, I presume that I will be able to just use the usual commands to fix this.


Bit of a poser, this one.  Does this ring bells for anyone out there on t'interweb?

I have an idea that in the event of not being able to connect to the internet, I may also be able to use the (currently running) USB liveCD/USB as a repository for fixing broken packages - but I don't know how to do that from the command line inside a chroot system.  I'd be grateful for any help you can give me.

I look forward to hearing suggestions as to how I fix the network issue from inside the chroot system so that I can then work on fixing the rest of it all.  I assume, of course, that once network connectivity is restored, that I will be able to work through all the packages to update/upgrade to where I need to be.

Many thanks in advance for your help.

Bag123.

---

### Post by smurphy_it on 2011-10-20
is the /etc/resolv.conf the same in the "live" environment and the "chroot" environment ?

---

### Post by bag123 on 2011-10-20
smurphy_it,

you superstar!

No, they weren't.  The live environment version had an IP address in it for name-server, the chroot version did not.  I copied the info from the live environment version into the chroot version and it is currently working through an apt-get update.

I will post further if I get stuck on the fix.

That was incredibly simple (so far) - I am pleasantly surprised that the internet access problem was fixed so easily.

Many thanks,

Bag123

---

### Post by bag123 on 2011-10-20
OK, so i managed to get access to the internet, but it doesn't solve the issue of packages and dependencies...

If I run the command

```
sudo dpkg -a --configure
```

then i get the output:

```
root@ubuntu:/# sudo dpkg -a --configure
sudo: unable to resolve host ubuntu
Setting up memtest86+ (4.20-1ubuntu1) ...
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up xorg (1:7.6+7ubuntu7) ...
Setting up tzdata-java (2011l-0ubuntu0.11.04) ...
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up gedit (3.2.0-0ubuntu1) ...
update-alternatives: using /usr/bin/gedit to provide /usr/bin/gnome-text-editor (gnome-text-editor) in auto mode.
Setting up gir1.2-dbusmenu-gtk-0.4 (0.5.0-0ubuntu3) ...
Setting up libgupnp-igd-1.0-3 (0.1.11-1) ...
Setting up libtotem-plparser17 (2.32.6-1) ...
Setting up dbus (1.4.14-1ubuntu1) ...
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
runlevel:/var/run/utmp: No such file or directory
start: Job failed to start
invoke-rc.d: initscript dbus, action "start" failed.
dpkg: error processing dbus (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up overlay-scrollbar (0.2.11-0ubuntu1) ...
Setting up gwibber-service-facebook (3.2.0.1-0ubuntu1) ...
dpkg: dependency problems prevent configuration of gconf2-common:
 gconf2-common depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing gconf2-common (--configure):
 dependency problems - leaving unconfigured
Setting up gir1.2-gnomebluetooth-1.0 (3.2.0-0ubuntu1) ...
Setting up compiz-plugins (1:0.9.6+bzr20110929-0ubuntu3) ...
Setting up libgwibber2 (3.2.0.1-0ubuntu1) ...
Setting up libappindicator1 (0.4.1-0ubuntu2) ...
Setting up python-appindicator (0.4.1-0ubuntu2) ...
Setting up splix (2.0.0+20110720-0ubuntu2) ...
dpkg: dependency problems prevent configuration of udisks:
 udisks depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing udisks (--configure):
 dependency problems - leaving unconfigured
Setting up transmission-gtk (2.33-0ubuntu2) ...
dpkg: dependency problems prevent configuration of consolekit:
 consolekit depends on dbus (>= 1.1.2); however:
  Package dbus is not configured yet.
dpkg: error processing consolekit (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-orca (3.2.0-0ubuntu1) ...
Installing new version of config file /etc/xdg/autostart/orca-autostart.desktop ...
dpkg: dependency problems prevent configuration of gnome-bluetooth:
 gnome-bluetooth depends on consolekit; however:
  Package consolekit is not configured yet.
dpkg: error processing gnome-bluetooth (--configure):
 dependency problems - leaving unconfigured
Setting up gwibber-service-identica (3.2.0.1-0ubuntu1) ...
dpkg: dependency problems prevent configuration of libunique-1.0-0:
 libunique-1.0-0 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing libunique-1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libunique-3.0-0:
 libunique-3.0-0 depends on dbus; however:
  Package dbus is not configured yet.
```

and so on...  this keeps going until it complains of too many errors and kicks me out.

running a simple 

```
sudo dpkg dbus --configure
```

doesn't seem to work either.

so then, what is the first step in fixing these things one at a time, so that i can reduce the list of errors down to a manageable size?  How would I go about this?

Any help is gratefully received.

Many thanks,

Bag123

---

### Post by smurphy_it on 2011-10-21
> sudo: unable to resolve host ubuntu

That is your first issue.  Do an ifconfig -a.  Then grab the IP for whatever interface that is and chuck it in your hosts file.

example.

```
sudo ifconfig -a eth0
echo "192.168.1.143 ubunutu" >> /etc/hosts

```

If the above echo fails, you can just paste it in with an editor like nano or vi.

> /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).


Most likely your chroot dev isn't mounted.  You can have multiple dev's mounted using bind.  Example ( sudo mount --bind udev /chroot/dev ).  You'll probably need to bind mount dev, dev/pts and possibly sysfs.

> Package memtest86+ is not configured yet.


```
sudo dpkg --reconfigure memtest86+
```
I could be slightly off with the switches and what not of the above command as it's been awhile since I ran that.

---

### Post by bag123 on 2011-10-21
smurphy_it

Many thanks for the help.

running the command 

```
ifconfig -a
```

returns an error message:

```
root@ubuntu:/# ifconfig -a
Warning: cannot open /proc/net/dev (No such file or directory). Limited output.
```

Is this because some areas around not bound to the chroot system?

Should I just go ahead and bind everything first? Is that the issue?

Forgive me here because I'm not entirely sure that I understand how to bind all the different sections/systems you talked about.  In particular, do I just type in the following, one at a time?

```
sudo mount --bind udev /chroot/dev
sudo mount --bind /dev/pts /chroot/dev/pts
sudo mount --bind /sysfs /chroot/dev/sysfs
```

Am concerned that I want to make this work correctly.  Would be grateful if you could respond with your thoughts before I try.

mant thanks,

Bag123

---

### Post by smurphy_it on 2011-10-21
> Forgive me here because I'm not entirely sure that I understand how to bind all the different sections/systems you talked about. In particular, do I just type in the following, one at a time?
sudo mount --bind udev /chroot/dev
sudo mount --bind /dev/pts /chroot/dev/pts
sudo mount --bind /sysfs /chroot/dev/sysfs


This is relative to where you don't your chroot.  You actually do the mounting outside of your chroot.  So in my example above, I'm assuming you are doing a chroot into direcotry /chroot.  Fix that up to where-ever you are doing your chroot.

So outside of the chroot, you would run those commands above.  If you unsure on the mount --bind command, or want to verify it's usage, just do a ```
man mount
```

---

### Post by bag123 on 2011-10-21
OK, so now I feel entirely stoopid.

It's been several days since I mounted the chroot, and I can't remember what I mounted it as...  Also, having run a zillion commands in the terminal, I can't go up through the history to find it...

Please can you let me know - is there a command that I can run either inside or outside of the chroot environment which will show me what I mounted it as...?

Now, do I feel silly or wot?

---

### Post by smurphy_it on 2011-10-21
just type ```
mount
``` and hit enter

---

### Post by smurphy_it on 2011-10-21
You should back all the way out of your chroot, so you can bind mount the dev directories.  The "Chroot" isn't typically mounted, however, you would of mounted your harddrive somewhere, and then afterwords you would of run "chroot /media/sda1 /bin/bash" or something along those lines.

Here is an example of the mount's.

```
sudo mount /dev/sdb1 /media/sdb1
```
That would mount your secondary harddirve (you can always run sudo fdisk -l first).

Next do the bind mount commands...
```
sudo mount --bind udev /media/sdb1/dev
sudo mount --bind devpts /media/sdb1/dev/pts
sudo mount --bind sysfs /media/sdb1/sys
```

Now that your mounts are done, you can do your change root.
```
sudo chroot /media/sdb1 /bin/bash
```

Now, verify your /etc/resolv.conf is right by catting it, and modifying if need be.
```
cat /etc/resolv.conf
```

Then you should be on the right track to getting to the root of the problem.

---

### Post by bag123 on 2011-10-21
smurphy_it

Apologies - I've been going around in circles a little...  mainly because I'm not sure that I follow what I'm supposed to be doing...

First, I ran mount, and saw that it was mounted as / (I think)...  details below:

```
root@ubuntu:/# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
```

I exited the chroot by typing 'exit', which brought me back out to the command line, presumably of the liveUSB system.

I see that I can't mount the files like you mentioned, because the files don't exist.  So I've created them - inside a new folder called /chroot
details are as below:

```
ubuntu@ubuntu:~$ sudo mkdir /chroot/dev
ubuntu@ubuntu:~$ sudo mkdir /chroot/dev/pts
ubuntu@ubuntu:~$ sudo mkdir /chroot/dev/sysfs
```

But now the problem is that I then tried to mount the first of the three systems that you mentioned, and it tells me that udev doesn't exist...  come to think of it - I don't see a folder called sysfs either - so is that one going to cause problems later?

```
ubuntu@ubuntu:~$ sudo mount --bind udev /dev
mount: special device udev does not exist
```

I'm pretty sure that I can follow your original commands if I can get the chroot system mounted, bound and up and running.  But I'd be grateful if you could just give me some pointers to get me back there!  I ave the feeling that when I originally made the chroot, I didn't do it properly and didn't create the files/directories that were needed...  so how do I get it right this time?

Thanks in advance for all the help.

Bag123

---

### Post by bag123 on 2011-10-22
murphy_it,

Right then, thanks for all your help so far - most valuable.

I was getting myself in a bit of a twist yesterday, and having had the same instance of Ubuntu LiveUSB running for several days with all sorts of stuff going on, multiple folders created all over the place, I thought that I'd just take the plunge and reboot, to give myself a clean Live USB slate etc.  Easier to follow your advice and go through the steps.

So, I rebooted, and ran through the chroot steps to get a working internet connection.  A "sudo dpkg -a --configure" kicked off a world of wonders that seemed to do a great job...

It finished off cleanly, and a further "sudo apt-get update" showed nothing else that needed to be updated etc, so I then took the plunge and rebooted again, hoping that it would all be done.

Unfortunately, no.

The system seems to boot, but then once the Ubuntu with five spots comes up, the system drops to a terminal output showing that it fails on plymouth activation, which is then removed/deactivated - and then the boot stalls....  nothing else. 

So, I've rebooted back into a LiveUSB version, and mounted the chroot system again.  However, I'm having some difficulty again.

I still can't get internet access again - and your previous trick of updating /etc/resolv.conf inside the chroot system doesn't seem to work now.  Pinging returns the following:

```
root@ubuntu:/# ping -c 4 www.yahoo.com
ping: unknown host www.yahoo.com
```

and also, running a "sudo apt-get update" returns the following:

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I'm pretty sure that once I can get internet access again, most things should be resolveable...  but would appreciate some help getting there.

---

### Post by bag123 on 2011-10-22
OK, so I went through the steps again, and found out that I'd made an error in inputting the IP address into /etc/hosts

I now have internet access from within the chroot

I have run a

```
sudo apt-get update
sudo apt-get upgrade
sudo dpkg -a --configure
```

and both of these finish without errors.  

However, this was the same beforehand - and it didn't boot last time!

I will give it another shot and try to reboot.  I presume that if all three of these (rather important) commands finish without an error, then it should be OK...

will be back later.  We'll see.

Cheers,

Bag123

---

### Post by bag123 on 2011-10-22
Luck is not on my side today.  

Rebooting got me nowhere fast.  Exactly the same thing - hung at the same point in the boot process, just after deactivating plymouth

I got something like:

```
mountall:  Plymouth command failed
mountall:  Disconnected from Plymouth
```

apologies if it's not exactly correct, but I had to remember it from notes, and reboot, so I lost the exact error message.

I did see though, that earlier up the list, PulseAudio failed too, and that automatic error reporting failed as well.  There may have been others, but they would have been off the top of the screen by the time that it dumped to a terminal and I could see any error messages.

So then, any ideas?  'cos I'm sure runnin' out of 'em!

:P

---

### Post by masgeeks on 2011-10-22
Yes - do a clean install.

I have learned across my long years of computing, both Linux and Windows, that OS upgrades are more trouble then they are worth - and why upgrade?  To save time?  With all the time spent trying to fix issues caused by an upgrade, a clean install would, in the end have been quicker, and cleaner...  :)

---

### Post by bag123 on 2011-10-22
Well, that's one way of looking at it - and I may get there yet...

Still, I already know how to install/reinstall...  but what would I learn if I took the easy option?

:D

After all, I'm pretty certain that I'm not that far off getting this thing solved - I just need to work out the last few tweaks.  All files seem to be updated, there's nothign left to 'fix' from the upgrade issue except for the minor issue that it hangs on boot.

I'll keep plugging away for a day or two, and if nothing sorts itslef by then, then I'll consider the reinstall.

Cheers for the input though.

Bag123

---

### Post by smurphy_it on 2011-10-24
Post the contents of your /etc/fstab, perhaps that will shed some light on the plymouth problem.  (From the balked install that is, so your chroot I guess you could say. )

---

### Post by bag123 on 2011-10-24
murphy_it,

fstab looks like this:


```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=be3012ef-a0f4-49e3-9782-33c9f6f2ed85 /               ext4    errors=remount-ro 0       1
# /home was on /dev/mmcblk1p1 during installation
UUID=51421d08-f7a5-4e8c-8337-9fbefd21e886 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
#UUID=a87ce2cb-5d97-4b2e-903d-7e04e2d44592 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

To explain, just in case it's not clear from the table...  I have an old Acer aspire one.  It only has an 8GB SDD with additional SD cards in the two slots.  I have put the / data on the /dev/sda1 - and used the whole 8GB for it (I ran out of space after a few updates on a previous version of Ubuntu).  /home is on a SD card, as are two other partitions that hold spurious other data etc.

that's about it.

Cheers.

Bag123

---

