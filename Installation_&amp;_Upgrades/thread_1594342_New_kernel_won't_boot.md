---
title: "New kernel won't boot"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by ChrisDennis on 2010-10-12
Recent kernels won't boot on a Toshiba Satellite Pro A40.

It's running Lucid 10.04 on /dev/sda5, multibooting with Windows on /dev/sda1.

Kernel 2.6.31-14-generic works fine.

None of the recent kernels (2.6.32-22 to 2.6.32-25) will boot -- they display normal-looking messages, then when the Ubuntu splash screen should appear, the screen goes black, disk activity stops, the keyboard won't respond to anything (ctrl-alt-F1, ctrl-alt-del etc.), and I can't get in via SSH either.

Recovery mode is fine.

When booting fails, there is very little in /var/log/syslog: 
[FONT="Courier New"]
Oct 11 18:41:38 chris-laptop rsyslogd: rsyslogd's userid changed to 101
Oct 11 18:41:38 chris-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 11 18:41:38 chris-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 11 18:41:38 chris-laptop kernel: [    0.000000] Linux version 2.6.32-25-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubu
ntu SMP Fri Sep 17 20:26:08 UTC 2010 (Ubuntu 2.6.32-25.44-generic 2.6.32.21+drm33.7)
Oct 11 18:41:38 chris-laptop kernel: [    0.000000] KERNEL supported cpus:
Oct 11 18:41:38 chris-laptop kernel: [    0.000000]   Intel GenuineIntel
Oct 11 18:41:38 chris-laptop kernel: [    0.000000]   AMD AuthenticAMD
Oct 11 18:41:38 chris-laptop kernel: [    0.000000]   NSC Geode by NSC
Oct 11 18:41:38 chris-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Oct 11 18:41:38 chris-laptop kernel: [    0.000000]   Centaur CentaurHauls
Oct 11 18:41:38 chris-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Oct 11 18:41:38 chris-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Oct 11 18:41:38 chris-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Oct 11 18:41:38 chris-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 11 18:41:38 chris-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 11 18:41:38 chris-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (rOct 12 10:44:28 chris-laptop kernel: imklog: Cannot read proc file system, 1.[/FONT]

Notice how the last line is interrupted -- it ends with "a0000 (r" immediately followed by a different date, which is the beginning of a successful boot to the old kernel.

I'm not sure what other information to provide -- it's all very standard stuff.

Any ideas?

cheers

Chris

---

### Post by jamie.myslik on 2011-02-11
I have almost exactly the same problem.  I can boot any older version, but the most recent version will never boot.  When the newest version I was running was 10.04 version ending 27, it wouldn't boot, but 26 would.  Now that the newest version I have is ending 28, 27 will boot but 28 won't.   As soon as I get the Ubuntu splash screen I lose hard drive activity and everything grinds to a halt.

(I don't know if it's a coincidence, but I'm getting authentication errors while running Update Manager.)

I'm thinking an upgrade to 10.10 might solve it?

---

### Post by nico_demo on 2011-02-11
@jamie.myslik: Sadly, I did a fresh install of Maverick (64-bit) this week and I can't boot the -25 Kernel either. But hey, you can still give it a try ;)

@Chris: It's an old thread no one replied to. Can you give us any hope? 
I don't know if this AMD-Related, but my CPU is AMD too.

---

### Post by Chris1492 on 2011-02-11
> @Chris: It's an old thread no one replied to. Can you give us any hope? 
I don't know if this AMD-Related, but my CPU is AMD too.

No, I never solved it.  The laptop in question went back to its owner unmended.

---

### Post by holoman on 2011-02-23
Try to update your rsyslog. 

I had the same problem (rsyslog 4.2.0) on Ubuntu 10.04. Now I installed V5.7.4 (i.e. [http://ftp.us.debian.org/debian/pool/main/r/rsyslog/rsyslog_5.7.4-2_i386.deb](http://ftp.us.debian.org/debian/pool/main/r/rsyslog/rsyslog_5.7.4-2_i386.deb)) and it works great!

Holoman

---

