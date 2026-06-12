---
title: "Upgraded to 10.04 and lack audio."
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by denn0069 on 2010-05-04
I just upgraded to 10.04 and had previously had 9.10 installed. I had removed all the pulseaudio gunk and was using oss. 
Now that I've upgraded it seems to have put pulseaudio back however none of them work when I change the settings through gstreamer-properties. 

Not a Linux pro so not sure what I'll need to do to get my audio back.

Any help is appreciated.
Thank you.

---

### Post by _0R10N on 2010-05-04
Can you post your alsa config and some information about your hardware?. Are you sure you're booting the right kernel?

---

### Post by denn0069 on 2010-05-04
Ya here's some info:

ossinfo
> Version info: OSS 4.2 (b 2002/200911060735) (0x00040100) TRIAL
Platform: Linux/i686 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 (dennmat-desktop)

Number of audio devices:	12
Number of audio engines:	20
Number of MIDI devices:		0
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: oss_audigyls0 AudigyLS interrupts=123382 (123382)
 2: oss_hdaudio0 Intel HD Audio interrupts=548 (36750)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086293e
    Subvendor ID 0x1043829f
     Codec  0: ALC883 (0x10ec0883/0x1043829f)
 3: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices
 0: AudigyLS Mixer (Mixer 0 of device object 1)
 1: High Definition Audio ALC883 (Mixer 0 of device object 2)

Audio devices
AudigyLS front                    /dev/oss/oss_audigyls0/pcm0  (device index 0)
AudigyLS center/lfe               /dev/oss/oss_audigyls0/pcm1  (device index 1)
AudigyLS surround                 /dev/oss/oss_audigyls0/pcm2  (device index 2)
AudigyLS 5.1 output               /dev/oss/oss_audigyls0/pcm3  (device index 3)
HD Audio play front               /dev/oss/oss_hdaudio0/pcm0  (device index 4)
HD Audio play rear                /dev/oss/oss_hdaudio0/pcm1  (device index 5)
HD Audio play center/LFE          /dev/oss/oss_hdaudio0/pcm2  (device index 6)
HD Audio play side                /dev/oss/oss_hdaudio0/pcm3  (device index 7)
HD Audio play pcm4                /dev/oss/oss_hdaudio0/pcm4  (device index 8)
HD Audio play spdif-out           /dev/oss/oss_hdaudio0/spdout0  (device index 9)
HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin0  (device index 10)
HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin1  (device index 11)

Nodes
  /dev/dsp -> /dev/oss/oss_audigyls0/pcm0
  /dev/dsp_in -> /dev/oss/oss_audigyls0/pcm0
  /dev/dsp_out -> /dev/oss/oss_audigyls0/pcm0
  /dev/dsp_ac3 -> /dev/oss/oss_audigyls0/pcm0
  /dev/dsp_mmap -> /dev/oss/oss_audigyls0/pcm0
  /dev/dsp_multich -> /dev/oss/oss_audigyls0/pcm3


Alsa configuration file (not sure if this is what you were refering to)
> #
#  ALSA library configuration file
#

# pre-load the configuration files

@hooks [
	{
		func load
		files [
			"/usr/share/alsa/pulse.conf"
			"/usr/share/alsa/bluetooth.conf"
			"/etc/asound.conf"
			"~/.asoundrc"
		]
		errors false
	}
]

# load card-specific configuration files (on request)

cards.@hooks [
	{
		func load
		files [
			{
				@func concat
				strings [
					{ @func datadir }
					"/cards/aliases.conf"
				]
			}
		]
	}
	{
		func load_for_all_cards
		files [
			{
				@func concat
				strings [
					{ @func datadir }
					"/cards/"
					{ @func private_string }
					".conf"
				]
			}
		]
		errors false
	}
]

#
# defaults
#

# show all name hints also for definitions without hint {} section
defaults.namehint.showall off
# show just basic name hints
defaults.namehint.basic on
# show extended name hints
defaults.namehint.extended off
#
defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
# truncate files via file or tee PCM
defaults.pcm.file_format	"raw"
defaults.pcm.file_truncate	true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0

#
#  PCM interface
#

# redirect to load-on-demand extended pcm definitions
pcm.cards cards.pcm

