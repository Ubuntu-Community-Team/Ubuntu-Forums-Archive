---
title: "[SOLVED] Virtualbox error &amp;quot;Failed to access the USB subsystem&amp;quot;"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bcasanov on 2008-10-29
Hi,

I have an error in Virtualbox after clicking on the settings button that says "Failed to access the USB subsystem."  I searched on Google and on the Ubuntu forums, and with these URLs in particular: [http://ubuntuforums.org/showthread.php?t=725900&page=2](http://ubuntuforums.org/showthread.php?t=725900&page=2) and [http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html) 

I followed the latter's instructions, which are given here below:
> Add USB support to you fstab file
In a terminal type:
sudo gedit /etc/fstab

And paste this line to the end of your fstab
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0

Enable USB
In a terminal type:
sudo gedit /etc/init.d/mountdevsubfs.sh 

You need to look for this section:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

And delete all the # shown, it should look exactly like this.

#Magic to make /proc/bus/usb work

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Find your vboxusers number
In a terminal type:
sudo gedit /etc/group

Look for this, the number following it is your vboxusers number
vboxusers:x:NUMBER

Next you have to add a line to your /etc/fstab to allow usb mounting
In a terminal type:
sudo gedit /etc/fstab

Add this line:
none /proc/bus/usb usbfs devgid= enter vboxusers number HERE,devmode=664 0 0

Allow access to /proc/bus/usb/
in a teminal type:
sudo chown -R root:vboxusers /proc/bus/usb

Once you Log out or reboot, you can start VirtualBox

Even after following the above instructions, I am still getting the same error.  What could be going on?

---

### Post by uidb4056 on 2008-10-29
Only the first part regarding fstab is necessary in Intrepid, the rest only is needed in hardy.

In your fstab you need to put:

none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0

being XXX the group ID of your user when you look under System-Administration-Users&Groups for the group vboxusers.

---

### Post by bcasanov on 2008-10-29
Thank you!  Your suggestion worked.  I went back and commented the specified lines in mountdevsubfs.sh, only put in the one line you gave me in the fstab file, and then, I restarted, and wuala, I don't have the error anymore!  I'll mark this thread as solved.

---

