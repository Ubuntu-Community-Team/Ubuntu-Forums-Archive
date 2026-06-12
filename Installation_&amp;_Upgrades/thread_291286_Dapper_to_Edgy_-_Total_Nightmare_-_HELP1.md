---
title: "Dapper to Edgy - Total Nightmare - HELP?1"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by myke on 2006-11-02
Hi.  I've used Ubuntu/Kubuntu since breezy and easily updated to dapper when it was firmly released.  As such, I though upgrading to edgy would be smooth as well.  Not so.  I followed the listed instructions implicitly for upgrading and did so while in KDE as comments seemed to indicate that KDE vs. Gnome upgrades were going smoother.  However, upon applying the updates it gave me an error stating that the ip address for two of the repositories had changed (but didn't say to what) and that 41 upgrades were not done.  It also prompted me to restart so I did.  After restarting, I got the commmand prompt ... no desktop ... which seemed to be a common problem.  I had written the command to fix this problem as suggested and utilized it:

sudo apt-get install xserver-xorg

It appeared to download and install the files successfully and restarted itself.  Then it wouldn't even fully boot the Linux kernel.   It gives me the following

> 0target filesystem doesn't have /sbin/init
BusyBox v1.1.3 (debian 1:1.1.3-2ubuntu3) built in shell (ash)
/bsin/sh; can't access tty: job control turned off
(initramfs)

After the (initramfs), the command cursor is blinking but I have no clue what to do from here.  I don't know what this means.   Can anyone help?   Unfortunately, all of my data was not backed up and I'll lose a ton of stuff if I have to do a clean install.  Is there anyway to get this back on track???  I'm really surprised what a mess I have after all of my smooth sailing up until now.

---

### Post by myke on 2006-11-02
Can no one help me here, ladies and gents?   I'm really desperate at this point.  Is there any way given the above to at least get me to a command prompt so that I could perhaps reinstall ubuntu-minimal and base and then update so I don't lose all of my data and files that was under dapper??  The only other thing I know to do is to wipe out the linux partition and do a clean install and frankly, i'm loathe to do that.

---

### Post by myke on 2006-11-02
Geez ... I hate replying to my own post but I've been trying to get this damned thing fixed for over 24 hours and I'm lost.

IS there not anyone that would know how to help me here??  Get me to a command prompt ... salvage some data ... anything???

---

### Post by mgmiller on 2006-11-02
I've never seen an error like yours, so I can't help with fixing it, but if your data is still there, you could boot from a live CD and mount the hard drive and try copying stuff off to a USB thumb drive.  If you don't know how to do this from an Edgy or Dapper disk, (Dapper made it a bit easier with a graphical mounter, edgy requires CLI to mount drives), you could use a puppy linux boot CD.  They are very small (only about 60 MB) and make mounting attached drives very easy.  Hopefully, you can get your stuff back.

---

### Post by caldevil on 2006-11-02
Your problem I think can be solved. You have messed up with the init system. I think the old initrd got removed from your system and the new upstart is not been installed. If you can access (which I guess you cannot) internet from the computer than 
```

sudo apt-get -f install upstart

```
should solve the problem. 
But as I see you cannot access the Internet then I think you should burn an edgy CD and use it as a repo. 

Don't panic nothing has happened to your data. In worst case you can always recover all of your data using knoppix or Ubuntu live CD.

---