pcm.default cards.pcm.default
pcm.front cards.pcm.front
pcm.rear cards.pcm.rear
pcm.center_lfe cards.pcm.center_lfe
pcm.side cards.pcm.side
pcm.surround40 cards.pcm.surround40
pcm.surround41 cards.pcm.surround41
pcm.surround50 cards.pcm.surround50
pcm.surround51 cards.pcm.surround51
pcm.surround71 cards.pcm.surround71
pcm.iec958 cards.pcm.iec958
pcm.spdif iec958
pcm.hdmi cards.pcm.hdmi
pcm.dmix cards.pcm.dmix
pcm.dsnoop cards.pcm.dsnoop
pcm.modem cards.pcm.modem
pcm.phoneline cards.pcm.phoneline

pcm.hw {
	@args [ CARD DEV SUBDEV ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_PCM_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.pcm.card
			}
		}
	}
	@args.DEV {
		type integer
		default {
			@func igetenv
			vars [
				ALSA_PCM_DEVICE
			]
			default {
				@func refer
				name defaults.pcm.device
			}
		}
	}
	@args.SUBDEV {
		type integer
		default {
			@func refer
			name defaults.pcm.subdevice
		}
	}		
	type hw
	card $CARD
	device $DEV
	subdevice $SUBDEV
	hint {
		show {
			@func refer
			name defaults.namehint.extended
		}
		description "Direct hardware device without any conversions"
	}
}

pcm.plughw {
	@args [ CARD DEV SUBDEV ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_PCM_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.pcm.card
			}
		}
	}
	@args.DEV {
		type integer
		default {
			@func igetenv
			vars [
				ALSA_PCM_DEVICE
			]
			default {
				@func refer
				name defaults.pcm.device
			}
		}
	}
	@args.SUBDEV {
		type integer
		default {
			@func refer
			name defaults.pcm.subdevice
		}
	}		
	type plug
	slave.pcm {
		type hw
		card $CARD
		device $DEV
		subdevice $SUBDEV
	}
	hint {
		show {
			@func refer
			name defaults.namehint.extended
		}
		description "Hardware device with all software conversions"
	}
}

pcm.plug {
	@args [ SLAVE ]
	@args.SLAVE {
		type string
	}
	type plug
	slave.pcm $SLAVE
}

pcm.shm {
	@args [ SOCKET PCM ]
	@args.SOCKET {
		type string
	}
	@args.PCM {
		type string
	}
	type shm
	server $SOCKET
	pcm $PCM
}

pcm.tee {
	@args [ SLAVE FILE FORMAT ]
	@args.SLAVE {
		type string
	}
	@args.FILE {
		type string
	}
	@args.FORMAT {
		type string
		default {
			@func refer
			name defaults.pcm.file_format
		}
	}
	type file
	slave.pcm $SLAVE
	file $FILE
	format $FORMAT
	truncate {
		@func refer
		name defaults.pcm.file_truncate
	}
}

pcm.file {
	@args [ FILE FORMAT ]
	@args.FILE {
		type string
	}
	@args.FORMAT {
		type string
		default {
			@func refer
			name defaults.pcm.file_format
		}
	}
	type file
	slave.pcm null
	file $FILE
	format $FORMAT
	truncate {
		@func refer
		name defaults.pcm.file_truncate
	}
}

pcm.null {
	type null
	hint {
		show {
			@func refer
			name defaults.namehint.basic
		}
		description "Discard all samples (playback) or generate zero samples (capture)"
	}
}

#
#  Control interface
#
	
ctl.default {
	type hw
	card {
		@func getenv
		vars [
			ALSA_CTL_CARD
			ALSA_CARD
		]
		default {
			@func refer
			name defaults.ctl.card
		}
	}
}

ctl.hw {
	@args [ CARD ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_CTL_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.ctl.card
			}
		}
	}
	type hw
	card $CARD
}

ctl.shm {
	@args [ SOCKET CTL ]
	@args.SOCKET {
		type string
	}
	@args.CTL {
		type string
	}
	type shm
	server $SOCKET
	ctl $CTL
}

#
#  RawMidi interface
#

rawmidi.default {
	type hw
	card {
		@func getenv
		vars [
			ALSA_RAWMIDI_CARD
			ALSA_CARD
		]
		default {
			@func refer
			name defaults.rawmidi.card
		}
	}
	device {
		@func igetenv
		vars [
			ALSA_RAWMIDI_DEVICE
		]
		default {
			@func refer
			name defaults.rawmidi.device
		}
	}
}

rawmidi.hw {
	@args [ CARD DEV SUBDEV ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_RAWMIDI_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.rawmidi.card
			}
		}
	}
	@args.DEV {
		type integer
		default {
			@func igetenv
			vars [
				ALSA_RAWMIDI_DEVICE
			]
			default {
				@func refer
				name defaults.rawmidi.device
			}
		}
	}
	@args.SUBDEV {
		type integer
		default -1
	}
	type hw
	card $CARD
	device $DEV
	subdevice $SUBDEV
	hint {
		description "Direct rawmidi driver device"
		device $DEV
	}
}

