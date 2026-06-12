---
title: "Running replication or synchronisation between two Ubuntu Servers 23"
date: 2023-12-09
forum: Installation &amp; Upgrades
---

### Post by seccon2 on 2023-12-09
I was wondering if there is a current free solution to replicate or mirror two Ubuntu servers on the same local network (1 at 192.168.1.12, 2 at 192.168.1.13), one being the primary where I do all my installations and configurations, and one secondary that the primary would push  or the secondary retrieve - all changes either immediately or once x period of time? 

Right now they are both guests in a Hyper-V host but that may change. Could use ESXi 8 instead. It is on the same physical machine. 
I realize having them like this is far from ideal, they should be on different physical servers, but it is a first step.

---

### Post by MAFoElffen on 2023-12-09
Been around a long time:
RE: 
[https://ubuntu.com/server/docs/ubuntu-ha-introduction](https://ubuntu.com/server/docs/ubuntu-ha-introduction)
[https://www.particleincell.com/2020/ubuntu-linux-cluster/](https://www.particleincell.com/2020/ubuntu-linux-cluster/)

---

### Post by TheFu on 2023-12-09
Replication for an active server isn't a minor thing.  The solution needs to take into account exactly what each part of the software stack does and have solutions for server-specific aspects.  Blindly copying everything is asking for something that doesn't work.

If there's a DBMS, you'll need to replicate that using DBMS techniques.
If there's an application server, you'll need to see what the normal solution for failover is for that. Are dropping connections fine?  Is forcing users to reconnect allowed?  Are there stateful connections involved? If so, you'll need a tool specific for that somewhere in the stack and it will need to be HA as well.
If there's a webserver, do you want active-active or active-passive setups?  Redundant webservers is the easiest of all these.

For a file server, there are considerations. I replicate my media library to other disks once a day. No RAID involved, because backups are 1000x more important than RAID.  Losing a few files that were modified/added in the last day due to a disk issue is a minor inconvenience.  OTOH, I can't afford to have have 365 versions of backups for large media files, like I do for documents, configs, and smaller files.  Also, I don't backup the OS, just the information to restore the OS within 30-45 minutes to effectively be the same as it was at the backup time (nightly backups).

There is a mix of solutions, optimized for hands off use, data safety, and the ability to bring up a new install onto completely new hardware, if needed.  I have 2 nearly identical systems from a hardware standpoint. In theory, 1 system can run all the software that both systems typically run.  The RAM and CPU load is under 50% on both systems.

On both systems, 
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi       2.7Gi        25Gi        79Mi       2.2Gi        27Gi
Swap:         4.1Gi          0B       4.1Gi

```
and the other:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        12Gi        14Gi        62Mi       3.6Gi        17Gi
Swap:         4.1Gi          0B       4.1Gi
```

The backup storage is in an external array - eSATA connected. Media backups are on USB storage (and often disconnect after a few weeks thanks to crappy USB connections). Both systems have eSATA-PM, so moving the backups to directly connect to the other system should work. I haven't tested it.  I have 1 backup server which is also a VM host for other things.

Anyway, my point is that normal backups and a tested restore process is the first step, before attempting anything HA.  HA gets complex.  I know, my day job was designing HA systems for huge corporations and ensuring they tested their process every few weeks. If you don't actually test it more than once a month, it quickly stops working thanks to the complexity.  We also handled DR failovers.  We had an outage - 8 hrs - in the middle of deploying the system, but before the automatic failover parts were handled.  The customer selected the order for completing the deployment and while they had paid for the services and hardware to provide what they needed, they'd never scheduled that work to be done.  These systems supported over 40M customers and about 25K employees, so downtime had real impacts - 10s of millions in lost wages/productivity after 1 hour of downtime.  Anyway, the gut reaction was to blame IT for the failures, but we'd done everything we were allowed to put the system in place for criticality of that specific system.

Of course, some systems are only needed a few hours a month, for a few people. Those don't have the same criticality and don't need HA.

Transactional financial systems can have millions flowing through them every minute. We'd all be unhappy if we were double billed for transactions due to an IT issue with the transaction processing company.

Free solutions? The answer is "it depends", but probably yes.

BTW, support for all versions of Ubuntu 23.xx either end this month or in June. Do you really want to build this on a non-LTS release? I wouldn't.

---

### Post by seccon2 on 2023-12-12
Its 22.04.3

---

### Post by TheFu on 2023-12-12
> **seccon2 said:**
> Its 22.04.3

That doesn't say anything about the different software running on it.  Blindly replicating programs, settings, DBMS, and data seldom works, if the intention is to have a standby system that can be brought up.  Replicating just file data, if it is a file server-only, can work, however, but not if there's any DBMS involved.  Programs and settings will need to be addresses separately.

About all that blind replication is good for is to restore everything as a blob onto the identical hardware.  If anything in the hardware changes, perhaps a HDD has died, then the restore will fail.

I'd rather not be a historical dentist trying to pull information from someone who has asked for help. Good luck to you .

---

### Post by MAFoElffen on 2023-12-12
@TheFu --

In his first post, the OP mentions he is using Hyper-V, and changes to the idea of Using ESXi...

It all depends on what he means as "Replication"... Because if he is using that term, and talking about Hyper-V, that term used with Hyper-V means something completely different than what we use in Linux and Unix.

In Linux and Unix, when we talk about server synchronization, for databases, we use replication server to sync copies of a database between more than one server. If we talk about fail-over server we talk about mirror servers in cluster so that when a server fails, in automatically switches over to another server in the cluster.

With Hyper-V, replication, how they use that term refers to their product Hyper-V Relica:
> 
Hyper-V Replica is an integral part of the Hyper-V role. It contributes to your disaster recovery strategy by replicating virtual machines from one Hyper-V host server to another to keep your workloads available. Hyper-V Replica creates a copy of a live virtual machine to a replica offline virtual machine.

RE: [https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/manage/set-up-hyper-v-replica](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/manage/set-up-hyper-v-replica)

...which is sort of a virtualized functionality of server clusters... synchronizing servers like as a mirror, but not really as a cluster.

@seccon2 -- I test, verify, and consult on Windows, Linux, and VMware solutions. So I have a fairly open understanding of what people from outside of Linux might be asking about, only because my niche is to try to get them to "work together"... But from what you have said, you are confusing everyone and more information is needed. That would be very helpful here.

I think a more detailed explanation from you, on what your goal "is" would really help us to help you. These very short abbreviated answers are not helping. We all need to be on the same page, with the same understanding of what you want to do.

---

### Post by TheFu on 2023-12-12
For replicating VMs, which I've done lots of times, it is fairly simple, but downtime is required for non-commercial solutions.

a) Dump the VM config file - with libvirt, this is wholly contained in the XML file that **virsh dump {VMname}** will provide.

b) Copy the powered off VM storage - whatever it is - can be any sort of storage - file, LVM, ZFS, whatever - to the new system. Or it could be shared storage that is available to both VM servers, just used exclusively by only 1.

