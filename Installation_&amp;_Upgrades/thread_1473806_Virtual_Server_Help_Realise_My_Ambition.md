---
title: "Virtual Server: Help Realise My Ambition"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by varunendra on 2010-05-05
_**Please rename & move the thread to whatever & wherever you  admins/mods find more suitable**_

OK guys, I may or may not  sound incredibly idiot here, but unless someone successfully convinces  me that it is disastrous idea, I'm gonna try it. No matter whatever  number of hurdles come across my way. So please try to help me if you  can't stop me.
I'm searching the net for last two days only to get  even more confused about what specs can suit my needs the best.

I'm  on a network which has to have 12+ terminals. It's P2P network at the  moment, internet being shared among all, but with no internet or file  management. So we can say I've to start almost from scratch.

Now  based upon my limited experience with Win2003AD+ISA2004, i'd like not to  implement 'infection-prone' Win server based networking. But at the  same time, I also like to have ActiveDirectory like advantages, like  centralized user access control & discrete login management.
We  are on a very constrained budget so while running a smooth running &  well-managed network, we also have to save on money.
 I don't want  to implement thin-clients either 'cause they're costlier than a low-end  diskless desktop system & aren't as much flexible.

**_Here's  All I Have_:**

[LIST=1]
[*]6 Core2Duo, 1GB RAM modern Desktops  (HP/HCL)
[*]4 Pentium-D, 256/512MB RAM old Systems (HCL/Lenovo)
[*]1  4-in-1 Shared Printer (HP 3050)
[*]1 Shared scanner (HP5590)
[/LIST]
**_What  We're Gonna Have_:**

[LIST=1]
[*]1 Server (*Hosting Virtual  Machines that would actually act as: Domain-Controller, File-Server  &, if possible, Terminal-Server*)
[*]2+ Terminals (*Desktops*)
[/LIST]
**_What  Our Users Do_:**

[LIST=1]
[*]**6** systems are used for **lightweight  apps** such as IE/Firefox, MS-Word2003, simple image editing tools,  pdf reader, etc.
[*]**3** systems also use **Photoshop/CorelDraw,  Pagemaker-7**.
[*]**2** are used for **multimedia  creation/editing** and thus will have their own local resources.
[*]**1**  would be used by **me** for **experiments/administration** as  well as a **backup server** in case the original server crashes.
[/LIST]
**_Here's  All I Want_:**

[LIST=1]
[*]Active Directory like central login  & access management
[*]Internet access/bandwidth management
[*]Converting  all but the two multimedia systems into  diskless systems to take  benefits of central files & application management & to save on  maintenance. I can use the recovered HDDs into the main server.
[*]On-the-run  backup server to take over immediately in case of a main server crash.
[*]Despite  having diskless systems, taking advantage of CPU & RAM in each  terminal (as opposed to Thin-Clients)
[/LIST]
**_My Plan So Far (The  Craziness Begins)_:**

