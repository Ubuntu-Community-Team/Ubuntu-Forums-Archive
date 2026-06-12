---
title: "sound out of control !"
date: 2005-08-18
forum: Installation &amp; Upgrades
---

### Post by art2003 on 2005-08-18
The volume control icon no longer controls the sound at all (mute doesn't work and the sliding bar doesn't make any difference)

Other than that I have sound configured as I wanted
with output through USB speakers/sound card and mic input through a quickcam with built-in micro.
On gstreamerproperties, both ESD and ALSA work when tested, but OSS gives a pipes error.

can somebody look at my asound.conf and suggest the necessary changes to get iit working properly?


# The top level shared pseudo device, with both PCM and CTL interfaces
# The ALSA default is "!default", but many programs like XMMS and aoss
# assume "dsp0" as default name for PCM and "mixer0" for CTL.

# Amazingly, XMMS has problems if one defines 'pcm.dsp0' to be
# 'plug' for 'pcm.asym0' and not directly as 'asym0'.

pcm.!default		{ type			asym;
			  capture.pcm		"dsnoop0";
			  playback.pcm		"dmix0"; }
ctl.!default		{ type hw; card 2; }

pcm.dsp0		{ type			asym;
			  capture.pcm		"dsnoop0";
			  playback.pcm		"dmix0"; } 
ctl.dsp0		{ type hw; card 0; }
ctl.mixer0		{ type hw; card 0; }
pcm.dsp1                { type hw; card 0; }
ctl.dsp1                { type hw; card 0; }
ctl.dsp2                { type hw; card 3; }
pcm.dsp2                { type  asym;
                           capture.pcm "hw:3,0"; }
########################################################################

pcm.asym0		{ type			asym;
			  capture.pcm		"dsnoop0";
			  playback.pcm		"dmix0"; }

pcm.dsnoop0		{ type			dsnoop;
			  ipc_key		13758;
			  slave.pcm		"hw:3,0"; }

# xxxxxxxx
#pcm.card0 {
#type hw
#card 0
#}


pcm.dmix0 {
type dmix
ipc_key 1025
slave {
pcm "hw:1,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

---

