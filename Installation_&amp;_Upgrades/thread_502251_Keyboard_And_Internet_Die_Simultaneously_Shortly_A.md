---
title: "Keyboard And Internet Die Simultaneously Shortly After Boot"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by danovotny on 2007-07-16
Hello,

First post! I am starting my journey into the world of desktop Linux. I spend most of the day at work in shell, so it's not 100% new to me (but most of the install/desktop/GUI portion is). I recently installed 7.04 to a USB pen drive. This worked flawlessly for me, installing from the alternate ISO, to the USB pen drive, while my primary internal SATA drives are disabled from BIOS. This allows me to test Ubuntu and not mess with my WinXP MBR disks. The drive has persistence (I read this was a problem with 7.04 but I haven't had a problem with it. Maybe this is an unrelated method?), and I can save files, themes, settings, etc.

My problem is that shortly after I log in, my keyboard and internet stop working, both at the same time. There is no consistent trigger to this, and the amount of time that passes before it happens is also inconsistent. I'm using a wired Microsoft Office Keyboard and the ethernet port is one of two integrated ports on my Motherboard (ASUS A8N32-SLI Deluxe).

On quick side question. I have an AMD64 bit processer, but installed the x386 ISO, is that ok?

Please let me know what additional information you might need in order for me to get this working. I'll try my best to get any information requested, but it can be a challenge to get a terminal open and type commands before the keyboard dies. I have seen the future of Windows (Vista) and I do not like it. I figure that now is as good of time as any to start the switch, and I really hope I can accomplish that.

---

### Post by Pumalite on 2007-07-16
Looks like the drive doesn't have persistence after all. Better install in your hard drive.

---

### Post by danovotny on 2007-07-16
Why do you say it doesn't have persistence? I can change theme, save files, uninstall packages?

---

### Post by Pumalite on 2007-07-16
I might be wrong, but it seems to be loosing configuration. Maybe someone more knowledgeable will  jump in.

---

### Post by Soybean on 2007-07-16
So... you're just going along, browsing the web or whatever... and suddenly, without any other symptoms, your network and keyboard simultaneously stop working? Like, at this point, you could still run a new program using your mouse?

If I'm understanding you correctly, that's *really* weird.

Umm... is it a USB or PS2 keyboard? Not that either of those options is less weird. Oh, if it's USB, you could try unplugging it and plugging it back in, though. Since USB is hot-pluggable, that might get it reinitialized, so at least you could use your keyboard to try to figure out what had just happened.

Beyond that, about all I can suggest is "look through your log files," in /var/log/, but I don't even really know which log file you should look in. There might be some sort of error happening that is causing these problems as a crazy side-effect. :confused: Good luck!

---

### Post by danovotny on 2007-07-16
Your summary is correct, Soybean. The mouse continues to function, and new programs can be opened. It is a USB keyboard, and I have tried unplugging and replugging it back in, which didn't work. I have even had it happen once before at the login screen itself, not allowing me to even type my username in. Is it possbile that is partly due to it being on a USB pen drive, as Pumalite mentioned? I would hate to partition and install on my internal drives if this same thing is going to happen?

---

### Post by Soybean on 2007-07-16
Well, yes, it could be related to the USB pen drive installation. Since that sounds like the most unusual part of your setup, it's even a fairly likely culprit. 

But then, it could also be some crazy other thing that's beyond my ability to imagine. ;) So you might not want to jump straight to the hard drive install.

Have you tried the "Live" install CD? It boots into a slow, but fully functional Ubuntu environment, and it doesn't write anything to your hard drive unless you tell it to install. You could boot that and just mess around with it for a while. If the problem doesn't reoccur, then you're probably safe with a hard drive install. If it does, then... well, it's all that much more mysterious. ;)

---

### Post by danovotny on 2007-07-16
I did have the same keyboard problems in the LiveCD, which is why I had to end up using the alternate, text-based install. I could usually run LiveCD and start the install until it asked me to type in my name, username, etc. At that screen, my keyboard would die.

---

