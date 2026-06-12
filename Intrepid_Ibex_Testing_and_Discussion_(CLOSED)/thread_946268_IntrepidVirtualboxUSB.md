---
title: "Intrepid/Virtualbox/USB"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by txHarleyMan on 2008-10-13
All,

Has anyone been able to get USB working with Virtualbox 2.0.2 ( non ose version ) ?  I'm running Intrepid Beta.


Mike

---

### Post by ju2wheels on 2008-10-13
Yea I have it working in mine. I forget the link to the source I used to set it up though, Ill look for it and post back here if I find it.

As usual make sure you have added yourself to the vboxusers group.

Also I checked my fstab so I know I had to add this to get it to enable on every boot:

```

#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

Ill look for that article to see if I changed anything else because I dont remember off the top of my head since the process was different from the way it was done on Hardy.

---

### Post by txHarleyMan on 2008-10-13
> **ju2wheels said:**
> Yea I have it working in mine. I forget the link to the source I used to set it up though, Ill look for it and post back here if I find it.

As usual make sure you have added yourself to the vboxusers group.

Also I checked my fstab so I know I had to add this to get it to enable on every boot:

```

#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

Ill look for that article to see if I changed anything else because I dont remember off the top of my head since the process was different from the way it was done on Hardy.

Thanks, JU.  I didn't add anything to my fstab.  Will try after work today!

Mike

---

### Post by The Cokeaholics on 2008-10-13
Here you go:
[HTML]http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html[/HTML] It mentions Hardy but worked out for me.

> Setup VirtualBox USB Support:
USB is disabled by default, so you'll probably want to enable it. Otherwise you'll get an error when you go into the "Settings" of your virtual machine. To correct this, you'll need to edit the mountdevsubfs.sh file:
sudo gedit /etc/init.d/mountdevsubfs.sh
You'll see a block of code that looks like this:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
Now uncomment the last 4 lines above to look like this:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Ok now logoff, then log back in so the vbox driver see's you are logged in to the vboxusers group.

If the above doesnt work try rebooting, if that doesnt enable usb you can try this:
Grab the vboxusers group id:
grep vbox /etc/group
vboxusers:x:124:ionstorm
Edit the fstab with the group id # in bold:
sudo gedit /etc/fstab
Append this to the fstab then save/exit:
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
Now lets edit the mountkernfs.sh file with the gid in bold:
sudo gedit /etc/init.d/mountkernfs.sh
Paste the 2 lines below above the line: "# Mount spufs, if Cell Broadband processor is detected"
## Mount the usbfs for use with Virtual Box
domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev,devgid=124,devmode=664

You may not need to reboot, try doing:
sudo /etc/init.d/mountkernfs.sh

If not, reboot, and virtualbox should detect your usb devices!

Regarding the part of 'magic' in mountdevsubfs.sh, you can compare with mine if it is not in your file:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs
# Required-Start:    mountkernfs
# Required-Stop:
# Should-Start:      udev
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO
#
# This script gets called multiple times during boot
#

PATH=/lib/init:/sbin:/bin
TTYGRP=5
TTYMODE=620
[ -f /etc/default/devpts ] && . /etc/default/devpts

TMPFS_SIZE=
[ -f /etc/default/tmpfs ] && . /etc/default/tmpfs

KERNEL="$(uname -s)"

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start () {
	#
	# Mount a tmpfs on /dev/shm
	#
	SHM_OPT=
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT=",size=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm tmpfs -onosuid,nodev$SHM_OPT

	#
	# Mount /dev/pts. Master ptmx node is already created by udev.
	#
        domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE

# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
}

case "$1" in
  "")
	echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2
	do_start
	;;
  start)
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: mountdevsubfs [start|stop]" >&2
	exit 3
	;;
esac
```

Robert

---

### Post by Delvien on 2008-10-13
> **The Cokeaholics said:**
> Here you go:
[HTML]http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html[/HTML] It mentions Hardy but worked out for me.




This doesn't work in intrepid due to the changes. You must add the information to fstab. Its alot easier to do imo: )

---

### Post by txHarleyMan on 2008-10-13
> **Delvien said:**
> This doesn't work in intrepid due to the changes. You must add the information to fstab. Its alot easier to do imo: )
Correct.  Working fine now.  Thanks, All!

---

### Post by c0mp13371331337 on 2008-10-24
> **ju2wheels said:**
> 
```

#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

This worked like a charm for me in Intrepid.  Thanks!

---

### Post by davidfg4 on 2008-10-25
This did not work for me.
I made sure I am in the vboxusers group, added the line from ju2wheels's post to my fstab, and restarted.
I also tried having devmode=666 and devgid=124 (the id of the vboxusers group).
No matter what I tried nothing ever showed up in the Devices > USB Devices menu.
I am on Intrepid and using virtualbox 2.0.2_OSE.
Any ideas as to what I am missing?

