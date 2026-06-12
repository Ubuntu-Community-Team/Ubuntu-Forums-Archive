---
title: "downgrading qemu on Ubuntu 18.04"
date: 2021-07-31
forum: Installation &amp; Upgrades
---

### Post by nataraj88 on 2021-07-31
I believe I was previously running the following version of qemu before the most recent upgrade 2 weeks ago::
 qemu 1:2.11+dfsg-1ubuntu7.36 (Accepted)2/22/21, 8:28 A

On 7/15/21 I installed the following update:
 ubuntu/bionic-updates] qemu 1:2.11+dfsg-1ubuntu7.37 (Accepted) 7/15/21

This update appears to have broken something and I am having problems with all of my VM's hanging.
I would like to downgrade, but the older version of qemu does not appear to be available in the repository:, possibly because the .37
version was issued twice (as indicated in the bionic-changes list)

```
t# aptitude versions qemu
Package qemu:                              
p   1:2.11+dfsg-1ubuntu7                          bionic                    500 
p   1:2.11+dfsg-1ubuntu7.37                       bionic-security           500 

Package qemu:i386:
p   1:2.11+dfsg-1ubuntu7                          bionic                    500 
p   1:2.11+dfsg-1ubuntu7.37                       bionic-security           500 
```

How can I downgrade qemu to the 7.36 version?

Thank You,
Natu

---

### Post by MAFoElffen on 2021-07-31
Please go back and edit your first post and wrap your output with these tags: [ c o d e ] Output_Text [ / c o d e ] ...
...Without the extra spaces I added there to display that to you as an example.

First, take a backup of where it is at now... Before you start making changes, so you have a fallback point.

Then... Please consider making the Canonical/Ubuntu system work for all of us, by reporting that update as a Bug to Launchpad. As a user of Qemu/KVM, that helps all of us.

If for some reason, you can't, or you have a requirement that prevents you from that... Then, well, I understand.

The missing info I see... Well, let me startup my other computer and spin up an 18.04 nested Qemu/KVM Server VM so I can look at it... BRB in another post. Right now, on this machine, I'm on Arm64 and a different release.

So I can look without chasing ghosts, you didn't mention kvm or libvirt, and you are on 18.04... Is your host 64bit or 32bit?

---

### Post by nataraj88 on 2021-07-31
libvirt was not updated during the time frame when the problem began for me (based on checking the bionic-changes list).  I should have mentioned kvm which includes at least linux-kvm and linux-meta-kvm.  Is there an easy way to downgrade an umbrella package like linux-meta-kvm?

---

### Post by nataraj88 on 2021-07-31
Oh yes, my host and VMs are all 64 bit.

---

### Post by MAFoElffen on 2021-07-31
But you installed the package qemu-kvm right?

If I go to an instance of Ubuntu server 18.04 LTS and look at
```
apt policy qemu
```
I do not see the package qemu as being installed in a normal install of qemu-kvm...

Now if I look at 
```
apt poilcy qemu-kvm
```
Now... That shows up as being that version currently... Could you please do that and check?

---

### Post by MAFoElffen on 2021-07-31
curious about what the update broke im your VM Guests?]

---

### Post by MAFoElffen on 2021-07-31
curious about what the update broke im your VM Guests?]

---

### Post by Dennis N on 2021-07-31
qemu is just a metapackage so it's non-functional except to perhaps install something else. The description even says you can remove it. Your problem lies somewhere else.

Why not delete qemu, and upgrade 18.04 to 20.04 and get newer packages? It may fix your problem as well.

---

