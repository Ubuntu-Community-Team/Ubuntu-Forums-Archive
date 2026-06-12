---
title: "transmission remote cannot connect"
date: 2019-01-29
forum: Installation &amp; Upgrades
---

### Post by jgw on 2019-01-29
This morning I noticed that my transmission, in firefox, was not connected.  I decided to reinstall transmission-remote, which I did.  I still cannot connect.  Here is my status after opening:
greg@movies:~$ sudo service transmission-daemon start
greg@movies:~$ sudo service transmission-daemon status
&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2019-01-29 10:43:26 PST; 5s ago
  Process: 20863 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=1/FAILURE)
 Main PID: 20863 (code=exited, status=1/FAILURE)

Jan 29 10:43:26 movies systemd[1]: Started Transmission BitTorrent Daemon.
Jan 29 10:43:26 movies transmission-daemon[20863]: [2019-01-29 10:43:26.395] JSON parse failed in /var/lib/transmission-daemon/.config/transmission-daemon/settings.json at p
Jan 29 10:43:26 movies transmission-daemon[20863]: [2019-01-29 10:43:26.395] transmission-daemon Error loading config file -- exiting. (daemon.c:693)
Jan 29 10:43:26 movies systemd[1]: transmission-daemon.service: Main process exited, code=exited, status=1/FAILURE
Jan 29 10:43:26 movies systemd[1]: transmission-daemon.service: Failed with result 'exit-code'.

Here is my .json file:
{
    "alt-speed-down": 50,
    "alt-speed-enabled": false,
    "alt-speed-time-begin": 540,
    "alt-speed-time-day": 127,
    "alt-speed-time-enabled": false,
    "alt-speed-time-end": 1020,
    "alt-speed-up": 50,
    "bind-address-ipv4": "0.0.0.0",
    "bind-address-ipv6": "::",
    "blocklist-enabled": false,
    "blocklist-url": "http://www.example.com/blocklist",
    "cache-size-mb": 4,
    "dht-enabled": true,
    "download-dir": "~/video/nzb/",
    "download-limit": 100,
    "download-limit-enabled": 0,
    "download-queue-enabled": true,
    "download-queue-size": 5,
    "encryption": 1,
    "idle-seeding-limit": 30,
    "idle-seeding-limit-enabled": false,
    "incomplete-dir": "~/video/incomplete/",
    "incomplete-dir-enabled": false,
    "lpd-enabled": false,
    "max-peers-global": 200,
    "message-level": 1,
    "peer-congestion-algorithm": "",
    "peer-id-ttl-hours": 6,
    "peer-limit-global": 200,
    "peer-limit-per-torrent": 50,
    "peer-port": 51413,
    "peer-port-random-high": 65535,
    "peer-port-random-low": 49152,
    "peer-port-random-on-start": false,
    "peer-socket-tos": "default",
    "pex-enabled": true,
    "port-forwarding-enabled": false,
    "preallocation": 1,
    "prefetch-enabled": true,
    "queue-stalled-enabled": true,
    "queue-stalled-minutes": 30,
    "ratio-limit": 2,
    "ratio-limit-enabled": false,
    "rename-partial-files": true,
    "rpc-authentication-required": false,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-host-whitelist": "",
    "rpc-host-whitelist-enabled": true,
    "rpc-password": "",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "",
    "rpc-whitelist": "127.0.0.1",
    "rpc-whitelist-enabled": true,
    "scrape-paused-torrents-enabled": true,
    "script-torrent-done-enabled": false,
    "script-torrent-done-filename": "",
    "seed-queue-enabled": false,
    "seed-queue-size": 10,
    "speed-limit-down": 100,
    "speed-limit-down-enabled": false,
    "speed-limit-up": 100,
    "speed-limit-up-enabled": false,
    "start-added-torrents": true,
    "trash-original-torrent-files": false,
    "umask": 2,
    "upload-limit": 100,
    "upload-limit-enabled": 0,
    "upload-slots-per-torrent": 14,
    "utp-enabled": true	
    "watch-dir": "/home/greg/video/nzb",
    "watch-dir-enabled": true
}

I have been trying a variety of stuff to figure this out and decided to post this before I really screwed something up.  I can run plain transmission with no problem its transmission-demon that is the problem.

Thank you.................

---

### Post by #&amp;thj^% on 2019-01-29
>  JSON parse failed in /var/lib/transmission-daemon/.config/transmission-daemon/settings.json
Seems like a good place to check.
[list][*]Try removing your config files, in case something got corrupted.
[*]Make sure no other Transmission processes are already running.
[/list]

---

### Post by jgw on 2019-01-29
Thank you for the reply!

I thought I had put this in the post.   The failure is in the first watch line at "/h" which doesn't make sense to me.  I did add those 2 lines which has worked in the past.  Somehow no more?   this is very strange to me as its been working flawlessly and then no more.  I reinstalled and changed some stuff in the .json file.  The stuff I changed was to set the rcp stuff - set authentication to false and got rid of the password and name, and set umask to 2.  I think thats pretty much it.  Screwed up - should have made a copy of it before I started screwing around (getting dumb in my old age).  Anyway, I think I will just rename the current file and restart and see what happens.

