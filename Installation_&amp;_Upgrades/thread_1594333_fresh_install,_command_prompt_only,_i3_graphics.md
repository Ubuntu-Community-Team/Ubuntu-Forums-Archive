---
title: "fresh install, command prompt only, i3 graphics"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by CrispyCritter on 2010-10-12
New install of 10.10, formatted all partitions so a fresh start.

X never starts.

I get the command line prompt.  If I do nothing, after 5 minutes everything goes blank and no response to anything.

I can log in (with administer account) and look around for about 5 minutes, and then a message flashes up too quick to read and I'm again put in the blank, unresponsive screen state.

If I run startx, I get the blank unresponsive screen state immediately.

No xorg.conf file in /etc/X11.

Live-CD. same disk as used to install, works fine (takes a couple of minutes of waiting - don't know if that's normal).  Is running X and Gnome fine.

Do have a completely separate disk with Windows 7 on it - don't see how that would affect anything.

Running analog connected display, i3 graphics (no graphics card installed), Biostar motherboard, 32bit desktop 10.10

Any ideas what I should be looking at in my 5 minutes of time?

---

### Post by CrispyCritter on 2010-10-12
I had been looking in /var/log/messages and nothing struck me, but dmesg was much more emphatic about running into a bug.

What next for me?  Is this the problem?
Is there more info from dmesg that would be helpful?  Note that it had detected the CPU and 4 processors correctly before this part of dmesg (dmesg too large to attach all of here).

Edit Note: switched from analog display connection to digital display connection before this boot (had no effect on problem).

```

...
[    5.563775] udev[416]: starting version 163
[    5.610673] intel ips 0000:00:1f.6: No CPUID match found.
[    5.610682] BUG: unable to handle kernel NULL pointer dereference at 00000008
[    5.610755] IP: [<f850b452>] ips_detect_cpu+0x62/0x180 [intel_ips]
[    5.610809] *pdpt = 000000003544b001 *pde = 0000000000000000 
[    5.610877] Oops: 0000 [#1] SMP 
[    5.610937] last sysfs file: /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/
device:00/uevent
[    5.610976] Modules linked in: intel_ips(+) serio_raw usbhid hid pata_via r81
69 mii
[    5.611153] 
[    5.611176] Pid: 528, comm: modprobe Not tainted 2.6.35-22-generic-pae #34-Ub
untu H55 HD/H55 HD
[    5.611216] EIP: 0060:[<f850b452>] EFLAGS: 00010286 CPU: 3
[    5.611249] EIP is at ips_detect_cpu+0x62/0x180 [intel_ips]
[    5.611281] EAX: 01a80248 EBX: 00000000 ECX: 01a80248 EDX: 00000000
[    5.611315] ESI: f5a37e04 EDI: f5597480 EBP: f5a37e14 ESP: f5a37de4
[    5.611348]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[    5.611380] Process modprobe (pid: 528, ti=f5a36000 task=f6bf0cb0 task.ti=f5a
36000)
[    5.611417] Stack:
[    5.611440]  f850cefc f850ce9e f75e0490 f5a37e14 c02162f1 f5a37e08 c05ee9c9 f
850beef
[    5.611599] <0> 00000000 f5597480 f7628800 fffffff4 f5a37e4c f850bf2b c027b6c
d f5a37e4c
[    5.611793] <0> c027ac77 f5a37e4c c027b07a f5a37e38 f7628800 f7628860 c037614
e f7628800
[    5.612022] Call Trace:
[    5.612069]  [<c02162f1>] ? kmem_cache_alloc_notrace+0x91/0xb0
[    5.612122]  [<c05ee9c9>] ? mutex_lock+0x19/0x40
[    5.612170]  [<f850beef>] ? ips_probe+0x1f/0x6a0 [intel_ips]
[    5.612220]  [<f850bf2b>] ? ips_probe+0x5b/0x6a0 [intel_ips]
[    5.612273]  [<c027b6cd>] ? sysfs_add_one+0x1d/0x110
[    5.612322]  [<c027ac77>] ? sysfs_new_dirent+0x67/0x100
[    5.612371]  [<c027b07a>] ? sysfs_addrm_finish+0x1a/0xb0
[    5.612423]  [<c037614e>] ? pci_match_device+0xbe/0xd0
[    5.612470]  [<c0375fe3>] ? local_pci_probe+0x13/0x20
[    5.612520]  [<c0376f98>] ? pci_device_probe+0x68/0x90
[    5.612571]  [<c0414d00>] ? really_probe+0x50/0x150
[    5.612621]  [<c041c387>] ? pm_runtime_barrier+0x57/0xb0
[    5.612671]  [<c0414e3c>] ? driver_probe_device+0x3c/0x60
[    5.612720]  [<c0414ee1>] ? __driver_attach+0x81/0x90
[    5.612770]  [<c0414303>] ? bus_for_each_dev+0x53/0x80
[    5.612820]  [<c0414bce>] ? driver_attach+0x1e/0x20
[    5.612867]  [<c0414e60>] ? __driver_attach+0x0/0x90
[    5.612917]  [<c0414595>] ? bus_add_driver+0xd5/0x280
[    5.612965]  [<c0376ed0>] ? pci_device_remove+0x0/0x40
[    5.613015]  [<c04151da>] ? driver_register+0x6a/0x130
[    5.613065]  [<c03771d5>] ? __pci_register_driver+0x45/0xb0
[    5.613115]  [<f8510017>] ? ips_init+0x17/0x19 [intel_ips]
[    5.613167]  [<c0103042>] ? do_one_initcall+0x32/0x1a0
[    5.613215]  [<f8510000>] ? ips_init+0x0/0x19 [intel_ips]
[    5.613267]  [<c0188f1b>] ? sys_init_module+0x9b/0x1e0
[    5.613317]  [<c0222ec2>] ? sys_write+0x42/0x70
[    5.613366]  [<c010939f>] ? sysenter_do_call+0x12/0x28
[    5.613415] Code: 75 c2 c7 90 ba f5 cd 50 f8 b8 8c 42 85 c0 e8 56 8a e5 c7 bb
 80 d4 50 f8 85 c0 74 35 b8 ac 01 00 00 89 f2 e8 21 75 c2 c7 90 89 c1 <8b> 53 08
 c1 e1 12 c1 e9 15 69 c1 e8 03 00 00 39 c2 75 75 89 d8 
[    5.614664] EIP: [<f850b452>] ips_detect_cpu+0x62/0x180 [intel_ips] SS:ESP 00
68:f5a37de4
[    5.614775] CR2: 0000000000000008
[    5.614841] ---[ end trace 4eee990b58723cfc ]---
[    5.726652] Linux agpgart interface v0.103
[    6.044069] lp: driver loaded but no devices found
[    6.047761] Adding 5119996k swap on /dev/sda5.  Priority:-1 extents:1 across:
5119996k 
[    6.049290] type=1400 audit(1286887610.315:2): apparmor="STATUS" operation="p
rofile_load" name="/sbin/dhclient3" pid=634 comm="apparmor_parser"
[    6.049782] type=1400 audit(1286887610.315:3):
apparmor="STATUS" operation="
...

```