c) Ensure any outside virtual hardware is named the same. If you use ethernet bridges, make the names br0, br1, br2, etc... on both VM hosts. 

d) Push the XML settings file to the other server and import it so the exact same virtual hardware is created there.  If the storage locations "appear" to be the same on both systems, no additional changes are needed. Same for networking, extra storage, RAM, virtual GPUs (if any), and virtual CPUs.  As long as the motherboard model is the same, this migration will likely work.

Again, migrating the storage requires it to be completely quiesced. The way to accomplish this is to shutdown the VM.  If you are good with volume managers, then you could take a snapshot on the running system and replicate that snapshot to the other system.  I'll leave that as an exercise. If you don't already know how to use volume management, that skill can change your IT administration life completely.  At a minimum, it makes backups without any corruption on a busy system possible.  MS-Windows has this idea of "shadow copies" ... in Unix/Linux, we do that using volume snapshots and they aren't automatic.

---

### Post by MAFoElffen on 2023-12-12
In Linux, yes, there's hundreds of ways to do the same kinds of things. I'm sure that the disconnect may be in the understanding of terminology between OS platforms.

Though, when he started talking about
> **seccon2 said:**
> ...or mirror two Ubuntu servers on the same  local network (1 at 192.168.1.12, 2 at 192.168.1.13), one being the  primary where I do all my installations and configurations, and one  secondary that the primary would push  or the secondary retrieve - all  changes either immediately or once x period of time?
That, to me, speaks fail-over cluster.

I agree, that he talks about having both VM Servers on the same physical VM Host. To both of us, that gives him very little "value". Most catastrophic failures of VM Servers are when something either happens with the physical host, or the networking that it is attached to, making the VM's on that machine not-available. So getting around that is to setup a VM Server cluster across multiple Virtual Hosts... Or as Windows Replica does, to replicate the same functionality. Or as You mentioned... Or to automate synchronization between two hosts, wherever they reside, and script a "what to do if you lose a heart-beat" situation...

It sounds like he is looking for solutions for highly-available.

My question is, if currently Hyper-V, and open to EXSi (vSphere) where they would dedicate hardware just for "virtualization" (and nothing else)... Then why not KVM, which has more of a market worldwide, and is more open to growth and scalable possibilities? Without the high costs in M$ and VMware licensing (per core & per VM guest OS). If commercial, I have to factor in the cost of doing business right? Or LXD containers? (He never hinted at what their job was going to be.)

Why? Because you started out with asking this:
> **seccon2 said:**
> I was wondering if there is a current free solution...
Answer: Yes. Many of them. They do not include Microsoft Windows Server nor VMware ESXi, which are not free.

