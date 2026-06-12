---
title: "Last set of gstreamer updates, lost volume control applet, no pauvcontrol"
date: 2009-11-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-11-22
Basically as title, pauvcontrol gives connection "failed:connection refused" will check for updates and see if dependencies is the answer.
Anyone else ?

---

### Post by ranch hand on 2009-11-22
Yup, having that problem with my 9.04>9.10>10.04 upgrade.  The 9.10>10.04 and the 10.04 both are fine.

This is causing some serious lock ups on this install and I can't seem to get anything to fix it.

---

### Post by psyke83 on 2009-11-22
As I mentioned in another thread - if you've been testing my equalizer, it could be the cause. Please give me the "pulseaudio-equalizer.sh debug" log first, and then you can reset to defaults (or uncheck Keep Settings) to get things working again.

---

### Post by ranch hand on 2009-11-22
I have an Audigy1 5.1 card in here and the gnome-alsamixer is what I use.  Works great.  Still works great but there is no little "speaker" volume applet.

This is worrying because, besides the lockups, every so often I have had to use that applet to "wiggle" the volume control to get sound.  Haven't had to, so far, since it disappeared.

---

### Post by Regenweald on 2009-11-22
> **psyke83 said:**
> As I mentioned in another thread - if you've been testing my equalizer, it could be the cause. Please give me the "pulseaudio-equalizer.sh debug" log first, and then you can reset to defaults (or uncheck Keep Settings) to get things working again.

Missed that, thanks ;) Log:
```

State: Initial state
---
SCRIPT_VERSION=2.4 (19/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=0
PA_EQUALIZER_PERSISTENCE=1
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-13.7,-17.9,-17.9
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=alsa_output.pci-0000_00_05.0.analog-stereo
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=alsa_output.pci-0000_00_05.0.analog-stereo
PA_CURRENT_MUTE=0
PA_CURRENT_VOLUME=100
PA_REAL_VOLUME=65536
PA_PREAMP=1.5
PA_REAL_PREAMP=
### BEGIN: Equalized audio configuration
### Generated from: pulseaudio-equalizer.sh
load-module module-ladspa-sink sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_05.0.analog-stereo plugin=mbeq_1197 label=mbeq control=-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-13.7,-17.9,-17.9
set-default-sink ladspa_output.mbeq_1197.mbeq
set-sink-volume alsa_output.pci-0000_00_05.0.analog-stereo 
set-sink-mute alsa_output.pci-0000_00_05.0.analog-stereo 0
### END: Equalized audio configuration
---

State: Disabled [not saved]
---
SCRIPT_VERSION=2.4 (19/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=0
PA_EQUALIZER_PERSISTENCE=0
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-13.7,-17.9,-17.9
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=alsa_output.pci-0000_00_05.0.analog-stereo
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=alsa_output.pci-0000_00_05.0.analog-stereo
PA_CURRENT_MUTE=0
PA_CURRENT_VOLUME=100
PA_REAL_VOLUME=65536
PA_PREAMP=1.5
PA_REAL_PREAMP=
---

State: Enabled [not saved]
---
SCRIPT_VERSION=2.4 (19/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=1
PA_EQUALIZER_PERSISTENCE=0
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-13.7,-17.9,-17.9
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=alsa_output.pci-0000_00_05.0.analog-stereo
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_MUTE=0
PA_CURRENT_VOLUME=100
PA_REAL_VOLUME=65536
PA_PREAMP=1.5
PA_REAL_PREAMP=
---

State: Disabled [saved]
---
SCRIPT_VERSION=2.4 (19/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=0
PA_EQUALIZER_PERSISTENCE=1
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-13.7,-17.9,-17.9
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=alsa_output.pci-0000_00_05.0.analog-stereo
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=alsa_output.pci-0000_00_05.0.analog-stereo
PA_CURRENT_MUTE=0
PA_CURRENT_VOLUME=100
PA_REAL_VOLUME=65536
PA_PREAMP=1.5
PA_REAL_PREAMP=
### BEGIN: Equalized audio configuration
### Generated from: pulseaudio-equalizer.sh
load-module module-ladspa-sink sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_05.0.analog-stereo plugin=mbeq_1197 label=mbeq control=-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-13.7,-17.9,-17.9
set-default-sink ladspa_output.mbeq_1197.mbeq
set-sink-volume alsa_output.pci-0000_00_05.0.analog-stereo 
set-sink-mute alsa_output.pci-0000_00_05.0.analog-stereo 0
### END: Equalized audio configuration
---

State: Enabled [saved]
---
SCRIPT_VERSION=2.4 (19/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=1
PA_EQUALIZER_PERSISTENCE=1
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-13.7,-17.9,-17.9
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=alsa_output.pci-0000_00_05.0.analog-stereo
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_MUTE=0
PA_CURRENT_VOLUME=100
PA_REAL_VOLUME=65536
PA_PREAMP=1.5
PA_REAL_PREAMP=
### BEGIN: Equalized audio configuration
### Generated from: pulseaudio-equalizer.sh
load-module module-ladspa-sink sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_05.0.analog-stereo plugin=mbeq_1197 label=mbeq control=-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-0.2,-13.7,-17.9,-17.9
set-default-sink ladspa_output.mbeq_1197.mbeq
set-sink-volume alsa_output.pci-0000_00_05.0.analog-stereo 
set-sink-mute alsa_output.pci-0000_00_05.0.analog-stereo 0
### END: Equalized audio configuration
---


```

---

