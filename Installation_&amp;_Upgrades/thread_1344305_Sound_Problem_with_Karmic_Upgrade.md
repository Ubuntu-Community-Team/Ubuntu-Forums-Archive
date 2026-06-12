---
title: "Sound Problem with Karmic Upgrade"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by claroche on 2009-12-02
Hi all,
So, I upgraded from Jaunty to Karmic a few days ago. I'm on a Macbook and at first the sound didn't work. As was pointed out elsewhere, I simply needed to get ASLA mixer and unmute everything.

However, before I came to this realization, I followed a set of directions on another thread aimed at Macbook users, ostensibly to update their sound kernels.

The first two directions of the thread were:

sudo rm -rf /lib/modules/`uname -r`/kernel/sound

and

sudo aptitude reinstall linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28

I'm reasonably new to ubuntu, but I am guessing that the first one deleted my sound kernel directory. The second command did not work -- "Couldn't find any package whose name or description matched "linux-headers-2.6.28-13-generic"

In any case, I gave up, found the ALSA mixer fix thread, which worked, but later rebooted. Lo and behold my computer no longer plays any sound post-reboot; the volume icon says there is no sound card installed.

How can I rectify the damage wrought by the "sudo rm -rf /lib/modules/`uname -r`/kernel/sound" command?

Note: I've gone through [this thread]("https://help.ubuntu.com/community/SoundTroubleshooting") step-by step. Here are my results:

COMMAND: aplay -l
RESULT: device_list:223: no soundcards found..

COMMAND: find /lib/modules/`uname -r` | grep snd
RESULT: /lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd-hrtimer.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd-pcm.ko
larochec@HAL9000:~$ sudo adduser larochec sound
adduser: The group `sound' does not exist.
larochec@HAL9000:~$ sudo aplay -l
aplay: device_list:223: no soundcards found...
larochec@HAL9000:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-opl3-synth.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec-cmedia.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-opti92x-ad1848.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-interwave-stb.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-cs5535audio.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-au8820.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-emux-synth.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-fm801.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-gus-lib.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-sis7019.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-soc-wm-hubs.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-sonicvibes.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-interwave.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-wavefront.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hrtimer.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-pdplus.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-korg1212.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-azt3328.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hifier.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-sb8.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-msnd-classic.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec-ca0110.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ad1848.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ak4114.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-pcm-oss.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-sc6000.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-util-mem.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-via82xx-modem.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-als300.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-atiixp-modem.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-indigodjx.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-seq-virmidi.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-cs8427.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-opl4-lib.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-pcsp.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-au8810.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-mona.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-seq-device.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-maestro3.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-virtuoso.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-wss-lib.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-mpu401.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-nm256.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-indigo.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-rme96.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-emu10k1-synth.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-sb16-dsp.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-indigoiox.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-cs5530.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-bt87x.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-aw2.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-sb8-dsp.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hdsp.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-vxpocket.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-sb-common.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-opl4-synth.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-serial-u16550.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-au8830.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-sb16.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-lx6464es.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-msnd-lib.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-dummy.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-cs4231.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-emu8000-synth.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-es1688.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-gina20.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ice1712.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-es1968.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-opl3sa2.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-usb-audio.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-tea575x-tuner.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-dt019x.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-rme32.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec-via.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-mpu401-uart.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-seq-midi-event.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-mia.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-usb-usx2y.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-cs4281.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-intel.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-vx222.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-als4000.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-via82xx.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hwdep.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-vx-lib.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-pt2258.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hdspm.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-oxygen.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-adlib.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-aloop.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec-conexant.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-layla20.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-es1688-lib.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ice1724.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-cs4236.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-seq-midi-emul.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-mixer-oss.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-timer.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ens1371.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-azt2320.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-pcxhr.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ad1816a.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-page-alloc.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-cs46xx.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-seq-dummy.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-es968.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-riptide.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-darla24.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-seq.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ak4xxx-adda.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-emu10k1x.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ctxfi.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-virmidi.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ens1370.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-seq-midi.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-mtpav.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-cmi8330.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ca0106.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-soc-core.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-rme9652.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-rawmidi.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-mts64.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-i2c.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-oxygen-lib.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-pcm.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-usb-lib.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-tea6330t.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-gusclassic.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-pdaudiocf.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-mixart.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-seq-oss.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ali5451.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ad1889.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-opl3-lib.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-indigodj.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-msnd-pinnacle.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-es18xx.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-portman2x4.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-indigoio.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-emu10k1.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-gusextreme.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-usb-us122l.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-es1938.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec-cirrus.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-sb16-csp.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-opti93x.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec-idt.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-opti92x-cs4231.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-asihpi.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-sbawe.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-cmipci.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-sgalaxy.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-usb-caiaq.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-miro.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-sscape.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ak4113.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-intel8x0.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-als100.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-hda-codec-analog.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ac97-codec.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-echo3g.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-layla24.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-gusmax.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ymfpci.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-atiixp.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-intel8x0m.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-gina24.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-trident.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-ak4117.ko
/lib/modules/2.6.31-15-generic-pae/updates/alsa/snd-darla20.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-twl4030.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-spdif.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/msnd
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/msnd/snd-msnd-classic.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/msnd/snd-msnd-lib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/oss/msnd.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd-hrtimer.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.31-15-generic-pae/kernel/sound/core/snd-pcm.ko

COMMAND: lspci -v | less
RESULT: 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: SigmaTel Device 7680
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at 50440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

COMMAND: wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh
RESULT:  [http://www.alsa-project.org/db/?f=b3856185926c960445790e445492d26a7d8eac41](http://www.alsa-project.org/db/?f=b3856185926c960445790e445492d26a7d8eac41)

Here I notice that my driver version is 1.0.20, but under
!!Loaded ALSA modules
!!------------------
There's nothing.

I've tried the manual installation further down, but this result does not seem to change.

---

### Post by AngelBreath on 2009-12-03
Confirm the problem. I have the same (Intel ICH 7 family) card and no sound. I guess its a bug, i m trying to find a solution for almost 2 months. Nothing in web working.

---

