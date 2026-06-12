---
title: "gnome-settings-daemon 60+% CPU"
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Xamiga on 2009-07-28
please help.... 
After many upgrades last night, gnome-settings-daemon is running in a loop - using 60%+ cpu.  I've deinstalled/reinstalled metacity but still same problem.  .xsession-errors file grows at ~ 1 meg/min. 


<code>
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-luWrdF/socket
SSH_AUTH_SOCK=/tmp/keyring-luWrdF/socket.ssh
GNOME_KEYRING_PID=3007

(gnome-settings-daemon:3004): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

** (gnome-settings-daemon:3004): WARNING **: Connection failed, reconnecting...
Window manager warning: Failed to read saved session file /home/al/.config/metacity/sessions/1036360faa2351d254124881813391917600000029410036.ms: Failed to open file '/home/al/.config/metacity/sessions/1036360faa2351d254124881813391917600000029410036.ms': No such file or directory

** (gnome-settings-daemon:3004): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:3004): WARNING **: Connection failed, reconnecting...

same continues forever...
</code>

One min file usage:
<code>
al@alt:~$ ll .xsession*
-rw------- 1 al al 3941298 2009-07-28 14:59 .xsession-errors
al@alt:~$ 
al@alt:~$ 
al@alt:~$ ll .xsession*
-rw------- 1 al al 4903416 2009-07-28 15:00 .xsession-errors
</code>

>> corrected file growth time frame.

---

### Post by Xamiga on 2009-07-28
humm... obviously not how to do code blocks...

---

### Post by psyke83 on 2009-07-28
> **Xamiga said:**
> humm... obviously not how to do code blocks...

Use [ brackets ] instead of < arrows >. The rich-text controls also allow you to automate the process (the CODE box is the hash symbol).

---

### Post by wayne_cat on 2009-07-28
you are not alone ... here is the bug report

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/404340](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/404340)

---

### Post by Xamiga on 2009-07-28
Thanks. I don't have pulseaudio.

---

### Post by psyke83 on 2009-07-28
> **Xamiga said:**
> Thanks. I don't have pulseaudio.

PulseAudio has been included in the GNOME release since 8.04 (Hardy), did you remove it manually?

---

### Post by wayne_cat on 2009-07-28
> **Xamiga said:**
> Thanks. I don't have pulseaudio.

are you sure?

```
root@macbook:~# ps -ef |grep pulseaudio |grep -v grep
rschmitt 19870     1  0 03:33 ?        00:00:00 /usr/bin/pulseaudio --start
rschmitt 19873 19870  0 03:33 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
root@macbook:~# 

```edit: I'm asking ... because ... the people in the bug report have this problem
because they **have stopped or removed pulseaudio**

---

### Post by ronacc on 2009-07-28
after updates this AM gonme-settings-daemon crashed ( along with a couple of other things ) on startup , after update this PM all is fixed .

---

### Post by wayne_cat on 2009-07-28
> **ronacc said:**
> after updates this AM gonme-settings-daemon crashed ( along with a couple of other things ) on startup , after update this PM all is fixed .

this?

[http://launchpadlibrarian.net/29637997/gnome-settings-daemon_2.27.5-0ubuntu1_i386.changes](http://launchpadlibrarian.net/29637997/gnome-settings-daemon_2.27.5-0ubuntu1_i386.changes)

---

### Post by ronacc on 2009-07-28
I don't know , I didn't get the crash when I rebooted after this PM's update and it's not eating CPU either .

---

### Post by wayne_cat on 2009-07-28
> **ronacc said:**
> I don't know , I didn't get the crash when I rebooted after this PM's update and it's not eating CPU either .

My CPU usage is also "healthy" ... maybe we have something in common ... you have not removed pulseaudio?

edit:

What do you think .. seems to be related to "pulseaudio missing"?

---

### Post by crys on 2009-07-29
It seems, that with the recent update of gnome-settings-daemon, pulseaudio was installed too. This seems to have solved the problem with the high CPU load. Because uninstalling pulseaudio again brings back this issue. Pity. Lets see, whether it stays this way.

---

### Post by chrisccoulson on 2009-07-29
> **crys said:**
> It seems, that with the recent update of gnome-settings-daemon, pulseaudio was installed too. This seems to have solved the problem with the high CPU load. Because uninstalling pulseaudio again brings back this issue. Pity. Lets see, whether it stays this way.

It probably won't stay that way - I've just fixed a similar issue with gnome-volume-control-applet too. However, if you remove Pulseaudio, your volume buttons will no longer control the volume. The media-keys plugin requires Pulseaudio to work properly now. This is why the package now recommends Pulseaudio (and why the recent update pulled in Pulseaudio for some people).

---

### Post by ronacc on 2009-07-29
> **wayne_cat said:**
> My CPU usage is also "healthy" ... maybe we have something in common ... you have not removed pulseaudio?

edit:

What do you think .. seems to be related to "pulseaudio missing"?

You are correct I had not removed pulseaudio. I wasn't having audio problems , atleast none that I noticed .I do see that there are several updates to pulse this AM .

---

