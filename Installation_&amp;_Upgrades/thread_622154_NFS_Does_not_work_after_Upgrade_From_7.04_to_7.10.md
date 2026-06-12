---
title: "NFS Does not work after Upgrade From 7.04 to 7.10"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by fostersimported on 2007-11-24
Just upgraded from 7.04 to 7.10 but cannot connect to my NFS server, I need some help from experts (only been using Linux 8mths) I have searched all sorts of forums but to no avail. :(

Before I started to investigate the problem this is the line in /etc/Fstab which was working before upgrade.

192.168.xx.xxx:/mnt/Zeus       /home/don/shared-media          nfs


Here is some info to help from the terminal.

don@don-laptop:~$ sudo mount 192.168.xx.xxx:/mnt/Zeus /home/don/shared-media
[sudo] password for don:
mount.nfs: mount to NFS server '192.168.xx.xxx' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.xx.xxx' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.xx.xxx' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.xx.xxx' failed: timed out, giving up

It Timed out, After some research I learnt some new commands:

don@don-laptop:~$ showmount -e 192.168.xx.xxx 
rpc mount export: RPC: Timed out

Now yesterday it was reporting back with somthing like
/mnt/Zeus  192.168.xx.0

Next part i dont really understand (read it on a forum) :

don@don-laptop:~$ rpcinfo -p localhost
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32768  status
    100024    1   tcp  36088  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  32770  nlockmgr
    100021    3   udp  32770  nlockmgr
    100021    4   udp  32770  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  41739  nlockmgr
    100021    3   tcp  41739  nlockmgr
    100021    4   tcp  41739  nlockmgr
    100005    1   udp  32771  mountd
    100005    1   tcp  54359  mountd
    100005    2   udp  32771  mountd
    100005    2   tcp  54359  mountd
    100005    3   udp  32771  mountd
    100005    3   tcp  54359  mountd

Info from server;

don@don-laptop:~$ rpcinfo -p 192.168.xx.xxx
   program vers proto   port
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100000    4     7    111  portmapper
    100000    3     7    111  portmapper
    100000    2     7    111  portmapper
    100005    1   udp    842  mountd
    100005    3   udp    842  mountd
    100005    1   tcp    932  mountd
    100005    3   tcp    932  mountd
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100024    1   udp    674  status
    100024    1   tcp    860  status

Please could some one help NFS is very important to my work, i might have to install 7.04 again.

I need a Fix asap,  I can still access the file through 'Places'>'Network' smb shares but i want NFS to work.

It was working before.

All help is appreciated in advance

Fostersimported

---

### Post by ofb on 2007-11-24
Details please.

Is it only the client that has been upgraded? No changes to the server?

What are you doing, if anything, for firewall? Are you using the Firestarter or Guarddog config GUIs?

The rpcinfo outputs are showing what ports the various NFS related protocols are using. Not necessarily relevant here.

While you're digging around, this is sounding familiar. Memory is suggesting a few people who upgraded (I did fresh install) had to run a command to refresh permission, even though the user had not changed. Have a look for those threads.

Also what's the physical connection? IE, are you using a separate NIC for the LAN, and have you confirmed yet that that NIC is actually enabled after the upgrade?

---

### Post by Jose Catre-Vandis on 2007-11-24
You might try adding a bit more to your entry in fstab:

```
192.168.xx.xxx:/mnt/Zeus /home/don/shared-media nfs rsize=8192,wsize=8192,timeo=14,intr,bg
```

I was using this under Edgy and Feisty and still works in Gutsy

Also, just run through the nfs setup routines on both client and server again just to make sure the nfs server is up and running: 

I use this howto to run several nfs shares on my home network

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