---

### Post by P4man on 2010-10-12
Looks like this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/648631](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/648631)

pending a  bugfix, try blacklisting intel_ips as suggested in that thread

---

### Post by apzane on 2010-10-12
I was having this exact problem with the same hardware. 

Creating a file /etc/modules.d/blacklist-custom with the line "blacklist intel_ips" in it fixed the problem. 

What is intel ips? Will having it blacklisted cause any problems?

---

### Post by P4man on 2010-10-12
I think its acronym for intel Intelligent Power Sharing, and it has to do with dynamically clocking cpu and gpu. Shouldnt give problems to blacklist it, but it may cost a bit of performance.

---

### Post by CrispyCritter on 2010-10-12
> **P4man said:**
> Looks like this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/648631](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/648631)

pending a  bugfix, try blacklisting intel_ips as suggested in that thread
Great, that was it! Blacklisting intel_ips worked beautifully, and all appears to be well.  Thanks very much!

Should I be reporting this bug myself through official channels so it gets into release notes (or fixed), or is the fact that it's currently being worked on (from your link) enough and I shouldn't bother the people already working on it?

---

### Post by P4man on 2010-10-12
Just click the "affects me too" link on that page (requires a login), and subscribe to it to keep informed of any updates

---

### Post by tvphil on 2010-10-12
Could you write a file template exactly as it should be entered. This would help a lot using nemo to enter it. Also, I have this same problem with a 7 year old pentium 4 box with an Nvidia geforce 4400 card. For this reason, I think this bug effects a lot more people than previously thought

---

### Post by P4man on 2010-10-12
You _sure_ its the same problem,a kernel oops in intel_ips module? It shouldnt even load on that machine as it couldnt possibly support it (unless intel_ips is something very different than I think)

---