David

EDIT: It looks like the OSE edition does not support usb, I will get the non OSE version.

---

### Post by davidfg4 on 2008-10-25
Alright, I got it working!
Thanks everyone!

---

### Post by inportb on 2008-10-25
Wow, I didn't know the solution would be so simple. I never really had to use USB in a VM, but the warning box was always a bit unsettling =p

It's easier than the Hardy fix.

---

### Post by billstei on 2008-10-26
Are the "magic" lines needed in /etc/init.d/mountdevsubfs.sh in Intrepid?  The one that the Intrepid upgrader put in does not have them, not even as commented out lines (I did have them in Hardy).

I have the line in fstab and I am a member of vboxusers, but I can't attach my wacom usb tablet.  It's sounds like that is all that is needed (now) in Intrepid, based on the discussion in this thread.

There are so many convoluted discussions about this issue it is hard to tell what exactly each person has that works.  There are at least 4 (or 5) different files involved depending on what "fix" you try:

/etc/fstab
/etc/init.d/mountdevsubfs.sh                 (the infamous "magic" lines)
/etc/init.d/mountkernfs.sh
/etc/udev/rules.d/40-permissions.rules       (older Ubuntu's ?)
/etc/udev/rules.d/40-basic-permissions.rules (newer Ubuntu's ?)

I have tried every permutation of the above, and nothing worked (in Hardy, to be fair).  I am currently using VirtualBox 2.0.4 and the error is (usually):

Failed to create a proxy device for the USB device. (Error: VERR_READ_ERROR).
Result Code:   NS_ERROR_FAILURE

Bill

---

### Post by davidfg4 on 2008-10-26
Hardy and Intrepid require two totally different methods to get USB working. Intrepid is much easier. Because it is being released in 4 days I recommend upgrading and doing those steps.
The Cokeaholics was talking about Hardy, everyone else was talking about Intrepid.

To get USB working on **Intrepid**:
Add the following line to fstab and reboot: none /proc/bus/usb usbfs devgid=46,devmode=666 0 0
Be in the vboxusers group.
You need the non OSE version. (get here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads), the hardy version worked for me)

To get USB working on **Hardy**: follow whatever The Cokeaholics said. (I can't vouch for these directions)

---

### Post by shuttleworthwannabe on 2008-10-27
> **davidfg4 said:**
> 

To get USB working on **Intrepid**:
Add the following line to fstab and reboot: none /proc/bus/usb usbfs devgid=46,devmode=666 0 0
Be in the vboxusers group.
You need the non OSE version. (get here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads), the hardy version worked for me)



recent updated version > VirtualBox 2.0.4 for Linux

Please choose the appropriate package for your Linux distribution: 
Ubuntu 8.04 ("Hardy Heron") i386 | AMD64 (24 Oct 2008 ) does not seem to install in Ibex (uses older kernel -24 instead of newer kernel -27.

Anyone have any luck installing this new VB non-free in Ibex?

PS: I have VB already installed from repo's in Ibex? Could this be the reason for the error in installation? should I remove VB OSE first then install the *.deb VB non-free from the site?

Thanks
S

EDIT: oh, todays update installed the v2.0.4; will tell you how things went with my VB XP installation, and usb workaround,

---

### Post by dennisharrison on 2008-10-27
Just installed it on 386 and 64bit on two fresh installs of ibex and full apt-get update and apt-get upgrade.

Testing the :

none /proc/bus/usb usbfs devgid=46,devmode=666 0 0

in /etc/fstab now.

Will update this post in a few minutes with results.

---

### Post by dennisharrison on 2008-10-27
Works like a charm!

Thank you davidfg4 :)

---

### Post by billstei on 2008-10-27
davidfg4: I appreciate your definitive answer.

Keeping then to the fstab entry and vboxusers group solution, I have two USB devices that I am trying to attach:

MIDI keyboard - results in Windows 2000 blue screen and rebooting to a locked up state.

Wacom tablet - same VERR_READ_ERROR as noted previously

To be fair the issues here are probably not related to the fstab and/or vboxusers group tweaks.  In the case of the wacom tablet, does the xserver-xorg-input-wacom software interfere with the attaching?  (why, if the kernel already has a wacom module, do we add xserver-xorg-input-wacom?) In the case of the MIDI keyboard, it probably attached and then crashed.

So I reluctantly say: Yay it works.

Bill

---

### Post by leonardoxiao on 2008-10-27
Does this method work with sync between iTunes and iPhone?

---

### Post by davidfg4 on 2008-10-27
I got it to work between my iPod and iTunes, so it should work for an iPhone.

---

### Post by chiccoch on 2008-10-28
THANKS davidfg4!

Works great in Intrepid (64bit)...

---

