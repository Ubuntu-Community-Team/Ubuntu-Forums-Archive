---
title: "Fresh Arch netinstall won't boot"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by Zerp64 on 2010-04-17
I've already posted this to Arch forums, but I haven't gotten a useful response there. Since there are more users on this site, I'm hoping that I'll get more help here:

> Kinda sucks, because I like Arch so far.

The first time I installed Arch, everything went fine. I had a good openbox/SLIM configuration, but for some reason I just got a black screen w/ a mouse that didn't move whenever I tried to use the radeon driver (which works with my card, by the way, so that wasn't the problem). By the way, if anyone has a fix for this I'd like to hear it.

Anyways, I uninstalled Arch and reinstalled Fedora, but after my second attempt to install Arch (I have nothing better to do), arch suddenly wouldn't boot at all after a netinstall. Doing a core install went fine, but when I tried to update it and reboot, the same thing happened as the netinstall: The screen goes on standby and the CPU is spiked at %100 (I know this because my fan goes to full speed when the CPU jumps up too high - long story). Not even doing that Skinny Elephants trick worked, so I'm guessing it was a complete kernel panic.

So anyways, does anyone have an idea of what's up? I don't exactly know how to check for logs when the system is unbootable, but in retrospect I coulda just booted into a livecd...

------------------

I just looked in /var/log of a recent Arch install on this computer, and there doesn't seem to be anything there. A file called 'lastlog', but I'm not sure it's anything. I can't open it with gedit or cat, so I'm assuming it's a garbage file.


Adding 'nomodprobe' into menu.lst in Arch allowed it to boot, but I could only use the vesa driver with Xorg (using radeon caused a black screen showing only a cursor), which isn't ideal.

