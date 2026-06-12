---
title: "How much /swap space do I realistically need for m.2 ssd and 16GB 2667MHz ram?"
date: 2024-04-29
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2024-04-29
So still researching dual boot Windows 10 and installing Kubuntu on my computer on a 1TB ssd hard drive and so far am planning of shrinking my Windows partition to 386GB and 64GB for / and the rest for /home. Last part I need to figure out is how much /Swap do I realistically need as my laptop has a M.2 ssd and also 16GB 2667 MHz ram. What would you recommend?

---

### Post by ubfan1 on 2024-04-29
Depends upon your workload and if you want to be able to hibernate. Check if you use any swap with the free command in a terminal when your workload is heavy.  Probably, no swap will be in use. Hibernate writes memory out to disk, so minimum of same memory size for swap.  The old rule of thumb of 2x memory is way overkill now with memory so cheap/plentiful.  I don't think about this too much, but just use a swap partition equal to my 16GB memory.

---

### Post by Omnios on 2024-04-29
> **ubfan1 said:**
> Depends upon your workload and if you want to be able to hibernate. Check if you use any swap with the free command in a terminal when your workload is heavy.  Probably, no swap will be in use. Hibernate writes memory out to disk, so minimum of same memory size for swap.  The old rule of thumb of 2x memory is way overkill now with memory so cheap/plentiful.  I don't think about this too much, but just use a swap partition equal to my 16GB memory.

Thanks for the reply. I find my laptop sleeps and hibernates a lot so will probably use 16GB , with a 1TB hard drive 16GB is not an issue.

---

### Post by MAFoElffen on 2024-04-29
My rule of thumb for swap on customer machines since 10.04 LTS has been 1.5 times the RAM. 

I have done over 2500 Linux installs. I adjust from there based on the expected workload. Example, if I am provisioning a VM to compile something, I might give it a bit more for the just in cases.

I am not a big fan of the recent swap files, instead of a swap partition. I usually install with swap partition. Just a bit harder to change the size of, but performance is better.

I've been around for awhile. The decision for that, I think, was a matter of convenience. I can resize a swap partition, easier than most when they try changing the size of a swap file. No biggie. The end result matters to me.

I do tests and benchmarks, for what I do, to determine the best outcome.

Besides... You have NVMe. You didn't say M.2 SATA or PCIe, big difference. Swap on SSD or NVMe? Very Fast. I do disk caches for SSD's RAID Arrays on M.2 PCIe NVMe...

---

### Post by TheFu on 2024-05-01
Depends on the workload, but the general answer is 4.1GB for a desktop and 500MB for a non-GUI server that has RAM installed for the workload.

OTOH, if you are running a VPS business and want to encourage all your cheap clients to upgrade to a better plan with a dedicated system, then install 8GB of RAM and use 200GB of swap and allow 200+ websites/clients on the single system.

Laptops shouldn't hibernate. It is a security thing.  If you allow it to be in standby mode, that's fine, but never relocate between buildings any laptop while in standby or hibernated.  It is a security thing.  Whenever relocating the laptop, it needs to be shutdown, completely.  It should go without any need to state, but laptops all need full drive encryption.

I don't like swapfiles and only use swap partitions.

About 2-3 yrs ago, there was a long thread in these forums about swap, purpose, and sizing. It is worth reading to get lots of data and opinions.

If you insist on using hibernation, then you are forced to have slightly more swap than RAM. Eeeew. I feel dirty just writing that line.

FWIW, I had a system with 16GB of RAM. I turned down the swap use and was hitting 15GB based on the workload at the time.  It had 4.1GB of swap, so the system wasn't going to crash when just a little more RAM was needed.

IMHO, the point of swap is to allow the users to "feel" that RAM is running out by the system becoming slower.  Really fast storage can make this harder to realize and total memory exhaustion can happen, leading to a system crash.  In Linux, RAM allocations are never validated for performance reasons.  This means that programs are free to allocate and allocate and allocate RAM well beyond what the system has and not be notified about any constraints.  I use Firejail to add RAM constraints to hog processes like Firefox and other modern browsers.  If you look at the requested memory for those programs, I've seen 69GB requested on a system with 16GB of RAM and 4G of swap.  In the end, to prevent this from happening, I set a RAM constraint of 4G for Firefox and it would crash after a day or two.  I moved it to 8G and it would crash after a week.  Moved it to 9GB and it has been stable for years now. How's that for bloat?

One system:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        19Gi       630Mi       101Mi        10Gi        10Gi
Swap:         4.1Gi       2.1Gi       2.0Gi

```
Another system:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi       4.7Gi        22Gi       107Mi       3.0Gi        25Gi
Swap:         4.1Gi       1.0Gi       3.1Gi
```

You can see that one system uses much more RAM than the other.  I sized each so that either one would be able to handle all the workload on all the systems here.

For systems with limited RAM, the rules are different, but for 2GB, 4GB, 8GB RAM systems, 4GB of swap seems to be required if you use modern browsers. Less than 4GB swap and those low-RAM systems lock up far to frequently.

IMHO.

---

### Post by MAFoElffen on 2024-05-02
As I said-- I am the same, in thought with using swap partitions, instead of swap files.

I hibernate/put to sleep, my laptops... But for those, I setup encrypted swaps, to get around my security concerns for those. That is not hard at all to setup.

I do circumvent the 1.5x rule-of-thumb swap size for my Server and Workstation. Both have 128GB RAM. Disk 'is' comparatively cheap now-a-days, but, 1.5x times those would be complete overkill. I do have a some sense of reality. (LOL)

---

