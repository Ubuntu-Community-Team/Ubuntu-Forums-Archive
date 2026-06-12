---
title: "Problem install and updating"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by davit on 2010-04-05
I seem to be having a constant error with updating 9.10 server of a new install.

It keeps failing on sources list update on

```

root@mine:~# aptitude update
Writing extended state information...Done
..
..
..
Err http://nl.archive.ubuntu.com karmic/universe Packages
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 5,133kb in 8s (575kB/s)
Reading package list ... Done


```

I have tried a lot of different repositories,mirrors apt-get and aptitude and still having the bzip2 error. for over 2 days trying.

I also tried 8.04 LTS (server edition) from Ubuntu disk and this too has problems with finding internet packages.

---

### Post by byStanderone on 2010-04-05
...this might be a bit off topic, but may i know what app you used in downloading your ubuntu installers?

---

### Post by davit on 2010-04-05
I used ftp and torrent.

ON the 9.10 server attempt
I was able to install base system and openssh  (no LAMP or other stuff)
I opened a ssh pipe from another box and tried update the server remotely.

I managed to getof all updates with error attempts

I tried a mix of US, NL and IE server mirrors

All were updated after a few tries but 
except 
universe packages

I have comment out the Sources line in /etc/apt/sources.list for 
unverse packages 

the  apt-get update && apt-get upgrade
is ok

except I now unable to get 
Webmin to install without 

 libnet-ssleay-perl 

this I blieve relies on 
universe packages (which I have comment out for now to trace the problem)

..
still trying

---