[LIST=1]
[*]Getting 1 powerful server,  single/double CPU based (you suggest)
[*]Running 3 Virtual Machines  on it simultaneously & seamlessly. (wish to know if it is  practically possible with all the network load)
[*]Of these VMs, 1  would be running server OS (CentOS/ SLES11/ Server2003) acting as a  Domain Controller+File/Terminal Server with shared resources being  located on a seperate physical HDD.
[*]2nd VM would be a backup  server (don't exactly know what it is & whether it has any  significance in my case)
[*]3rd VM would run "Untangle Dedicated  Firewall" with 1GB RAM. With all free components.
[*]Host would be  Ubuntu. Whichever version supports VMs best. Running w/o X-Server or any  unnecessary mods if possible to save on resources, but without  compromising VMs performance.
[*]If required, booting the diskless  terminals off USB stick (even leaving it plugged in) if it can give some  advantage over PXE booting.
[*]Some terminals would still run  WinXP (though I don't know how am I gonna do it).
[*]Maintaining  daily backup of the server VM (in form of archived image) onto a  seperate HDD in my desktop which would be powerful enough to temporarily  handle the server VM + normal maintenance operations (on host) in case  the main "physical" server crashes. (would preferably be a quad core,  single CPU system)
[/LIST]
[SIZE=2][COLOR=DarkRed]**_Finally,  Here Are My Questions_:**[/COLOR][/SIZE]

[LIST=1]
[*]What would be the best  configuration for the server? (I'm in India as you can notice)
[*]Best  configuration for my Desktop I'd be using for my regular works  including experiments on VMs. Would also be a temporary server (restored  server VM) in case of original server crash.
[*]For the above  desktop, I'm currently planning to go with this: *Core2Quad CPU (Q8400  or Q9400), Gigabyte GA-EP45 UD3R motherboard, 2x2GB DDR2 (Transcend or  Simmtronics)*. Please tell me if someone has a better suggestion  (within similar price-range), and if it can be as powerful as 2-CPU  based system (especially on handling 2-3 VMs simultaneously)
[*]Will  it improve performance placing 'Host + Firewall VM' on one HDD, 'Server  VM' on another and 'Shared Resources' on a third one?
[*]Will it  improve security to **not connect server VM to internet** (not  defining gateway) & connecting only to the LAN through Firewall VM?  Especially if, for any reason, I've to run Win Server2003. (In past,  despite using ISA2004, the server was infected)
[*]If I go for a  dual CPU Intel Xeon based server, then is it possible to configure the  server VM such that it can also run flawlessly on a single Quad-Core CPU  based system? (I'm concerned about the step in creating a VM where  we've to select the no. of CPUs it'll use.)
[*]If above is  possible, is it also possible for the virtual server to switch between  single & double CPU modes as and when required? (to take advantage  of both CPUs available in the server)
[*]I'm leaning towards  Dual CPU based system for server 'cause I've an impression that it has  significant advantage over single CPU system especially while running  multiple VMs simultaneously. Is this idea correct?
[*](*Now this  will definitely certify me an IDIOT !*) How can I run XP or Ubuntu on  a diskless terminal ????
[/LIST]
**_End Note_:** My basic idea  behind all this hassle is a low-cost network setup with easy to  backup/restore server.
Being quite confident about my backup plan,  I'm concerned more about performance than stability.

I know even  reading this post thoroughly is gonna consume a lot of your brains &  time, so a lot of thanks in advance to anyone who attempts:p.

---

### Post by gordintoronto on 2010-05-05
You've spec'd out a week's consulting at $1000 a day, in North America.

Question 9: Ubuntu will run just fine from a 4 GB flash drive. Maybe that's cheating on the "diskless" parameter, but it's cheap. It's just a little bit slow. If the diskless computers are also 256 MB, you might want to compare Lubuntu, Crunchbang and Puppy Linux. There are other lightweight variants, but they tend to be less capable.

---

### Post by varunendra on 2010-05-05
> **gordintoronto said:**
> You've spec'd out a week's consulting at $1000 a day, in North America.
That's exactly why I love "Open" source & this forum:grin:

Hey, but u just forgot to rate my craziness !!:grin::grin: I mean how many stars do I deserve????:grin::grin::grin::grin:????

---

### Post by Old_Grey_Wolf on 2010-05-05
You are not crazy.

You need to specify if you are wanting to use all Free Open Source Software or are you willing to pay for Proprietary Software. That will affect your design. For example, Ubuntu Enterprise Cloud does some things while VMware vSphere does others.

Edit: You also don't mention if the computers you have support the Intel or AMD virtual extensions. That affect weather you can run Type 1 or Type 2 Hypervisors.

---

### Post by varunendra on 2010-05-06
> **Old_Gray_Wolf said:**
> You are not crazy.(Sigh of relief..) Thanx.
> You need to specify if you are wanting to use all Free Open Source Software or are you willing to pay for Proprietary Software. That will affect your design. For example, Ubuntu Enterprise Cloud does some things while VMware vSphere does others.
We've already got license for XP Pro & Server2003SBS so we 'can' use them when & if needed. But apart from that, I'm opting for all free software since this is at experimental level for me. Also, we aren't a profit making unit so I don't want to even think of enterprize level commercial software when a free alternative is there.
In short, we can only think of commercial software if it can bring a very significant improvement at a non-significant cost.
> You also don't mention if the computers you have support the Intel or  AMD virtual extensions. That affect weather you can run Type 1 or Type 2  Hypervisors.Our 6 newer systems have Intel Core2Duo E7400 CPU, but I'm not sure if it supports VT-x or not.
But since those are meant to be 'terminals', so I think this has to be considered only in the context of the ones we are going to have as server & backup server. Of these, the one I,ve planned for my Desktop (cum backup server) does support Intel virtual extension. The main server is yet to be planned but that too would be an Intel CPU with VT-x.

---

### Post by Old_Grey_Wolf on 2010-05-06
You may what to look into building a private cloud (virtualization) with Ubuntu Enterprise Cloud. [http://www.ubuntu.com/cloud/private](http://www.ubuntu.com/cloud/private). I set up a cloud on a weekend using it. Oh, it is Free.

---

### Post by varunendra on 2010-05-16
> **Old_Gray_Wolf said:**
> You may what to look into building a  private cloud (virtualization) with Ubuntu Enterprise Cloud. [http://www.ubuntu.com/cloud/private](http://www.ubuntu.com/cloud/private).  I set up a cloud on a weekend using it. Oh, it is Free.
Thanx & sorry for a late response. Actually at first glance, I  couldn't understand what kind of architecture a cloud computing is. I  was more interested in finding a way to run XP from RAM of diskless  computers, snatching preinstalled images from server via PXE. Although  now it seems to be quite a challenge for even experts to do so with 1 GB  RAM (loading only XP kernel in memory and leaving remaining OS files on  a remote file-system is the challenge. I found it is done by Neoware,  but couldn't find how. Neoware isn't free either!)

However, I planned to study your suggestions thoroughly & could only  today find the time for that.
With your link & some googling, what I've understood is that **in  cloud-computing, client computers only "see" and "command" the  applications while the entire workload is shared by a cluster of  dedicated "remote" computers** (i.e., the cloud). Now that is a  problem with me.
We already have some 8-10 PCs which have decent amount of RAM  (512MB-1GB) & P4/Dual-Core CPUs of their own; and** I want to  utilize their own computing power**. I can't  dedicate them to the  'cloud'.

So my idea was to look for a solution where (diskless) **client  computers can share** one (or two- in case of Ubuntu-XP mixed  environment) **read-only kernel image(s) **located on server,  download it to their memory **via PXE**, & then **use remote  file-system** (located on server- NFS most probably) **for their  input-output**.

I haven't got the server yet so couldn't do much experiments. But I'd  surely post here as soon as I make any significant progress.
Thanks for your time!

---

### Post by afarenci on 2010-05-17
I'll be watching your progress.  I recently purchased an HP Elite 9280t (Core i7 920 CPU, 1366 MoBo, 12GB RAM. 1.5TB RAID 0) with the intention of running it as a Virtual Server and emulator for training and evaluations of Cloud Computing/MS Windows Server-Networks/LINUX Server-Networks/TelCom environments (Cisco/Juniper emulation). I'm still using it as a workstation running Ubuntu Desktop 10.04(64bit) having yet to decide on my host OS for Virtual Server.

Can't promise to be responsive on any given week, but why don't you post configurations you want to check out. I'm covered for any in shop MS Server/product.

---

### Post by varunendra on 2010-05-17
Given the attitude of my current **computer illiterate employers**,  I'm  afraid I may have to leave this project since they still haven't come up  with a decision about the purchase of the server or a powerful desktop  for me (even though they've ridiculously held 3-4 short meetings so far  with the sole purpose of coming up with the execution plan for that).  For now, I'll have to wait & see what happens.

> **afarenci said:**
> Can't promise to be responsive on any given  week, but why don't you post configurations you want to check out. I'm  covered for any in shop MS Server/product.
See my first post (***My Plan So Far....***). Actually, my whole  experience about virtualization is now 3 months old (I had a decent  workstation in my previous job, 3 months earlier, but wasn't allowed to  play around with the server or networking there). My current plans are  entirely "paper-plans" so far. A crude & buggy workaround to my  original aspirations maybe:-

[LIST]
[*]**Keep Ubuntu 8.10 or 9.04 the HOST**. These are in examples of  **enabling Direct 3D on guest XP **over VMware. I couldn't succeed  with 9.10 ([see  my thread]("http://ubuntuforums.org/showthread.php?t=1448134"))
[*]First VM is assigned 1GB share of RAM & holds 'Untangle  Dedicated Firewall'.
[*]Second VM holds 'Server 2003 as Domain Controller + ISA server  2004 or 2006'.
[*]Third VM Holds XP with multiple remote desktop sessions enabled ([see  how]("http://www.golod.com/2005/10/enabling-multiple-remote-desktop-sessions-in-windows-xp-professional-and-media-center-edition-2005/")).
[*]Host ubuntu also holds a read-only PXE boot-image of any distro  which can boot clients via PXE & run RDP/RDPV5 remote desktop  sessions on them (to the XP guest)
[/LIST]
 Now enabling multiple remote desktop sessions to the single guest XP may  be a problem due to the domain policies imposed by Server 2k3 domain  controller. If this cannot be overcome by changing domain policies, I'd prefer  to remove server guest & run XP alone in conjunction with Untangle  Firewall guest.

But again, this would violate my original idea of utilizing clients' own  computing power. So this would be a last resolution (if practically  possible at all).

Edit: [Here]("http://openforge.co.cc/archives/2010/04/22/149") is the alternate link for patched termsrv.dll to enable more than 3 simultaneous RDP sessions on XP.

---

