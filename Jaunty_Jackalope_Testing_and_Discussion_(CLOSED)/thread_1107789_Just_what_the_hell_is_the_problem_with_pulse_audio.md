---
title: "Just what the hell is the problem with pulse audio??"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2009-03-27
Intel HDA ALC662

Ok, so I just installed the new Beta and set up the sound. Everything worked totally fine. Pulse was running smoothly.

Then i rebooted after installing the Nvidia driver and Pulse is up to its old tricks.

The only option for the default sink is NULL OUTPUT. So,yes, as per bloody usual the sound device can't be found and now i'm back to no audio.

If I select the ALSA driver in the sound settings in Ubuntu I get sound. So that's working fine.

I've had exactly the same problem with all other Ubuntu releases with Pulse Audio and I am very disappointed that this is still a frustrating issue because when it is working Pulse is a great sound server.

Why does it fail to find my sound card all the time? Even though it's been working now and then. It's very frustrating.

When it happened with intrepid i tried the latest Pulse PPAs and even upgrade ALSA and it's the same thing. The sound works until reboot and then I get this NULL OUTPUT again in the sink.

---

### Post by gnomeuser on 2009-03-27
> **sonicb00m said:**
> 
Then i rebooted after installing the Nvidia driver and Pulse is up to its old tricks.


The proprietary NVidia driver is known to cause problems with a number of things, you use it at your own peril. This is just one of the incidents. PulseAudio is not to blame for your problem.

---

### Post by smbm on 2009-03-27
> **gnomeuser said:**
> The proprietary NVidia driver is known to cause problems with a number of things, you use it at your own peril. This is just one of the incidents. PulseAudio is not to blame for your problem.

Exactly.

---

### Post by sonicb00m on 2009-03-27
> **gnomeuser said:**
> The proprietary NVidia driver is known to cause problems with a number of things, you use it at your own peril. This is just one of the incidents. PulseAudio is not to blame for your problem.

Have you got any proof that nvidia driver is to blame for the fact pulseaudio looses it's sink every now again? I've never come across anyone saying that it's the video driver that causes pulseaudio not to work correctly.

Incidentally, i shut the pulsemanager down unplugged my usb phone, logged out and logged back in and for now the Audio sink has come back for the intel. How this can be the fault of the video driver seems a little premature?

---

### Post by Nullack on 2009-03-27
Exactly, Ive never experienced this

---

### Post by smbm on 2009-03-27
Have you tried uninstalling the drivers to see if that helps?

That way you can know for sure.

EDIT: Posted at the same time as Nullack, I'd go with what he said.

---

### Post by taavikko on 2009-03-27
> **Nullack said:**
> Exactly, Ive never experienced this

+1

This isn't related to nvidia drivers, but an reported bug on linux/pulseaudio

There are update on the queue that should resolve this.

---

### Post by BUGabundo on 2009-03-27
This is a know and since today fixed bug

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/330814](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/330814)

---

### Post by ronacc on 2009-03-27
there are some who want to blame everything on the Nvidia driver , even problems with ati and intel gpus .

---

### Post by smbm on 2009-03-27
I was a little premature assigning blame. 

The same could be said for Pulse though, lots of people seem to think it's the root of all problems.

---

### Post by sonicb00m on 2009-03-27
> **smbm said:**
> I was a little premature assigning blame. 

The same could be said for Pulse though, lots of people seem to think it's the root of all problems.

It's the route of all sound problems i've ever experienced. Usually i would uninstall it but i decided it to give it a real crack and see if i could get it stable but it never keeps that why for more than a few days and i always result back to alsa. Which is a shame because when it's working it's glorius.

---

### Post by markbuntu on 2009-03-27
I have pulseaudio working in Hardy 386, amd64, intrepid, mandriva, jaunty???. It works great for me once it is set up properly, which unfortunately is a big failing of Ubuntu. 

Leaving out the pa volume control because someone does not like the gui and replacing it with nothing is just really bad decision making. That and starting pulse but setting sound default to autodetect and leaving out other packages critical for a pleasant sound experience. It was criminally incompetent what they did with pulseaudio in Hardy and then they did it again in Intrepid.

