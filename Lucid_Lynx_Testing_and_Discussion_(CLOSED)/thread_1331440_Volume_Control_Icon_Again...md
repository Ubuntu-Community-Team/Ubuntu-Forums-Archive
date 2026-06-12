---
title: "Volume Control Icon Again.."
date: 2009-11-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-11-19
is missing..note, all I have done is apply updates.  I can see the launcher--it does show up, but no volume control knob i'd guess you say.  Add to panel, just gives me the launcher..Any ideas why it would suddenl disappear again?

---

### Post by sports fan Matt on 2009-11-19
Volume works as designed..not a big thing, just a minor issue.  Any help if ya'll have any is appreciated.

---

### Post by psyke83 on 2009-11-19
It could be related to my equalizer that you tested.

Please give me the output of this command:

```
$ pulseaudio-equalizer.sh log
```

---

### Post by sports fan Matt on 2009-11-19
Ok,,found the issue.  The DEB. that you had provided for pulseaudio-equalizer_2.4_all.deb had been uninstalled.  

Reinstalling it gives me back my icon and the required script: SCRIPT_VERSION=2.4 (19/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=1
PA_EQUALIZER_PERSISTENCE=1
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=alsa_output.pci-0000_00_1b.0.analog-stereo
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_MUTE=0
PA_CURRENT_VOLUME=52
PA_REAL_VOLUME=34078
PA_PREAMP=2
PA_REAL_PREAMP=131072
### BEGIN: Equalized audio configuration
### Generated from: pulseaudio-equalizer.sh
load-module module-ladspa-sink sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=mbeq_1197 label=mbeq control=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
set-default-sink ladspa_output.mbeq_1197.mbeq
set-sink-volume alsa_output.pci-0000_00_1b.0.analog-stereo 131072
set-sink-mute alsa_output.pci-0000_00_1b.0.analog-stereo 0
### END: Equalized audio configuration
All is well:)

---

