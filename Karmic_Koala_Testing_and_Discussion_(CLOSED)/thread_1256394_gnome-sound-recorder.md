---
title: "gnome-sound-recorder"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pulpo69 on 2009-09-02
has somebody gnome-sound-recorder working? for it doesn't work. i don't know why.

---

### Post by taavikko on 2009-09-02
It's working correctly here.

Does it print out anything if started via terminal?

---

### Post by GeorgeVita on 2009-09-02
Hi **pulpo69**,
I just tested on my EeePC 1000H using MIC and works:

Record from input: capture
From menu: File > Open Volume control > Input
input level raised, bargraph shows volume, internal audio analog stereo was selected
Record 5 seconds, Stop, Play, playback volume raised from speaker icon (top panel)
... all OK here!

Regards,
George

---

### Post by pulpo69 on 2009-09-02
when i start it in terminal the output is the following:
(gnome-sound-recorder:5875): GStreamer-CRITICAL **: gst_implements_interface_cast: assertion `gst_element_implements_interface (GST_ELEMENT (from), iface_type)' failed

---

