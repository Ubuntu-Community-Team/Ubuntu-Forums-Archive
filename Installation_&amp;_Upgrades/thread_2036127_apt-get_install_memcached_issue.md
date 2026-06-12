---
title: "apt-get install memcached issue"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by zenbly on 2012-08-01
Hello,

We have issue to install memcached at Ubuntu 10.4.4 but successfully on apt-get install rsync python-netifaces python-xattr python-memcache

============apt-get install memcached start ============

    root@gplab24:/home/bas/packages# apt-get install memcached
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    memcached is already the newest version.
    0 upgraded, 0 newly installed, 0 to remove and 254 not upgraded.
    1 not fully installed or removed.
    Need to get 0 B/75.3 kB of archives.
    After this operation, 0 B of additional disk space will be used.
    Do you want to continue [Y/n]? y
    Use of uninitialized value $type in ucfirst at /usr/perl5/Debconf/AutoSelect.pm line 35, <> line 1.
    Selecting previously unselected package memcached.
    (Reading database ... 48744 files and directories currently installed.)
    Preparing to replace memcached 1.4.13-0ubuntu2 (using .../memcached_1.4.13-0ubuntu2_amd64.deb) ...
    Use of uninitialized value in subroutine entry at /etc/init.d/memcached line 74, <$etchandle> line 48.
    Can't use string ("") as a subroutine ref while "strict refs" in use at /etc/init.d/memcached line 74, <$etchandle> line 48.
    invoke-rc.d: initscript memcached, action "stop" failed.
    dpkg: warning: subprocess old pre-removal script returned error exit status 255
    dpkg - trying script from the new package instead ...
        ........
        same error loop
============apt-get install memcached end ============

There's empty at var/log/memcache.log.

================ /etc/memcached.conf start ===========
    # memcached default config file
    # 2003 - Jay Bonci <jaybonci@debian.org>
    # This configuration file is read by the start-memcached script provided as
    # part of the Debian GNU/Linux distribution. 
    
    # Run memcached as a daemon. This command is implied, and is not needed for the
    # daemon to run. See the README.Debian that comes with this package for more
    # information.
    -d
    
    # Log memcached's output to /var/log/memcached
    logfile /var/log/memcached.log
    
    # Be verbose
    # -v
    
    # Be even more verbose (print client commands as well)
    # -vv
    
    # Start with a cap of 64 megs of memory. It's reasonable, and the daemon default
    # Note that the daemon will grow to this size, but does not start out holding this much
    # memory
    -m 64
    
    # Default connection port is 11211
    -p 11211 
    
    # Run the daemon as root. The start-memcached will default to running as root if no
    # -u command is present in this config file
    -u nobody
    
    # Specify which IP address to listen on. The default is to listen on all IP addresses
    # This parameter is one of the only security measures that memcached has, so make sure
    # it's listening on a firewalled interface.
    -l 127.0.0.1
    #-1 <PROXY_LOCAL_NET_IP>
    # Limit the number of simultaneous incoming connections. The daemon default is 1024
    # -c 1024
    
    # Lock down all paged memory. Consult with the README and homepage before you do this
    # -k
    
    # Return error when memory is exhausted (rather than removing items)
    # -M
    
    # Maximize core file limit
    # -r
    CACHE_BACKEND = 'memcached://127.0.0.1:11211/'
================ /etc/memcached.conf end =============

Can somebody help me? Appreciate in advance and looking forward to your feedback. :)

---

