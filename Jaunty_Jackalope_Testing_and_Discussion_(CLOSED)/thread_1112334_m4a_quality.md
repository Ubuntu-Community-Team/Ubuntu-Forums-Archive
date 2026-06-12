---
title: "m4a quality"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vaskark on 2009-03-31
I want to rip some music from cd to m4a format using sound-juicer. I'd like to be able to rip these songs with a bitrate of 192 Kbps (just like iTunes allows me to do). I'm guessing the default is ripping to 128. Is it possible to modify the Gstreamer pipeline config for AAC? Here it is as it looks now:

*audio/x-raw-int,rate=44100,channels=2 ! faac profile=2 ! ffmux_mp4*

Any help will be appreciated. Thanks.

---

### Post by phenest on 2009-03-31
Bitrates are the old way of doing things, whereas m4a (aac codec) is better when done as a quality setting, which is how aac works best (smaller files, better quality sound). Both Sound Juicer and Rhythmbox use gstreamer to encode but both are set with a low quality setting by default.

If you check the profile for m4a in Sound Juicer, you may find this:
```
audio/x-raw-int,rate=44100,channels=2 ! faac profile=2 ! ffmux_mp4
```
If 'profile=2' is missing, add it so the pipe looks like the above. This enables the high efficiency in aac (HE-AAC), whereas the default low complexity (LC-AAC) is more suitable for ipods.

---

### Post by phenest on 2009-03-31
Incidentally, I don't believe gstreamer allows encoding to a bitrate anyway. Personally, I used the command line to rip CD's with cdparanoia and encoded with faac. More long winded, but I get the results I wanted.

---

### Post by RAOF on 2009-03-31
> **phenest said:**
> Incidentally, I don't believe gstreamer allows encoding to a bitrate anyway. Personally, I used the command line to rip CD's with cdparanoia and encoded with faac. More long winded, but I get the results I wanted.

Yes, it does.  To see all the options a given element accepts, you can use the *gst-inspect* command, like so:
```

&#9492;&#9472;(09:32:%)&#9472;&#9472; gst-inspect faac                                                                                                     &#9472;&#9472;(Wed,Apr01)&#9472;&#9496;
Factory Details:
  Long name:	AAC audio encoder
  Class:	Codec/Encoder/Audio
  Description:	Free MPEG-2/4 AAC encoder
  Author(s):	Ronald Bultje <rbultje@ronald.bitfreak.net>
  Rank:		none (0)

Plugin Details:
  Name:			faac
  Description:		Free AAC Encoder (FAAC)
  Filename:		/usr/lib/gstreamer-0.10/libgstfaac.so
  Version:		0.10.10.2
  License:		LGPL
  Source module:	gst-plugins-bad
  Binary package:	GStreamer Bad Multiverse Plugins (Ubuntu)
  Origin URL:		https://launchpad.net/distros/ubuntu/+source/gst-plugins-bad-multiverse0.10

GObject
 +----GstObject
       +----GstElement
             +----GstFaac

Pad Templates:
  SRC template: 'src'
    Availability: Always
    Capabilities:
      audio/mpeg
            mpegversion: { 4, 2 }
               channels: [ 1, 6 ]
                   rate: [ 8000, 96000 ]

  SINK template: 'sink'
    Availability: Always
    Capabilities:
      audio/x-raw-int
             endianness: 1234
                 signed: true
                  width: 16
                  depth: 16
                   rate: [ 8000, 96000 ]
               channels: [ 1, 6 ]


Element Flags:
  no flags set

Element Implementation:
  Has change_state() function: gst_faac_change_state
  Has custom save_thyself() function: gst_element_save_thyself
  Has custom restore_thyself() function: gst_element_restore_thyself

Element has no clocking capabilities.
Element has no indexing capabilities.
Element has no URI handling capabilities.

Pads:
  SRC: 'src'
    Implementation:
      Has custom eventfunc(): gst_pad_event_default
      Has custom queryfunc(): gst_pad_query_default
        Provides query types:
      Has custom intconnfunc(): gst_pad_get_internal_links_default
    Pad Template: 'src'
  SINK: 'sink'
    Implementation:
      Has chainfunc(): gst_faac_chain
      Has custom eventfunc(): gst_faac_sink_event
      Has custom queryfunc(): gst_pad_query_default
        Provides query types:
      Has custom intconnfunc(): gst_pad_get_internal_links_default
    Pad Template: 'sink'

Element Properties:
  name                : The name of the object
                        flags: readable, writable
                        String. Default: null Current: "faac0"
  outputformat        : Format of output frames
                        flags: readable, writable
                        Enum "GstFaacOutputFormat" Default: 0, "Raw AAC" Current: 0, "Raw AAC"
                           (0): Raw AAC          - OUTPUTFORMAT_RAW
                           (1): ADTS headers     - OUTPUTFORMAT_ADTS
  bitrate             : Bitrate in bits/sec
                        flags: readable, writable
                        Integer. Range: 8000 - 320000 Default: 128000 Current: 128000
  profile             : MPEG/AAC encoding profile
                        flags: readable, writable
                        Enum "GstFaacProfile" Default: 1, "Main profile" Current: 1, "Main profile"
                           (1): Main profile     - MAIN
                           (2): Low complexity profile - LC
                           (3): Scalable sampling rate profile - SSR
                           (4): Long term prediction profile - LTP
  tns                 : Use temporal noise shaping
                        flags: readable, writable
                        Boolean. Default: false Current: false
  midside             : Allow mid/side encoding
                        flags: readable, writable
                        Boolean. Default: true Current: true
  shortctl            : Block type encorcing
                        flags: readable, writable
                        Enum "GstFaacShortCtl" Default: 1, "No short blocks" Current: 0, "Normal block type"
                           (0): Normal block type - SHORTCTL_NORMAL
                           (1): No short blocks  - SHORTCTL_NOSHORT
                           (2): No long blocks   - SHORTCTL_NOLONG

```
So, you'd want to set something like "faac profile=2 bitrate=192000".

---

### Post by vaskark on 2009-03-31
Thanks so much for the help, guys :)

I've now added bitrate=192000 to the pipeline and it works great now. I was getting close, though: I added bitrate=192 but it didn't work. I'm sure I would have eventually tried 192000. I'm ... sure.

---

### Post by Yashiro on 2009-04-01
If you want higher quality AAC encoding you can use the NeroAAC encoder.
You will probably have to use a tool other than Sound Juicer like Rubyripper or Grip.

---