### Post by nataraj88 on 2021-07-31
You are correct in that neither qemu nor kvm are installed separately.    ```
 $ apt policy qemu kvm qemu-kvm linux-kvm
qemu:
  Installed: (none)
  Candidate: 1:2.11+dfsg-1ubuntu7.37
  Version table:
     1:2.11+dfsg-1ubuntu7.37 500
        500 http://mirrors.namecheap.com/ubuntu bionic-security/universe amd64 Packages
     1:2.11+dfsg-1ubuntu7 500
        500 http://mirrors.namecheap.com/ubuntu bionic/universe amd64 Packages
kvm:
  Installed: (none)
  Candidate: (none)
  Version table:
qemu-kvm:
  Installed: 1:2.11+dfsg-1ubuntu7.37
  Candidate: 1:2.11+dfsg-1ubuntu7.37
  Version table:
 *** 1:2.11+dfsg-1ubuntu7.37 500
        500 http://mirrors.namecheap.com/ubuntu bionic-security/main amd64 Packages
        100 /var/lib/dpkg/status
linux-kvm:
  Installed: (none)
  Candidate: 4.15.0.1097.93
  Version table:
     4.15.0.1097.93 500
        500 http://mirrors.namecheap.com/ubuntu bionic-security/main amd64 Packages

```

I got these package names from the bionic-changes list.  So the package linux-kvm is actually installed and was last updated on 7/5 and again on 7/20, so that would make this package my first suspect.

---

### Post by MAFoElffen on 2021-07-31
I do not see a path backwards, only current and forward... 7.36 does not exist in any of the repo's anymore...

Now... What rpoblems are you having with your guest?

---

### Post by monkeybrain20122 on 2021-07-31
There is no downgrading.  AFAIK the only Linux distros that let you downgrade are Arch and its derivatives (there is actually a utility called downgrade from  the AUR) 

Maybe upgrading your qemu-kvm and libvirt packages will solve your problem. Upgrading the host to 20.04 because of this seems to be massive overkill. I would try this [ppa]("https://launchpad.net/~jacob/+archive/ubuntu/virtualisation?field.series_filter=bionic") first instead.

---

### Post by TheFu on 2021-07-31
I'm on 
```
$ dpkg -l *kvm* |egrep '^ii'
ii  qemu-kvm       1:2.11+dfsg-1ubuntu7.37 amd64        QEMU Full virtualization on x86 hardware
```
Haven't had any issues on either Intel or Ryzen CPUs with any VMs.

The KVM host kernels on 3 systems are:
```
$ uname -r
5.4.0-80-generic

```
that's the HWE kernel.

The guest VMs are almost every supported Ubuntu version and a few EoL Windows systems.

What do the log files show related to warnings and errors on the VM host?  Always check the logs.

**Update:**
I run apt-cacher-ng, but the APT cache doesn't keep packages forever. They automatically expire.  Only have
```
-rw-r--r-- 1 apt-cacher-ng apt-cacher-ng 13176 Jul 17 09:44 /var/cache/apt-cacher-ng/uburep/pool/main/q/qemu/qemu-kvm_2.11+dfsg-1ubuntu7.37_amd64.deb
```
Let me check my system backups for that machine. I don't usually backup /var/ stuff.  Nope.  Nothing from /var/ in the backups. Sorry.

---

### Post by MAFoElffen on 2021-07-31
As an example, the KVM version of KVM in 18.04 is 2.11. This is what TheFu is currently on. He knows KVM inside and out.

In 20.04.2, KVM is version 4.2.1. 21.10 Dev, KVM is version 6.0. These are what I am currently on and testing.

KVM upstream now in dev is version 6.1-beta, which monkeybrains compiled and is testing... KVM releases 6.1 at the end of August. I see that as the version for 22.04.

You now have 3 people here to help you... If you can explain what is going on.

---

### Post by nataraj88 on 2021-08-01
Interesting, I may try the HWE kernel, though my system is a Dell XPS from around 2017.  The problem Iis that the VM's hang and ultimately the whole system hangs, if not during operation of the VM, during system shutdown.  I will gather more info the next time it occurs.

---

### Post by TheFu on 2021-08-01
> **nataraj88 said:**
> Interesting, I may try the HWE kernel, though my system is a Dell XPS from around 2017.  The problem Iis that the VM's hang and ultimately the whole system hangs, if not during operation of the VM, during system shutdown.  I will gather more info the next time it occurs.

Did you check the logs for issues?  There should be *something* in the logs which will provide a hint.  I was able to track down a RAM issue by reviewing the logs last week and about a month before that.

---

### Post by MAFoElffen on 2021-08-01
The logs he is referring to are located at /var/log/libvirt/qemu/<domain_name.>.log ... There should be one log file for each VM Guest you have...

