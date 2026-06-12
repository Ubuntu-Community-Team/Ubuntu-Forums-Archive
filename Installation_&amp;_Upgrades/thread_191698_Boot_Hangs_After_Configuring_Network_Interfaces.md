---
title: "Boot Hangs After Configuring Network Interfaces"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by mbsatgt on 2006-06-07
OK, so, last weekend, I tried to update my server to Dapper. Alas, it seems to have failed. Now, when I start my computer, it hangs after 
"Configuring Network Interfaces... OK"
It hangs in the same place in all of: Standard Mode, Recovery Mode, and an old kernel boot in both Standard and Recovery Mode.
I did try the procedure given here:
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)
for when you can't even get to a console. And, after I got everything mounted, I ran the chroot command. Alas, when I ran the 
dpkg --configure -a
 everything was already configured. And when I ran 
apt-get -f remove
nothing happened. Well, it put me back on a prompt. So, after that, I tried the 
apt-get install ubuntu-minimal
apt-get install ubuntu-base
and
apt-get install xserver-xorg x-window-system-core ubuntu-desktop
Alas, it said all of these were already installed and up to date.
I then tried
dpkg-reconfigure xserver-xorg
but that (after going through the whole config) spit me back out outside of my chroot (which seems weird). 
dpkg-reconfigure gdm 
wouldn't let me do it after that, even after I went back into the chroot.

So, now I am at a loss. What happens after Configuring Network Interfaces? My computer has a lot of disc action (well, not a lot, but the disc does work hard) and then the computer completely hangs with the hdd light still on, but nothing else is occuring. This computer worked before with breezy, and I never had a complaint. I am regretting attempting to upgrade now. Any ideas, anyone?
I can get config files off the live cd, but since the xserver on the live cd freezes using my video card and the vesa config fails another way, it is sort of a pain. 
I am currently using Windows on another computer to post this.
Matthew Simmons

---

### Post by mbsatgt on 2006-06-08
OK, so I am still looking for a way to fix this. So, after looking at it again, in recovery mode, the line before "Configuring Network Interfaces... OK" is 
```
/etc/rcS.d/S40ifrename: line 12: /sbin/ifrename: No such file or directory
```
Could this be the issue? How would I go about reinstalling this part of the OS? Could I just copy in this file? Is the rc file incorrect to assume that is where the ifrename binary should be in dapper? If I were to comment out this rc script, would it cause a problem? Could this even stop the system from booting? I don't really want to chase down a dead alley.

The only other errors I can see on the screen when the boot hangs are:
[it recovers the journal from /usr (which is a Software RAID device) and declares it clean]
```
udevd-event[3075]: wait_for_sysfs: waiting for '/sys/devices/platform/i82365.0/bus' failed
```
After this error, it declares "...done." for the "Checking all filesystems..." start item.

If neither of these are possible problems that can be fixed, is there some file I can try to check that might give me other errors during startup from the live cd chroot? It is still hard to post files from the live-cd, but I could probably do it, if it would help. I figured out that I can ftp to my work's ftp server from command line and then upload the files from there...

---

### Post by mbsatgt on 2006-06-09
OK, now I finally have it running. Which is exciting :D !

Neither of the errors I mentioned before were the problem (well at least not the *only* problem if they were a problem).

So, now I just want to make sure that what I had to do to get the computer running isn't going to cause problems... Since I knew that Networking was getting accomplished correctly, I commented out the S40ifrename rc script, but since that didn't get it running, I commented out pretty much everything after S40networking. So, I need to make sure that having these scripts commented out won't cause huge problems:
```

matthew@provolone:/etc/rcS.d$ ls _*
_S40ifrename  _S40pcmcia  _S60displayconfig-hwprobe.py  _S70screen  _S70x11-common
```
I noticed that the live CD didn't have ifrename, so, I am not too worried about having that commented out, but I don't know what screen or x11-common do. I assume the hardware probe was probably what was feezing the computer, but I don't know. Everything seems to be working correctly now (including X), so, I guess if I hear nothing, I won't worry about it too much.

---

