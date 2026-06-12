---
title: "HP Laptop installation problems"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by shaun_d on 2010-03-24
I'm new here (well actually this is my first post) but I do have some experience with Ubuntu, I've been actively using it since October last year (karmic)

I was wondering if someone could help me.

One of my friends recently specifically asked me to put Ubuntu on his laptop (he'd been running Vista with 512MB of RAM) so I said sure, and tried to install Karmic via an ISO cd, once the installation had finished when it booted it just came up with a grub screen saying something like:

"Minimal Bash script usuable, tab lists supported"

When I hit tab it came up with a list of commands e.g. "xnu_kernel" and "xnu_splash" (I think) I tried reinstalling with the same results. Recently he asked me again, I tried with the beta 1 of 10.04, I tried using it without installing for a bit and everything worked absolutely fine, I used the desktop icon to install it, after I tried booting exactly the same thing happened.

I tried typing "xnu_kernel" and it said it needed a file name, I tried "xnu_kernel/" with the same result.

I'm guessing it didn't load the Kernel for some reason, I have no idea why and I don't know what needs to be typed in to rectify it (I have minial experience with the terminal and only know basic commands)

I'd appreciate any help ;)

Shaun_d

---

### Post by lemming465 on 2010-03-28
Where there any error messages late in the install process?  It sounds like maybe something went wrong with the grub2 bootloader install phase.

Is your friends systems trying to be Linux only, or is it trying to dual-boot Vista and Linux?

If you boot the Live desktop CD again, could we see the output of *sudo fdisk -lu*?  Run that at a bash prompt from Applications -> Accessories -> Terminal.

Can you mount what is supposed to be the Linux root filesystem from the live CD, and does it look fairly complete?  A freshly installed Ubuntu will use about 2GB of disk space, about 120 thousand inodes (files), and the root directory will have subdirectories such as dev, proc, bin, sys, sbin, usr, var, home.

We can offer some more specific repair advice once we know a little more about your situation.

---

### Post by shaun_d on 2010-03-29
Sorry the first message was vague, in answer to your questions.

-There were no error messages in the install, the install process was flawless, the only notable thing was that after the install process the laptop shut down. the disk ejected and I took it out and shut the disk tray as instructed by install prompt's after this many lines of code appeared, all reading the same thing (I can't remember what it said though . . . sorry)

- He is trying to be a 'linux only' person, apart from gaming, but he has a separate PC for that. In the install I chose to overwrite the windows partition and install Ubuntu and only Ubuntu on the hd (it wiped everything else)

- I'll see what I can do about running '*sudo fdisk -lu'* from a teminal via a live CD, I don't have access to it at the moment but I'll get into contact with my friend. Expect the results in a day or so.

'Can you mount what is supposed to be the Linux root filesystem from the  live CD, and does it look fairly complete?  A freshly installed Ubuntu  will use about 2GB of disk space, about 120 thousand inodes (files), and  the root directory will have subdirectories such as dev, proc, bin,  sys, sbin, usr, var, home.'

Do you mean view through Nautilus? Or mount through the terminal? If so I'd need some sort of advice / help, I have very little experience with the terminal.

Thank you for your help and sorry my knowledge on Ubuntu isn't up to par with most people browsing these forums.

---

### Post by lemming465 on 2010-03-30
Thanks for the additional details.  
> ... sorry my knowledge on Ubuntu isn't up to par ...
No apology necessary; we all started somewhere, and the whole point of the support forums is to help people learn things and fix problems.

After booting a live CD, for mounting the root partition, try the GUI "Places" menu; it's probably listed under there.  However, some of the stuff we want to know is easier to figure out from the command line (Applications -> Accessories -> Terminal).  Most administrative commands need root (administrator) permissions, so the first thing to do in the terminal window is ```
sudo -i
```
The shell prompt will change from '$' to '#' to reflect the increased permissions.
The "df" command (display filesystem) can tell you about how many files are present and how much disk space is being used.  We're interested in the inode count (number of files) and space (blocks). In the terminal window run ```
df -i; df -m
```
There will be lots of lines out output; ignore all the stuff about /proc, tmpfs, and the CD-ROM and find the lines with the long UUID tag or /dev/sda1, which should be the mounted filesystem off the hard disk.  What you are hoping to see is roughly 2GB of space used, and more than 100,000 inodes (files and directories) used.  If so, the install was reasonably complete, and maybe just the boot loader part messed up.

Your first goal should be to try and update the on-disk install with any patches and bug fixes, as that may help with the boot loader problem.  This needs to be done from inside a "chroot"; you want to switch the terminal window from running off the CD-ROM to running off the hard disk partition that got mounted.  First you have to find it.  The /media directory is used for temporary filesystem mounts (grafting a partition onto an existing directory tree, to make the contents accessible, kind of like a windows drive letter); if you type "mount" it will show you a bunch of stuff.  Only one of them will match what you found in the middle of the df output previously.  In the terminal window type "cd /media/" and hit tab; it should autocomplete the possibly long name.  With the current directory of the terminal window set to the hard drive mount point, now set up the chroot environment.```
for f in sys proc dev; do mount -o bind /$f $f; done
chroot .
```
The terminal window is now using the hard disk files, not the CD-ROM files.  Time to try an update it:```
aptitude update  # refresh repository contents
aptitude full-upgrade # apply new bug fix packages
```
Next try re-installing the grub2 bootloader```
update-grub
```
Reboot the PC from the GUI shutdown/logout icon, and see if it's any better.

---

