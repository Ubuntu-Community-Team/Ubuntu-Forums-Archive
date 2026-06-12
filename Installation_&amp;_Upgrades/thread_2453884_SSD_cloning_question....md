---
title: "SSD cloning question..."
date: 2020-11-18
forum: Installation &amp; Upgrades
---

### Post by RallyDarkstrike on 2020-11-18
Hi all - I have a few questions about cloning my install (or other Ubuntu-based installs) to an SSD! :)

I have an HP Pavilion Touchsmart 14 laptop (AMD A6 2.0Ghz CPU, 12GB RAM, 500GB mechanical HDD). I've been happily running Linux on it for awhile. I've got some SSDs laying around and am contemplating cloning my install to one of the SSDs and then installing that to speed the laptop up. Now, I know on a fresh install, Linux would know it's being installed onto an SSD and adjust itself accordingly (enable TRIM, etc)...BUT, will it do this if it is CLONED from a mechanical HDD where it was originally installed ONTO an SSD?

I know that Windows 10, for example, WILL configure itself automatically for an SSD if it is CLONED or INSTALLED onto one. If you boot up on a cloned SSD, it just realizes it's on an SSD now and sets things up correctly....but I just want some info on if Linux does the same?

...SO...two  questions:

1. Do I need to change any settings (activate TRIM, for example) after the clone or will things automatically get adjusted after booting up into the SSD and the OS seeing that the install is on an SSD drive now and not a  mechanical drive...?

2. Should I set up SWAP on an SSD? Something tells me 'no' as that would  lead to unnecessary read/write on the SSD and, therefore, wear? BUT, that being said, I know Windows 10 does keep a page file active on SSD installs, but just won't use it unless it REALLY needs to?

