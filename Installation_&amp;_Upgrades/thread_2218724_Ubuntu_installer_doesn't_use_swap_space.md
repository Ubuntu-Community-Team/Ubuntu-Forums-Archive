---
title: "Ubuntu installer doesn't use swap space"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by GigabyteProduction on 2014-04-21
I am trying to install Ubuntu Server 14.04 onto an old laptop that only has 128 MB of ram, but the installer runs out of RAM while loading data from the disk (the step right after setting the keyboard layout). The interface claims it's for an unknown reason, but while looking in dmesg, it complains about running out of space (without specifying what kind of space) and i noticed i only had 5 MB left when using the free command, so i am pretty sure that it's talking about ram, because no drives have been specified for use yet.

I have attempted to make the system use the swap space by:
[LIST]
[*] using swapon with my swap partition /proc/sys/vm/swapiness 
[*]setting /proc/sys/vm/swapiness to 100 (i know this is probably bad, but this was just to see if i could get *anything* to swap) 
[*]setting /proc/sys/vm/overcommit_memory to 2 
[*]setting /proc/sys/vm/overcommit_ratio to 100 
[*]using ```
for i in /proc/*/oom_adj do; echo -17 > $i; done
``` to disable out-of-memory-killer. I'm not even sure if oom killer is used in the kernel build for the minimalistic installer that the Ubuntu Server installation disk and the alternative disks for the other variations use because /proc/sys/vm/oom-kill doesn't exist, but i still used the code above to disable it just in case. 
[/LIST]

After doing the above, my problem persisits. The free command displays that absolutely no swap space was used. Are any of the steps i listed above incorrect? If not, is there any way to make the installer use swap space?

---

### Post by GigabyteProduction on 2014-04-26
Well i found out that setting /proc/sys/vm/overcommit_memory to 2 means not to overcommit at all, i tried using the value of 1 which means to always allow overcommitting, but that didn't work either...........

---

### Post by Bashing-om on 2014-04-26
GigabyteProduction; Hi !

How bout this for a thought.

Pre partition the hard disk(s), and in the partitioning stage set up the swap partition. If I am not mistaken, the installer will use that "swap space" provided on the hard disk.

[INDENT]bet
[INDENT][INDENT]it's worth a shot
[/INDENT][/INDENT][/INDENT]

---

### Post by GigabyteProduction on 2014-04-26
I have a swap space setup already, i need a manual way to initialize it's usage because i can't complete the step where it loads the installation resources from the disk. Some of the resources that includes is the disk partitioning setup, so i ironically can't try this without setting up swap from the start, but it's refusing it use it....

---

### Post by Bashing-om on 2014-04-26
GigabyteProduction; UnGood !

Should not have to do any tweak'n ! Humm.. ok, what does the partition editor 'GParted" see for the hard disk ? Does it see that swap partition ?

Maybe, now just maybe as a thought, in GPARted - if the swap partition is recognized - turn swap on from the editor(?), and then try and install ?

Never mind - Houston we have a problem.
Minimum specs !
> 
 Ubuntu Server (CLI) Installation
300 MHz x86 processor
192 MiB of system memory (RAM)
1 GB of disk space
Graphics card and monitor capable of 640x480
CD drive

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

[INDENT]The times they are a chang'n[/INDENT]

---

### Post by GigabyteProduction on 2014-04-26
i am in what's basically the alternative disk, because it's ubuntu server, so no gparted. swapon also throws errors if the disk isn't swap, and it's not throwing errors for this partition. The partition's also been swap since i installed ubuntu server 13.10. I was also on the page with the minimum requirements, and it even says it's "minimum" includes a set of servers, i'm not using any servers, i'm just using ubuntu server as a router for a vpn, so. I have this all setup with 13.10 and it doesn't even end up requiring swap space. All i need is to get swap to work with the installation disk's instance and i'll be set, because swap works with the final product, i even got a game server to run with 2 gigs of "ram" as a little test with my swap space.

isn't there any way to make swap work? it doesn't make sense that it's ignoring swap and my virtual memory options...

---

### Post by ibjsb4 on 2014-04-26
The mini.iso will install on 64M of ram.  Why not use it?

---

### Post by GigabyteProduction on 2014-04-26
I haven't seen a mini.iso. I was looking for an alternative disk for ubuntu server but didn't find one, so i thought it was already as minimal of an installer as it gets. May i please have a link to it?

---

### Post by Bashing-om on 2014-04-26
GigabyteProduction; Hey ,

Sounds like a plan to me !
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Hopefully that makes you
[INDENT][INDENT][INDENT]good to go
[/INDENT][/INDENT][/INDENT]

---

### Post by GigabyteProduction on 2014-04-26
this is even worse, it doesn't even go to the language chooser when using only 128 mb....

---

### Post by Bashing-om on 2014-04-26
GigabyteProduction; yuk,

Any of the insatll mediums have the memory test option ? - as the desktop install does, I do not recall about the minimal if that tool is included.
Sounds like maybe that memory needs to be tested.

[INDENT]dont know for sure
[INDENT][INDENT]sounds reasonable
[/INDENT][/INDENT][/INDENT]

---

### Post by GigabyteProduction on 2014-04-26
i'm testing all of this in a virtual machine with virtualbox to test if it was anything with the way i was booting it on the laptop since the laptop's disk drive is dying and can't read the entire disk, so it's not a hardware issue.

---

### Post by GigabyteProduction on 2014-04-30
It just hit me with more experimentation that the reason my swap thing with overcommit isn't working for me because the space that the ramdisk uses from the start is the limit, i forgot that linux runs from a ramfs. Does anyone have advice as to reinitializing the ramdisk or append space to it while live?

---

### Post by GigabyteProduction on 2014-04-30
Well I just figured out I can just do a remount with size option set to whatever size I want because I think initrd is loaded as tmpfs which can use swap space, so problem is solved!

I hope this helps other people with the same problem, I doubt a lot of people use systems with 128 MB of ram like I am, though, but there might be.

A summary of what's required:

[LIST]
[*]Swap space must be present before starting this, because you can't create it from the CD without loading the CD components, which is where my case starts by running out of space, maybe if you have a little more ram, you can get past that 1 step without running out of ram and maybe load fdisk with expert mode. 
[*]After booting, go to another shell (another tty might be better, the drop to shell option in the installer acts wierd when wrapping lines) 
[*]Use the code:
```
echo 1 > /proc/sys/vm/overcommit_memory
echo 100 > /proc/sys/vm/overcommit_ratio
swapon device_here
mount -o remount -o size=size_here / ## I used a gigabyte for this, but you can probably use like 192 MB or whatever the system requirements said, have swap prepared.
``` 
[/LIST]

Now you may continue installation normally, it will swap a lot to compensate for low ram if you're in such a low ram case like me.

---

### Post by Bashing-om on 2014-04-30
GigabyteProduction; Wow !

Now that my friend is some good work.
Appreciate that you shared the solution. Regret that I did not have the ability to advise ( a non contributing response is discouraged !).

Again,
[INDENT][INDENT]it just goes to show
[INDENT][INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

