---
title: "Jaunty Upgrade Broke MPD"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mark76 on 2009-03-31
Apparently something else is using the port (6600) that MPD uses.

What do I do?

---

### Post by cariboo on 2009-03-31
Check to see what service is using the port or change the port in the mpd configuration file. Have a look at the mpd [wiki]("http://mpd.wikia.com/wiki/Configuration")

Jim

---

### Post by Mark76 on 2009-04-01
How do you find out what service is using the port and what ports are available?

---

### Post by DJ_Peng on 2009-04-12
I ended up purging mpd from my system before realizing I just had to pick a new port, and since I changed the port to 6700 I now keep getting permission errors on restarting mpd.
> :~$ sudo /etc/init.d/mpd restart
 * Stopping Music Player Daemon mpd                                      [ OK ] 
 * Starting Music Player Daemon mpd 
failed to stat music directory "/home/peng/Music/Collection" (config line 8 ): Permission deniedI tried to use [Caspar Clemens Mierau's instructions]("http://www.screenage.de/blog/2008/06/10/my-package-of-the-day-mpd-the-music-player-daemon/") but I'm still getting errors.

Here's my Required Paths from my /etc/mpd.conf
```
music_directory        "/home/peng/Music/Collection"
playlist_directory    "/var/lib/mpd/playlists"
db_file            "/var/lib/mpd/tag_cache"
log_file        "/var/log/mpd/mpd.log"
error_file        "/var/log/mpd/errors.log"
```Since I have to use folders on two partitions there are two links in /home/peng/Music/Collection:

[LIST]
[*]/media/WinData/jmh/D_Drive/My_Music
[*]/media/OldUbuntu/peng/My_Music_2
[/LIST]
I tried setting the permissions with
```
$ find /home/peng/Music/Collection -type d -exec chmod 755 '{}' \;
$ find /home/peng/Music/Collection -type f -exec chmod 644 '{}' \;
``` (as I was doing before without any problems) and I'm still getting the permission error. I hope someone can point out what is probably a pretty simple thing I'm missing. For those who want to see my entire mpd.conf I'm attaching it.

---

### Post by BwackNinja on 2009-04-12
Oh, simple. Change localhost to 127.0.0.1 in your mpd.conf

Don't know why that works, iirc, there is a bug report too.

---

### Post by DJ_Peng on 2009-04-12
Nope, that didn't make any difference for me. I still get the "failed to stat music directory "/home/peng/Music/Collection" (config line 8 ): Permission denied" message

---

### Post by BwackNinja on 2009-04-12
That's a different problem than the OP, but I'd try first with an empty directory, then add each symlink individually if that works.

---

### Post by DJ_Peng on 2009-04-15
I ended up completely reinstalling Sonata from Casper's tutorial and undoing some of the changes I'd made recently. It turns out that I had made one fairly small change to how I had created my system links and now everything's working properly. Now if only I could get the Local MPD plugin to stay enabled I'd be all set. Thanks for the assists. It may not look like it but you definitely pointed me in the right direction.

**ETA:** On careful examination it turns out that my MPD is still well and truly borked. I'd love to know what changed between the version I used in Intrepid and the one I use in Jaunty that caused the poor pooch to me so badly molested. :(

---

