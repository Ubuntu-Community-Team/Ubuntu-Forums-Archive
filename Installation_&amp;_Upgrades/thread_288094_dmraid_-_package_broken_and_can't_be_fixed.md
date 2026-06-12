---
title: "dmraid - package broken and can't be fixed?"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Scoodaddy on 2006-10-29
I dual-boot Ubuntu Linux 6.10 and Windows XP, and I have an ntfs RAID1 (mirror) SATA disk array installed.  I wanted to view (read-only) the data on this ntfs array from Ubuntu, so I installed dmraid.  The installation generated an error message but it apparently worked: once I mounted the disk (from /dev/mapper) I was able to view and copy its contents.

The problem is that now I cannot reconfigure, re-install or even remove dmraid, and every time I change or add any other package I get an error message about dmraid being improperly installed.  When I try to re-install it Synaptic gives me:

```
E: dmraid: subprocess post-installation script returned error exit status 139
```

and when I try to remove it I get:

```
E: dmraid: subprocess pre-removal script returned error exit status 139
```

From the command line using dpkg to remove it I get:

```
tom@ubuntu-tower:~$ sudo dpkg -r dmraid
(Reading database ... 127782 files and directories currently installed.)
Removing dmraid ...
 * Shutting down DMRAID devices...                                                                                                                           /etc/init.d/dmraid: line 13: 21724 Segmentation fault      (core dumped) /sbin/dmraid --activate no --ignorelocking >/dev/null 2>&1
invoke-rc.d: initscript dmraid, action "stop" failed.
dpkg: error processing dmraid (--remove):
 subprocess pre-removal script returned error exit status 139
 * Setting up DMRAID devices...                                                                                                                              /etc/init.d/dmraid: line 13: 21758 Segmentation fault      (core dumped) /sbin/dmraid --activate yes --ignorelocking >/dev/null 2>&1
invoke-rc.d: initscript dmraid, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 dmraid
```

and dpkg-reconfigure gives me:

```
tom@ubuntu-tower:~$ sudo dpkg-reconfigure dmraid
/usr/sbin/dpkg-reconfigure: dmraid is broken or not fully installed

```
So even though it seems to be "working" for my purposes, dmraid is stuck in a broken state.  How can I correct this?

I've already looked at the FakeRaidHowTo but I didn't see anything applicable to this problem.  I am running an Asus A8V motherboard with an onboard VIA VT6420 SATA RAID Controller (and I'm pretty much a Linux newbie).  Thanks!

---

### Post by Scoodaddy on 2006-11-03
Anyone?  I know there is an option to force dpkg to remove a package; should I try that on dmraid?  Or is there a better way to resolve this broken package?

---

### Post by Scoodaddy on 2006-11-07
Can anyone at least point me in the direction of a resource so I can figure out how I might resolve this broken package?  I am loath to force a removal of it, since it actually works at the moment, but I'd love to fix it so Synaptic stops giving me the error message.

---

### Post by lukeo on 2007-02-02
I have exactly the same problem, dmraid is broken, i can't reinstall it I can't remove it, I can't update it. 

It's driving me nuts, and unlike you my raid doesnt work.

---

### Post by Mozgus on 2007-04-08
Same problem here. Big mistake installing this thing.

---

### Post by cucscspr on 2007-04-08
I had a simular experience with DMRAID, I have a Promise Fasttrak TX4200, from what I have read it is obsolete and the last drivers for it from promise are for 2.4 kernel.  I tried DMRAID and it seems to have picked it up.

I have 2 disks in JBOD mode and 2 disks in a RAID 0 mode (4 port controller)

The JBOD disks were seen and mounted but the RAID set was  giving me this error:

ERROR: pdc: wrong # of devices in RAID set "pdc_bggdjhhbg" [1/2] on /dev/sda
ERROR: removing inconsistent RAID set "pdc_bggdjhhbg"
No RAID sets

Yet my RAID works fine in windows.  I have searched and searched and can't seem to understand what could be wrong.

Back to my point, I could not reinstall or remove/purge DMRAID because it kept giving errorcode 1 and quitting.

What I did was:

cd /var/lib/dpkg/info

edit the files 

[dmraid.prerm] and [dmraid.postinst] 

and remove the script part about if -x /etc/rc.d/dmraid blah blah blah

that way it won't try to open or close the raid set and error out, and it will either install or remove.  I supposed you should make sure to close/de-activate the raid set before you perform this hack.

Hope this helps!

DISCLAIMER - Use at your own risk, Make backups when possible

---

