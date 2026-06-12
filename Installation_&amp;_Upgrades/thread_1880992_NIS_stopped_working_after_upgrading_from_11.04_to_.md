---
title: "NIS stopped working after upgrading from 11.04 to 11.10"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by ankurgupta1985 on 2011-11-14
[FONT=Arial]NIS stopped working after upgrading from 11.04 to 11.10

I have a small network which used to run NIS on Ubuntu 11.04 just fine.  After I upgraded the master server to 11.10, every client machine (which  are also slave servers) that was restarted does not recognize usernames in NIS database.  But the client (also slave servers) machines which were not restarted  work just fine. 

I updated and upgraded the master server but it doesn't help. I restarted portmap, which  seems to work. But when I restart nis, it fails to bind to YP server. It  takes 10 very long attempts and then fails in the end.[/FONT] [FONT=Arial]

Setting up nis (3.17-32ubuntu1) ...
 * Stopping NIS services                                                 [ OK ] 
 * Setting NIS domainname to: [deleted]
 * Starting NIS services   
* binding to YP server...                                                
* ....                                                                       
* ....                                                                        
* ....                                                                          
* ....                                                                          
* ....                                                                          
* ....                                                                          
* ....                                                                          
* ....                                                                          
* ....                                                                          
* ....                                                                  [fail] 
                                                                         [ OK ]
  
I checked

$ ps aux | grep rpcbind[/FONT] [FONT=Arial]
root       621  0.0  0.0  27652  1688 ?        Ss   Nov11   0:00 rpcbind -w

and found that rpcbind was running. Then I checked

$ ps aux | grep yp
root      6063  0.0  0.0  12708   640 ?        S    16:02   0:00 /usr/sbin/ypserv
root      6066  0.0  0.0   6452   464 ?        S    16:02   0:00 /usr/sbin/rpc.yppasswdd -D /etc -e chsh
root      6069  0.0  0.0   6328   580 ?        S    16:02   0:00 /usr/sbin/rpc.ypxfrd
root      6076  0.0  0.0  75352  1632 ?        Sl   16:02   0:00 /usr/sbin/ypbind

and found that ypserv was running too. But when I type 
[/FONT][FONT=Arial]$ rpcinfo -p localhost
rpcinfo: can't contact portmapper: RPC: Timed out 
I restarted portmap and still this error persists. Also, checking ypserv gives an error:

$ ypserv_test
localhost: RPC: Port mapper failure - RPC: Timed out

Then I killed the yp processes manually and then restarted nis and checked 
$ rpcinfo -p localhost
   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  48068  status
    100024    1   tcp  33375  status
    100004    2   udp    950  ypserv
    100004    1   udp    950  ypserv
    100004    2   tcp    951  ypserv
    100004    1   tcp    951  ypserv
    100009    1   udp    953  yppasswdd
 600100069    1   udp    956  fypxfrd
 600100069    1   tcp    957  fypxfrd
    100007    2   udp    964  ypbind
    100007    1   udp    964  ypbind
    100007    2   tcp    965  ypbind
    100007    1   tcp    965  ypbind

This time I get the required services but when I try to remake NIS database I get this error.

$ sudo /usr/lib/yp/ypinit -m
Updating passwd.byname...
failed to send 'clear' to local ypserv: RPC: Port mapper failureUpdating passwd.byuid...

So I thought this might be the rpcbind bug due to a separate /var partition ([Bug # 875471]("https://bugs.launchpad.net/ubuntu/+source/rpcbind/+bug/875471")) so I checked the version of rpcbind on my master server.

$ dpkg -s rpcbind
Package: rpcbind
Status: install ok installed
Priority: standard
Section: net
Installed-Size: 196
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.2.0-6ubuntu3.1
Replaces: portmap
Provides: portmap
Depends: libc6 (>= 2.4), libtirpc1, libwrap0 (>= 7.6-4~), upstart-job, lsb-base (>= 3.2-14), insserv (>= 1.14.0-2.1) | file-rc, initscripts (>= 2.88dsf-13.3)
Pre-Depends: dpkg (>= 1.15.7.2)
Conflicts: portmap
Conffiles:
 /etc/init/portmap.conf 9c0fe5de58712169799b161cbcc9b8f2
 /etc/init/rpcbind-boot.conf 73a7b949697222b8d1616334629269be
 /etc/init/portmap-wait.conf 21abf1424012cd65d26fc0b1f6c07181
 /etc/insserv.conf.d/rpcbind 669a5c3a6ffa8b5b5ce263057934d118

The version of rpcbind is 0.2.0-6ubuntu3.1 which should be the fixed version. So this is not the bug. 
Is this a new ubuntu 11.10 bug in NIS or rpcbind. Is there something wrong with my procedures?

[/FONT][FONT=Arial]Many users cannot login into their computers because of this problem. Any help will be very appreciated.[/FONT] [FONT=Arial]

[/FONT]

---

