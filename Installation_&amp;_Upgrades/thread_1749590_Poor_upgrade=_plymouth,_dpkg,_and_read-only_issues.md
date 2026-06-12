---
title: "Poor upgrade= plymouth, dpkg, and read-only issues"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by HamburgerTurtle on 2011-05-04
I have an hp 2300. I was running the ubuntu netbook edition. I was busy and on and off my computer. The upgrade box came up and I hit it without a second look and left. When i came back (hours later) everything was frozen. I've encountered freezie screens running ubuntu on desktops before so i just hit a hard reset and figured that would fix it.

It didn't.

Here's what happens:

I restart and get a box with 10 options in it asking me what i want to boot with.

```
Ubuntu, with Linux 2.6.35-28-generic
Ubuntu, with Linux 2.6.35-28-generic (recovery mode)
Ubuntu, with Linux 2.6.35-27-generic
Ubuntu, with Linux 2.6.35-27-generic (recovery mode)
Ubuntu, with Linux 2.6.35-25-generic
Ubuntu, with Linux 2.6.35-25-generic (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
```If I pick one without recovery mode It goes to the usual boot up screen and then tells me: 

```
 The disk drive for / is not ready yet or not present.
Continue to wait; or press S to skip mounting or M for manual recovery
```If i hit S i get:

```
mountall: plymouth command failed
mountall: disconnected from plymouth
```And then i can't do anything. If i hit M i get a working terminal.

I've tried:

```
sudo us
sudo apt-get install -f
sudo apt-get update
sudo apt-get clean
```I got issues with dpkg. Tells me i need to input:
```
sudo dpkg --configure -a. 
```When i do that I get:

```
dpgk: error: unable to access dpkg status area: Read-only file system
```I tired:

```
sudo dpgk --reconfigure plymouth
```

I've googled all over and found other people with the same codes, but none in the same predicament.

It seems no matter what I put in I'm getting errors. A list of things to type to get help with dpgk shows up sometimes. I type those, but I don't understand anything I'm seeing there. I would like to either move forward with the install or (ideally) just go back to the netbook version. I would like avoid a clean install if possible because I didn't back up my files before all this.

I'm sorry if this repeats, I searched for a good hour and couldn't find anything that answered me.

Any help would be much appreciated.
Thank you.

---

### Post by HamburgerTurtle on 2011-05-08
I fixed it myself. Ended up booting from a live usb w/ 10.04 on it. I installed along side what i already had and was able to move my files over and then delete the old partition. The clean install is a bit lame cause i have to download all my drivers again, but it worked out in saving my files so I don't mind. I suppose my itty-bity netbook just can't handle the Natty Narwhal.

---

### Post by neobadandy on 2011-05-30
i had the EXACT same problem.
im repairing my mom's little netbook, she ran updates and it f***ed up badly.
you can get rid of read only errors with
```
sudo mount -o -n remount /
```
i know nothing about ubuntu really, i just read that somewhere and it works.
after that you can re run the ```
sudo dpkg --configure -a
``` thingamadoo.
that's what i'm doing right now, i'll keep you posted as to whether this solves any problems with the plymouth B.S.

dont need to keep you posted, it finished, i typed reboot, booted it up, and it works. all good.
so just remount with the 1st command up there,
and then reconfigure the packages or whatever, with the second command.
and ur all set...
BAHAHAHHAAHAHAHAHAAHHAHAHA

i hope this helps someone

---