**(A note - I've been a Linux user for years, but I use Win10 as a reference as the only computer I currently have an SSD installed in runs Win10)**

Thanks and cheers!

---

### Post by oldfred on 2020-11-18
I am a believer in new install and restore from your backup.
That also confirms your backup has everything you need when drive fails and have to do a new install.

With 12GB of RAM, you would not normally use swap. New install will create swap file, but if swap partition found will use the partition.
I have a swap partition from an old install & have to tell installer not to use swap partition with my new install and that does work.
My older system with only 4GB of RAM never used swap, but I did not edit videos or very large photos, so never ran anything that used a lot of RAM.
SSDs now have similar reliability as HDD, but if never writing to swap, it does not matter where swap is.

---

### Post by RallyDarkstrike on 2020-11-18
That's the thing though...I just finished doing a full reinstall a few months ago and the setup I use is very involved and tweaked and takes me hours to put things back the way I want and get the software back installed and setup the way I like, so I'd really like to avoid having to do a fresh install seeing as this was a relatively fresh install months ago anyway and because of the time it takes to set everything back up / copy all my data back. If by backup, you mean TimeShift....I have it set up, but I am a  bit leery as I have tried to use it twice in the past and it failed to restore to a running OS correctly both times and I had to reinstall anyway.

As for swap, I don't do a lot of high-memory (video editing, for example) stuff on this, but I do routinely have a lot of tabs open in Firefox that I leave open all the time. That and Discord are what I use most of the time. I have 'swappiness' set to '10' with 14GB of Swap to give me ample (somebody once told me you should have as much swap as you have RAM...I have 12GB or RAM, so gave a little extra swap), but even when the RAM is not all used, it starts using swap anyway?

[ATTACH=CONFIG]287384[/ATTACH]

I do often have like...20 tabs open in Firefox as I need to for my work.

---

### Post by mastablasta on 2020-11-19
you need 12 Gb swap if you plan to hibernate with 12 GB occupied. or or maybe 4 would be enough. i let it do a file on Nvme disk.

swap is not constantly used, only when it is needed. i use USB drive as disk for server and i set the swapiness so it doens't use the swap partition much. i set the partition on to HDD. and if i check swap is actually rarely used. server usually needs less than 500 MB ram. even if i run minecraft on it, it uses 2 GB ram (i set this limit) and that still leaves it with about 1.5 GB free.

---

### Post by coley9225 on 2020-11-19
Hello Rally. I'm very new to linux systems, only started using lubuntu in Feb. of this year. I have a pretty weak computer so I upgraded from a 1TB HDD to a 1TB SSD about 3 months ago. I don't remember what I used to clone the drive, I still had windows then so probably used Macrum reflect free. I haven't had any issues at all. Any time I run fstrim, there isn't much for it to do, so I think its running trim automatically. If your concerned about that, you can run fstrim manually, or set up a cron entry to run it for you on a regular basis. I also use timeshift for backing up my OS, set to do daily backups. I have it set to backup / and /home(turned off by default), and recently had to roll back 1 week, and it went flawlessly. I haven't had to restore to a fresh install(yet...lol), but I browse the backups and all my document, pictures, etc seem to be there. And as far as the swap, I have 8GB of ram, I have whatever swap was put in place during the fresh install, and I've yet to see it used. I have 3 window open for firefox(on 3 different desktops), 1 of those regularly have 4 plus tabs open, plus I have a desktop with Google Chrome running, at time with multiple tabs, plus whatever I'm working on at any given time. I think you'll be fine on the swap. I wish you the best of lick on this, but like EVERYONE says, make sure you have a full backup, in case something goes sideways.

---

### Post by TheFu on 2020-11-19
I would worry about sector alignment mainly.  If both are aligned on the same boundaries, then a pure clone should be fine.  I think trim is run weekly by default. Check /etc/cron.weekly/fstrim.  All my systems have that, even those without any SSDs.

But if your restore process is taking more than 45 minutes to re-setup the core OS + applications + settings, then I think you need a better backup+restore method.  

My rule of thumb for fixing any new issue is to spend 30 minutes trying to fix it. After 30 minutes, I use the backup from last night to restore the system. Takes 30-45 minutes and I move onto getting work done. Of course, huge amounts of data storage can take longer to restore, but those usually aren't placed into the OS file system or into the HOME file system. I keep the OS, home and data on separate file systems so the restore from backup only need touch the OS and perhaps /home/, not the data.  If data becomes corrupted, I can restore it separately from the OS or home areas.

I use cloning of storage for the same sort of things you are doing here, but I ensure sector alignment is correct. With SSDs, all the storage is virtual, so sector alignment *shouldn't* matter at all, but who knows.  BTW, hopefully, you are leaving 20% of the SSD empty, unused, unallocated, so the wear leveling algorithm has some extra space to extend the SSD life.

---

### Post by RallyDarkstrike on 2020-11-19
> **TheFu said:**
> BTW, hopefully, you are leaving 20% of the SSD empty, unused, unallocated, so the wear leveling algorithm has some extra space to extend the SSD life.

Pretty sure this isn't necessary as don't SSDs already come with walled-off space now that can't be formatted for normal use that is allocated only for extending SSD life?

---

### Post by TheFu on 2020-11-19
> **RallyDarkstrike said:**
> Pretty sure this isn't necessary as don't SSDs already come with walled-off space now that can't be formatted for normal use that is allocated only for extending SSD life?

Enterprise ones, yes.  They come over-provisioned.
Consumer ones, doubtful.  Check the TBW and Endurance numbers for any SSD bought.  If a company refuses to publish TBW - run away.  
I've used cheap consumer, brand-named consumer and enterprise SSDs. My sample size is tiny, so it is probably statistically useless, except in my mind.  The cheap consumer ones lasted 12-18 months. They provided feedback of impending failures by going into read-only mode for 1-2 months before total failure. I was lucky.  

I have Samsung and Micron SSDs too. Both of these are doing well and nearing the 24 month old point on each.  The warranted TBW for each are far far away from the current numbers. Both are 512 GB models.  I watch almost all storage here with weekly SMART reporting.  With the Micro, SMART attribute 202 has the remaining life of the SSD:
```
202 Unknown_SSD_Attribute   0x0030   **096**   096   001    Old_age   Offline      -       4
```
So, after 18 months of 24/7/365 use with about 10 VMs running 24/7 on the SSD, my careful storage design has left 96% of this SSD life remaining.  Very nice.

The actual places inside any SSD where data is written has been a super-secret for over 5 yrs as the different controllers use proprietary techniques to level the writes. With solid state storage, I'm not even certain that 1 block is 1 block on those chips. It is all emulated to look like HDD storage for the OS. The actual internal techniques used are super-duper-secrets.

On the Samsung, I've left about 50% of it empty. It is in a laptop, so the data needs really aren't high. 
On the VM server, well, I need to do better with my allocations. ;)  There is over 100G unused, but it is allocated to a VG, so it isn't really unused. ;(

