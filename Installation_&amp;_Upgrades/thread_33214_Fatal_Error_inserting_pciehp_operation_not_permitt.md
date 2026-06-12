---
title: "Fatal: Error inserting pciehp operation not permitted"
date: 2005-05-09
forum: Installation &amp; Upgrades
---

### Post by xmastree on 2005-05-09
I'm trying to install ubuntu 4.10 for the first time, and I get the above error, followed by a similar one:

modprobe: Fatal: Error inserting shpchp. operation not permitted

Then after a pause, it continues and sems to install correctly. Upon starting X, I get an error window:

error activating XKB configuration

Is that keyboard related? I didn't like the way I had to type the keyboard layout, when I had already chosen it from a list earlier in the installation. It ought to have known... It's UK.

On rebooting, the same 'inserting' error appears, and pauses long enough to make me think it had stopped. Eventually it continues, and I get the same XKB error.

Apart from that it looks impressive. USB flash disk works fine, CD ripping and sound are fine, that's all I've tried so far...

Any ideas what's up?

The system is a Athlon 2400, Asus A7V8X, 512MB, 3.2GB HDD, 128MB Geforce-4.

I know the HDD seems small, but it's just a spare one I had lying around...


Update:
I just tried it again today, and it didn't take so ling to boot up. The error was still there, but it didn't seem to slow it down as much...

---

### Post by spd106 on 2005-05-10
Hi, look at the following thread

[http://www.ubuntuforums.org/showthread.php?t=21198](http://www.ubuntuforums.org/showthread.php?t=21198)

I'm not sure about the XKB error though.

Hope this helps

---

### Post by xmastree on 2005-05-11
Ok, thanks. Seems I asked a FAQ...  :roll: 
 
Anyway, having done that, it worked once, but now it hangs at 'Starting hotplug subsystem...' 

As for the XKB thing, I went into the Gnome keyboard settings and changed it from uk to united kingdon, from the list, and that's fixed the error, but I now get asked if I want to use the X setting or the Gnome setting. No big deal though

---

### Post by xmastree on 2005-05-14
> hangs at 'Starting hotplug subsystem...'I found what's causing this, or rather how to stop it...
It's my card reader.  :| 

Although it works perfectly, it sometimes causes the system to hang at this point during boot. If I unplug it, it boots right up, but if I leave it connected (preferred method) it only boots about once in every five attempts...  ](*,)

---

