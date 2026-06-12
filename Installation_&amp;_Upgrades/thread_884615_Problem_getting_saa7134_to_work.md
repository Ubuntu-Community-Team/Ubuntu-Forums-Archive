---
title: "Problem getting saa7134 to work"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by BiscuitTin on 2008-08-09
My Sony Media centre has a built in saa7134 chipset based TV/DVB card, however although the system appears to recognise the card, it doesn't seem to hook the appropriate drivers, consequently the card is not visible to any applications (using MeTv and MythTV).

lsmod |grep 7134 gives me this:

saa7134_dvb            21644  0
videobuf_dvb            7812  1 saa7134_dvb
dvb_core               81404  2 saa7134_dvb,videobuf_dvb
saa7134               147924  1 saa7134_dvb
ir_common              42244  1 saa7134
videodev               36864  2 tuner,saa7134[/HTML]
compat_ioctl32          2304  1 saa7134
v4l2_common            12672  2 tuner,saa7134
videobuf_dma_sg        14980  2 saa7134_dvb,saa7134
videobuf_core          19716  3 videobuf_dvb,saa7134,videobuf_dma_sg
tveeprom               13444  1 saa7134
i2c_core               24832  6 tda1004x,saa7134_dvb,tuner,saa7134,v4l2_common,tveeprom

However is dmesg I get this:

[   22.713494] ata5.00: ATAPI: SONY    DVD RW AW-G540A, 1.X0, max UDMA/33
[   34.194569] saa7134_alsa: disagrees about version of symbol saa7134_tvaudio_setmute
[   34.194575] saa7134_alsa: Unknown symbol saa7134_tvaudio_setmute
[   34.194787] saa7134_alsa: disagrees about version of symbol saa_dsp_writel
[   34.194789] saa7134_alsa: Unknown symbol saa_dsp_writel
[   34.194956] saa7134_alsa: disagrees about version of symbol videobuf_dma_free
[   34.194958] saa7134_alsa: Unknown symbol videobuf_dma_free
[   34.195153] saa7134_alsa: disagrees about version of symbol saa7134_pgtable_alloc
[   34.195156] saa7134_alsa: Unknown symbol saa7134_pgtable_alloc
[   34.195202] saa7134_alsa: disagrees about version of symbol saa7134_pgtable_build
[   34.195205] saa7134_alsa: Unknown symbol saa7134_pgtable_build
[   34.195244] saa7134_alsa: disagrees about version of symbol saa7134_pgtable_free
[   34.195246] saa7134_alsa: Unknown symbol saa7134_pgtable_free
[   34.195285] saa7134_alsa: disagrees about version of symbol saa7134_dmasound_init
[   34.195287] saa7134_alsa: Unknown symbol saa7134_dmasound_init
[   34.195413] saa7134_alsa: disagrees about version of symbol saa7134_dmasound_exit
[   34.195415] saa7134_alsa: Unknown symbol saa7134_dmasound_exit
[   34.195508] saa7134_alsa: disagrees about version of symbol videobuf_dma_init
[   34.195510] saa7134_alsa: Unknown symbol videobuf_dma_init
[   34.195646] saa7134_alsa: disagrees about version of symbol videobuf_dma_init_kernel
[   34.195648] saa7134_alsa: Unknown symbol videobuf_dma_init_kernel
[   34.195753] saa7134_alsa: Unknown symbol videobuf_pci_dma_unmap
[   34.195880] saa7134_alsa: Unknown symbol videobuf_pci_dma_map
[   34.195925] saa7134_alsa: disagrees about version of symbol saa7134_set_dmabits
[   34.195927] saa7134_alsa: Unknown symbol saa7134_set_dmabits
[ 1682.188507] saa7134_alsa: disagrees about version of symbol saa7134_tvaudio_setmute
[ 1682.188515] saa7134_alsa: Unknown symbol saa7134_tvaudio_setmute
[ 1682.188663] saa7134_alsa: disagrees about version of symbol saa_dsp_writel
[ 1682.188666] saa7134_alsa: Unknown symbol saa_dsp_writel
[ 1682.188835] saa7134_alsa: disagrees about version of symbol videobuf_dma_free
[ 1682.188838] saa7134_alsa: Unknown symbol videobuf_dma_free
[ 1682.189027] saa7134_alsa: disagrees about version of symbol saa7134_pgtable_alloc
[ 1682.189031] saa7134_alsa: Unknown symbol saa7134_pgtable_alloc
:
[ 1682.189080] saa7134_alsa: Unknown symbol saa7134_pgtable_build

I am also not getting a /dev/dvb directory or any decives under it.

uname -a returns:
Linux tinman 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

Can someone please give me a clue as to what is wrong?

---

### Post by caillean on 2008-08-18
Hey BiscuitTin,

I'm not sure about your problem, but I have a saa7134 card, too, and I here's what I figured out to get it working.

Your lsmod output shows v4l-common.You'll need v4l-dvb to use the card for digital TV. You can download it from [http://linuxtv.org]("http://linuxtv.org").

Perhaps you will have to provide the firmware for the card's tuner to the kernel's hotplug service. After installing v4l-dvb there should be a dvb folder in /usr/src/Documentation, containing a script "get_dvb_firmware" that will download the firmware for you. Copy the *.fw file to /lib/firmware.

Make sure the saa7134_dvb module is loaded automatically during boot.

I hope this will help, anyway, it worked for me...

Greetings,
Caillean

---