*Edit:* It sounds an awful lot like this: [http://forums.virtualbox.org/viewtopic.php?f=3&t=19143](http://forums.virtualbox.org/viewtopic.php?f=3&t=19143)

---

### Post by kelvin spratt on 2010-04-17
This is what you need to follow. The Wiki will guide you. 
[http://wiki.archlinux.org/index.php/Beginners%27_Guide]("http://wiki.archlinux.org/index.php/Beginners%27_Guide")
It does for anybody that cares to read it properly. 
The forums are very helpful don't expect people to hold your hand
Net install is the best way to install arch linux as you get the latest software and settings, your the core install is out of date the day it is released that is the nature of a rolling release.
its a matter of getting a mirror thats up  to date  use this link [https://www.archlinux.de/?page=MirrorStatus](https://www.archlinux.de/?page=MirrorStatus) check before you do your install and use a up to date mirror some times the mirrors are down.
[URL="http://wiki.archlinux.org/index.php/Beginners%27_Guide"]
[/URL]

---

### Post by Zerp64 on 2010-04-17
I followed the guide. That's why I posted on the forums, because I believe I followed instructions perfectly. Also, I'd figure that doing a fresh netinstall would work out-of-the-box. I know to look for help before I post on a forum.

---

### Post by wilee-nilee on 2010-04-17
> **Zerp64 said:**
> I followed the guide. That's why I posted on the forums, because I believe I followed instructions perfectly. Also, I'd figure that doing a fresh netinstall would work out-of-the-box. I know to look for help before I post on a forum.

I just started using arch, actually there are a lot of arch users on here or at least lurking. Make sure you have the appropriate additions added per the wiki in the appropriate files. I installed and didn't follow the instructions exactly, but was able to go back and follow them and have a running arch set up with the Ubuntu desktop.

---

### Post by kelvin spratt on 2010-04-17
A net install only installs a base system, "pacman -S xorg" only installs the vesa driver  you have to install video drivers to suit Your video card go back to the wiki  [http://wiki.archlinux.org/index.php/Category:Graphics_%28English%29](http://wiki.archlinux.org/index.php/Category:Graphics_%28English%29) follow the instructions. Its all quite easy really then post on the Arch forum if you have problems. 
I'm not being bolshy but I'm dyslexic I use Arch, I copy past every thing from the Wiki with no problems at all, Arch does not by design install anything you don't ask it to also with some things you have to Use items from the AUR repro.

---

### Post by Zerp64 on 2010-04-17
Hey, I c&p most everything, too. But I've been around linux for about five years (jeez... has it really been that long?) and I know when I need to install drivers, make modules run at bootup, and all that jazz. It's not a problem, especially when Arch makes it so darn easy. What I'm saying is that Arch has a(n apparent) kernel panic when it boots up with a fresh system - no Xorg, just base and base-devel groups installed.

But I'll try what Wille said. I'll go through the install again and follow everything to the letter. I'll report back here when I'm done. Thank God I have some livecds still in case it inevitably goes wrong again.

---

### Post by kelvin spratt on 2010-04-17
If you get kernel panics You have set it up incorrectly A lot of people make mistakes using nano and things don't get saved correctly I did on my 1st attempts many of them. Now I can do a net install with a fully working LXDE setup in 20min. If you still keep failing cheat go here  [http://godane.wordpress.com/](http://godane.wordpress.com/) This is a live Arch cd you can install a fully working desktop. It also installs a lot of drivers you don't want. Give it a try then when you get competent with Arch go back to the net install.

---

### Post by Zerp64 on 2010-04-18
I reinstalled Arch and the same thing happened: the system panics when udev begins to load. After around two hours of work I found that not only was the radeon driver being loaded at bootup by udev, but so was my onboard card. Apparently they conflicted and caused the panic. So blacklisting the internal video card modules worked and I managed to get the system to boot up without disabling KMS.

But I'm still having a problem. I can't start Xorg at all, because doing so causes the system to freeze. Even using the vesa drivers causes this freeze. It's pretty damned annoying. Does anyone have any ideas from here? I have the standard Xorg group installed, along with the ati, mouse, keyboard, and evdev packages. I might be missing something totally obvious... I'll check the wiki, but if you guys have any ideas let me know.

The modules I've blacklisted, by the way, are the via_agp and i2c_viapro modules. I've blacklisted them in both /etc/rc.conf and /etc/mkinitsomethingorother.conf, just to be sure. Could that be causing this?

*Edit:* Yeah, via_agp is for AGP cards... I got that now. Anyways, that's a part of the problem. Check this out:

```

Apr 17 21:57:40 desktop kernel: BUG: unable to handle kernel NULL pointer dereference at 00000040
Apr 17 21:57:40 desktop kernel: IP: [<f8ae0c84>] radeon_agp_init+0x14/0x3d0 [radeon]
Apr 17 21:57:40 desktop kernel: *pde = 00000000 
Apr 17 21:57:40 desktop kernel: Oops: 0000 [#1] PREEMPT SMP 
Apr 17 21:57:40 desktop kernel: last sysfs file: /sys/module/snd_timer/initstate
Apr 17 21:57:40 desktop kernel: Modules linked in: snd_seq_oss(+) snd_seq_midi_event snd_seq radeon(+) ttm drm_kms_helper drm snd_pcm_oss snd_mixer_oss agpgart i2c_algo_bit snd_emu10k1(+) snd_rawmidi fan snd_via82xx_modem(+) snd_ac97_codec ac97_bus snd_seq_device snd_util_mem snd_hwdep snd_pcm snd_timer firewire_ohci uhci_hcd snd i2c_viapro emu10k1_gp lp soundcore snd_page_alloc psmouse button thermal processor ppdev firewire_core crc_itu_t shpchp i2c_core ehci_hcd gameport sg usbcore evdev serio_raw via_rhine mii pci_hotplug pcspkr parport_pc parport tpm_tis tpm tpm_bios rtc_cmos rtc_core rtc_lib ext4 mbcache jbd2 crc16 sr_mod sd_mod cdrom sata_via ata_generic pata_acpi pata_via libata scsi_mod
Apr 17 21:57:40 desktop kernel: 
Apr 17 21:57:40 desktop kernel: Pid: 1885, comm: modprobe Not tainted 2.6.33-ARCH #1 Kelut /PP163AA-ABA A800N
Apr 17 21:57:40 desktop kernel: EIP: 0060:[<f8ae0c84>] EFLAGS: 00010286 CPU: 0
Apr 17 21:57:40 desktop kernel: EIP is at radeon_agp_init+0x14/0x3d0 [radeon]
Apr 17 21:57:40 desktop kernel: EAX: f6b92400 EBX: f7025000 ECX: f73d2600 EDX: 00000000
Apr 17 21:57:40 desktop kernel: ESI: 00000000 EDI: 00000024 EBP: f6531d68 ESP: f6531d14
Apr 17 21:57:40 desktop kernel: DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Apr 17 21:57:40 desktop kernel: Process modprobe (pid: 1885, ti=f6530000 task=f67791c0 task.ti=f6530000)
Apr 17 21:57:40 desktop kernel: Stack:
Apr 17 21:57:40 desktop kernel: f8b55794 00000001 f7025000 f6531d3c f8adc5bd f73d2600 00000001 f7025000
Apr 17 21:57:40 desktop kernel: <0> 00000000 f702567c f6531d44 f8aeaf92 f6531d68 f8aeb2f9 00000024 f6531d58
Apr 17 21:57:40 desktop kernel: <0> f8b3aa02 00000282 f7025000 00000000 00000024 f6531d90 f8b2dd65 201a9551
Apr 17 21:57:40 desktop kernel: Call Trace:
Apr 17 21:57:40 desktop kernel: [<f8adc5bd>] ? radeon_debugfs_add_files+0x8d/0xe0 [radeon]
Apr 17 21:57:40 desktop kernel: [<f8aeaf92>] ? radeon_debugfs_fence_init+0x12/0x20 [radeon]
Apr 17 21:57:40 desktop kernel: [<f8aeb2f9>] ? radeon_fence_driver_init+0xc9/0x140 [radeon]
Apr 17 21:57:40 desktop kernel: [<f8b3aa02>] ? radeon_debugfs_pm_init+0x12/0x20 [radeon]
Apr 17 21:57:40 desktop kernel: [<f8b2dd65>] ? rv770_init+0x1e5/0x2d0 [radeon]
Apr 17 21:57:40 desktop kernel: [<c1204de3>] ? vga_client_register+0x63/0x80
Apr 17 21:57:40 desktop kernel: [<f8adcd47>] ? radeon_device_init+0x227/0x2f0 [radeon]
Apr 17 21:57:40 desktop kernel: [<f8adc0f0>] ? radeon_vga_set_decode+0x0/0x20 [radeon]
Apr 17 21:57:40 desktop kernel: [<f8add9d6>] ? radeon_driver_load_kms+0x76/0x1b0 [radeon]
Apr 17 21:57:40 desktop kernel: [<f899c498>] ? drm_get_dev+0x2b8/0x4e0 [drm]
Apr 17 21:57:40 desktop kernel: [<c12d2c7b>] ? mutex_lock+0xb/0x20
Apr 17 21:57:40 desktop kernel: [<f8b3d3e0>] ? radeon_pci_probe+0xd/0x177 [radeon]
Apr 17 21:57:40 desktop kernel: [<c119ac3e>] ? local_pci_probe+0xe/0x10
Apr 17 21:57:40 desktop kernel: [<c119b9b0>] ? pci_device_probe+0x60/0x80
Apr 17 21:57:40 desktop kernel: [<c1210ea7>] ? driver_probe_device+0x77/0x170
Apr 17 21:57:40 desktop kernel: [<c1211019>] ? __driver_attach+0x79/0x80
Apr 17 21:57:40 desktop kernel: [<c12106e8>] ? bus_for_each_dev+0x48/0x70
Apr 17 21:57:40 desktop kernel: [<c1210d49>] ? driver_attach+0x19/0x20
Apr 17 21:57:40 desktop kernel: [<c1210fa0>] ? __driver_attach+0x0/0x80
Apr 17 21:57:40 desktop kernel: [<c120ffef>] ? bus_add_driver+0xbf/0x2c0
Apr 17 21:57:40 desktop kernel: [<c119b8f0>] ? pci_device_remove+0x0/0x40
Apr 17 21:57:40 desktop kernel: [<c12112b5>] ? driver_register+0x65/0x120
Apr 17 21:57:40 desktop kernel: [<c12d2868>] ? mutex_unlock+0x8/0x10
Apr 17 21:57:40 desktop kernel: [<c119bbd0>] ? __pci_register_driver+0x40/0xb0
Apr 17 21:57:40 desktop kernel: [<f89974ab>] ? drm_init+0xeb/0x100 [drm]
Apr 17 21:57:40 desktop kernel: [<f8b650b2>] ? radeon_init+0xb2/0xb4 [radeon]
Apr 17 21:57:40 desktop kernel: [<c100112d>] ? do_one_initcall+0x2d/0x190
Apr 17 21:57:40 desktop kernel: [<f8b65000>] ? radeon_init+0x0/0xb4 [radeon]
Apr 17 21:57:40 desktop kernel: [<c10797a1>] ? sys_init_module+0xb1/0x220
Apr 17 21:57:40 desktop kernel: [<c100389f>] ? sysenter_do_call+0x12/0x28
Apr 17 21:57:40 desktop kernel: Code: 8d b4 26 00 00 00 00 e8 1b c8 eb ff 5d 66 90 c3 8d b4 26 00 00 00 00 55 89 e5 57 56 53 89 c3 83 ec 48 8b 40 04 8b 90 38 02 00 00 <8b> 4a 40 85 c9 75 12 e8 60 c7 eb ff 85 c0 89 c7 0f 85 1d 03 00 
Apr 17 21:57:40 desktop kernel: EIP: [<f8ae0c84>] radeon_agp_init+0x14/0x3d0 [radeon] SS:ESP 0068:f6531d14
Apr 17 21:57:40 desktop kernel: CR2: 0000000000000040
Apr 17 21:57:40 desktop kernel: VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
Apr 17 21:57:40 desktop kernel: usb 1-3: new high speed USB device using ehci_hcd and address 6
Apr 17 21:57:40 desktop kernel: ---[ end trace 784b2a7ade9eb1ea ]---

```

Looks like: [http://permalink.gmane.org/gmane.linux.drivers.e1000.devel/6841](http://permalink.gmane.org/gmane.linux.drivers.e1000.devel/6841) and [http://permalink.gmane.org/gmane.comp.video.dri.devel/45181](http://permalink.gmane.org/gmane.comp.video.dri.devel/45181)

But maybe I'm just paranoid...

---

### Post by kelvin spratt on 2010-04-18
have you put "hal" in etc/conf/deamons list so your mouse and keyboard work. this is mine
i'm on a desktop. DAEMONS=(!!addmods syslog-ng @network @!ntpdate @ntp dbus hal @rpcbind !stbd alsa gdm @cups  !!!crond )  add ! = disable  @= to start in background.

---

### Post by wilee-nilee on 2010-04-18
> **kelvin spratt said:**
> have you put "hal" in etc/conf/deamons list so your mouse and keyboard work. this is mine
i'm on a desktop. DAEMONS=(!!addmods syslog-ng @network @!ntpdate @ntp dbus hal @rpcbind !stbd alsa gdm @cups  !!!crond )  add ! = disable  @= to start in background.

That was my problem on a first install last week no hal=no mouse or keyboard and what seemed like kernel panic.

---

### Post by Zerp64 on 2010-04-18
Did uh... did you guys see what I posted..?

---

### Post by kelvin spratt on 2010-04-18
So what did you post.
You should not have to blacklist your internal graphic card in arch. It should be disabled in your bias. the same as I do then it does not load after post.
You really need to be asking this on the Arch forum not on here would you get help on a windows forum for Linux, I don't think so. If you want answers fast use the Arch irc channel word your questions correct you will get answers. Have you by any chance been told something you don't like on the Arch forum as I find folks there very friendly.[http://wiki.archlinux.org/index.php/Post_Installation_Tips#End_of_the_Boot_Process](http://wiki.archlinux.org/index.php/Post_Installation_Tips#End_of_the_Boot_Process)

---

