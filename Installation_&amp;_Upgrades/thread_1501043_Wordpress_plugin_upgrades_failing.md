---
title: "Wordpress plugin upgrades failing"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2010-06-03
I'm not certain that my problem is due to an Ubuntu upgrade, but I'm running out of options.

My private Wordpress installation was working fine, including being able to upgrade plugins and WP versions within the application.

I've been doing all of the Ubuntu updates as I'm notified. I'm still on 9.10, but was planning to upgrade to 10.04 shortly - as soon as I get the Wordpress installation upgraded in fact.

But the plugin upgrades, and the Wordpress upgrades, are both failing with fopen errors, like so:

Download failed. Could not open handle for fopen() to [http://downloads.wordpress.org/plugin/XYZ](http://downloads.wordpress.org/plugin/XYZ)

After checking everything else I can think of (including temporarily making the wordpress directory hierarchy 777), and looking at the php.ini file, I wonder if some Ubuntu update is messing things up.  Or if I've somehow changed something else that is causing the problem.

Any ideas greatly appreciated.

Thanks!
Mike

---

### Post by 5circles on 2010-06-14
I found the problem after much effort and help from a couple of Ubuntu gurus.  Ultimately I used strace to dig into the system calls for wget (which worked) and a script with fopen (which didn't).  The issue seems to be that fopen tries to set up a stream for background processing (I'm not sure of the terminology) while wget sets up a stream for immediate download.  

Calls from fopen:
```
socket(PF_INET, SOCK_STREAM, IPPROTO_IP) = 3
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(3, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
connect(3, {sa_family=AF_INET, sin_port=htons(80), sin_addr=inet_addr("pub.lic.ip.add")}, 16) = -1 EINPROGRESS (Operation now in progress)

```

Calls from wget:
```
socket(PF_INET, SOCK_STREAM, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(80), sin_addr=inet_addr("pub.lic.ip.add")}, 16) = 0

```

I "solved" the issue temporarily by connecting the Ubuntu machine directly to the router on the Internet connection.  Previously it had been behind a hardware firewall.  I didn't see any errors in the log of the firewall, so I think it is a Ubuntu configuration issue.  fopen failed even with a local file, which supports this conclusion.

Now I can do what I wanted with Wordpress, but I have a different issue.  I can't browse the LAN by name from either the Ubuntu machine or the Windows computers.  I can ping the Ubuntu machine by IP address from Windows using either one of the IP addresses.  But I can't ping from the Ubuntu machine to the private subnet.

I think I need to clean everything up - probably it is a good time for a new Ubuntu 10.04 install.  So I'm looking for a simple guide to set up a new installation with the right network setup.  I'll search the other categories, but I've never had much luck finding a good guide that worked for me in the past.

---

