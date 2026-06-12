---
title: "Raidz2 with Ubuntu &amp; Windows dual boot"
date: 2024-07-03
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2024-07-03
I am setting up a Raidz2 NAS with 4 hard drives and it is my first time using RAID of any type. At the moment operating systems are not installed.

I hope to be able to have both OS systems running side by side across the drive array but cannot find any information if this is possible.

I understand I need to have windows running under AHCI so I am thinking I need to install windows, change the bios to run it using AHCI before installing Ubuntu. However, will I be able to treat the drive array as one drive with both OS on it, or do the OS go on separate drives?

Are there and guides available?

---

### Post by TheFu on 2024-07-06
I haven't dual booted in over 15 yrs, but stop thinking "drives" and think "partitions".

To my knowledge, ZFS isn't supported by MS-Windows, so that is a complete fail if you intend to do that.

What does the NAS have to do with any of this?  The NAS storage is on a different system, accessed over the network.  The NAS system will either be commercial and require you to use whatever hardware and volume manager they like with whatever file system they like 
OR
the NAS will be something you build yourself and have control over.

If you don't have any experience with RAID of any sort, why would you jump into something like RAIDz2?  That isn't a beginner topic.

With Linux, you'll need to learn as you go.  Like a baby who learns to raise his head before learning to roll over, before crawling, before standing, before waddling, before walking, before ..... until you are sprinting with hurdles.  RAIDz2 is for sprinters, not waddlers, if I have to guess the skill level needed for acceptable outcomes.  Maybe start with RAIDz first and use that for a few years?

Also, never use an entire drive as a RAID device. Always step partitions so when the drive fails, you have an exact size that can be replace that isn't dependent on getting the exact same drive model and size 3 yrs later.

Of course, you will learn all sorts of things that nobody else here knows if you actually try to accomplish what you want.  Don't let someone like me stop you from trying.  Things are always changing and perhaps you can do things we don't know are possible.

---

### Post by makem2 on 2024-07-07
[COLOR=#464D4D][FONT=&amp]Thank you for your comment @TheFu, it is appreciated.[/FONT][/COLOR]

 [COLOR=#464D4D][FONT=&amp]I will be using Proxmox[/FONT][/COLOR][COLOR=#464D4D][FONT=&amp] Virtual Environment and Docker. I have learned that the two operating systems will be on a separate nvme drive, not part of the RAID drives.

Progress will be slow but that is to be expected. The NAS is being built from scratch. Will have to look into your stepping partitions in RAIDz2.[/FONT][/COLOR]

---

### Post by TheFu on 2024-07-07
Proxmox takes over the whole machine. Beware.

---

### Post by makem2 on 2024-07-07
> **TheFu said:**
> Proxmox takes over the whole machine. Beware.

Yes I am aware of that. Please tell me why you say beware or is that just because it does so, or, do you have or have heard of experience of the software?

---

### Post by TheFu on 2024-07-08
You said you wanted to dual boot.  Proxmox takes over the entire machine.  No dual booting.  Also, once you commit to proxmox, you'll be in a specialized world of how to do things, which can be important.  Proxmox fills a niche need nicely, but home users with only 1 system probably wouldn't want to give up their desktop to run it.

---

### Post by makem2 on 2024-07-09
> **TheFu said:**
> You said you wanted to dual boot.  Proxmox takes over the entire machine.  No dual booting.  Also, once you commit to proxmox, you'll be in a specialized world of how to do things, which can be important.  Proxmox fills a niche need nicely, but home users with only 1 system probably wouldn't want to give up their desktop to run it.

I have learned a lot in the past few days about VM's, Docker, Proxmox and UnRAID.

I have decided that I should go with UnRAID:

[https://nascompares.com/guide/pros-and-cons-of-unraid-nas-os/](https://nascompares.com/guide/pros-and-cons-of-unraid-nas-os/)

However, I still remember your caution about using whole drives. I will look into 'stepping' the partitions but could you enlighten me on that a little. Given that UnRAID comes as an ISO and the bootable USB must always be in the NAS as it is the OS. At first glance I don't see how I get an option to do anything about partition sizes.

As UnRAID can use any size drives and is expandable it sounds as if stepping would not come into it.

I now see I don't need 'Dual Boot' because if I need two OS then they would be in containers.

---

### Post by TheFu on 2024-07-09
Containers aren't the same as VMs and have lots of security ramifications.  Also, containers cannot be used to run MS-Windows, if that's your intent.

I've never used UnRAID.  Long ago, I read up on the way it works and decided I wasn't willing to trust my data to that method.  YMMV. Perhaps my data is more important to me than yours is to you?

---

### Post by makem2 on 2024-07-09
> **TheFu said:**
> Containers aren't the same as VMs and have lots of security ramifications.  Also, containers cannot be used to run MS-Windows, if that's your intent.

I've never used UnRAID.  Long ago, I read up on the way it works and decided I wasn't willing to trust my data to that method.  YMMV. Perhaps my data is more important to me than yours is to you?

UnRAID offers VM's in which you can run MS-Windows. I erred in saying containers previously.

I lack the knowledge to decide if the method used can be trusted or not. Would you explain what decided you please?

---