So a soft lockup? Interesting read on this qemu-kvm bug report at launchpad, between response #3 and #15...

LaunchPad > Bug # 1730717 > Some VMs fail to reboot with "watchdog: BUG: soft lockup - CPU#0 stuck for 22s! [systemd:1]"
 = [https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/1730717\](https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/1730717\)

At first you are going to see the title and ask me what that has to do with you... Well, it's tied and intertwined with another Bug Report

LaunchPad > Bug # 1713751 > soft lockup / stall on CPU when shutting down with hwe 4.10 kernel
 = [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1713751](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1713751)

Is not just that kernel, but a range of Kernels... Not saying that is anything like you... but something you said reminded me of these interrelated bugs. And you are on 18.04 ,and I was thinking maybe something setup a perfect storm(?) or not.. Just me always thinking. 

You haven't even looked at "your logs" yet... But if you do see messages in those logs saying "soft lockup - CPU#0 stuck for 22s!"... Well...

---

### Post by nataraj88 on 2021-08-02
The Errors that I'm finding so far in my logs are these (Note this is just a few of each error, edited down )

```

Leaked cluster 253193 refcount=3 reference=2
Leaked cluster 262568 refcount=5 reference=4

ERROR cluster 267915 refcount=0 reference=1
ERROR cluster 267916 refcount=0 reference=1

Leaked cluster 275793 refcount=5 reference=4
Leaked cluster 412410 refcount=5 reference=4

Rebuilding refcount structure
Repairing cluster 250896 refcount=1 reference=0
Repairing cluster 250897 refcount=1 reference=0

```


I took the VM down and ran this:

```
# qemu-img info ubuntu18.04.qemu
image: ubuntu18.04.qemu
file format: qcow2
virtual size: 15G (16106127360 bytes)
disk size: 33G
cluster_size: 65536
Snapshot list:
ID        TAG                 VM SIZE                DATE       VM CLOCK
1         Ubuntu 18.04 initial install      0 2018-04-24 01:16:36   00:00:00.00\
0
153       21-01-22-01               0 2021-01-22 08:21:28   00:00:00.000
156       21-03-22-01               0 2021-03-22 14:11:23   00:00:00.000
159       21-06-04-02               0 2021-06-04 01:52:25   00:00:00.000
160       21-07-16-01               0 2021-07-16 20:11:04   00:00:00.000
Format specific information:
    compat: 1.1
    lazy refcounts: true
    refcount bits: 16
    corrupt: false
# qemu-img check ubuntu18.04.qemu
No errors were found on the image.
245760/245760 = 100.00% allocated, 15.12% fragmented, 0.00% compressed clusters
Image end offset: 60129673216

```

So if the image was corrupt it has been repaired now.

---

### Post by nataraj88 on 2021-08-02
So at this point, I will see if the problem recurs and try to track down more information.  I will also run memtest on my system later tonight.

---

### Post by TheFu on 2021-08-02
> **nataraj88 said:**
> So at this point, I will see if the problem recurs and try to track down more information.  I will also run memtest on my system later tonight.

I use LVM LVs for my VM storage.  The LV is passed as a block device into the VM. libvirt understands how to use an LVM storage pool.  Creating a 50G VM storage area is nearly instant - another reason to use LVM for storage.  Being able to resize the storage while the VM keeps running in 5 seconds is handy too. Too hard to get a perfectly clean backup from a running VM without using LVM snapshots.

File-based VM storage is so ... so ... 2010.  Though I do admit to using it for a few needs, but nothing used in production.

---

### Post by nataraj88 on 2021-08-02
Thank you.  That is a good point.  I do have LVM storage on a few of my VM's that do heavier IO.

---

### Post by nataraj88 on 2021-08-02
> **MAFoElffen said:**
> The logs he is referring to are located at /var/log/libvirt/qemu/<domain_name.>.log ... There should be one log file for each VM Guest you have...

So a soft lockup? Interesting read on this qemu-kvm bug report at launchpad, between response #3 and #15...


The first bug seems to fit the description, but I don't see the errors in the log.  Next time it happens I'll check the logs right away.

---

### Post by TheFu on 2021-08-02
HW errors will be in the hostOS logs.

---

