---
title: "Boot time improvements"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by lemmi150570 on 2005-04-16
Hi,

I'd like do a couple of things to reduce my boot time, maybe someone can help...

1) How do I tell Ubuntu not to look up an ip adress over DHCP even when the network is not automatically active on bootup?

2) How do I tell Ubuntu not to synchronize the clock with the web but simply use the hardware clock during bootup?

3) I've included my Windows partitions in /etc/fstab - How do I tell Ubuntu not to perform a dosfsck on every single bootup?

1+2+3 together take about 2 minutes time when I'm not connected to the internet.

Thanks for all help, Joachim

---

### Post by MaX on 2005-04-16
[QUOTE=lemmi150570]Hi,

I'd like do a couple of things to reduce my boot time, maybe someone can help...

1) How do I tell Ubuntu not to look up an ip adress over DHCP even when the network is not automatically active on bootup?

2) How do I tell Ubuntu not to synchronize the clock with the web but simply use the hardware clock during bootup?

3) I've included my Windows partitions in /etc/fstab - How do I tell Ubuntu not to perform a dosfsck on every single bootup?

1+2+3 together take about 2 minutes time when I'm not connected to the internet.

Thanks for all help, Joachim[/QUOTE]
 3) Why does it do that??? There must be something wrong with it?
I have both my Windows FAT32 partitions and one NTFS partition in fstab and I have never had boot run those for me.

1 and 2 I'd like an answer for too

---

### Post by bored2k on 2005-04-16
2) sudo chmod -x /etc/init.d/ntpdate

[http://ubuntuguide.org/#temporaryskipboot-upservice](http://ubuntuguide.org/#temporaryskipboot-upservice)

---

### Post by jerome bettis on 2005-04-16
you can press ctrl + c during the configuring network interfaces step

and you can sudo apt-get sysv-rc-conf ; sudo sysv-rc-conf and uncheck the ntpdate service to get rid of that.

---

### Post by diebels on 2005-04-16
[QUOTE=lemmi150570]
3) I've included my Windows partitions in /etc/fstab - How do I tell Ubuntu not to perform a dosfsck on every single bootup?
[/QUOTE]

The two numbers on the right side in /etc/fstab is called pass numbers for fsck. Set them to 0 0 for your windows partition and it will not be checked on bootup.

---

### Post by lemmi150570 on 2005-04-17
Thanks, Guys.

Joachim

---

### Post by MaX on 2005-04-18
[QUOTE=diebels]The two numbers on the right side in /etc/fstab is called pass numbers for fsck. Set them to 0 0 for your windows partition and it will not be checked on bootup.[/QUOTE]
 How do I get my ReiserFS system to run the Journal checker at boot? It says something about the device being in read only mode so it won't run the journal thingymajong :)

---

### Post by izmaelis on 2005-07-29
Ok. Disabling local time update from network server reduced about 10 secs from total boot time. I will try to set my network configuration not to receive IP address (etc.) with DHCP too. I think it will help too. (-:

---

### Post by kosmic on 2005-07-29
The firts thing for me to speed up the ubuntu boot process is to install BUM ( Ubuntu Bootup manager or sys-rc.conf and then desactivate the processes I don't use in my machine.

The first is the NTP sync Date with ubuntu
2 ª RAID DEVICES AND LVM (when is not in use in the machine)
3 ª For my the principal bootneck of the ubuntu boot process is the Hotplug, with thakes between 10 and 12 seconds to acomplish the detection of the devices :(
4ª if the macinhe doesn't have internet acess then I deactivate all the process that is necessary for the internet to work :)

---

### Post by kkass on 2005-08-02
I am using Ubuntu on my laptop, and i frequently switch between wireless networks and wired networks depending on where I am.  In some cases I was very annoyed by the time waiting for the network interfaces to give up on ce=onnecting.  (On a side note, Ubuntu gives up much faster than Fedora!)

To speed this up edit the networking startup script:

```
sudo vi /etc/init.d/networking
```


make the following change to the 'start' case:

```
if [ "$VERBOSE" != no ]; then
     ifup -a
else
     ifup -a >/dev/null 2>&1
fi
```

...to...

```
if [ "$VERBOSE" != no ]; then
     ifup -a &
else
     ifup -a >/dev/null 2>&1 &
fi
```

This makes the system try to bring the interfaces up in a background process.  Allowing the boot procedure.  You can probably do the same thing to NTP if you like.

---

