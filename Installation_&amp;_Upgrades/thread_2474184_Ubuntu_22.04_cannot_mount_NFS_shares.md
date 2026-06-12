---
title: "Ubuntu 22.04 cannot mount NFS shares"
date: 2022-04-23
forum: Installation &amp; Upgrades
---

### Post by nocom2 on 2022-04-23
I installed Ubuntu 22.04 on a new partition today. Everything is allright, except that I cannot mount my NFS shares residing on a Qnap server. I can ping and traceroute to that server. I do have normal internet. When I enter:

    mount -t nfs <server>:/files/files /media/i-files 

the command hangs. I installed nfs-common on my client, nothing more.

On my Ubuntu 21.10 client I can mount the NFS shares from the same server. Both 21.10 and 22.04 reside on the same client, but on different partitions.

What am I doing wrong?

---

### Post by TheFu on 2022-04-23
What does **showmount -e <server>** return?

I suspect it is something simple, but I don't have 22.04 yet.  Perhaps in June.

---

### Post by nocom2 on 2022-04-24
I have nfs-common installed but I use nfs4 so there is no showmount (clnt_create: RPC: Program not registered). This reaction is the same on 22.04 as on 21.10 (the working client). However, rpcinfo -p works and its output is:

>    
program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100011    1   udp  30002  rquotad
    100011    2   udp  30002  rquotad
    100011    1   tcp  30002  rquotad
    100011    2   tcp  30002  rquotad
    100005    1   udp  30000  mountd
    100005    1   tcp  30000  mountd
    100005    2   udp  30000  mountd
    100005    2   tcp  30000  mountd
    100005    3   udp  30000  mountd
    100005    3   tcp  30000  mountd
    100003    4   tcp   2049  nfs
    100024    1   udp  30001  status
    100024    1   tcp  30001  status



a mount tinctoris:/files/files /media/files command hangs (well, I terminated it after 10 mins). More things I can do?

---

### Post by TheFu on 2022-04-24
I'll drop a 22.04 server install into a VM somewhere and try out NFS.  I'll likely get sidetracked - busy day here - and I have to wait for the ISO to download from the local university mirror.
**showmount -e** should work for nfsv4. It does here on 20.04 and 18.04 releases.  But until I get 22.04 up, I really don't *know*.

---

### Post by TheFu on 2022-04-24
So, just installed 22.04 server - selected the minimal install.
installed nfs-common, then rebooted. Kernel module, may not have been needed.
showmount -e is working.
 
```
$ sudo mount -vvv -t nfs romulus:/raid/media/VMs /mnt/foo
mount.nfs: timeout set for Sun Apr 24 14:30:16 2022
mount.nfs: trying text-based options 'vers=4.2,addr=172.22.22.4,clientaddr=172.22.22.70'
```

```
$ df -Th /mnt/foo
romulus:/raid/media/VMs  nfs4   1.8T  1.7T  8.5G 100% /mnt/foo
```

I do see permission denied trying to access an NFS share that isn't open to the specific client.

I don't know what else to say. Working.  Romulus is 18.04.  The /etc/exports on Romulus is:
```
/raid/media/VMs 172.22.22.0/24(fsid=3,rw,async,no_subtree_check)
```
And of course, if any change to that file happens, the nfs-server needs to be -HUP'd or use **exportfs -r**

---

### Post by nocom2 on 2022-04-25
Oops,I see my message was not clear enough, sorry. 

I have a qnap server that offers nfs4 to my home network. Ubuntu PC's and Android tablets can access files from the server. On the same PC that runs 21.10 i have created a partition with 22.04 and installed nfs-common. When I try to mount a partion from the server the mount command hangs and as far as I can tell the client does not see the exports while the server can be pinged and tracerouted. I opened ports 111 and 2049 just in case. That nfs-client is not able to access the QNAP server. 

When I switch to the untuntu 21.10 client access is flawless. So what's been changed in Ubuntu 22.04 that nfs4 exports are not recognized even when nfs-common is installed?

Thanks for all your help and sorry for not being very clear in the beginning.

---

### Post by TheFu on 2022-04-25
I think I understood initially, but thanks for the clarification.  

Try using the IP address rather than a machine name for the mounts.  I didn't see any issues connecting using nfsv4.

On my network, I have DNS, so all but the newest clients are resolved through that DNS.  Above, istar and romulus are the NFS servers.  Only the client, u2204-srv, isn't in DNS. It still worked.

I don't have a qnap, so I can only test with the systems I have. They worked.

Can you post the exporrts lines from the qnap and the mount command using -vvv (verbose)? It is hard to guess at issues without seeing any configuration files.

---

### Post by mikkopeiponen on 2022-04-25
> **nocom2 said:**
> I have a qnap server that offers nfs4 to my home network. Ubuntu PC's and Android tablets can access files from the server. On the same PC that runs 21.10 i have created a partition with 22.04 and installed nfs-common. When I try to mount a partion from the server the mount command hangs and as far as I can tell the client does not see the exports while the server can be pinged and tracerouted. I opened ports 111 and 2049 just in case. That nfs-client is not able to access the QNAP server.

I'm having the same issue. Ubuntu 22.04+qnap nas+nfsv4 hangs the mount command. As a workaround, I have switched/downgraded to nfsv3.

Mounting qnap shares over nfsv4 has been working fine with earlier Ubuntu versions (21.10, 21.04, etc)

---

### Post by TheFu on 2022-04-25
[https://forum.qnap.com/viewtopic.php?f=35&p=812661#p812661](https://forum.qnap.com/viewtopic.php?f=35&p=812661#p812661) is what google found. Seems to say that newer Linux kernels aren't compatible with qnap because they include newer versions of nfs.
Setting the mount options from the client side to "**nfsvers=4.0**" seems to be the current workaround until NFS v4.2 is supported by qnap.

Please test and report back if this is the solution.

---

### Post by mikkopeiponen on 2022-04-25
Thanks @TheFu, that fixed the issue for me.

My /etc/fstab after the fix
```

nas001.foo.net:myshare          /mymountpoint     nfs     **vers=4.0**        0       0

```

---

### Post by TheFu on 2022-04-25
Great.  Don't thank me. Thank the qnap forums. They had the solution.

BTW, if you want to up the performance a few %, you can add some other options.  **async,nconnect=2**  Tweak the number based on what works fastest for your systems.  I tested 1 - 16 on mine when I had a dual-core Pentium CPU. I need to retest with the newer 6-core (12 thread) Ryzen in the system now.  NFS really isn't the main purpose for that system. It is a relatively minor aspect compared to the transcoding, media serving, ebooks, backups, and VM hosting that it does. The nconnect option was added with nfsv4. I think it made it into the clients about 3 yrs ago - I know 18.04 clients support it.

---

### Post by nocom2 on 2022-04-25
It works! Thanks @the_fu.

---

### Post by ajgreeny on 2022-04-26
Great news!

Please mark as SOLVED  from the Thread tools menu at the top right of this thread; it's a great help to others searching the forum.

---

### Post by marw85 on 2022-05-19
I had the same issue, but on Ubuntu 21.10 after some updates on 10th of May 2022
Kernel 5.13.0-41-generic
nfs-common 1:1.3.4-6ubuntu1
mount tried nfsvers=4.2 but hang after, adding nfsvers=4.0 helped, thanks!

---

