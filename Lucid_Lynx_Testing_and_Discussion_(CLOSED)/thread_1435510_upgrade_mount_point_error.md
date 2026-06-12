---
title: "upgrade mount point error"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by HarmonicaGoldfish on 2010-03-21
I just upgraded to the latest development release of lucid from karmic. The upgrade process went smoothly until the restart,

I see the Dell splash, then I get this message and it does not go any further.

Mount: mount point /proc/bus/usb does not exist
Mountall: mount /proc/bus/usb [351] terminated with status 32
Mountall: filesystem could not be mounted: /proc/bus/usb

I did a hard shut down and was met with the same message.

Has anyone seen this and what should I do?

I used update-manager -d to upgrade 

My computer is a dell inspiron laptop 1525

Thanks in advance for any help.

---

### Post by HarmonicaGoldfish on 2010-03-21
I reported this as a bug in launchpad

[https://bugs.launchpad.net/ubuntu/+bug/543716](https://bugs.launchpad.net/ubuntu/+bug/543716)

---

### Post by MaindotC on 2010-03-21
I had this problem on my machine when I upgraded from 9.10 to 10.04 alpha, so I just re-installed a small 10.04 partition and I kept my /home directory on a separate partition so I just used the new 10.04 partition.  Now I ran updates and I'm getting this error as well, so unless I reinstall I'm locked out of both partitions.  Any ideas?  I'll check the bug report and paste a copy of this if necessary.

---

### Post by HarmonicaGoldfish on 2010-03-21
Has anyone else seen this or know what it is?

---

### Post by MaindotC on 2010-03-21
I'm searching all the text files in the o/s for something that says "/proc/bus/usb".  It's taking a while.  From googling "Mount: mount point /proc/bus/usb does not exist" I've seen other users talk about some sort of startup script that searches for this directory.  I guess it makes sense - there's some instruction, somewhere, that says "look for this directory" on startup and probably a condition that says "if you don't find that directory, exit" - speaking in pseudocode.

I'm not a dev so I don't know precisely where to find these things but I thought maybe if I suggested then we may be able to solve this ourselves.  You have any ideas?

---

### Post by VMC on 2010-03-21
I didn't do any upgrade just install of lucid, but I don't even have reference to usb in proc or fstab:
```
$ ls /proc/bus
input  pci
============
$ cat /etc/fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
...

```

Edit: I should have added, I don't have any issues. Plug flash drive in or USB HD and its detected.

---

### Post by cariboo on 2010-03-21
My install works reasonable well, I don't have a /proc/usb directory either, even with a usb device inserted in one of the ports.

---

### Post by MaindotC on 2010-03-21
It seems that this will affect VBox users.  Per user "setuid" in #ubuntu+1, he advised I boot from a livecd, comment out the following in /etc/fstab:
```

none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

```

Which I did and now I can boot into both installations.  This makes sense because it wasn't until today that I wanted to utilize USB functionality in my VM's and I followed the [VirtualBoxUSB Guide](https://help.ubuntu.com/community/VirtualBox/USB) in the community docs.  I don't know what the procedure is for notifying VBox users of this situation but if someone will either do it or advise me then I'll do it.  That guide should probably have an annotation regarding rebooting as well.

---

### Post by HarmonicaGoldfish on 2010-03-22
I am a vbox user. You're right, It would have been nice to know before the upgrade! 

So...what can I do now? If I boot from a live cd and comment out the line you mentioned will this be enough or will I have to then do a fresh install from that cd, losing my data and settings? How do I get past that message so I can tweak things to work?

---

### Post by MaindotC on 2010-03-22
You do not need to do a fresh install.  Just comment out that line and reboot.  At this time I'm not sure how to uncomment it and enable a safe boot, but I'm just avoiding using USB devices with the VM until this is fixed.

---

### Post by HarmonicaGoldfish on 2010-03-27
I ended up doing a fresh install. Luckily I had recently backed up most of my files to an external hard drive so I figured why not? Haven't tried to install vbox yet. I only use it for itunes and my itouch, with ubuntuone store available I think I'll try out rhythmbox for a while.

---

### Post by MaindotC on 2010-03-27
I'm still getting the error when I uncomment that line in fstab so I guess it hasn't been resolved yet.

---

### Post by blackSP on 2010-04-27
Is there some sort of status update on this one as it also effects Wine (at least with me).

I always connect my Garming 60CSx to Mapsource through Wine.
In order for Mapsource to see the GPS I need to add: usbfs /proc/bus/usb usbfs auto 0 0 in fstab. This line however also results in the same mount point error and the system halting during boot.


[FONT=arial][/FONT]

---

