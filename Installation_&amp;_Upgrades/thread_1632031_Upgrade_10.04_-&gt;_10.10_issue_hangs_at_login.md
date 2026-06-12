---
title: "Upgrade 10.04 -&gt; 10.10 issue: hangs at login"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by LexMortis on 2010-11-27
Hi all,

Recently I decided to upgrade my 10.04 installation the lazy way, by clicking the upgrade button instead of a clean install (32bit). Please bare with me as Ive already tested a lot, so big post...

Now, I can only get into Ubuntu with the recovery mode.

If I let the system boot the normal way, I end up at the login screen where I (correctly) enter my password and then nothing else happens. I can move the mouse, the clock ticks on, and I can even use the restart button, etc. But the login screen stays gray and does nothing else, so no desktop.

With recovery-mode I can use the failsafeX option to get into the desktop, everything works fine there. And even though it calls it a low-graphics environment or so, everything looks normal, its even my native resolution of 1440x900.

My first idea was some driver issue for my Ati Radeon HD 2600 Mobility card, so I looked into that. I've checked/done the following:

- Installed the drivers manually (downloaded from AMD)
- Uninstalled those drivers
- Used aptitude to remove any fglrx things
- Installed Jockey
- Installed the drivers with Jockey
- Removed the drivers with Jockey (Ive read this is the cleanest option)
- "no drivers" at this point
- Use generic/default X config, make specific X config (both from the failsafe X boot thing)

Nothing helped at all, booting still only works with recovery option and then the low graphics mode. Otherwise, it will just "hang" on the login part.

When I boot first recovery mode, and then pick the resume option, I'll see some errors near the end of the booting process.

Ive seen 2 errors which might be related to my issue:
- "Unable to allocate crypto cipher with name [ecb(aes)]" (home is encrypted, and accessible with safe boot)
- BUG: CPU#1 stuck for 61s!

Now, the second error seems to "match" with hanging at login. I login, something is stuck and churns the CPU... and never gets unstuck, so login just hangs there. However, I can't find any information related to that stuck CPU thing. Only changing PIDs and other numbers/stack traces, no processname or any other name to work with. So I'm at a loss here.

Big dump of possibly interesting part of kern.log:

```

Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572381] BUG: unable to handle kernel NULL pointer dereference at 00000021
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572386] IP: [<c027c1b0>] sysfs_delete_link+0x30/0x70
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572397] *pdpt = 0000000035f29001 *pde = 0000000000000000
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572401] Oops: 0000 [#1] SMP
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572404] last sysfs file: /sys/devices/pci0000:00/0000:00:13.5/usb1/1-9/1-9:1.0/asus_oled/oled_1/picture
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572408] Modules linked in: binfmt_misc rfcomm sco bnep l2cap parport_pc ppdev dm_crypt snd_hda_codec_atihdmi snd_hda_codec_si305$
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572454]
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572459] Pid: 1607, comm: rmmod Tainted: P         C  2.6.35-23-generic-pae #40-Ubuntu G2K       /G2K
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572463] EIP: 0060:[<c027c1b0>] EFLAGS: 00010282 CPU: 1
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572466] EIP is at sysfs_delete_link+0x30/0x70
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572469] EAX: f5390a20 EBX: c14e63cc ECX: f5340788 EDX: 00000000
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572471] ESI: c1403e08 EDI: f5340788 EBP: f5fb7e54 ESP: f5fb7e48
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572474]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572477] Process rmmod (pid: 1607, ti=f5fb6000 task=f4c88cb0 task.ti=f5fb6000)
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572479] Stack:
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572481]  c1403e08 c1403e00 c16a6a1c f5fb7e64 c04120fe c1403e00 c1616a40 f5fb7e78
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572487] <0> c0412497 c1403e00 c16a6a1c c16a6a00 f5fb7e84 c04125c0 c1616900 f5fb7ea4
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572493] <0> f8bcf467 c04978b1 00000000 c14f6400 c16a6a00 c16a6a1c f8bd0680 f5fb7ec0
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572508]  [<c04120fe>] ? device_remove_class_symlinks+0x4e/0x70
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572512]  [<c0412497>] ? device_del+0x67/0x180
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572515]  [<c04125c0>] ? device_unregister+0x10/0x20
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572520]  [<f8bcf467>] ? asus_oled_disconnect+0x47/0xb0 [asus_oled]
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572525]  [<c04978b1>] ? usb_disable_interface+0x41/0x60
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572530]  [<c049aad0>] ? usb_unbind_interface+0x40/0x150
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572534]  [<c0415031>] ? __device_release_driver+0x51/0xb0
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572537]  [<c041511f>] ? driver_detach+0x8f/0xa0
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572541]  [<c04142f3>] ? bus_remove_driver+0x63/0xa0
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572545]  [<c04156d9>] ? driver_unregister+0x49/0x80
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572549]  [<c027a694>] ? sysfs_remove_file+0x14/0x20
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572552]  [<c049a8a5>] ? usb_deregister+0xa5/0xb0
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572557]  [<f8bd01cb>] ? asus_oled_exit+0x2b/0x2d [asus_oled]
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572563]  [<c01867dd>] ? sys_delete_module+0x13d/0x200
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572568]  [<c02018f2>] ? do_munmap+0x212/0x300
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572574]  [<c010939f>] ? sysenter_do_call+0x12/0x28
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572577] Code: 0c 89 1c 24 89 74 24 04 89 7c 24 08 0f 1f 44 00 00 89 d6 89 c3 b8 44 f7 9d c0 89 cf e8 2a 43 37 00 8b 46 18 85 c0 $
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572609] EIP: [<c027c1b0>] sysfs_delete_link+0x30/0x70 SS:ESP 0068:f5fb7e48
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572614] CR2: 0000000000000021
Nov 26 20:31:25 lexmortis-laptop kernel: [   44.572618] ---[ end trace 4127c1143962ee98 ]---
Nov 26 20:33:03 lexmortis-laptop kernel: [  142.788022] Unable to allocate crypto cipher with name [ecb(aes)]; rc = [-110]
Nov 26 20:33:03 lexmortis-laptop kernel: [  142.788028] Error attempting to initialize key TFM cipher with name = [aes]; rc = [-110]
Nov 26 20:33:03 lexmortis-laptop kernel: [  142.788032] Error attempting to initialize cipher with name = [aes] and key size = [16]; rc = [-110]
Nov 26 20:33:03 lexmortis-laptop kernel: [  142.788037] Error parsing options; rc = [-22]
Nov 26 20:33:08 lexmortis-laptop kernel: [  148.177003] BUG: soft lockup - CPU#1 stuck for 61s! [modprobe:1754]
Nov 26 20:33:08 lexmortis-laptop kernel: [  148.177006] Modules linked in: aes_i586(+) aes_generic binfmt_misc rfcomm sco bnep l2cap parport_pc ppdev dm_crypt snd_hda_codec_ati$
Nov 26 20:33:08 lexmortis-laptop kernel: [  148.177006] Modules linked in: aes_i586(+) aes_generic binfmt_misc rfcomm sco bnep l2cap parport_pc ppdev dm_crypt snd_hda_codec_ati$
Nov 26 20:33:08 lexNov 26 20:36:38 lexmortis-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.

```

Despite that with low graphics mode everything works, it seems to be a non-graphical issue here (stuck CPU on some process?). Unless I missed another option I can test for the graphics/drivers. Any clue where/how I could find more info on stuck CPUs during boot?

Any help/tips would be greatly appreciated, thanks in advance.

---

### Post by LexMortis on 2010-11-27
It's fixed! :)

A friend helped me out, and he said that it looks like asus_oled was the culprit. I removed that module and rebooted, now it all works fine. 

I hope this post can help others with similar issues, here is partially how he figured it out:

The top of the dump shows "Oops" followed by "asus_oled" stuff. Right after that there is the tainted kernel line. Tainted kernel with "P" == kernel plus proprietary modules. So put 2 and 2 together, and you come to the conclusion that the module might be iffy. After removing the module, which can be found in: /lib/module/<version>/extra, it all works fine.

---