The biggest problem now is crappy alsa drivers and bad alsa plugins from application devs. The alsa drivers have moved to the kernel. Important security considerations must be taken into account which many devs have chosen to ignore. That is the biggest reason why applications fail with pulseaudio. That and going with the partial upgrade pulse0.9.14 for Jaunty instead of 0.9.15.

I really don't expect to see any of this get really fixed until Koala at the soonest.

---

### Post by sonicb00m on 2009-03-31
This null output seems to be because pulse is failing to load first time on reboot. If I log out and back in it seems ok.

The weird thing is though I often have to go to the gnome-alsamixer and unmute the primary channel and raise the volume. Despite this it's defintely running through pulseaudio though.

---

### Post by Flag on 2009-03-31
Well, hope it can be fixed before the Jaunty final, otherwise, for me, it's another one to be skipper like 8.10.

---

### Post by eye208 on 2009-03-31
Last year when I removed PulseAudio from my Ubuntu 8.04 install, there were people telling me that PulseAudio was the future of Linux audio, so I better get used to it.

Oh well... Last weekend I switched to Debian 5.0, released in February 2009, and guess what, there's no PulseAudio in the standard install. Just plain ALSA, and of course it works right out of the box.

It's kind of sad to see that one year after its deployment with several major Linux distributions, PulseAudio is still unstable and its fans are still playing the blame game.

---

### Post by sonicb00m on 2009-03-31
> **eye208 said:**
> Last year when I removed PulseAudio from my Ubuntu 8.04 install, there were people telling me that PulseAudio was the future of Linux audio, so I better get used to it.

Oh well... Last weekend I switched to Debian 5.0, released in February 2009, and guess what, there's no PulseAudio in the standard install. Just plain ALSA, and of course it works right out of the box.

It's kind of sad to see that one year after its deployment with several major Linux distributions, PulseAudio is still unstable and its fans are still playing the blame game.

Yeah, the concept of it is fantastic but it is still lacking in execution (at least in Ubuntu).

It seems to have settled down a bit now with my onboard soundcard.

I just recently bought an Maudio fast track pro and I can't get it to work with Pulseaudio at all. So that's only getting switched on in windows for recording music.

I am disappointed that after all this time pulse still isn't 100% but it seems to be slowly getting better but it isn't good enough yet.

The biggest problem now is it seems more difficult in Jaunty to get a plain vanilla install of Alsa back as more and more apps are being tied into pulse.

---

### Post by IanW on 2009-03-31
Markbuntu - Are you _sure_ pulseaudio is working correctly for you?

Look for lines like this in /var/log/messages:-

```
pulseaudio[8346]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
pulseaudio[8346]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
pulseaudio[8346]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 23.00 dB to 23.00 dB which makes no sense.
```

Since when does 7.1 channel Intel ALC885 codec not support 2 channels & 44100Hz sampling?

---

### Post by ameyer on 2009-03-31
> **IanW said:**
> 

Since when does 7.1 channel Intel ALC885 codec not support 2 channels & 44100Hz sampling?
A lot of consumer hardware only supports 48 kHz.
And it's possible that the codec doesn't have hardware support for stereo, though $audio_software could open all 7.1 channels and only use the left-front and right-front.
EDIT: on the other hand, my tv capture card throws a similar error message (except it switches to 48 kHz).  I'll agree with the post below me.

---

### Post by markbuntu on 2009-03-31
> **IanW said:**
> Markbuntu - Are you _sure_ pulseaudio is working correctly for you?

Look for lines like this in /var/log/messages:-

```
pulseaudio[8346]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
pulseaudio[8346]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
pulseaudio[8346]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 23.00 dB to 23.00 dB which makes no sense.
```

Since when does 7.1 channel Intel ALC885 codec not support 2 channels & 44100Hz sampling?

I have that message for my usb web cam which is only 16000hz and mono but not for my on-board ALC883 or my C-media pci card or my usb headset or my AC'97 on my other machine all of which work just fine

In any case those are messages hal gets from parsing the alsa hardware driver in the kernel and passes on to pulseaudio. In this case it definitely looks like the alsa kernel module is reporting hw:1 correctly since this is most likely your webcam. Your ALC885 is most likely hw:0 or hw:2.

You can check this with cat /proc/asound/cards

---

### Post by sonicb00m on 2009-04-01
Ok I think the null output problem on reboot is because I have the automatic login enabled. Once I log out and manually log back in Pulse is fine.

