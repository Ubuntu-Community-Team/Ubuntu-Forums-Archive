---
title: "Up grade problem"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by raheadrick on 2012-05-31
I was updating my ubuntu system. My wife accidentially closed up my laptop. Now I can't get my laptop to boot up. I have a black screen and I am able to get as far as a prompt that reads ~$. Help!!

---

### Post by SmokeyMaverick on 2012-05-31
I'm going to add all of my details to this thread, as I feel like we both have the same issue, and hope this cuts down on threads (at least a bit!).  I feel as though many folks are having this same issue..

I too was trying to upgrade from Ubuntu 10 something to 12.04.  I was doing this via Ubuntu's GUI (will NEVER do that again - I've learned my lesson - I'll use terminal here on out) and it somehow failed - not sure how.  But when I rebooted, at the grub menu I select "Ubuntu, with Linux 3.0.0-19-generic-pae" I just get a blank screen with nothing thereafter.  

Now I've done quite a bit of searching and poking around, different things, but I still can't recover my system, not even reinstall Ubuntu (I have all of my files backed up, so I don't care if I blow current installation away).  I don't want to completely reformat the entire harddrive, as I have Windows installed on sda2, and I'd really like to keep that there.

Onto what I've done to try and figure this out thus far...

1. From grub menu, I select and drop into "(recovery mode)"
2. I select fsck - and get this in the results (sda5 is my Linux partion):

```
/dev/sda5: Superblock last mount time is in the future.  (by less than a day, probably due to the hardware clock being incorrectly set) FIXED.
/dev/sda5:  ***** REBOOT LINUX *****
/dev/sda5: 358954/13860864 files (1.1% non-contiguous), 38900946/55430266 blocks
mountall: fsck / [510] terminated with status 3
mountall: System must be rebooted: /

Finished, please press ENTER
```

3. Ok, thanks fsck, whatever that means..  Next, from the recovery option menu, I select "netroot".  From here I type:

```
apt-get update
```

And the result is my primary issue I'm trying to resolve by booting in with a LiveCD:

```
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
```

4.  Ok, fine, I'll just delete this lock as I've seen suggested on other posts:

```
$: rm -r /var/lib/dpkg/lock
$: rm: cannot remove '/var/lib/dpkg/lock': Read-only file system
```

5.  Ok, so at this point, after reading other forum posts, I have a read only file system somehow, which I can somehow fix by going into a LiveCD boot.  So I try to boot into a 12.04 LiveCD I've created, and I get some kernel panic error:

```
Kernel panic - not syncing: Fatal exception in interrupt
Pid: 357, comm: mount.ntfs Tainted: G D 3.2.0.23-generic #36-Ubuntu
Call Trace:
<IRQ> [<ffffffff81644023>] panic+0x91/0x1a4
[<ffffffff81...>] oops_end+0xea/0xf0
[<ffffffff81...>] no-context+0x150/0x15d
[<ffffffff81...>] __bad_area_nosemaphore+0x1c9/0x1e8
[<ffffffff81...>] ? cfg_dispatch_requests+0x48/0x1b0
[<ffffffff81...>] bad_area_nosemaphore+0x13/0x15
[<ffffffff81...>] do_page_fault+0x426/0x520
[<ffffffff81...>] ? scsi_request_ ..
[<ffffffff81...>] ? blk_run_queue+0x..
[<ffffffff81...>] ? kobject_put+..
[<ffffffff81...>] page_fault+0x25/0x30
[<ffffffff81...>] ? ite_cir_isr+0x59
[<ffffffff81...>] handle_irq_event_percpu+0x55..
[<ffffffff81...>] ? check_preempt_curr+0x84
[<ffffffff81...>] handle_irq_event+0x51..
[<ffffffff81...>] handle_edge_irq+0x87..
[<ffffffff81...>] handle_irq+0x22..
[<ffffffff81...>] do_IRQ+0x5a/0xe0
[<ffffffff81...>] common_interrupt+0x6e/0x6e
<EOI> [<ffffffff81664a82>] ? system_call_fastpath+0x16/0x1b
panic occurred, switching back to text console
```

Now, I've seen this 'kernel panic' at a few points over the past few nights as I was trying to debug this, I can't remember what I was doing (probably trying to boot into Ubuntu with a previous Linux kernel from my grub menu).  

So now I'm stuck - I can't boot into Ubuntu, I can't upgrade my kernel, if thats broken, I can't boot into a LiveCD version of Ubuntu as I get the 'panic' issue.  I can still successfully boot into my recovery root command line as well as my Windows instance.  

Anyone have any ideas/steps that I could try out to install Ubuntu on sda5 (without harming Windows on sda2)?  Thanks to anyone with any ideas for raheadrick and I. 

ps - Sorry if this isn't your exact problem raheadrick, but after wrestling with this these past few nights and researching, I'm pretty sure you might have the same problem I have.  This way we can resolve the issue in 1 thread instead of having multiple splintered threads littering the forum.

---

### Post by jadtech on 2012-05-31
first codes  commands have to start with sudo to get root access .. 

for an incomplete upgrade if you have network connection and you can get to a terminal or shell,   .. 

```
 
sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get install -f

configure -a


```

the -f with upgrade will build a dependency tree and down load all the missing peices and then start or continue the install in a perfect world leaveing you with  at least a system that can get to a desk top and be tweaked .. 

the same with the -f in the install command if the upgrade was already installing it will build a dependency list and then continue the install in an order as not to cause more dependency issues .. 

configure -a  if the system was complete installed or near so and had parts sitting unconfigured..

some time these measure will work sometimes if you can get to recovery that will work other times its best to just  make  or use a bootable disk or USB abd get in to salvage files and then  reinstall clean ..

---

### Post by SmokeyMaverick on 2012-05-31
> **jadtech said:**
> first codes  commands have to start with sudo to get root access .. 

for an incomplete upgrade if you have network connection and you can get to a terminal or shell,   .. 

```
 
sudo apt-get update
```

Thanks jadtech, but I don't have to use sudo as when I dropped into "netroot" option from the recovery grub menu, I was already root (I checked via "whoami" quite a few times) - so I don't think the "sudo apt-get update" would give me any different result than my "apt-get update" run as root.

---

### Post by jadtech on 2012-05-31
right  understand but then too you are locked read only for some reason I  am no expert but  your not gonna write much of nothing including upgrade  when its read only :) 