EDIT: The next question to this would be, is this for personal growth and learning? Or is there a commercial and/or real-world requirement you are trying to fulfill?

---

### Post by TheFu on 2023-12-12
> **MAFoElffen said:**
> In Linux, yes, there's hundreds of ways to do the same kinds of things. I'm sure that the disconnect may be in the understanding of terminology between OS platforms.

Though, when he started talking about

That, to me, speaks fail-over cluster.
 

Or slightly delayed replication of a DBMS.  The performance difference between forcing synchronized DB updates to 2 DB servers and having a 10-30 second delay of replay logs send to a second DBMS are impressive.  I've had to do both at work.  Synchronized writes effectively take the client 2x longer.  The 10 second delay replication doesn't impact client-side performance and provides nearly the same safety - not money transaction safety, but it is good enough for most business process transactions.

I have to admit, I've never done either of these things on F/LOSS DBMS, just the major commercial ones - Oracle, DB2, Informix, and a few others that are dead now. If I was going to do it with a F/LOSS DBMS, it would be Postgres.  I've been to some training and they are the only one I trust for and active-standby/failover solution.  No toy DBMS need apply if you need HA.

I don't want to guess what the OP needs. We need many more details or questions if we haven't been clear.

---

### Post by seccon2 on 2023-12-13
I am sorry to have sparked such verbatim discussion and conjectures about my initial post. 

Elaborating a bit on my scenario it is still Hyper-V. I suggested ESXi (8) only because I do know that VMWare have some inherent tools for guest replication, or backup-restore. That is not currently running, but might be an easier way to cope with this. That is in itself, not really a huge issue or depending on any kind of corporate disaster-recovery solutions. I am not a business, but my home network is equally, or more, important to me, although with significantly less resources and finances.

I have a few web apps hosted via Docker and the data gathered is of course increasing over time, so does the need for a relevant backup-restore solution. The Windows Hyper-V OS itself is of course backed up, but since replication requires at least two physical machines, that is currently not possible using Hyper-V functionality. Also looking at more granularity in the backup, reducing file size and increasing availability.  Backup "this" and restore "this" - ignore the rest. 

So that is why I thought it might be more relevant to backup the Ubuntu guests between each other, rather than the entire OS Hosts. As someone already pointed out, even the relevant application directories instead of the entire OS image. But that is another hurdle, I am not very familiar with application directory structure in Linux, Ubuntu. Having used Docker, one might assume just replicating the Docker directory might be enough.

It occurs to me there are other - to me, simpler - options, considering backup solutions like VEEAM works with Hyper-V guests, so that might be a relevant solution, considering they have so called "community editions" as well. That would let me store those on a different host all together.

---

### Post by ActionParsnip on 2023-12-13
Something like lsyncd
[https://www.digitalocean.com/community/tutorials/how-to-mirror-local-and-remote-directories-on-a-vps-with-lsyncd](https://www.digitalocean.com/community/tutorials/how-to-mirror-local-and-remote-directories-on-a-vps-with-lsyncd)

---

### Post by TheFu on 2023-12-13
I've used VEAM with ESX and ESXi.  It is crap. Avoid unless you want to pay $1000.  VMware ESXi toools are all paid addons and VMware just announced they are going 100% subscription plans yesterday.

If you just need to backup files, then just backup files, but if those files are being modified during the backup time, expect file corruption.

---

### Post by seccon2 on 2023-12-14
> **TheFu said:**
> I've used VEAM with ESX and ESXi.  It is crap. Avoid unless you want to pay $1000.  VMware ESXi toools are all paid addons and VMware just announced they are going 100% subscription plans yesterday.

Yeah, well, it's the usual, not to in any way diminish your opinion, I am sure you have good reasons, some say some is crap, other say it's ok. Been nuff years in the business to be mindful. VMWare has the WMUG option, should that happen, unless they scrap that to. 

> **TheFu said:**
> If you just need to backup files, then just backup files, but if those files are being modified during the backup time, expect file corruption.
Oh, yes, backup will be run when activity is zero, if I can determine such time.

---

### Post by TheFu on 2023-12-14
> **seccon2 said:**
> Yeah, well, it's the usual, not to in any way diminish your opinion, I am sure you have good reasons, some say some is crap, other say it's ok. Been nuff years in the business to be mindful. VMWare has the WMUG option, should that happen, unless they scrap that to. 


Oh, yes, backup will be run when activity is zero, if I can determine such time.

Any backup solution that doesn't support versioning and efficiently handle versioned backups isn't worth your time or money.

Using a volume manager, you can take a snapshot to completely quiesce the storage and take the backup of that snapshot. This is the Unix-way. It means the system doesn't need any downtime for backups.

---

