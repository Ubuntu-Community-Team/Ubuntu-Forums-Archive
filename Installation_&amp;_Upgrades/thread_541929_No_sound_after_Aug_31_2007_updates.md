---
title: "No sound after Aug 31 2007 updates"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by foxmuldr on 2007-09-03
The kernel update the other day was 2.6.20-16-generic (#2 SMP Fri Aug 31 00:55:27 UTC 2007).  After the update and required reboot, no sound.

I have an ASUS M2N32-SLI Premium motherboard, Athlon X2 4400+ CPU.  Everything worked fine.  Now, I see this:

ALSA lib confmisc.c:670: (snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500: (_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3500: (_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070: (snd_func_refer) error evaluating name
ALSA lib conf.c:3500: (_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968: (snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145: (snd_pcm_open_noupdate) Unknown PCM default

Any ideas?  I can provide more info, just tell me what.

---

### Post by linuxwizard on 2007-09-03
Try booting your computer using the 2.6.20-15 kernel and see if your sound comes back.

[http://ubuntuforums.org/showthread.php?t=540966](http://ubuntuforums.org/showthread.php?t=540966)

---

### Post by foxmuldr on 2007-09-03
2.6.20-generic-15 kernel is no longer on my system.  Only 16.  How can I revert a previous version manually (suppose I wanted to go to 10 or 12 even, how then)?

---

### Post by Gremlinzzz on 2007-09-03
See if 2.6.20-15 is in your synaptic package manager
put linux-image in the search window

---

### Post by linuxwizard on 2007-09-03
Did you delete/remove 2.6.20-generic-15 kernel or you just don't see it?

Try this
If you need to get into the grub menu, to modify boot options or choose a different kernel, you need to press 'ESC' just after it starts. By default you have to press 'ESC' very quickly.After pressing 'ESC' you will be presented with a list of kernels and operating systems that you can boot.

---

### Post by froebi on 2007-09-03
Hi,

I experience the same thing: no sound for my anymore after this update. My motherboard is an ASUSM2V. Sound driver is hda-intel with these options (had a hard time to figure them out):
options snd-hda-intel model=3stack-660

dmesg shows this:
```
[   15.784000] snd_rawmidi: Unknown symbol snd_register_device
[   15.788000] snd_seq_midi: Unknown symbol snd_rawmidi_info_select
[   15.788000] snd_seq_midi: Unknown symbol snd_rawmidi_output_params
[   15.788000] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_read
[   15.788000] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_write
[   15.788000] snd_seq_midi: Unknown symbol snd_rawmidi_drain_output
[   15.788000] snd_seq_midi: Unknown symbol snd_rawmidi_input_params
[   15.788000] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_open
[   15.788000] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_release
[   16.016000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   16.016000] snd_hda_codec: Unknown symbol snd_ctl_add
[   16.016000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   16.016000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   16.016000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   16.016000] snd_hda_codec: Unknown symbol snd_ctl_new1
[   16.016000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_list
[   16.016000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[   16.016000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[   16.016000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[   16.016000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   16.016000] snd_hda_intel: Unknown symbol snd_pcm_new
[   16.016000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   16.016000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   16.016000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   16.016000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   16.020000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[   16.020000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[   16.020000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[   16.020000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[   16.020000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   16.020000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   16.020000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   16.020000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   16.020000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   16.020000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   16.020000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[   16.020000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   16.020000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   16.020000] snd_hda_intel: Unknown symbol snd_hda_suspend
[   16.020000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   16.020000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   16.020000] snd_hda_intel: Unknown symbol snd_hda_resume
[   16.020000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   16.020000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   16.020000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[   16.020000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   16.020000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   16.020000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   16.020000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step

```

Hope this is helpful to solve this issue. If not, let me know what else you need. -- I'd really like to stick with the updates...

regards,
  Christian

---

### Post by froebi on 2007-09-03
PS: I just tried the 2.6.20-15 kernel. Sound still works with this one.

---

### Post by froebi on 2007-09-03
Oops, sorry, I guess I was a little too fast.

I already mentioned that I had a hard time getting the hda-intel driver to work. Back then I went the hard way of installing Alsa drivers, lib and utils myself. -- It's quite a while ago now, so I completely forgot about it.

Now, with the new kernel, I gave it another shot: I reinstalled the alsa packages. But no luck this time either. So -- again -- I built the alsa stuff myself. After that sound was working again.

But I guess this won't help anyone else here...

---

### Post by foxmuldr on 2007-09-04
> **linuxwizard said:**
> Try booting your computer using the 2.6.20-15 kernel and see if your sound comes back.

After re-installing 2.6.20-15-generic and rebooting the sound did come back.  Still no go in 2.6.20-16-generic with the recent .31 update.

---

### Post by foxmuldr on 2007-09-04
Here's the error message when I'm getting when I follow this tutorial:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[FONT="Courier New"]rick@rick-desktop:~$ sudo modprobe snd-hda-intel
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
[/FONT]

Is it a kernel source issue?  Is there something I don't have installed that I need installed?  I'd like to rebuild my ALSA driver like the other poster said, but don't know how to do it.

---

### Post by foxmuldr on 2007-09-04
Here's the dmesg output:  (Note:  The previous block is at 1991.xxx from previous error.)

[FONT="Courier New"][SIZE="2"][ 2193.636000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[ 2193.636000] snd_hda_codec: Unknown symbol snd_ctl_add
[ 2193.636000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[ 2193.636000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[ 2193.636000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[ 2193.636000] snd_hda_codec: Unknown symbol snd_ctl_new1
[ 2193.636000] snd_hda_codec: disagrees about version of symbol snd_component_add
[ 2193.636000] snd_hda_codec: Unknown symbol snd_component_add
[ 2193.636000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_list
[ 2193.636000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[ 2193.636000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[ 2193.636000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[ 2193.644000] snd_hda_intel: Unknown symbol snd_pcm_new
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[ 2193.644000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_card_register
[ 2193.644000] snd_hda_intel: Unknown symbol snd_card_register
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_card_free
[ 2193.644000] snd_hda_intel: Unknown symbol snd_card_free
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[ 2193.644000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 2193.644000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[ 2193.644000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[ 2193.644000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[ 2193.644000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_card_new
[ 2193.644000] snd_hda_intel: Unknown symbol snd_card_new
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[ 2193.644000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[ 2193.644000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[ 2193.644000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[ 2193.644000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[ 2193.644000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[ 2193.644000] snd_hda_intel: Unknown symbol snd_hda_suspend
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[ 2193.644000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[ 2193.644000] snd_hda_intel: Unknown symbol snd_card_disconnect
[ 2193.644000] snd_hda_intel: Unknown symbol snd_hda_resume
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 2193.644000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[ 2193.644000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[ 2193.644000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[ 2193.644000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[ 2193.644000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
rick@rick-desktop:~$ [/SIZE][/FONT]

---

### Post by foxmuldr on 2007-09-04
When I try to do the ALSA compilation, I get to 6's "sudo make" and I get these errors (no error during ./configure"):

[FONT="Courier New"][SIZE="2"]make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of &#8216;jiffies_to_msecs&#8217;
include/linux/jiffies.h:268: error: previous definition of &#8216;jiffies_to_msecs&#8217; was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of &#8216;msecs_to_jiffies&#8217;
include/linux/jiffies.h:290: error: previous definition of &#8216;msecs_to_jiffies&#8217; was here
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_save_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function &#8216;pci_save_state&#8217;
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_restore_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function &#8216;pci_restore_state&#8217;
make[3]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2
rick@rick-desktop:/usr/src/modules/alsa-driver$ 
[/SIZE][/FONT]

---

### Post by JS Lemming on 2007-09-04
> **foxmuldr said:**
> After re-installing 2.6.20-15-generic and rebooting the sound did come back.  Still no go in 2.6.20-16-generic with the recent .31 update.
I have the exact same problem as you. But I don't know how to re-install my old 2.6.20-15-generic. Can you explain how you did it?

---

### Post by Nuance on 2007-09-04
Also stuck in the same boat. Tried following the cmpreshensive sound guide but got as far as this step. Can't do sudo make.

Can anyone help?

---

### Post by froebi on 2007-09-04
Hi foxmuldr,

if you want to build the Alsa-drivers yourself, here's what I did:

Download from [http://www.alsa-project.org]("http://www.alsa-project.org") the packages alsa-driver, alsa-lib, alsa-utils.

In order to compile the packages you need some other things as well, such as the linux kernel headers (linux-headers*). If something is missing, you should get an error message upon configure or compilation which should give you a hint on what packages are missing.

Then build and install each package:

alsa-lib:
$ ./configure
$ make
$ make install

alsa-driver:
$ ./configure --with-cards=hda-intel
$ make
$ make install

alsa-utils:
$ ./configure
$ make
$ make install

Hope this helps.

---

### Post by schegi on 2007-09-05
Same Problem

System: MacBook Pro SantaRosa

Alsadriver own build with:

"rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-driver alsa
 rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-kernel alsa
 [download patch_realtek.c.diff] [https://bugtrack.alsa-project.org/al...=2097&type=bug](https://bugtrack.alsa-project.org/al...=2097&type=bug)
 cd alsa/alsa-kernel
 patch -p1 < ../../patch_realtek.c.diff
 cd ../alsa-driver
 ./hgcompile
 make
 make install
 /etc/init.d/alsasound stop
 lsmod [verify all snd modules are unloaded]
 modprobe snd-hda-intel
"
Since yesterday dmesg says:

[  953.864000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[  953.864000] snd_hda_codec: Unknown symbol snd_ctl_add
[  953.864000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[  953.864000] snd_hda_codec: Unknown symbol snd_card_proc_new
[  953.864000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[  953.864000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[  953.864000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[  953.864000] snd_hda_codec: Unknown symbol snd_ctl_new1
[  953.864000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_read
[  953.864000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[  953.864000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_write
[  953.864000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[  953.864000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_list
[  953.864000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[  953.864000] snd_hda_codec: disagrees about version of symbol snd_device_new
[  953.864000] snd_hda_codec: Unknown symbol snd_device_new
[  953.864000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
...
..
.
aso

Tryed to restart, again the same

 lspci -v says:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at 9b500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

 but aplay -l only says:

aplay: device_list:222: no soundcard found...

---

### Post by foxmuldr on 2007-09-05
I found the 2.6.20-16.29 download site.  Scroll all the way to the bottom.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/2.6.20-16.29](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/2.6.20-16.29)

---

### Post by foxmuldr on 2007-09-05
It's official:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/137319](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/137319)

---

### Post by foxmuldr on 2007-09-05
The fix/work-around is the alsa-driver, alsa-util, alsa-lib solution suggested above.  Follow the bug tracker link here for instructions:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/137319](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/137319)

alsa-driver
alsa-utils
alsa-lib

Download these packages, untar, recompile each one by one, and then it's fixed.  The sound comes back.

Also, suggest adding some kind of "revert" ability to the debian packaging system.  Something that lets you undo a recent update or upgrade.  It's taken me four days to get to the point where I had the time to take a possible solution and actually get it to work.  That's several days without sound unless I reverted to the 2.6.20-15.27-generic kernel, and that also presented a problem on my system because the proprietary Nvidia driver would not compile for that version, meaning I had to use the built-in NV driver, and that one does not support rotated displays.

---

