---
title: "kernel upgrade"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by vista on 2006-08-17
I want to upgrade from kernel 386 to kernel k7.
What's the easiest and safest way to do so, 
without messing up my system? 
Synaptic or apt-get? 

AMD athlon xp 2100+     256Mb
          Nivida geforce4 mx440
          Soundblaster audigy platinum 
          Ubuntu dapper

---

### Post by mlind on 2006-08-17
It doesn't matter which apt front-end you'll use. Synaptic, apt-get, aptitude are all good. (Although apt-get is deperecated in favour of aptitude).
You can have multiple kernels installed, so don't remove you 386 kernel before you know that k7 one works.

To install **newest** k7 architechture kernel using aptitude
```

sudo aptitude install **linux-image-k7**

```

linux-image-k7 is a meta package that will always depend on newest k7 kernel. If you also want to depend on restricted-modules package (nvidia, fglrx, ..), install **linux-k7** meta package.

---

### Post by John.Michael.Kane on 2006-08-17
Open synaptic search for linux-. 

once you find the kernel you want select it. install it.

upon rebooting the machine,and making sure the new kernel works.

Re-open synaptic search for linux-,and remove the 386 kernel.

---

### Post by vista on 2006-08-19
Ok, I upgraded through synaptic, so far so good.
But i've noticed that when using the new amd kernel,
my cpu is at a konstant 12-15% when idle. Why is that?
The 386 was only at 1-2% cpu usage when idle.

If you want to stream videos at youtube the cpu 
goes up to 60-80% and stays there through out.

My comp feels more responsive than before, but still
the cpu thing is not good.

What causes these cpu spikes? Is there a way to fix this?

Also do you have to download the linux-k7 headers? Is that important?

---

### Post by mlind on 2006-08-19
> **vista said:**
> Ok, I upgraded through synaptic, so far so good.
But i've noticed that when using the new amd kernel,
my cpu is at a konstant 12-15% when idle. Why is that?
The 386 was only at 1-2% cpu usage when idle.

If you want to stream videos at youtube the cpu 
goes up to 60-80% and stays there through out.

My comp feels more responsive than before, but still
the cpu thing is not good.

What causes these cpu spikes? Is there a way to fix this?

Also do you have to download the linux-k7 headers? Is that important?

Are you sure it's kernel related? There's no process eating cpu time? I've seen releated bugreport, where laptop users have same behaviour with idle system.
Tuning a kernel parameter reportedly fixes this issue, but I couldn't find the bugreport from launchpad..

You don't need to install linux-k7 headers package is you're not about to compile custom kernel modules.

---

### Post by vista on 2006-08-19
This is what I get when I run the command "top" 

> top - 03:30:16 up 58 min,  2 users,  load average: 0.17, 0.19, 0.23
Tasks:  91 total,   1 running,  90 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.3% us,  3.0% sy,  0.0% ni, 74.2% id,  0.0% wa,  1.0% hi, 10.6% si
Mem:    255576k total,   242824k used,    12752k free,     8708k buffers
Swap:   746980k total,    18444k used,   728536k free,    76492k cached


I was wondering, why is all my memory almost used up?
Could this be right? In GKrellM app it says : 250Mb-105Mb available.
Im running gnome desktop, should I switch desktop perhaps?

I also ran this command: sudo gedit /etc/hdparm.conf

> 
# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode
# --security-freeze Freeze the drive's security status
# security_freeze
# --security-unlock Unlock the drive's security
# security_unlock = PWD
# --security-set-pass Set security password
# security_pass = password
# --security-disable Disable drive locking
# security_disable
# --user-master Select password to use
# user-master = u
# --security-mode Set the security mode
# security_mode = h

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda


---

