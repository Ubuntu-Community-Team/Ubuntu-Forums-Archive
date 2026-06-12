---
title: "Squid and SquidGuard Setup Help"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by cypherus on 2005-08-10
Hey,

I am trying to set up a webfilter for myself and am having a hard time doing so.  I setup up the squid and squidGuard config files like a couple of different tutorials online state, but I can't figure out why it's still not blocking.  

I did however look at the logs in /var/log/squid and the only one that has information was cache.log and it says some weird stuff...

Squid Cache (Version 2.5.STABLE8): Terminated abnormally.
CPU Usage: 0.044 seconds = 0.023 user + 0.021 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Memory usage for squid via mallinfo():
        total space in arena:    2112 KB
        Ordinary blocks:         2050 KB      2 blks
        Small blocks:               0 KB      0 blks
        Holding blocks:           196 KB      1 blks
        Free Small blocks:          0 KB
        Free Ordinary blocks:      61 KB
        Total in use:            2246 KB 106%
        Total free:                61 KB 3%
2005/08/10 11:44:30| Starting Squid Cache version 2.5.STABLE8 for i386-debian-linux-gnu...
2005/08/10 11:44:30| Process ID 16430
2005/08/10 11:44:30| With 1024 file descriptors available
2005/08/10 11:44:30| DNS Socket created at 0.0.0.0, port 32783, FD 6
2005/08/10 11:44:30| Adding nameserver 68.87.64.196 from /etc/resolv.conf
2005/08/10 11:44:30| Adding nameserver 68.87.66.196 from /etc/resolv.conf
2005/08/10 11:44:30| Adding nameserver 68.46.144.6 from /etc/resolv.conf
2005/08/10 11:44:30| helperOpenServers: Starting 5 'squidGuard' processes
2005/08/10 11:44:30| User-Agent logging is disabled.
2005/08/10 11:44:30| Referer logging is disabled.
2005/08/10 11:44:30| Unlinkd pipe opened on FD 16
2005/08/10 11:44:30| Swap maxSize 102400 KB, estimated 7876 objects
2005/08/10 11:44:30| Target number of buckets: 393
2005/08/10 11:44:30| Using 8192 Store buckets
2005/08/10 11:44:30| Max Mem  size: 8192 KB
2005/08/10 11:44:30| Max Swap size: 102400 KB
2005/08/10 11:44:30| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2005/08/10 11:44:30| Rebuilding storage in /var/spool/squid (DIRTY)
2005/08/10 11:44:30| Using Least Load store dir selection
2005/08/10 11:44:30| Set Current Directory to /var/spool/squid
2005/08/10 11:44:30| Loaded Icons.
2005/08/10 11:44:31| Accepting HTTP connections at 0.0.0.0, port 3128, FD 17.
2005/08/10 11:44:31| Accepting ICP messages at 0.0.0.0, port 3130, FD 18.
2005/08/10 11:44:31| HTCP Disabled.
2005/08/10 11:44:31| WCCP Disabled.
2005/08/10 11:44:31| Ready to serve requests.
2005/08/10 11:44:31| WARNING: redirector #1 (FD 8) exited
2005/08/10 11:44:31| WARNING: redirector #2 (FD 9) exited
2005/08/10 11:44:31| WARNING: redirector #3 (FD 10) exited
2005/08/10 11:44:31| Too few redirector processes are running
FATAL: The redirector helpers are crashing too rapidly, need help!

Squid Cache (Version 2.5.STABLE8): Terminated abnormally.
CPU Usage: 0.045 seconds = 0.023 user + 0.022 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Memory usage for squid via mallinfo():
        total space in arena:    2112 KB
        Ordinary blocks:         2050 KB      2 blks
        Small blocks:               0 KB      0 blks
        Holding blocks:           196 KB      1 blks
        Free Small blocks:          0 KB
        Free Ordinary blocks:      61 KB
        Total in use:            2246 KB 106%
        Total free:                61 KB 3%
2005/08/10 11:44:34| Starting Squid Cache version 2.5.STABLE8 for i386-debian-linux-gnu...
2005/08/10 11:44:34| Process ID 16441
2005/08/10 11:44:34| With 1024 file descriptors available
2005/08/10 11:44:34| DNS Socket created at 0.0.0.0, port 32783, FD 6
2005/08/10 11:44:34| Adding nameserver 68.87.64.196 from /etc/resolv.conf
2005/08/10 11:44:34| Adding nameserver 68.87.66.196 from /etc/resolv.conf
2005/08/10 11:44:34| Adding nameserver 68.46.144.6 from /etc/resolv.conf
2005/08/10 11:44:34| helperOpenServers: Starting 5 'squidGuard' processes
2005/08/10 11:44:37| User-Agent logging is disabled.
2005/08/10 11:44:37| Referer logging is disabled.
2005/08/10 11:44:37| Unlinkd pipe opened on FD 16
2005/08/10 11:44:37| Swap maxSize 102400 KB, estimated 7876 objects
2005/08/10 11:44:37| Target number of buckets: 393
2005/08/10 11:44:37| Using 8192 Store buckets
2005/08/10 11:44:37| Max Mem  size: 8192 KB
2005/08/10 11:44:37| Max Swap size: 102400 KB
2005/08/10 11:44:37| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2005/08/10 11:44:37| Rebuilding storage in /var/spool/squid (DIRTY)
2005/08/10 11:44:37| Using Least Load store dir selection
2005/08/10 11:44:37| Set Current Directory to /var/spool/squid
2005/08/10 11:44:37| Loaded Icons.
2005/08/10 11:44:37| Accepting HTTP connections at 0.0.0.0, port 3128, FD 17.
2005/08/10 11:44:37| Accepting ICP messages at 0.0.0.0, port 3130, FD 18.
2005/08/10 11:44:37| HTCP Disabled.
2005/08/10 11:44:37| WCCP Disabled.
2005/08/10 11:44:37| Ready to serve requests.
2005/08/10 11:44:37| WARNING: redirector #1 (FD 8) exited
2005/08/10 11:44:37| WARNING: redirector #2 (FD 9) exited
2005/08/10 11:44:37| WARNING: redirector #3 (FD 10) exited
2005/08/10 11:44:37| Too few redirector processes are running
FATAL: The redirector helpers are crashing too rapidly, need help!

Squid Cache (Version 2.5.STABLE8): Terminated abnormally.
CPU Usage: 0.042 seconds = 0.021 user + 0.021 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Memory usage for squid via mallinfo():
        total space in arena:    2112 KB
        Ordinary blocks:         2050 KB      2 blks
        Small blocks:               0 KB      0 blks
        Holding blocks:           196 KB      1 blks
        Free Small blocks:          0 KB
        Free Ordinary blocks:      61 KB
        Total in use:            2246 KB 106%
        Total free:                61 KB 3%

---

### Post by Abhi Kalyan on 2007-01-28
[http://www.ubuntuforums.org/showthread.php?t=320733&highlight=squid](http://www.ubuntuforums.org/showthread.php?t=320733&highlight=squid)

---

