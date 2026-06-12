---
title: "CUPS, Samba etc. don't start up automatically"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by mkluwe on 2010-01-24
Hi!

After my update to 9.10 I had not notice that CUPS, Samba, lighttpd (and maybe other serives that I've not missed until now) don't start up during system start no longer.

After all, things look quite normal in the directory /etc/rc3.d, which has the appropriate links S20samba, S20lighttpd and S50cups, all of them working when I use them directly.

But wait! Ubuntu uses updstart now, does it? I have yet to understand what that means to the classic startup scripts in /etc/init.d.

Please give a hint what additional diagnosis I can provide.

Regards,
Matthias

---

### Post by angelcaf on 2010-01-28
Same issue with me!!! (Kubuntu Karmic)

---

### Post by doas777 on 2010-01-28
is your network up at the time the services try to load? if you use network-manager, or wicd or any other userspace network config tool,  then there is a possibility that it has not yet started.

---

### Post by chaanakya_chiraag on 2010-01-28
Did you upgrade or do a fresh install?  Maybe somethings didn't update correctly (symlinks, etc.) when you upgraded, causing that to fail.

---

### Post by mkluwe on 2010-01-29
> **doas777 said:**
> is your network up at the time the services try to load? if you use network-manager, or wicd or any other userspace network config tool,  then there is a possibility that it has not yet started.

Well, how do I know if it is up? In fact, I do use network-manager and had some issues in switching to that during the update to 9.04, IIRC.

As this machine should provide some services in my small network (lighttpd for example), it does not make any sense that these won't start without me logging in :-(

---

### Post by mkluwe on 2010-01-29
> **chaanakya_chiraag said:**
> Did you upgrade or do a fresh install?  Maybe somethings didn't update correctly (symlinks, etc.) when you upgraded, causing that to fail.

Yes, it's an update. This machine has been update several times, beginning with 6.10. I've already tested some symlinks, /etc/rc3.d/S50cups works well, for example.

---

### Post by MoRoBoShi on 2010-01-29
You can try to force manually load samba daemons at boot.
What happen if you edit your /etc/rc.local to do that:

sudo /etc/init.d/samba start



And reboot???

---

### Post by doas777 on 2010-01-29
> **mkluwe said:**
> Well, how do I know if it is up? In fact, I do use network-manager and had some issues in switching to that during the update to 9.04, IIRC.

As this machine should provide some services in my small network (lighttpd for example), it does not make any sense that these won't start without me logging in :-(

well you can find a trace in teh syslog or the mesglog indicating that samba attempted to load, but failed because it could not bind to an interface, if that is the case. I'm told that the NM way to fix that, is to check the box on your connection that says "connection is available to all users", or if you want to ditch NM, just configure your /etc/network/interfaces file (though I'm told that that file is obsoleted in lucid).

or you can jsut restart samba from a line in your start up apps if you can wait until user login to start samba.

---

### Post by llawwehttam on 2010-01-29
Bit strange as mine works fine but I did a clean install.

Try re-installing samba```
sudo apt-get purge samba ; sudo apt-get install samba
```

---

### Post by chaanakya_chiraag on 2010-01-29
The above might work, but a likely cause is that the update didn't go as perfectly as planned, therefore some things (like autostarting samba, cups, etc) are not working.  I personally like to do a clean install, as it is much safer than an upgrade.  If you have a separate /home partition, I would recommend a clean install.  To get a backup script, you can tweak the script found in the second link in my signature.

---

