---
title: "Nvidia driver broken after kernel update"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by johnrunsubntlnx on 2011-01-29
I had a working ubuntu 10.10 system two days ago with kernel 2.6.35-24.  I have a gtx 460 card so I have the driver from Jockey/Additional Drivers installed.

Two days ago update manager prompted me to install 2.6.35-25.  I've never had problems updating kernels so I did.  I Rebooted my machine and gdm/gnome no longer starts.  I always get stuck on the tty1 screen.  I did some troubleshooting and figured out that my current NVidia drivers seems to be messing it up.  So I booted into my older kernel (2.6.35-24) and removed my NVidia driver.

I used these steps to switch from nvidia to nouveau:
[NvidiaDriverSwitching]("https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching#Problem:  Need to fully remove -nvidia and installing or reinstall -nouveau from scratch")



I can now boot into my latest kernel (2.6.35-25) but now I'm having problems trying to reinstall the nvidia drivers.

jockey sometimes doesn't list any available drivers.  and when it does, it gives me an "System InstallArchive() error"  when trying to install.

I tried installing nvidia-current via apt-get and I get these errors:

```
Setting up nvidia-current (260.19.06-0ubuntu1) ...
Removing old nvidia-current-260.19.06 DKMS files...
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.

Error! Bad conf file.
File: /var/lib/dkms/nvidia-current/260.19.06/source/dkms.conf does not represent
a valid dkms.conf file.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 5
Setting up nvidia-settings (260.19.06-0ubuntu1) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Any suggestions?  Thanks

---

### Post by johnrunsubntlnx on 2011-01-30
any help guys?


my next step is to reinstall ubuntu but I'm trying to avoid that right now because it's too much work.

---

### Post by DinoT1985 on 2011-01-30
> **johnrunsubntlnx said:**
> any help guys?


my next step is to reinstall ubuntu but I'm trying to avoid that right now because it's too much work.
instead of reinstalling, just boot from the old kernel. the new one made my Plymouth go into text mode but everything else seems ok so im noy fussed. however if i boot from an older kernel, i get the graphic Plymouth theme back.

---

### Post by johnrunsubntlnx on 2011-01-31
> **DinoT1985 said:**
> instead of reinstalling, just boot from the old kernel. the new one made my Plymouth go into text mode but everything else seems ok so im noy fussed. however if i boot from an older kernel, i get the graphic Plymouth theme back.

i tried booting into the older kernel and installing nvidia-current using that.  I am still getting the same error


which leads me to think, maybe the latest nvidia (260.19.06) doesn't have proper dkms info in it yet?  just a guess


hope you guys can shed some light

---

### Post by CattyNebulart on 2011-01-31
I'm having the same issue, it looks like the nvida drivers for .25 are not there yet or not working. I haven't seen an issue like this in years, and even then there was a fix within hours. This is very disappointing.

BTW I also have a geforce 460, maybe it's specific to just this type of card?

For now I'll just boot into -24 and wait until a fixed package is out.

---

### Post by duncanmc on 2011-02-01
I think I see a related problem. After applying the latest updates today, my kubuntu 10.10 on Mac Pro no longer boots. It halts with an all blue screen during startup after showing the startup screen writing kubuntu 10.10 and a few dots under them. The problem is seen only under 2.6.35-25-generic kernel. I can boot the previous 2.6.35-22-generic kernel without any problems. I am using NVIDIA GPU GeForce 7300 GT with Nvidia driver. Below is the the end of syslog file. It shows "unable to handle kernel paging request" error.


Feb  1 18:15:15 o-d kernel: [   24.405177] BUG: unable to handle kernel paging request at ffffffffa0de58aa
Feb  1 18:15:15 o-d kernel: [   24.405183] IP: [<ffffffffa0213df8>] _nv026629rm+0x44/0x176 [nvidia]
Feb  1 18:15:15 o-d kernel: [   24.405434] PGD 1a2c067 PUD 1a30063 PMD 46a565067 PTE 0
Feb  1 18:15:15 o-d kernel: [   24.405438] Oops: 0000 [#1] SMP 
Feb  1 18:15:15 o-d kernel: [   24.405441] last sysfs file: /sys/power/state
Feb  1 18:15:15 o-d kernel: [   24.405443] CPU 5 
Feb  1 18:15:15 o-d kernel: [   24.405445] Modules linked in: parport_pc ppdev usbhid ioatdma hid snd_hda_codec_realtek nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi coretemp sbp2 snd_seq_midi_event ieee1394 dca snd_seq snd_timer snd_seq_device i5000_edac applesmc led_class input_polldev snd edac_core i5k_amb soundcore snd_page_alloc shpchp lp parport firewire_ohci firewire_core crc_itu_t e1000e
Feb  1 18:15:15 o-d kernel: [   24.405466] 
Feb  1 18:15:15 o-d kernel: [   24.405468] Pid: 1264, comm: Xorg Tainted: P            2.6.35-25-generic #44-Ubuntu Mac-F4208DA9/MacPro2,1
Feb  1 18:15:15 o-d kernel: [   24.405470] RIP: 0010:[<ffffffffa0213df8>]  [<ffffffffa0213df8>] _nv026629rm+0x44/0x176 [nvidia]
Feb  1 18:15:15 o-d kernel: [   24.405592] RSP: 0018:ffff88045bd29aa8  EFLAGS: 00010282
Feb  1 18:15:15 o-d kernel: [   24.405593] RAX: ffff88045bd7c000 RBX: ffff88045bc28000 RCX: 0000000000000001
Feb  1 18:15:15 o-d kernel: [   24.405595] RDX: ffff88045bd7c000 RSI: 0000000000000016 RDI: ffff88045f81e000
Feb  1 18:15:15 o-d kernel: [   24.405597] RBP: ffff88045d87df68 R08: ffff88045fa00000 R09: ffff880469cb7400
Feb  1 18:15:15 o-d kernel: [   24.405598] R10: 00000000ffffffff R11: 0000000000000077 R12: ffff88045bc2c000
Feb  1 18:15:15 o-d kernel: [   24.405600] R13: ffff88045f81e000 R14: ffff88045bd7c000 R15: ffff88046007c400
Feb  1 18:15:15 o-d kernel: [   24.405602] FS:  00007fa11f7da840(0000) GS:ffff880001f40000(0000) knlGS:0000000000000000
Feb  1 18:15:15 o-d kernel: [   24.405604] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb  1 18:15:15 o-d kernel: [   24.405606] CR2: ffffffffa0de58aa CR3: 00000004600de000 CR4: 00000000000006e0
Feb  1 18:15:15 o-d kernel: [   24.405607] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb  1 18:15:15 o-d kernel: [   24.405609] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb  1 18:15:15 o-d kernel: [   24.405611] Process Xorg (pid: 1264, threadinfo ffff88045bd28000, task ffff880469f696e0)
Feb  1 18:15:15 o-d kernel: [   24.405612] Stack:
Feb  1 18:15:15 o-d kernel: [   24.405613]  ffffc9001294d000 ffff88045f81e000 ffff88045d87dfe8 ffff88045bc2c000
Feb  1 18:15:15 o-d kernel: [   24.405616] <0> ffffc9001294d000 ffffffffa0577e7c ffff8804607c3400 ffff88046007c400
Feb  1 18:15:15 o-d kernel: [   24.405619] <0> ffff88045f81e000 ffffc9001294d000 ffff88046a703800 ffffffffa0578e36
Feb  1 18:15:15 o-d kernel: [   24.405623] Call Trace:
Feb  1 18:15:15 o-d kernel: [   24.405750]  [<ffffffffa0577e7c>] ? _nv002152rm+0x213/0x256 [nvidia]
Feb  1 18:15:15 o-d kernel: [   24.405866]  [<ffffffffa0578e36>] ? _nv002145rm+0x406/0x65a [nvidia]
Feb  1 18:15:15 o-d kernel: [   24.405982]  [<ffffffffa057e8d9>] ? rm_init_adapter+0x89/0xfd [nvidia]
Feb  1 18:15:15 o-d kernel: [   24.406098]  [<ffffffffa059bfde>] ? nv_kern_open+0x5ae/0x760 [nvidia]
Feb  1 18:15:15 o-d kernel: [   24.406103]  [<ffffffff81156e3a>] ? chrdev_open+0x10a/0x200
Feb  1 18:15:15 o-d kernel: [   24.406106]  [<ffffffff81156d30>] ? chrdev_open+0x0/0x200
Feb  1 18:15:15 o-d kernel: [   24.406109]  [<ffffffff81151295>] ? __dentry_open+0xe5/0x330
Feb  1 18:15:15 o-d kernel: [   24.406113]  [<ffffffff81260e0f>] ? security_inode_permission+0x1f/0x30
Feb  1 18:15:15 o-d kernel: [   24.406116]  [<ffffffff811515f4>] ? nameidata_to_filp+0x54/0x70
Feb  1 18:15:15 o-d kernel: [   24.406118]  [<ffffffff8115e358>] ? finish_open+0xe8/0x1d0
Feb  1 18:15:15 o-d kernel: [   24.406121]  [<ffffffff81166fdf>] ? dput+0xdf/0x1b0
Feb  1 18:15:15 o-d kernel: [   24.406123]  [<ffffffff8115f7b6>] ? do_last+0x86/0x460
Feb  1 18:15:15 o-d kernel: [   24.406126]  [<ffffffff81161aeb>] ? do_filp_open+0x21b/0x660
Feb  1 18:15:15 o-d kernel: [   24.406129]  [<ffffffff8116d2fa>] ? alloc_fd+0x10a/0x150
Feb  1 18:15:15 o-d kernel: [   24.406131]  [<ffffffff81151039>] ? do_sys_open+0x69/0x170
Feb  1 18:15:15 o-d kernel: [   24.406134]  [<ffffffff81151180>] ? sys_open+0x20/0x30
Feb  1 18:15:15 o-d kernel: [   24.406138]  [<ffffffff8100a0f2>] ? system_call_fastpath+0x16/0x1b
Feb  1 18:15:15 o-d kernel: [   24.406139] Code: 00 ba 00 00 00 00 be 3d 00 00 00 41 ff 55 20 48 89 c3 b9 01 00 00 00 ba 00 00 00 00 be 16 00 00 00 4c 89 ef 41 ff 55 20 49 89 c6 <48> 8b 05 ab 1a bd 00 48 89 45 10 8b 05 a9 1a bd 00 89 45 18 0f 
Feb  1 18:15:15 o-d kernel: [   24.406164] RIP  [<ffffffffa0213df8>] _nv026629rm+0x44/0x176 [nvidia]
Feb  1 18:15:15 o-d kernel: [   24.406283]  RSP <ffff88045bd29aa8>
Feb  1 18:15:15 o-d kernel: [   24.406284] CR2: ffffffffa0de58aa
Feb  1 18:15:15 o-d kernel: [   24.406287] ---[ end trace 4b5def3ff24962c7 ]---
Feb  1 18:15:15 o-d anacron[1473]: Anacron 2.3 started on 2011-02-01
Feb  1 18:15:15 o-d anacron[1473]: Normal exit (0 jobs run)
Feb  1 18:15:15 o-d init: ssh main process (537) terminated with status 255
Feb  1 18:15:16 o-d avahi-daemon[844]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::21d:4fff:fe44:d678.
Feb  1 18:15:16 o-d avahi-daemon[844]: New relevant interface eth0.IPv6 for mDNS.
Feb  1 18:15:16 o-d avahi-daemon[844]: Registering new address record for fe80::21d:4fff:fe44:d678 on eth0.*.
Feb  1 18:15:16 o-d ntpdate[1503]: step time server 91.189.94.4 offset -0.378777 sec
Feb  1 18:15:18 o-d avahi-daemon[844]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::21d:4fff:fe44:d678.
Feb  1 18:15:18 o-d avahi-daemon[844]: Joining mDNS multicast group on interface eth0.IPv6 with address 2001:2f8:23:100:21d:4fff:fe44:d678.
Feb  1 18:15:18 o-d avahi-daemon[844]: Registering new address record for 2001:2f8:23:100:21d:4fff:fe44:d678 on eth0.*.
Feb  1 18:15:18 o-d avahi-daemon[844]: Withdrawing address record for fe80::21d:4fff:fe44:d678 on eth0.
Feb  1 18:15:25 o-d acpid: client 1264[0:0] has disconnected
Feb  1 18:15:25 o-d kernel: [   34.782814] Adding 7999996k swap on /swapfile.  Priority:-1 extents:2018 across:8161480k 
Feb  1 18:15:25 o-d kernel: Kernel logging (proc) stopped.

---

### Post by johnrunsubntlnx on 2011-02-03
> **CattyNebulart said:**
> I'm having the same issue, it looks like the nvida drivers for .25 are not there yet or not working. I haven't seen an issue like this in years, and even then there was a fix within hours. This is very disappointing.

BTW I also have a geforce 460, maybe it's specific to just this type of card?

For now I'll just boot into -24 and wait until a fixed package is out.

if you're having the same problem i'm having, i figured out how to fix this :D


as far as I understand with my newbie understanding, whenever a new kernel comes out, nvidia drivers are supposed to be rebuilt using the new kernel's headers.  I think dkms is supposed to handle this somehow, that why when i upgraded -22 to -23 to -24 I didn't have any problems.  

but dkms for some reason wasn't able to handle this for the -25 update.


when I uninstalled my nvidia drivers, dkms did not fully remove the dkms nvidia info.  that's why reinstalling it says that i have a bad dkms config, because it's looking at old/missing files



the solution:

I went into /var/lib/dkms and sure enough the old nvidia stuff was there so I deleted/moved them

I tried the reinstall process again and it worked flawlessly.  checking /var/lib/dkms again shows that it now has the -25 files

hope this fix works for you too :D

---

### Post by kouakou on 2012-06-29
works like a champ.... thanks for the help

---