rawmidi.virtual {
	@args [ MERGE ]
	@args.MERGE {
		type string
		default 1
	}
	type virtual
	merge $MERGE
}

#
#  Sequencer interface
#
fig
seq.default {
	type hw
}

seq.hw {
	type hw
}

#
#  HwDep interface
#

hwdep.default {
	type hw
	card {
		@func getenv
		vars [
			ALSA_HWDEP_CARD
			ALSA_CARD
		]
		default {
			@func refer
			name defaults.hwdep.card
		}
	}
	device {
		@func igetenv
		vars [
			ALSA_HWDEP_DEVICE
		]
		default {
			@func refer
			name defaults.hwdep.device
		}
	}
}

hwdep.hw {
	@args [ CARD DEV ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_HWDEP_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.hwdep.card
			}
		}
	}
	@args.DEV {
		type integer
		default {
			@func igetenv
			vars [
				ALSA_HWDEP_DEVICE
			]
			default {
				@func refer
				name defaults.hwdep.device
			}
		}
	}
	type hw
	card $CARD
	device $DEV
}

#
#  Timer interface
#

timer_query.default {
	type hw
}

timer_query.hw {
	type hw
}

timer.default {
	type hw
	class {
		@func refer
		name defaults.timer.class
	}
	sclass {
		@func refer
		name defaults.timer.sclass
	}
	card {
		@func refer
		name defaults.timer.card
	}
	device {
		@func refer
		name defaults.timer.device
	}
	subdevice {
		@func refer
		name defaults.timer.subdevice
	}
	hint.description "Default direct hardware timer device"
}

timer.hw {
	@args [ CLASS SCLASS CARD DEV SUBDEV ]
	@args.CLASS {
		type integer
		default {
			@func refer
			name defaults.timer.class
		}
	}
	@args.SCLASS {
		type integer
		default {
			@func refer
			name defaults.timer.sclass
		}
	}
	@args.CARD {
		type string
		default {
			@func refer
			name defaults.timer.card
		}
	}
	@args.DEV {
		type integer
		default {
			@func refer
			name defaults.timer.device
		}
	}
	@args.SUBDEV {
		type integer
		default {
			@func refer
			name defaults.timer.subdevice
		}
	}
	type hw
	class $CLASS
	sclass $SCLASS
	card $CARD
	device $DEV
	subdevice $SUBDEV
}

lshw:
> description: Multimedia audio controller
                product: CA0106 Soundblaster
                vendor: Creative Labs
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=oss_audigyls latency=64 maxlatency=20 mingnt=2
                resources: irq:16 ioport:ec00(size=32)


If you need more let me know, guaranteed its just some retarded setting I managed to screw up when I removed pulseaudio on my 9.10 instance.

---

### Post by VastOne on 2010-05-04
I apologize up front if this offensive, but isn't this why one would want a clean install with a separate /home partition so that you could keep most of what you have and have the pristine 10.4 setup?  

Did it your sound work when you ran livecd?

---

### Post by denn0069 on 2010-05-04
I didn't use a CD, I used the update manager, clicked the button that said Upgrade right beside the notification that said 10.04 was available. 

Audio worked before the upgrade however it doesn't anymore.

---

### Post by tgalati4 on 2010-05-04
So you removed pulseaudio because presumably it wasn't working with your previous distro.  Then you upgraded in-place and pulseaudio gets reinstalled.  (It's the default sound server--like it or not).  Sound is still not working (no surprise as it didn't work previously under pulseaudio).

To remove pulseaudio and get OSS working requires some tweaking.  But you no longer have those tweaks.

What did you try previously to get pulseaudio to work?  Perhaps some simple configuration can get your hardware to work with ALSA which is what pulseaudio uses to communicate with the sound card.

What is the output of:

aplay -l

You have two soundcards, the built-in Intel HDA and the Audigy.  Do you need the Intel HDA?  Can you turn it off in the BIOS?

---

### Post by denn0069 on 2010-05-10
Hey sorry for the reply latency I was the best man at a wedding haven't been around for the last 5 days. 

However I did as you suggested I turned off my built in intel HDA in the BIOS. Then removed and re-setup pulseaudio and after a bit of tinkering I got me some audio.

Not sure what the issue was before but I think it was getting confused between the 2 sound cards.

Thanks guys
Learning more and more as I go.

---

