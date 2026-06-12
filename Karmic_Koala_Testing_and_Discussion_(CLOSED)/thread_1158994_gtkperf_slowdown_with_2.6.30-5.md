---
title: "gtkperf slowdown with 2.6.30-5"
date: 2009-05-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2009-05-14
For whatever it measures, gtkperf slows down on 2.6.30-5 on IBM ThinkCentre A30 2 gHz Celeron i845 Intel integrated graphics.

While a nice usable pc, it is relatively slow compared to my other test systems so it shows up performance differences.

karmic from sources.list
2.6.28-11 gtkperf 31.0 seconds
2.6.30-5  gtkperf 32.4 seconds

There are a few other performance measures around like gtkdragon and the mega suite Phronix.  I used gtkperf just because it is on synaptic.

?  

Jerry

---

### Post by taavikko on 2009-05-14
Just tested on most recent kernel, with ATI HD3450
I got
```
gtkperf -aGtkPerf 0.40 - Starting testing: Thu May 14 17:13:50 2009

GtkEntry - time:  0.00
GtkComboBox - time:  3.36
GtkComboBoxEntry - time:  2.83
GtkSpinButton - time:  0.33
GtkProgressBar - time:  0.15
GtkToggleButton - time:  0.27
GtkCheckButton - time:  0.11
GtkRadioButton - time:  0.31
GtkTextView - Add text - time:  0.27
GtkTextView - Scroll - time:  0.19
GtkDrawingArea - Lines - time:  0.94
GtkDrawingArea - Circles - time:  1.71
GtkDrawingArea - Text - time:  1.20
GtkDrawingArea - Pixbufs - time:  0.19
 --- 
Total time: 11.85
```

don't have a clue if that's good or bad, but just for comparison only.

Cant test more since this is only machine with karmic and no more .28 kernel available.

---

### Post by jerrylamos on 2009-05-15
Thanks for the data.  I do have a faster machine in that range but haven't put karmic on it yet.

Jerry

---

