---
title: "[64 bit] Update manager Error"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by xmillsa on 2010-02-17
Hi, new to ubuntu and the linux world, ive been trying to move myself away from windows, but it seems like ubuntu just wont have it, either that or win7 puts some curse on ubuntu :twisted:

Just done my 3rd(3rd time this error has now happened) fresh install of ubuntu 9.10 onto my second hard drive(first hard drive has win7), install seemed fine, boots up nicely into grub, got the internet working fine(worked out of the box, wireless), other programs run fine, all seems to be working wonderfully well!

Until I tried to update, started up the update manager, clicked on check, its finds loads of updates so I let it download them, downloads all 200+ updates, starts to install them.
The updates are installing fine but then about three quarters of the way along the progress bar for installing it gets an error.

Heres the details it showed at the error: (the rest of the details just looked like successful installs/updates)

```
Setting up gtk2-engines-pixbuf (2.18.3-lubuntu2.2)
dpkg: unrecoverable fatal error, aborting:
unable to fsync updated status of 'gtk2-engines-pixbuf': input/ouput error touch: cannot touch '/var/lib/update-notifier/dpkg-run-stamp': read-only file system
E: sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
dpkg: unable to access dpkg status area: read-only file system.
```and thats the end of it.

After I close the message another one pops up:

```
An error occurred
E: ERROR: Could not create log directory /root/.synaptic/log/ -mkdir
(30: Read-only file system)
E: Failed to write commit log
```Then I close that one and the whole system is in an unusable state.
The update manager wont close and other programs cant open fully, ill explain:
I open up gedit, its just an empty window, the cursor will change icon to suggest im hovering over the writeable area, however I cant see anything, its just a grey blank window...
This also happens with other things I try to open, even the restart confirmation menu is blank, but I can still click the button at the bottom right to continue restart, or the one just to the left of it to cancel. Only I cant actually see the buttons or text... just a grey empty window.
Yes this was all working fine and I could see everything before the update error.

Its like the whole system has set itself into a read only state. (Just my guess from the error above)

After I manage to restart ubuntu(guessing were the buttons are...) itll load up grub, now with a new ubuntu boot item.
```
Ubuntu, Linux 2.6.31-19 - Generic
Ubuntu, Linux 2.6.31-19 - Generic (recovery mode)
```Still contains the old items too:

```
Ubuntu, Linux 2.6.31-14 - Generic
Ubuntu, Linux 2.6.31-14 - Generic (recovery mode)
memorytest (memtest86+)
memorytest (memtest86+, serial console 115200)
windows 7
```When trying to boot up on the new version(2.6.31-19) I get this lovely bundle of joy...

```
udevadm trigger is not permitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
svgalib: Cannot open /dev/mem.
Gave up waiting for root device. Common Problems:
boot args (cat /proc/cmdline)
check rootdelay= (did the system wait long enough?)
check root= (did the system wait for the righ device?)
missing modules (cat /proc/modules: ls /dev)
ALERT! /dev/disk/by-uuid/fa4590fd-5eb8-44f5-a46d-6129a9747522 does not exist.
Dropping to a shell![I]

(initramfs)[/I]
```(Then starts a console thing... but no idea what to do...)

So, I give up there and move onto the older/previous version(2.6.31-14) and get this instead!
```
mount of filesystem failed
A maintenance shell will now be started
root@xmillsa-desktop:~# [      13.745083] /build/buildd/linux-2.6.31/drivers/hid/usbhid/hid-core.c : usb_submit_urb(ctrl) failed
* Starting init crypto disks...             [OK]
```(Then starts a console thing... but no idea what to do...)


So.... after that I usually reinstall ubuntu and try again, but this is the 3rd time now so I need some help...
I think ill try 9.04 and see if I can install that, then upgrade from that to 9.10.

I cant understand why a completely clean install would have a problem  from a normal update.
I have tried re-burning the image but still same problem. :P

Any help would be much appreciated!

- Xmillsa

EDIT: Just noticed how long this post is, gonna try... some sort of formatting to make it easier to read.

---

### Post by oldos2er on 2010-02-17
What are your system specs?

---

### Post by xmillsa on 2010-02-17
CPU: Intel Core2 Quad Q6600 @2.4ghz
Ram: 4GB
GPU: Nvidia 275gtx
Motherboard: EVGA 780i SLI FTW version
Hard Drive: 1TB (Win7)
Hard Drive: 160GB (Ubuntu)

I managed to fix my problem!!! :D

Clean install of 9.04 and upgraded from that rather than a clean install of 9.10.

So, anyone else who for some strange unknown reason gets this problem, do this...
1 ) Download version 9.04 [(Found Here)]("http://releases.ubuntu.com/9.04/")

2 ) Burn to CD and boot from it.

3 ) Install Ubuntu 9.04, I assume you can already do these 3 steps to get the same error as me.

4 ) Run the update manager, click on Check, download all updates but DONT click on the upgrade to 9.10 just yet!

5 ) Once all updates have downloaded and installed (hopefully successfully), reboot.

6 ) Again go into the update manager, click on check to make sure there aren't any more updates, if there are, go to step 4 and repeat until no more updates appear.

7 ) Once you have installed all the available updates, click on upgrade to 9.10 and let it do whatever it needs to do until complete, then restart your computer again(it should prompt you anyway).

8 ) Start up ubuntu, go to update manager, check there are no updates(there shouldnt be any since you already have everything, plus have just upgraded to 9.10, but its just to make sure).

9 ) Hopefully, you now have a fully upgraded and WORKING ubuntu 9.10!

At least thats what worked for me. :KS

Id still like to know what caused it to fail each time when upgrading in a clean install of 9.10 but if not, at least I have a work around...

I wont set the post as Solved just yet, since the initial error is still unsolved.

---

