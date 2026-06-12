---
title: "Audacity won't launch"
date: 2017-04-15
forum: Installation &amp; Upgrades
---

### Post by violetalisboa on 2017-04-15
Installed Audacity 2.1.2-1 in my ubuntu 14.04 and it doesn't launch. It appears as icon and when i click a first image of the logo appears but nothing else happens after that.
Have uninstalled and reinstalled it a few times in different ways.
whe i try to start it from terminal i get this script...
```
user@user-Lenovo-B580:~$ audacity
lilv_world_add_plugin(): warning: Reloading plugin <http://kunz.corrupt.ch/products/tal-noisemaker>
lilv_world_add_plugin(): warning: Reloading plugin <https://community.ardour.org/node/7596>
lilv_world_add_plugin(): warning: Reloading plugin <http://kunz.corrupt.ch/products/tal-vocoder>
lilv_world_add_plugin(): warning: Reloading plugin <urn:juce:TalFilter2>
lilv_world_add_plugin(): warning: Reloading plugin <http://zynaddsubfx.sourceforge.net/fx#Echo>
lilv_world_add_plugin(): warning: Reloading plugin <https://github.com/asb2m10/dexed>
lilv_world_add_plugin(): warning: Reloading plugin <http://zynaddsubfx.sourceforge.net>
lilv_world_add_plugin(): warning: Reloading plugin <http://zynaddsubfx.sourceforge.net/fx#Reverb>
lilv_world_add_plugin(): warning: Reloading plugin <urn:juce:TalFilter>
lilv_world_add_plugin(): warning: Reloading plugin <http://zynaddsubfx.sourceforge.net/fx#AlienWah>
lilv_world_add_plugin(): warning: Reloading plugin <http://zynaddsubfx.sourceforge.net/fx#DynamicFilter>
lilv_world_add_plugin(): warning: Reloading plugin <urn:ardour:a-delay>
lilv_world_add_plugin(): warning: Reloading plugin <urn:ardour:a-reverb>
lilv_world_add_plugin(): warning: Reloading plugin <urn:juce:TalReverb3>
lilv_world_add_plugin(): warning: Reloading plugin <urn:juce:TalDub3>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/compressor/mono>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/compressor/stereo>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/delay/mono>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/delay/sum>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/erreverb/mono>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/erreverb/sum>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/filter/hpf/mono>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/filter/hpf/stereo>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/filter/lpf/mono>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/filter/lpf/stereo>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/input>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/meter>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/phaser/mono>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/phaser/stereo>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/phaser/sum>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/testtone>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/tube/mono>
lilv_world_add_plugin(): warning: Reloading plugin <http://invadarecords.com/plugins/lv2/tube/stereo>
lilv_world_add_plugin(): warning: Reloading plugin <http://gareus.org/oss/lv2/gmsynth>
lilv_world_add_plugin(): warning: Reloading plugin <http://zynaddsubfx.sourceforge.net/fx#Chorus>
lilv_world_add_plugin(): warning: Reloading plugin <http://zynaddsubfx.sourceforge.net/fx#Phaser>
lilv_world_add_plugin(): warning: Reloading plugin <urn:ardour:a-fluidsynth>
lilv_world_add_plugin(): warning: Reloading plugin <urn:ardour:a-comp>
lilv_world_add_plugin(): warning: Reloading plugin <urn:ardour:a-comp#stereo>
lilv_world_add_plugin(): warning: Reloading plugin <http://zynaddsubfx.sourceforge.net/fx#Distortion>
lilv_world_add_plugin(): warning: Reloading plugin <urn:juce:TalReverb2>
lilv_world_add_plugin(): warning: Reloading plugin <urn:ardour:a-eq>
lilv_world_add_plugin(): warning: Reloading plugin <urn:juce:TalReverb>
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
audacity: symbol lookup error: audacity: undefined symbol: Pa_GetStreamHostApiType
user@user-Lenovo-B580:~$
```

---

