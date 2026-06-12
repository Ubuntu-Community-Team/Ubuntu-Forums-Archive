---
title: "Ubuntu 10.04 (Lucid) boot failed after upgrade on Sony Vaio"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by marciotavares on 2010-07-25
Hello everybody,
 
I upgraded from Ubuntu 9.10 to 10.04 (Lucid), last friday (23/jul), and, after a couple of hours, the system asked me to restart and then nothing happened. The system hangs at boot time, splash screen, but no relevant error messages appeared, on normal boot or recovery mode.
 
For the last 3 days, I have been trying to find some information about this, maybe someone with the exact same problem (after all Lucid was released three months ago), but it is currently very difficult. I did find some people with similar problems and different machine configs, and that did not help me at all.
 
I have a Sony Vaio model VGN-FW270AE, a model sold in brazilian market, with the following configuration:
 
- Intel Core 2 Duo P8400 processor
- ATI Mobility Radeon HD 3470 video adapter
 
There were a few short messages indicating some problem with the network interfaces. When pressing Ctrl + Alt + Backspace at splash screen, I can see the following short messages:
 
```

fsck from util-linux-ng 2.17.2
/dev/sda6: clean, 835790/12836864 files, 32540768/51315618 blocks
init: network-interface (eth0) pre-start process (559) terminated with status 1
init: network-interface (eth0) post-stop process (568) terminated with status 1
init: network-interface (lo) pre-start process (647) terminated with status 1
init: network-interface (lo) post-stop process (649) terminated with status 1
init: network-interface (wlan0) pre-start process (750) terminated with status 1
init: network-interface (wlan0) post-stop process (754) terminated with status 1

```Then, the cursor keeps on blinking, but the system activity stops completely. Other terminals are still accessible, but I can't do anything on them.
 
I googled this network "start/stop" issue and I found a known bug ([https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/512253](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/512253)) with some startup procedure on Lucid. After fixing the "problem" as stated on Launchpad bug and tried to boot Lucid again, but unfortunately I got the same behaviour, this time without network interface error messages. Something like that:
 
```

fsck from util-linux-ng 2.17.2
/dev/sda6: clean, 835790/12836864 files, 32540768/51315618 blocks

```With the same blinking cursor and no further activity.
 
After that I noticed an error message quickly appearing and disappearing when choosing normal boot on Grub:
 
```

mount: mounting none on /dev/pts failed: Device or resource busy
Starting up ...

```This message does not appear when choosing recovery mode. Unfortunately I did not find any important information about that "mount" issue.
 
Another thing that caught my attention was a message appearing when I press Ctrl + Alt + Del, after system activity stops:
 
```

Checking for running unattended-upgrades: * Asking all remaining process to terminate...
* All processes ended within 1 seconds....
* Deconfiguring network interfaces... [OK]
* Deactivating swap... [OK]
* Unmounting weak filesystems... [OK]
* Will now restart

```I don't know whether this "unattended-upgrades" is good or bad. It was another thing I did not find any important information about, but I think it's worth mentioning.
 
Besides that I have found some information about problems on certain types of video cards, with suggestions to add parameters to Grub boot lines (nomodeset, radeon.modeset=0, acpi=off, noacpi ...), and other minor suggestions that unfortunatelly did not solve my problem.

I'm sorry for the long report but **this is a very very very annoying situation** and it's greatly frustrating not to have any concrete sign of solution. It seems to me that this problem will be solved with a simple solution, but it's beyond my reach at this moment. At least I know my data is safe, but it's taking forever and I can't wait any longer.
 
In case anyone have any important information that could help me solve this huge problem, I appreciate it.

---

### Post by marciotavares on 2010-07-28
Hello guys, here I am again. Sorry for bringing this post back to the top, but I want to give you some report.

After  almost 5 days searching for a solution to my problem, I am giving up. I  tried almost "everything" possible, I have read thousands of bug  reports of similar problems, a lot of articles, tons of suggestions and  I'm very tired of all this. I'm very frustrated with this situation and I  think it's a shame for a big product like Ubuntu to have a critical  problem like that without a feasible solution for such a long time.  Unfortunately I have noticed I'm not the only person sharing this  opinion.

Just to let you know, the last couple of things I tried to solve  this problem involved configuration of tools like plymouth, mountall,  upstart and udev. Just to mention a few of them, last night I removed  config files of plymouth from the system (following a specific  suggestion), which successfully stopped it from loading at boot time,  but the system behaviour was still the same. After that, I activated a  "verbose" option of mountall, to see what was happening, but nothing  wrong appeared, neither at boot time nor on log files.

By now the only thing I think can be some kind of clue is something  about mountall trying to automatically mount my Windows partition (which  is not listed in fstab, but is listed in Grub) and maybe that's what is  leading the system to hang. But with the lack of information (as I  said, there's nothing wrong on the logs) I'm not sure if it's really a  problem and, even if it is, I have no idea on how to figure out this  problem and I'm giving up on trying.

Next weekend I'll prepare my machine to do a clean and fresh  install, although I was avoiding it with all my forces, since I have a  lot of apps and tools installed and I'm very lazy to do all that  configuration again :)

---

### Post by P4man on 2010-07-28
One thing you could do (and probably should have done before upgrading) is simply booting a 10.04 livecd to verify everything works with the new kernel and the rest.

---

### Post by marciotavares on 2010-07-28
> **P4man said:**
> One thing you could do (and probably should have done before upgrading) is simply booting a 10.04 livecd to verify everything works with the new kernel and the rest.

Yeah, you're right, I should have used some method to assure nothing wrong could happen, although Lucid LiveCD works almost fine on my machine, and that's the way I'm using to copy my personal data before formatting the HD. I've read somewhere this problem is specific of upgrade processes. Fresh installations are working well as far as I've read.

Anyway, it looks like the upgrade process is not safe at all. It seems to me that there's always a risk of something going very wrong with the upgrade and I personally think this is a very very serious issue, even more for that particular feature, whick I think is very important for the growing adoption of non-technical users. It should be transparent and fail-safe for everybody, but it's not.

I've seen a lot of technical users, hard users, server and network maintainers (in other words, people that deal with very complex situations daily) struggling with this problem, launchpad users and maintainers almost fighting each other (that's surreal to me)... what could we imagine a non-technical user would do on a situation like that? He will probably format his machine and install Windows. Or will buy an Apple machine. Simple like that. He doesn't care about philosophical and technical stuff... he only wants his machine working to do his job and there's a high risk of some upgrade to prevent that.

I'm sorry for dumping my frustrations here, I'll not stop using Ubuntu because of that, but I think this problem and its consequences are serious enough and deserves a mention here. Canonical should carefully look at this problem to prevent its image and Ubuntu's one from being scratched.

---

