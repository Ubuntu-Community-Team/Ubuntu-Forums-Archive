---
title: "Instability with 14.04 Server on Asus A8V-VM motherboard"
date: 2015-01-01
forum: Installation &amp; Upgrades
---

### Post by lgarfiel on 2015-01-01
I've a home-built computer, about 9 years old save for the hard drive(s) which are brand new.  Athlon 64 2 GHz.  All of the parts are built onto the motherboard, as it functions primarily as a headless server.  The motherboard is an Asus A8V-VM (no SE or other suffix that I can see):

[http://support.asus.com/download.aspx?SLanguage=en&p=1&s=21&m=A8V-VM&os=&hashedid=gxG8gfPAL8pSnNn6](http://support.asus.com/download.aspx?SLanguage=en&p=1&s=21&m=A8V-VM&os=&hashedid=gxG8gfPAL8pSnNn6)

It was previously successfully running Ubuntu 12.04.  I am trying to install Ubuntu 14.04 on it (kernel version 3.13.0-43).  However, sometime after booting one of a couple of different symptoms will manifest, in order of frequency:

- The networking stack will simply fail silently. No error message, it just will stop responding to network requests and running dhclient has no effect or output.  This usually happens when transferring large (multi-GB) quantities of data (which will be the computer's primary function).

- Kernel panic, with the backtrace mentioning SCSI and IRQs.  (We confirmed that the hard drive and networking were not using the same IRQ.)

- "Recursive error detected", and handled, but an instruction I need to reboot.

We have confirmed that with an older version of Linux (via bootable CD) it will transfer data just fine.  We have also attempted to use the same Ubuntu 14.04 on another system (a Dell Optiplex Core2 Duo desktop), which was also fine.  The symptoms hold true whether in a RAID configuration or not.  (I have tried both, as someone in IRC suspected it might be a RAID-related issue.)

The working theory is that there is some newly-introduced incompatibility between the latest kernel and one of the on-board devices, although we have not been able to determine which one. Obviously networking and the SATA controller are the obvious suspects.  I have attached the output of lspci below to identify the hardware in question.

Some Googling turned up the following bugs that seem related, but their lack of resolution does not give me hope:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1269412](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1269412)
[https://lists.launchpad.net/kernel-packages/msg85055.html](https://lists.launchpad.net/kernel-packages/msg85055.html)

Any suggestions, other than randomly buying add-on cards and trying them until one of them seems to work?  I fear I may be SOL.

---

### Post by MAFoElffen on 2015-01-01
You know... I had a problem like this on one of my servers... Would come up with an intermittent NMI during big disk writes. 24 GB ECC registered memory... ended up being that it was a bad stick. Ran fine until it got to a big disk write and used enough memory to hit that stick. That is where I would start testing.

How much install RAM and what do you have your Swap set to. How does the paging look during that?

Had another IBM Server, where it was a BIOS challenge between itself and a certain brand of HBA fiber channel card. That only started between 12.04LTS and 14.04LTS. It too would say that it was a "recursive error." IBM told me that a system BIOS firmware update would fix it, Ended up changing that card out and it works fine now. Funny thing is that during that challenge, I tested it with Win 2008 and Win2008R2... and it had that same error between those versions on that server. The way I found that was, 1st I tested the memory (because the above had just recently happened to me), then I pulled all the boards off the system/bare boned... It worked fine, so I added boards back until I found which one was causing the problem.

*** A Moderator should move this to the "Server Section", so it can get the exposure it needs, there. (Appropriate feedback and better exposure to the hardware and OS to you...)

---

### Post by lgarfiel on 2015-01-01
2 GB RAM, 4 GB swap.  As I said, with an older boot CD I was able to copy over 200 GB over the network without a hitch.  

I can't pull things off the boad as it's all integrated on the board.  There's no add-on cards at all; everything's on-board.  (It's a server, so as long as it has gigabit ethernet and VGA output I don't need anything else.)

There is apparently a BIOS upgrade for this motherboard from many years ago (2007 I think), but nothing since. It's a .exe file, though; not sure if it's Windows or DOS, and I don't have a DOS-bootable disk around anyway. :-)  (And no floppy drive.)

(I'm fine moving this thread to wherever makes sense.)

---

### Post by MAFoElffen on 2015-01-01
Probably dos or WIn Server 2003. What I do for my firmware updates on my Linux servers, is I keep  a PLOP boot CD disk around so I can use a WIN2003 bootable USB stick. I also made a DOS bootable USB Stick. I copy my firmware updates to those USB sticks.  For some of those, I've setup my grub menu with a custon menu item to boot an ISO file, just to do firmware updates from USB. You can do most the same with a more recent Win boot disk, but some firmware updates look for DOS utils of flavor command.com instead of cmd.exe...

Yes, less than half my servers have a floppy drive and most are old enough that they don't boot from USB. But all of those still have USB ports.

---

### Post by MAFoElffen on 2015-01-01
Getting the firmware up-to-date is always good, But... I'm going back on what I said-- The second bug report seems to the same as yours. Since seeing that, I checked on the specs on your motherboard and the On-Board NIC chipset... Then did a Google on "Realtek 8201CL PHY TX timeout error" Many owners seem to be plagued on both Windows and Linux. So not just common to Linux alone. Seems more a hardware issue?

That doesn't look like good news does it? I would suggest, since it is bare already, dropping a name-brand NIC card in it and seeing if that corrects it.

---

### Post by lgarfiel on 2015-01-01
OK, more data!  I purchased a new gigabit PCI NIC at the nearest computer hardware store.  The chipset on it is a Realtek RTL8169.  (It seems most things are Realtek something.)

I installed it and disabled the onboard NIC in the BIOS, then did a fresh install of 14.04.  After setup was complete and apt updated with everything and rebooted, I tried to copy the same big wad of data as before over rsync-ssh.

This time, I got the following error showing on the console (not over the network), which was sitting idle:

-----
EXT4-fs error (device sda1) in ext4_reserve_inode_write:4902: IO failure
Aborting journal on devices sda1-8
Remounting filesystem read-only
EXT4-fs error in ext4_dirty_inode:5021: IO failure
Detected aborted journal
-----

(There's a few other lines but those are the key ones.)

Funny story... the remote system (that was running the rsync) kept on copying for several more files(!) for several minutes before finally stopping with an rsync error.

So, um, what just happened?  The file system driver flipped out now? Why?  Does that mean the issue isn't the NIC?

---

### Post by MAFoElffen on 2015-01-01
Hmmm-- so before it was dropping the network layer... and it seemed that historically the onboard NIC was known for that...

But now the network layer is fine, you found a filesystem error. It could have been that previously the network layer timed out because the filesystem failed and the pipes backup until the network timed out (on a chipset that was already know to have TX timeout challenges)... But your network layer did stay up this time, so even if there was an underlying cause on the old NIC that caused it to time out (or at least puched the envelope on that), the old one has a reputation of timing out and this one stayed up. If it were me, I would hang on to the new card, even after this is resolved. Bu that seemed to be stressed, but not the underlying problem,

The error ext4_reserve_inode_write happens after other "actual errors." The actual error that triggered that would be in the system log before that point.  Could you search your system log file of that instance for anything beforehand mentioning "ext4", "EXT4-fs", or "jbd2", or "journal"? (and post those result please?) And when was the last fschk on that disk?

---

### Post by lgarfiel on 2015-01-02
The hard drive was purchased new 2 weeks ago, and has been repartitioned/reformatted multiple times since then as part of testing.  I haven't run fsck on it since I've just been reformatting it each time.

I am rerunning the test now to see if I can get useful log data abou the journal. Stand by.

---

### Post by lgarfiel on 2015-01-02
[Removed as dupe, sorry]

---

### Post by MAFoElffen on 2015-01-02
(That Last double posted, please edit the last with your new results... or the Mod will probably delete it)

Still look through the logs for that. May be the controller or disk. 

Shouldn't be the disk, especially if it is only 2 weeks old, but stranger things have happened! I just diagnosed a friend's Desktop, where he upgrade his box with new (sale) gaming RAM and one of the sticks was bad... Took us probably 3 times as long to find that, because we assumed the new sticks were good. 

Sideline note-- I have to admit that MAC's have humbled me on RAM. They are real finicky on things being the right type and that things match exactly from bank to bank.

What I was saying is that there are usually errors that are previous to that. The journally didn't just fail (with that error). The journaling is set to a set percentage size. There were enough previous errors, that the journaling not could keep them all, so it turned itself off. At least that is what usually happens with that.

---

### Post by lgarfiel on 2015-01-02
This is interesting. Now I get a totally different error on screen.  Highlights:

-----
Kernel BUG at /build/buildd/linux-3.13.0/fs/buffer.c:3306!
invalid opcode: 0000 [#1] SMP
...
CPU: 0 PID: 29 Comm: kswapd0 Not tainted 3.13.0-43-generic  #72-Ubuntu
Hardware name: System manufacturer System Product Name/A8V-VM, BIOS 080012 06/19/2006
[lots of register information]
Call Trace: 
jdb2_journal_try_to_Free_buffers
ext4_releasepage
try_to_release_page
shrink_page_list
shirnk_inactive_list
shrink_lruvec
shrink_zone
balance_pgdat
kswapd
prepare_to_wait_event
balance_pgdat
kthread
kthread_create_on_node
ret_from_fork
kthread_create_on_node
free_buffer_head
--------------------------

And yet the system kept copying data to completion!

Checking syslog, the same stack trace appears there as well.  The immediately preceeding error, from about a minute before the kernel BUG message, is:

perf samples too long (2505 > 2500) lowering kernel.perf_event_max_sample_rate to 5000

(If it's a minute before I don't know if that's too long to be related.)  Messages before that are from 15 minutes before and mundane cron-like stuff.

---

### Post by MAFoElffen on 2015-01-02
> **lgarfiel said:**
> This is interesting. Now I get a totally different error on screen.  Highlights:

-----
Kernel BUG at /build/buildd/linux-3.13.0/fs/buffer.c:3306!
invalid opcode: 0000 [#1] SMP
...
CPU: 0 PID: 29 Comm: kswapd0 Not tainted 3.13.0-43-generic  #72-Ubuntu
Hardware name: System manufacturer System Product Name/A8V-VM, BIOS 080012 06/19/2006
[lots of register information]
Call Trace: 
```

jdb2_journal_try_to_Free_buffers      [COLOR=#ff0000]# try to free those buffers again with journal locked[/COLOR]
ext4_releasepage                           [COLOR=#ff0000]# release page cache[/COLOR]
try_to_release_page                       [COLOR=#ff0000]# fs/ext4/move_extent.c, If any of extents in range became initialized we have to fallback to data copying... one of the inodes was busy, release and try again[/COLOR]
shrink_page_list                             [COLOR=#ff0000]# fs/ext4/inode.c, returns the number of reclaimed pages[/COLOR]
shrink_inactive_list                         [COLOR=#ff0000]# mm/vmscan.c & drivers/misc/lkdtm.c, Helper to return the number of reclaimed pages[/COLOR]
shrink_lruvec                                [COLOR=#ff0000]# mm/vmscan.c, This is a basic per-zone page freer.  Used by both kswapd and direct reclaim.[/COLOR]
shrink_zone                                  [COLOR=#ff0000]# mm/vmscan.c, Direct reclaim and kswapd have to scan all memory cgroups to fulfill the overall scan target for the zone. Returns boolean.
[/COLOR]kswapd                                        [COLOR=#ff0000]# kernel swap daemon managing swap space in response to memory demands[/COLOR] 
prepare_to_wait_event                   [COLOR=#ff0000]# kernel/sched/wait.c, On Finish, Sets thread back to running state and removes the wait descriptor from the given waitqueue if still queued.[/COLOR]
balance_pgdat                              [COLOR=#ff0000] # mm/vmscan.c, 
[/COLOR][COLOR=#ff0000]                                                     /*[/COLOR]
[COLOR=#ff0000]                                                      * For kswapd, balance_pgdat() will work across all this node's zones until[/COLOR]
[COLOR=#ff0000]                                                      * they are all at high_wmark_pages(zone).[/COLOR]
[COLOR=#ff0000]                                                      *[/COLOR]
[COLOR=#ff0000]                                                      * Returns the final order kswapd was reclaiming at[/COLOR]
[COLOR=#ff0000]                                                      *[/COLOR]
[COLOR=#ff0000]                                                      * There is special handling here for zones which are full of pinned pages.[/COLOR]
[COLOR=#ff0000]                                                      * This can happen if the pages are all mlocked, or if they are all used by[/COLOR]
[COLOR=#ff0000]                                                      * device drivers (say, ZONE_DMA).  Or if they are all in use by hugetlb.[/COLOR]
[COLOR=#ff0000]                                                      * What we do is to detect the case where all pages in the zone have been[/COLOR]
[COLOR=#ff0000]                                                      * scanned twice and there has been zero successful reclaim.  Mark the zone as[/COLOR]
[COLOR=#ff0000]                                                      * dead and from now on, only perform a short scan.  Basically we're polling[/COLOR]
[COLOR=#ff0000]                                                      * the zone for when the problem goes away.[/COLOR]
[COLOR=#ff0000]                                                      *[/COLOR]
[COLOR=#ff0000]                                                      * kswapd scans the zones in the highmem->normal->dma direction.  It skips[/COLOR]
[COLOR=#ff0000]                                                      * zones which have free_pages > high_wmark_pages(zone), but once a zone is[/COLOR]
[COLOR=#ff0000]                                                      * found to have free_pages <= high_wmark_pages(zone), we scan that zone and the[/COLOR]
[COLOR=#ff0000]                                                      * lower zones regardless of the number of free pages in the lower zones. This[/COLOR]
[COLOR=#ff0000]                                                      * interoperates with the page allocator fallback scheme to ensure that aging[/COLOR]
[COLOR=#ff0000]                                                      * of pages is balanced across the zones.[/COLOR]
[COLOR=#ff0000]                                                      */[/COLOR]
kthread                                        [COLOR=#ff0000]# start kernel thread[/COLOR]
kthread_create_on_node                [COLOR=#ff0000] # create a kernel thread, passing args[/COLOR] 
ret_from_fork                               [COLOR=#ff0000]# arch/x86/kernel/process_64, thread returns[/COLOR]
kthread_create_on_node                 [COLOR=#ff0000]# create a kernel thread, passing args[/COLOR]
free_buffer_head                           [COLOR=#ff0000]# fs/jbd/commit.c, free the cache[/COLOR]
--------------------------

```
And yet the system kept copying data to completion!

Checking syslog, the same stack trace appears there as well.  The immediately preceeding error, from about a minute before the kernel BUG message, is:

perf samples too long (2505 > 2500) lowering kernel.perf_event_max_sample_rate to 5000

(If it's a minute before I don't know if that's too long to be related.)  Messages before that are from 15 minutes before and mundane cron-like stuff.
So it finished, but with warnings on your paging. (Look at my notes inside your quote).

I would test it again, but with another virt tty logged in... or in Byobu with 2 panels up... with one visible using "top" to watch your memery used and the paging used during that... How much RAM and Swap?

---

### Post by lgarfiel on 2015-01-02
Running now.  A few minutes after starting, according to Top:

sshd: 45% of CPU
rsync: 30% CPU

CPU: 19.3 idle

Memory:
KiB Mem: 1984084 total, 1916644 used, 6100 buffers
KiB Swap: 2029564 total, 0 used, 2029564 free, 1695144 cached Mem

(All numbers are approximate since they of course change a bi tover time)

It doesn't seem to be even touching swap yet. I will update this comment when it's done or errors or does something interesting.

---

### Post by MAFoElffen on 2015-01-02
kk

---

### Post by lgarfiel on 2015-01-02
And it just finished... with no errors this time. It never touched swap as far as I can tell.  I wasn't watching it the whole time but top still reports swap usage at 0.

I do not trust it.

---

### Post by MAFoElffen on 2015-01-02
So going back to the first post:

- Your network layer is not timing out any more
- You are able to copy over 200GB without timing out.
- Memory tests out okay(?)
- On new disk.
- on a recently upgrade 14.04 system.
 -- on a home server(?)

I'm thinking a 200GB data move doesn't happen very often on a home-built home server. And that is not taking into account any other network traffic or load. If it were FTP, TCP would help out with the checksums. Not sure of the details of that dat move (you didn't explain any details of that).

But even I have to watch that. If I do a git on MAAS or on some source repo's... My wife will be very upset if if effects her gaming!!!

What are your concerns?

---

