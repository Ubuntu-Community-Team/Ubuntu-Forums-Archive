---
title: "mt-daapd"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rubberglove on 2008-10-05
I'd like to ask if anyone has had any luck running mt-daapd on intrepid?

Currently, I have it installed and running. It scans/serves my ~/Music folder just fine (to iTunes on my powerbook, for example), but I cannot get it to work with a password.

the browser-based admin interface won't accept my password (set in /etc/mt-daapd.conf with admin_pw) and iTunes won't connect if I set a password for the music share (using password in /etc/mt-daapd.conf)

In each case, running mt-daapd in foreground mode shows:
```

Entering ws_returnerror (401: Unauthorized)
```

When trying to connect (to the web interface or through iTunes).
commenting out the 'password' setting in mt-daapd.conf allows me to access the share via iTunes.

However, I'd really prefer to have a password on there (as I happen to share my wireless connection with my neighbours).

Am I missing something, or is this a bug, perhaps related to this:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=496217](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=496217)

thanks

Here's my mt-daapd.conf file (minus comments), just in case. It's basically the default, aside from my mp3_dir


```
[general]
web_root = /usr/share/mt-daapd/admin-root
port = 3689
admin_pw = mt-daapd
db_type = sqlite3
db_parms = /usr/var/cache/mt-daapd
mp3_dir = /home/martin/Music
servername = Firefly %v on %h
runas = mt-daapd
#password = mp3
extensions = .mp3,.m4a,.m4p,.ogg,.flac,.mpc
scan_type = 2
[plugins]
plugin_dir = /usr/lib/mt-daapd/plugins
plugins = rsp.so,ssc-ffmpeg.so
[scanning]
process_playlists = 1
 
process_itunes = 1
process_m3u = 1
```

---

### Post by wgrant on 2008-10-05
See [bug #277746](https://bugs.edge.launchpad.net/ubuntu/+source/mt-daapd/+bug/277746) - when that is fixed, this will be.

---

### Post by plun on 2008-10-07
Well, I just checked this and Ubuntus package is stone dead....

Debian Sids package works just fine

[http://packages.debian.org/sid/mt-daapd](http://packages.debian.org/sid/mt-daapd)

Minor trouble with libjs-scriptaculous,   apt-get install -f solved that
 

Freeze stone dead packages...:confused:

---

### Post by wgrant on 2008-10-07
> **plun said:**
> Well, I just checked this and Ubuntus package is stone dead....

Debian Sids package works just fine

[http://packages.debian.org/sid/mt-daapd](http://packages.debian.org/sid/mt-daapd)

Minor trouble with libjs-scriptaculous,   apt-get install -f solved that
 

Freeze stone dead packages...:confused:

Did you even bother to read the only other reply in this thread?

---

### Post by plun on 2008-10-07
> **wgrant said:**
> Did you even bother to read the only other reply in this thread?

Yes and I cannot find any freeze expectation for this package.

Without that,  packages must be removed from a repo.  IMHO


In this case its really confusing because login is blocked to the
Firefly server.

---

### Post by wgrant on 2008-10-07
> **plun said:**
> Yes and I cannot find any freeze expectation for this package.

Without that,  packages must be removed from a repo.  IMHO


In this case its really confusing because login is blocked to the
Firefly server.

That is a confirmed sync request, by an Ubuntu developer. We are not hardfrozen. No freeze exception is required. We also will not remove a package from the archive just because it has a bug for which a fix is known... that would be very stupid.

---

### Post by plun on 2008-10-07
> **wgrant said:**
> That is a confirmed sync request, by an Ubuntu developer. We are not hardfrozen. No freeze exception is required. We also will not remove a package from the archive just because it has a bug for which a fix is known... that would be very stupid.

Ok, thanks....

All software includes bugs and some bugs causes severe trouble..:)

In this case its a "grave" bug.... 


So I installed mt-daapd yesterday evening on my Ubuntu server and couldn't figure out why I couldn't login....](*,)

Then I searched this forum and found the answer....its a bug...:^o


Next test is Mpd on my "Jukebox"....  no LAMP...:)

---