raheadrick on the other hand may be able to just continue  not really  much info to know  if they are in read only mode. the upggrade -f is always worth a shot   :)

---

### Post by SmokeyMaverick on 2012-06-01
> **jadtech said:**
> raheadrick on the other hand may be able to just continue  not really  much info to know  if they are in read only mode. the upggrade -f is always worth a shot   :)

Very true jadtech - sorry about that.  This is what I get for trying to save the forums from multi threads!  

Give that a try raheadrick, and please report back.

I've got $5 saying you'll have a read only system as well :P

---

### Post by jadtech on 2012-06-01
well if they do you have found someone to work with on it , pain in the butt gfor sure at the same time if ya dont weaken it can be learning ..

---

### Post by SmokeyMaverick on 2012-06-04
I resolved my issue (in a way), and wanted to posted it in case anyone else stumbled upon this thread...

Many of the forums said to boot into a LiveCD to fix the issue of my file system being read only.  However I tried to boot into a LiveCD of Ubuntu 12.04 as well as a LiveCD of Fedora 17 and both gave me 'kernel panic' errors when trying to boot.  I had an older Fedora 14 LiveCD lying around, tried that and I was able to boot into that.  From there I just blew away my Linux partition, sda5, and reinstalled a distro (Fedora 14 since that's what I was Live booted into).

So LiveCD is the way to go, and if you get a kernel panic issue, try an earlier version of a distro's LiveCD, or maybe Knoppix.  Also, I used [this thread]("http://sixgun.org/forum/viewtopic.php?id=4203") to help debug my problem further.

---

