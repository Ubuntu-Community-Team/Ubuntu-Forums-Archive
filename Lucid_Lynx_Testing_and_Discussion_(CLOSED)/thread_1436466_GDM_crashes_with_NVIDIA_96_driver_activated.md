---
title: "GDM crashes with NVIDIA 96 driver activated"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jrothwell97 on 2010-03-22
I've installed the the NVIDIA 96 driver through Jockey, and it *sort-of* works. Plymouth's ASCII boot screen works just fine, and it can be beaten into displaying the "pretty" one by setting grub's gfxmode.

However, problems commence once GDM starts: on selecting a user name from the list, it crashes while attempting to draw the password box, bringing down the whole of X with it, and restarting.

I can bypass GDM by tabbing away to a tty, stopping GDM and starting X manually (a fudge which works remarkably well). However, regardless of whether GRUB gfxmode is set or not, GDM still crashes.

Both Plymouth and GDM work fine under nouveau.

Possibly-relevant information:
[list][*]Relevant lspci line:
```
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
```
[*]Relevant stuff from syslog (I've emboldened parts I think may be the culprit):
```
**Mar 22 22:19:25 Bronowski-UL gdm-session-worker[1103]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed**
Mar 22 22:19:25 Bronowski-UL ntpdate[1263]: adjust time server 91.189.94.4 offset -0.434514 sec
Mar 22 22:19:25 Bronowski-UL kernel: [   22.472009] eth0: no IPv6 routers present
**Mar 22 22:19:28 Bronowski-UL gdm-simple-slave[1279]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory**
Mar 22 22:19:28 Bronowski-UL acpid: client 837[0:0] has disconnected
Mar 22 22:19:28 Bronowski-UL acpid: client connected from 1281[0:0]
Mar 22 22:19:28 Bronowski-UL acpid: 1 client rule loaded
Mar 22 22:19:28 Bronowski-UL kernel: [   25.575552] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
Mar 22 22:19:28 Bronowski-UL kernel: [   25.575576] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
Mar 22 22:19:28 Bronowski-UL kernel: [   25.575615] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[B]Mar 22 22:19:30 Bronowski-UL gdm-session-worker[1318]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar 22 22:19:30 Bronowski-UL gdm-simple-greeter[1317]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Mar 22 22:19:33 Bronowski-UL gdm-session-worker[1318]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed[/B]
Mar 22 22:19:35 Bronowski-UL pulseaudio[1109]: ratelimit.c: 3 events suppressed
Mar 22 22:19:37 Bronowski-UL gdm-simple-slave[1337]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar 22 22:19:37 Bronowski-UL acpid: client 1281[0:0] has disconnected
Mar 22 22:19:37 Bronowski-UL acpid: client connected from 1339[0:0]
Mar 22 22:19:37 Bronowski-UL acpid: 1 client rule loaded
Mar 22 22:19:37 Bronowski-UL kernel: [   34.105504] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
Mar 22 22:19:37 Bronowski-UL kernel: [   34.105529] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
Mar 22 22:19:37 Bronowski-UL kernel: [   34.105568] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[B]Mar 22 22:19:38 Bronowski-UL gdm-session-worker[1376]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar 22 22:19:39 Bronowski-UL gdm-simple-greeter[1375]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow[/B]
```[/list]

---

### Post by jrothwell97 on 2010-03-23
No change after today's GDM updates, although I have noticed that dbus-daemon appears to be crashing at around the same time.

(shameless bump) Any ideas?

---

### Post by dino99 on 2010-03-23
That's why testing is funny ;)

i have myself the same warnings but gdm

try to remove/purge gdm package then reinstall & reboot

if it still cant find its conf file, try dpkg-reconfigure gdm

---

### Post by andrek on 2010-03-23
Sorry, but what do you mean by "it can be beaten into displaying the "pretty" one by setting grub's gfxmode."? Would you mind explaining in few words how to achieve that?

---

### Post by jrothwell97 on 2010-03-23
No luck, unfortunately.

I think this is down to one of two things:

[list][*]A bug in the Nvidia drivers (which would explain why it doesn't show up when nouveau is enabled.)
[*]A bug in GDM - my suspicion of which is brought about by this line in syslog:
```
Mar 23 20:18:32 Bronowski-UL gdm-simple-greeter[1274]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
```[/list]

---

### Post by scalawag_ on 2010-03-31
It's strange that this bug only appeared to me today after doing an update this morning, and I've been doing updates everyday since i upgraded from 9.10 to 10.04 beta1.

---

### Post by macstevejb on 2010-03-31
scalawag_: exactly the same situation for me. This only started to happen after installing this morning's updates.

It definitely has something to do with the nvidia drivers.....if I revert to the nouveau drivers, I can login via gdm without a problem.

I found this temp workaround elsewhere:

At the gdm screen:
Ctrl+alt+F2
login with username and password
sudo service gdm stop
startx

not the most elegant solution, but works for now until this matter is resolved.

Regards,

---

### Post by zhangsong023 on 2010-03-31
The same problem here.

---

### Post by ubusheep on 2010-04-01
same here. I'm trying to install the official drivers from the nvidia website.. No luck at all..

Can't we downgrade gdm/nvidia-glx-96 packages someway?

---

### Post by zhangsong023 on 2010-04-01
After the latest upgrading, the problem is still here.

---

### Post by macstevejb on 2010-04-02
oops pls disregard

---

### Post by leeezly on 2010-04-02
Uninstalling "xubuntu-gdm-theme" does solve the problem for me. If your running gnome, maybe there is a similar package ... ubuntu-gdm-theme?

I am gonna wait for a fix before reinstalling it.

Cheers

---

### Post by disco_stew on 2010-04-05
This bug has been affecting me for about the last week as well (GeForce3 Ti 500). I've been doing updates daily, but no luck yet. 

There is at least one other thread [here]("http://swiss.ubuntuforums.org/showthread.php?t=1443520") discussing this same issue. On that one there is a post referencing [bug #553200]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553200"), which seems to be for this issue. So far it has yet to be triaged.

I encourage everyone to comment on the bug report too, to try and get this noticed.

---

### Post by jrothwell97 on 2010-04-05
Thanks, Stew - that was my initial intention with this thread, to gather enough information about exactly what was causing it to be able to file a meaningful bug report.

So yes, *comment on it, subscribe to it, mark yourself as affected, **get the bug noticed*** as this is a potentially major issue if it doesn't get fixed.

---

### Post by dannyboy79 on 2010-04-05
> **ubusheep said:**
> same here. I'm trying to install the official drivers from the nvidia website.. No luck at all..

Can't we downgrade gdm/nvidia-glx-96 packages someway?

official drivers from nvidia website will no longer work at all in lucid. please read changes within lucid:
[http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)
read the part about jocky not supporting the new nvidia alternatives system in place.

---

### Post by jhansonxi on 2010-04-06
See **[bug #553200]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553200")** and if this affects you then subscribe and select the "Does this bug affect you?" link at the top and change status accordingly.

---

### Post by AaronP_ on 2010-04-20
> **jhansonxi said:**
> See **[bug #553200]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553200")** and if this affects you then subscribe and select the "Does this bug affect you?" link at the top and change status accordingly.
This is fixed in 96.43.17 and an Ubuntu package with the update should be out soon.

---

### Post by dannyboy79 on 2010-04-20
i find it weird that if it's the nvidia driver then shouldn't xdm or kdm fail also? cause I just installed xdm and use that for now. no crashing loop with xdm. it must be the relationship between gdm and the nvidia driver.

---

### Post by AaronP_ on 2010-04-20
> **dannyboy79 said:**
> i find it weird that if it's the nvidia driver then shouldn't xdm or kdm fail also? cause I just installed xdm and use that for now. no crashing loop with xdm. it must be the relationship between gdm and the nvidia driver.

Right.  The problem is triggered by a specific sequence of rendering commands that the updated GDM theme uses but that those other display managers or themes apparently don't do.

---

### Post by ubusheep on 2010-04-28
> **AaronP_ said:**
> This is fixed in 96.43.17 and an Ubuntu package with the update should be out soon.

anyone still got the problem? I've running the nouveau drivers now..

---

### Post by jrothwell97 on 2010-04-28
I believe this was fixed with the last update to nvidia-96, so yes, it's working now.

---