I think you are telling me that if I remove or rename the .json file it will re create it?

"watch-dir": "/home/greg/video/nzb",
"watch-dir-enabled": true

---

### Post by #&amp;thj^% on 2019-01-29
> **jgw said:**
> 
I thought I had put this in the post.   The failure is in the first watch line at "/h" which doesn't make sense to me. 
:) I'm notorious for not reading all of a post. So if you did, forgive me.;)
> **jgw said:**
> 

I think you are telling me that if I remove or rename the .json file it will re create it?


It should.
BTW Here is mine if needed
```
{
    "alt-speed-down": 50,
    "alt-speed-enabled": false,
    "alt-speed-time-begin": 540,
    "alt-speed-time-day": 127,
    "alt-speed-time-enabled": false,
    "alt-speed-time-end": 1020,
    "alt-speed-up": 50,
    "bind-address-ipv4": "0.0.0.0",
    "bind-address-ipv6": "::",
    "blocklist-enabled": false,
    "blocklist-updates-enabled": true,
    "blocklist-url": "http://www.example.com/blocklist",
    "cache-size-mb": 4,
    "compact-view": false,
    "dht-enabled": true,
    "download-dir": "/home/me/Downloads",
    "download-queue-enabled": true,
    "download-queue-size": 5,
    "encryption": 2,
    "idle-seeding-limit": 30,
    "idle-seeding-limit-enabled": false,
    "incomplete-dir": "/home/me/Downloads",
    "incomplete-dir-enabled": false,
    "inhibit-desktop-hibernation": true,
    "lpd-enabled": false,
    "main-window-height": 517,
    "main-window-is-maximized": 0,
    "main-window-width": 1339,
    "main-window-x": 50,
    "main-window-y": 50,
    "message-level": 2,
    "open-dialog-dir": "/home/me",
    "peer-congestion-algorithm": "",
    "peer-id-ttl-hours": 6,
    "peer-limit-global": 200,
    "peer-limit-per-torrent": 50,
    "peer-port": 51413,
    "peer-port-random-high": 65535,
    "peer-port-random-low": 49152,
    "peer-port-random-on-start": true,
    "peer-socket-tos": "default",
    "pex-enabled": true,
    "port-forwarding-enabled": true,
    "preallocation": 1,
    "prefetch-enabled": true,
    "queue-stalled-enabled": true,
    "queue-stalled-minutes": 30,
    "ratio-limit": 2,
    "ratio-limit-enabled": false,
    "rename-partial-files": true,
    "rpc-authentication-required": false,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": false,
    "rpc-host-whitelist": "",
    "rpc-host-whitelist-enabled": true,
    "rpc-password": "{Snip by OP",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "",
    "rpc-whitelist": "127.0.0.1",
    "rpc-whitelist-enabled": true,
    "scrape-paused-torrents-enabled": true,
    "script-torrent-done-enabled": false,
    "script-torrent-done-filename": "/home/me",
    "seed-queue-enabled": false,
    "seed-queue-size": 10,
    "show-backup-trackers": false,
    "show-extra-peer-details": false,
    "show-filterbar": true,
    "show-notification-area-icon": true,
    "show-options-window": true,
    "show-statusbar": true,
    "show-toolbar": true,
    "show-tracker-scrapes": false,
    "sort-mode": "sort-by-name",
    "sort-reversed": false,
    "speed-limit-down": 10,
    "speed-limit-down-enabled": true,
    "speed-limit-up": 100,
    "speed-limit-up-enabled": false,
    "start-added-torrents": true,
    "statusbar-stats": "total-ratio",
    "torrent-added-notification-enabled": true,
    "torrent-complete-notification-enabled": true,
    "torrent-complete-sound-command": "canberra-gtk-play -i complete-download -d 'transmission torrent downloaded'",
    "torrent-complete-sound-enabled": true,
    "trash-can-enabled": true,
    "trash-original-torrent-files": false,
    "umask": 18,
    "upload-slots-per-torrent": 14,
    "user-has-given-informed-consent": true,
    "utp-enabled": true,
    "watch-dir": "/home/me/Downloads",
    "watch-dir-enabled": false
}
```

---

### Post by jgw on 2019-01-29
OK, I have now gone through the whole thing.  It is the watch line that screws it up.  The reason it screws it up is because I didn't remove the comma from the end of the file when I added the 2 watch lines.  Its only taken me all afternoon to figure out how I screwed it up!  You sent me your file and here is what I did.  First, I removed the existing settings.json and then ran transmission-daemon.  That did create a new settngs.json.  I then started editing it, change by change.  Everything worked.  Then I added the 2 watch lines, without first removing the comma that signaled the end of the file.  It stopped working.  Then I studied on it, then I thought on it, the the light went off and I remembered about the comma.  The tipoff was the status error which kept telling me it was at "/h" - figured it out after reading it about 50 times <sigh>  

Now I have stuff working and I may have even learned something - I have full faith that I will also forget it <sigh>.   

Thanks for your help - I would still be wasting my time without it (really!)

I will mark this one as solved <G>

---

