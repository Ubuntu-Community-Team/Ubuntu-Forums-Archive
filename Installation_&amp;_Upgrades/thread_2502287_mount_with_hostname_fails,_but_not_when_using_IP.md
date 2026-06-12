---
title: "mount with hostname fails, but not when using IP"
date: 2024-11-08
forum: Installation &amp; Upgrades
---

### Post by folmilsch on 2024-11-08
Hey y'all,

I have a problem with mounting an NFS share when using the hostname. There is no problem to connect to the share, when I use the direct IP address. **Establishing the connection via the hostname worked beforehand **(and with beforehand I mean yesterday).

My system credentials are:
Operating System: Ubuntu 22.04.5 LTS              
          Kernel: Linux 5.15.0-125-generic


Here is the problem:
Using mount with a hostname
```
$ sudo mount -v -t nfs -o "user=myusername" hostname:nfs_share target
mount.nfs: mount(2): Operation not permitted
mount.nfs: trying aaa.bbb.ccc.ddd prog 100003 vers 3 prot TCP port 2049
mount.nfs: trying aaa.bbb.ccc.ddd prog 100005 vers 3 prot UDP port 300
mount.nfs: mount(2): No such file or directory
mount.nfs: Operation not permitted
mount.nfs: timeout set for Fri Nov  8 12:54:35 2024
mount.nfs: trying text-based options 'vers=4.2,addr=aaa.bbb.ccc.ddd,clientaddr=xxx.xxx.xxx.xxx'
mount.nfs: trying text-based options 'addr=aaa.bbb.ccc.ddd'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: prog 100005, trying vers=3, prot=17
```

Same command, but with an IP address.
```
$ sudo mount -v -t nfs -o "user=myusername" aaa.bbb.ccc.ddd:nfs_share target
mount.nfs: timeout set for Fri Nov  8 12:54:34 2024
mount.nfs: trying text-based options 'vers=4.2,addr=aaa.bbb.ccc.ddd,clientaddr=xxx.xxx.xxx.xxx
```

Additional infos: pinging the hostname works, nslookup works. I have no access to the server with the NFS share. 

Does anyone have an idea where I should start to investigate?

Cheers,
Renato

---

### Post by TheFu on 2024-11-08
If both sides of the NFS client/server have different answers for the hostname, then it won't work.  I've seen this when I incorrectly setup or forgot the set the local domain on the system or in DNS.

I've never seen -o "user=myusername" with NFS before, but I've only been administrating NFS since 1993.

Does **showmount -e** work from the client to the  NFS server?

Lastly, sometimes systemd doesn't run all the needed dependencies, so check that the NFS server is actually running the 3-4 daemons required for NFS to work.

---

### Post by folmilsch on 2024-11-08
Thank you for your response! You are hopefully the one able to help me! :)

> **TheFu said:**
> If both sides of the NFS client/server have different answers for the hostname, then it won't work.  I've seen this when I incorrectly setup or forgot the set the local domain on the system or in DNS.
As mentioned in the description, mounting the share (done via PAM mount) worked perfectly fine since the last restart. From our side there was no direct setup process done in that period of time. If I want to check the actual setup, how should I do this? Do you have an advice for me? 

> **TheFu said:**
> I've never seen -o "user=myusername" with NFS before, but I've only been administrating NFS since 1993.
The mounting of the NFS share is   actually done during PAM mount and, unfortunately, I am in the middle of  self-teaching how to deal with the client side Ubuntu system. You are  definitely right that "-o ..." is not correct and I used it without thinking to much. 

> **TheFu said:**
> Does **showmount -e** work from the client to the  NFS server?
Yes, my IP address is listed.

> **TheFu said:**
> Lastly, sometimes systemd doesn't run all the needed dependencies, so check that the NFS server is actually running the 3-4 daemons required for NFS to work.
I think, but I am not perfectly sure, that the NFS mount is served from a Windows system. It was assured to me that it is running fine. There are other clients as well and they do not have such problems.


So again thank you and hoping to hear from you soon!

Cheers

---

### Post by yancek on 2024-11-08
If i understand your post, you are using nfs as a client and at some other computer or location there is a server which may or may not be using windows??
Nfs can work with windows but is not commonly used, instead samba is.  The first link below is a tutorial on setting up both the nfs client and server and you might review it to see if there are thing they did which you did not or vice versa.  If I understand your situation, you only have control of the client end, correct?  The 2nd link is dealing whith hostname resolution on the server end.

[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-22-04)

[https://www.ibm.com/docs/nl/aix/7.1?topic=nfs-host-name-resolution-server](https://www.ibm.com/docs/nl/aix/7.1?topic=nfs-host-name-resolution-server)

---

### Post by TheFu on 2024-11-08
> **folmilsch said:**
> Yes, my IP address is listed.
That's  could be the issue.  Inside the exports file, I use specific FQDN, not subnets.
Can you verify that the answer for each system for ```
hostname --long
```
matches what you are seeing in the exports file?

> **folmilsch said:**
> I think, but I am not perfectly sure, that the NFS mount is served from a Windows system. It was assured to me that it is running fine. There are other clients as well and they do not have such problems.

In the mid-1990s, a project I was on migrated off NFS Servers from Netware which we had ZERO issues with, to NFS on UNIX which worked excellent, to NFS on MS-Windows, which had no end of issues.  Bad support, bad software, slow performance, too many manual updates to keep the Unix and Windows user mappings sync'd, etc. It was a pain.

Around that time, I did run NFS clients on MS-Windows desktops and that worked well enough, but the server just sucked.  To be fair, MSFT NFS was pretty new at the time and our NFS servers were the only non-UNIX systems allowed on the network. It was an air-gapped network for about 2000 systems.

Did you check that all the processes needed to be running on the NFS server were?  I assume most of the clients are Unix/Linux, so can you check with other admins that aren't having issues?

---

