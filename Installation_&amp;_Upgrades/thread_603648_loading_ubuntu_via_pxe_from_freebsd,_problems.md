---
title: "loading ubuntu via pxe from freebsd, problems"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by hryamzik on 2007-11-05
Well, I'm trying to boot linux to thin clients using pxe and nfs. From freeBSD 6.2 u see... 

I've found the [_tutorial_:]("https://help.ubuntu.com/community/DisklessUbuntuHowto")

I've tried ubuntu 7.04 and 7.10, so here are the boot screens:
7.04
[IMG]http://pics.livejournal.com/hryamzik/pic/0001tptw[/IMG]
7.10
[IMG]http://pics.livejournal.com/hryamzik/pic/0001wpz9[/IMG]

But nfs tcp works and I could mount nfs partition to my mac with 
```
# mount -o tcp,intr,nfsv3,-w=32768,-r=32768 192.168.7.1:/usr/nfsroot/
```

What permissions do I need on my nfs server? Of couse I've seen linux parameters for exports file (rw,no_root_squash,async) but I'm not sure how to tell them to a bsd server.

First of all here are some of my bsd configs and command outputs:

**/etc/exports**
```
/usr/nfsroot -alldirs,maproot=0
```
So as you can see roots from clients could write, everyone could read. I've tried -public parameter with no effect. So only su have write permissions. :(

**/usr/local/etc/dhcpd.conf**
```
option domain-name "hereisthename";
option domain-name-servers 192.168.7.1, 192.168.7.3;
filename "pxelinux.0";
default-lease-time 600;
max-lease-time 7200;
ddns-update-style none;

subnet 192.168.7.0 netmask 255.255.255.0 {
  range 192.168.7.50 192.168.7.250 ;
  next-server 192.168.7.1;
  option routers 192.168.7.3;
  option root-path "192.168.7.1:/usr/nfsroot";
}
```

**rpcinfo -p**
```
   program vers proto   port  service
    100000    4   tcp    111  rpcbind
    100000    3   tcp    111  rpcbind
    100000    2   tcp    111  rpcbind
    100000    4   udp    111  rpcbind
    100000    3   udp    111  rpcbind
    100000    2   udp    111  rpcbind
    100000    4 local    111  rpcbind
    100000    3 local    111  rpcbind
    100000    2 local    111  rpcbind
    100005    1   udp    787  mountd
    100005    3   udp    787  mountd
    100005    1   tcp    643  mountd
    100005    3   tcp    643  mountd
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
```

**netstat -tl**
```
Active Internet connections
Proto Recv-Q Send-Q  Local Address          Foreign Address        (state)
tcp4       0      0  192.168.7.1.nfsd       192.168.7.8.676        ESTABLISHED
tcp4       0      0  192.168.7.1.4779       192.168.7.249.50029    ESTABLISHED
```

And maybe I should show you some clients configs... Well, they are just the same as in the tutorial, so I'll just «print» fstub file, I'm not sure whether it's correct.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/nfs       /               nfs    defaults          1       1
# /dev/sda1
#UUID=4a98f871-52ef-42ed-ad9f-ffb0411e08a8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
#UUID=9de3f213-17de-44c4-8d49-dc80a96fc4f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Mmm. Any comments? :)

---