---

### Post by IanW on 2009-04-01
> **markbuntu said:**
> I have that message for my usb web cam which is only 16000hz and mono but not for my on-board ALC883 or my C-media pci card or my usb headset or my AC'97 on my other machine all of which work just fine

In any case those are messages hal gets from parsing the alsa hardware driver in the kernel and passes on to pulseaudio. In this case it definitely looks like the alsa kernel module is reporting hw:1 correctly since this is most likely your webcam. Your ALC885 is most likely hw:0 or hw:2.

You can check this with cat /proc/asound/cards

Checking...
```
~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc100000 irq 22
 1 [U0x46d0x9a4    ]: USB-Audio - USB Device 0x46d:0x9a4
                      USB Device 0x46d:0x9a4 at usb-0000:00:1d.7-5, high speed
```

Confirmed. Thanks. BTW It's an ALC889a

---

### Post by eye208 on 2009-04-01
> **ameyer said:**
> A lot of consumer hardware only supports 48 kHz.
This is a thing of the past. Today even the cheapest mainboards come with HDA (high definition audio) chipsets. The Realtek ALC885 supports 44.1, 48, 96 and 192 kHz sampling rates.

To find out what is supported by your chipset/card, you can use the "aplay" tool like this:
```
$ aplay -v -d 1 -D hw:0,0 -f S16_LE -c 2 -r 44100 < /dev/zero
Playing raw data 'stdin' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 44100
  exact rate   : 44100 (44100/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 4096
  period_time  : 92879
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 4096
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
```
You can test arbitrary sample rates by modifying the -r option. If you specify an unsupported rate, you'll see a warning like this:
```
$ aplay -v -d 1 -D hw:0,0 -f S16_LE -c 2 -r 88200 < /dev/zero
Playing raw data 'stdin' : Signed 16 bit Little Endian, Rate 88200 Hz, Stereo
Warning: rate is not accurate (requested = 88200Hz, got = 96000Hz)
         please, try the plug plugin 
Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 96000
  exact rate   : 96000 (96000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 4096
  period_time  : 42666
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 4096
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
```
This means that the hardware device does not support 88.2 kHz output natively. ALSA will automatically switch to 96 kHz. If you want to play back a 88.2 kHz audio stream, you'll have to insert a sample rate converter (e.g. by using plughw:0,0 instead of hw:0,0):
```
$ aplay -v -d 1 -D plughw:0,0 -f S16_LE -c 2 -r 88200 < /dev/zero
Playing raw data 'stdin' : Signed 16 bit Little Endian, Rate 88200 Hz, Stereo
Plug PCM: Rate conversion PCM (96000, sformat=S16_LE)
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 88200
  exact rate   : 88200 (88200/1)
  msbits       : 16
  buffer_size  : 15052
  period_size  : 3763
  period_time  : 42666
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 3763
  start_threshold  : 15052
  stop_threshold   : 15052
  silence_threshold: 0
  silence_size : 0
  boundary     : 986447872
Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 96000
  exact rate   : 96000 (96000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 4096
  period_time  : 42666
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 4096
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
```
To find out the default sample rate used by ALSA's software stream mixer, change the -D option like this:
```
$ aplay -v -d 1 -D default -f S16_LE -c 2 -r 96000 < /dev/zero
Playing raw data 'stdin' : Signed 16 bit Little Endian, Rate 96000 Hz, Stereo
Plug PCM: Rate conversion PCM (48000, sformat=S32_LE)
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 96000
  exact rate   : 96000 (96000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 2048
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 2048
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Slave: Soft volume PCM
Control: PCM Playback Volume
min_dB: -51
max_dB: 0
resolution: 256
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1024
  start_threshold  : 8192
  stop_threshold   : 8192
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Slave: Direct Stream Mixing PCM
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1024
  start_threshold  : 8192
  stop_threshold   : 8192
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : ENABLE
  period_step  : 1
  avail_min    : 1024
  start_threshold  : 1
  stop_threshold   : 1073741824
  silence_threshold: 0
  silence_size : 1073741824
  boundary     : 1073741824
```
As you can see, all audio sent through ALSA's "default" device gets mixed and converted to a single 32bit@48kHz stream by default, but this can be changed easily using a custom .asoundrc configuration file.

---

