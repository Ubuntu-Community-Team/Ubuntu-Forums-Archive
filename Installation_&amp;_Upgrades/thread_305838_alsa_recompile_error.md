---
title: "alsa recompile error"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by naga123 on 2006-11-24
Hi all,
  I installed alsa drivers and tried to insert modules into the kernel. But I got the following error.... Plz help me regarding this.

# modprobe snd-via82xx;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss
FATAL: Error inserting snd_via82xx (/lib/modules/2.6.17-10-generic/kernel/sound/pci/snd-via82xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_via82xx
FATAL: Error inserting snd_seq (/lib/modules/2.6.17-10-generic/kernel/sound/acore/seq/snd-seq.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_seq
WARNING: Error inserting snd_seq_midi_event (/lib/modules/2.6.17-10-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.17-10-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