---

### Post by RallyDarkstrike on 2020-11-19
My Win10 desktop has a Samsung Evo 860 250GB that has been in it for about 2 years. It's fully formatted (not over-provisioned) and is at 96% health, so it's doing fine. The drive I am putting into my laptop is a 500GB Crucial M500...also highly reviewed in the consumer space.

I still can't seem to find anybody who can give me a straight answer on whether I need a swap partition with an SSD and whether Linux will auto-activate TRIM or not though. After forum posts in various places and a lot of Google searches, there are so many different opinions, but nobody seems to be able to tell me for sure.....I wish I could just ask the devs!

---

### Post by TheFu on 2020-11-19
> **RallyDarkstrike said:**
>  I still can't seem to find anybody who can give me a straight answer on whether I need a swap partition with an SSD and whether Linux will auto-activate TRIM or not though. After forum posts in various places and a lot of Google searches, there are so many different opinions, but nobody seems to be able to tell me for sure.....I wish I could just ask the devs!


Trim - there is a weekly script run in all Ubuntu distros that does an fstrim on all connected devices.
It is in /etc/cron.weekly/ - as stated in post #6 above.  Look for yourself. It is there.

Swap and SSDs are separate questions.  You need swap if you run out of RAM.  For some versions of the kernel, there is a bug in that they need "some" amount of swap or bad things happen.  For a typical desktop using modern browsers, I create 4.1G of swap into a swap LV - that's like a partition, but for enterprise storage people and much more flexible than partitions.  There are reasons to make it larger or smaller. Just depends on the system, the workload, and the users.

I don't remember which specific kernel versions had the swap issue, so don't ask me. It was just a few. I don't know if those were deployed on Ubuntu either.  On my servers, I try to setup sufficient RAM for the workload so that no swap is ever necessary.  On desktops, that is harder since a modern browser can balloon to use 32G of swap if there's a bug in an addon.  I've seen this multiple times this week when running firefox over remote X11. Something bad happens that freaks out Firefox. Since I don't have 32G to spare and think adding 32G of swap is stupid for the workload, I just wait for the program to crash, send the bug report off to Mozilla and wait.  I don't think they will ever fix the issue and honestly doubt they even care.  To them, running programs over remote X11 isn't worth their time or consideration since so few users do it.  Plus, they are in the majority in thinking that X11 is dead and that everyone should stop using it in preference for Wayland.  Pffft.

Often when we ask "simple questions" and don't find or get simple answers, it is because our question isn't really simple or doesn't apply.

---

### Post by tea for one on 2020-11-20
Using Ubuntu 20.04 with and Gnome 3.36.3, here is a bit more info about fstrim:-

```
edited@edited:~$ sudo systemctl status fstrim.timer
[sudo] password for edited: 
&#9679; fstrim.timer - Discard unused blocks once a week
     Loaded: loaded (/lib/systemd/system/fstrim.timer; enabled; vendor preset: >
     Active: [COLOR="#0000FF"]active[/COLOR] (waiting) since Fri 2020-11-20 09:21:54 GMT; 29min ago
    Trigger: Mon 2020-11-23 00:00:00 GMT; 2 days left
   Triggers: &#9679; fstrim.service
       Docs: man:fstrim

Nov 20 09:21:54 edited systemd[1]: Started Discard unused blocks once a week.
lines 1-8/8 (END)

```

It looks like systemd is in the mix. I did not activate the trim service, I assume/guess it was activated during the install of Ubuntu 20.04 LTS

---

