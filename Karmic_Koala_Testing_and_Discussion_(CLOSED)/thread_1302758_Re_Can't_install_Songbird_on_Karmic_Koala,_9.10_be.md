---
title: "Re: Can't install Songbird on Karmic Koala, 9.10 beta."
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tbennekik on 2009-10-27
Hello I am a newbie Ubuntu fan.

In version 9.04 I already used Songbird and it's the only music program I like in Ubuntu because it feels familiar when you are used to Itunes.

Now I am using Ubuntu 9.10 Bèta and Songbird will not install. I'm following the instructions but when I am in the Songbird directory and I type the command "./songbird" then I get a lot of error messages:

(songbird-bin:3201): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:3201): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsthdvparse.so': /usr/lib/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:3201): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdv.so': /usr/lib/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

(songbird-bin:3201): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libresindvd.so': /usr/lib/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:3201): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:3201): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstlibvisual.so': /usr/lib/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:3201): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegdemux.so': /usr/lib/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Fout bij het herdoorlopen van de registry , child terminated by signal

Does anyone knows what to do? 

tbennekik

---

### Post by Sef on 2009-10-27
Have you upgraded to the Karmic RC?  That may resolve your problem.

---