### Post by Pumalite on 2007-07-16
Restart with the basics. Do an Md5sum on your iso. Burn at 4x or less. Check for corruption of CD before install. If you have to download again: torrent better than HTTP or FTP. On the other hand, make sure you don't have loose connections or a hardware malfunction. Good luck.

---

### Post by Soybean on 2007-07-16
Ah... well, in that case, it's probably *not* the USB drive. Curiouser and curiouser. 

So, I'm back to my first suggestion... try to find an error in a log file that might explain this. I'd start with /var/log/dmesg.0 or /var/log/syslog.0 or maybe /var/log/messages.0

Just look for something that sounds like a problem, even if it doesn't seem related to the keyboard or network card. Ideally, try to make a note of the exact time when the keyboard stops working, then reboot and check the logs for something that happened at that time (I think at least two of those files have timestamped entries).

---

### Post by danovotny on 2007-07-16
From syslog around the time of the crash:

BUG: soft lockup detected on CPU#0!

I will try and get the full paste from the log as soon as I figrure out how to get the log on to another PC.

---

### Post by danovotny on 2007-07-16
Also,

When I try to restart I get:

[1766.444000] rt61MlmeEnqueue: full, msg dropped and may corrupt MLME

---

### Post by danovotny on 2007-07-16
Attched is part of my syslog. The lockup on keyboard and internet happened around 18:23.

---

### Post by Soybean on 2007-07-17
Looking around, this seems to be a newish bug, and I'm not seeing much in the way of solutions. However... rt61 is a wireless card driver. Do you have a wireless card in the system, and if so, are you using it? You may be able to temporarily fix this by dropping that driver if you don't need it.

EDIT: I looked into this a bit more, and it does seem to be a known bug with the rt61 drivers. I guess they don't get along with SMP kernels. If you really need your wireless card to work in Ubuntu, it sounds like the CVS rt61 driver from SerialMonkey ([http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)) ought to work. But personally, I'd recommend disabling the driver and sticking to wired networking for a while, if possible.

---

### Post by danovotny on 2007-07-17
I'm currently using my wired ports for internet, although, I would like to switch to wireless at some point.

How would I go about "dropping the driver", or for that matter, temporarily disabling it until I can complie and configure the files from the link you gave me?

Do you think the rt61 device triggers this line (and the lines following it) or is it a separate, unrelated issue?
Jul 16 18:23:28 phoenix kernel: [   89.332000] BUG: soft lockup detected on CPU#0!

---

### Post by Soybean on 2007-07-17
> **danovotny said:**
> Do you think the rt61 device triggers this line (and the lines following it) or is it a separate, unrelated issue?
Jul 16 18:23:28 phoenix kernel: [   89.332000] BUG: soft lockup detected on CPU#0!

It's all the same thing -- it's a bit of an odd situation where the wireless card fails to connect to an AP, so the driver freaks out and partially locks your kernel. 

To disable the driver... you just need to add one line to a config file and save it. Do you think you're likely to have time to do that before your keyboard locks up? Assuming the answer is "yes," you need to edit /etc/modprobe.d/blacklist with root privileges:
```
gksudo gedit /etc/modprobe.d/blacklist
```
In case you're not familiar with gksudo, the password it asks for is just the same password you use to log in.
Add the following line at the end of the file:
```
blacklist rt61
```

Then save and reboot. I *think* that should be all it takes.

If you try installing the CVS driver, you'll probably have to take that line back out to use it. Also, I believe that Ubuntu uses the SerialMonkey driver for rt61, so just applying Ubuntu's automatic updates should eventually fix your driver (whenever the fix works its way into the repositories). At that point, again, you'd have to remove that line to make it work.

---

### Post by danovotny on 2007-07-17
Thanks Soybean! I'll try it tonight when I get home. Even if I don't have enough time to type before things freak out, I have devised a slow, but functional method of typing without a keyboard! I have a file that I can open in gedit and copy and paste characters (even returns!) with the mouse in order to form comman line strings. Sluggish but effective! I'll let you know if this helps at all.

---

### Post by danovotny on 2007-07-17
SUCCESS!

I added rt61 to the blacklist, and the keyboard and internet work like a charm now! This is being posted from Ubuntu! HOORAY!

---

