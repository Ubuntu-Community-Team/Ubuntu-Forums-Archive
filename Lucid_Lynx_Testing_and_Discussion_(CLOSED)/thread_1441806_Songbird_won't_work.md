---
title: "Songbird won't work"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by woodbj on 2010-03-29
Can anybody get song bird to work? I have tried the nightly build and the latest stable but I always get this code on Lucid 64 bit
```
(songbird-bin:11179): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstaiff.so': /usr/lib64/gstreamer-0.10/libgstaiff.so: undefined symbol: gst_byte_writer_put_uint32_be

(songbird-bin:11179): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libresindvd.so': /usr/lib64/gstreamer-0.10/libresindvd.so: undefined symbol: gst_video_event_parse_still_frame

(songbird-bin:11179): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstjpegformat.so': /usr/lib64/gstreamer-0.10/libgstjpegformat.so: undefined symbol: gst_byte_writer_put_uint8
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_xml_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

---

### Post by ankspo71 on 2010-03-29
Hi,
I just got it working on Lucid 32bit.
First I downloaded songbird from here: [http://skyzim.com/downloads/](http://skyzim.com/downloads/)
Installed it as usual.

Now refer to this link:
[http://www.ubuntugeek.com/how-to-install-songbird-1-4-1-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-songbird-1-4-1-in-ubuntu.html)

I chose to use solution 1 from the above link:
```
sudo mv /usr/lib/python2.6/dist-packages/gst-0.10/  /usr/lib/python2.6/dist-packages/gst-0.10_bad
```64bit might have slightly different directory paths. It's working for me but I don't know if moving gstreamer plugins is going to break other apps. Hope this helps.

**CORRECTION** : The above command will get songbird working, but at the expense of causing some of Rhythmbox's plugins to not work anymore in Lucid (like music store, etc). The above command renames the folder "gst-0.10" to "gst-0.10_bad" so that they will work in Songbird. To get Rhythmbox plugins working again we will need to reverse the command above:
```
sudo mv /usr/lib/python2.6/dist-packages/gst-0.10_bad/   /usr/lib/python2.6/dist-packages/gst-0.10
```Unfortunately, I am having a hard time trying to satisfy both Rhythmbox and Songbird by trying to keep both "gst-0.10_bad" and "gst-0.10" folders. It looks like 'one or the other' for now.

---

### Post by ankspo71 on 2010-03-31
bumped...
because I added important info above concerning rhythmbox plugins versus Songbird in Lucid.

---

### Post by woodbj on 2010-03-31
haha thanks I was just trying to figure out why they weren't working and thanks for all the info

---

