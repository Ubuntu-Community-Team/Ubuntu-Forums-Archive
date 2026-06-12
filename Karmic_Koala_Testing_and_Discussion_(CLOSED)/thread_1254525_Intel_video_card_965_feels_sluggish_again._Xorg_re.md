---
title: "Intel video card 965 feels sluggish again. Xorg regression?"
date: 2009-08-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-08-31
What would be the best way to test if this is true and not just my subjective impression? I think since the last Xorg/Compiz update performance went down to Jaunty levels.

My video card controller is "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"

---

### Post by jerrylamos on 2009-08-31
One easy video graphics test is GtkPerf available from Synaptic or apt-get.  I'm dual or triple or quad booted so I can boot any image and try the tests.  I like to do a fresh boot, then run GtkPerf first, maybe 3 times, then select a representative set of the results into a text file.  Then put into an Open Office spreadsheet for comparison.  For example launchpad bug #399559.

I've written a couple of intel and ati launchpad video driver bugs using GtkPerf.  KMS support has slowed things down recently; I haven't tried it with the driver improvements that are coming out.

Jerry

---

### Post by jerrylamos on 2009-08-31
I have an intel video i845 which doesn't boot unless it is in "vesa" so I can't give performance results on recent intel drivers.  Last time it would boot with intel driver was Alpha 2.  Yes, there are launchpad bugs #406640 for example.

I can give some #'s with ati:

GtkPerf with ati radeon mobility 7500 slower with karmic:
jaunty 12.54 seconds
karmic 18.18 seconds that's with kernel 2.6.31-8 and radeon driver 6.12.99

Note that is with KMS modeset=0 which is the default for ati.

Jerry

---

### Post by andresmh on 2009-08-31
OK, I tried GtkPerf on my hardware "VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)". The best time I got was this one:

GtkEntry - time:  0.00
GtkComboBox - time:  2.04
GtkComboBoxEntry - time:  1.87
GtkSpinButton - time:  0.51
GtkProgressBar - time:  0.29
GtkToggleButton - time:  0.39
GtkCheckButton - time:  0.42
GtkRadioButton - time:  0.57
GtkTextView - Add text - time:  0.55
GtkTextView - Scroll - time:  0.50
GtkDrawingArea - Lines - time:  1.84
GtkDrawingArea - Circles - time:  3.56
GtkDrawingArea - Text - time:  2.64
GtkDrawingArea - Pixbufs - time:  0.43
 --- 
Total time: 15.61

---

### Post by jerrylamos on 2009-08-31
> **andresmh said:**
> OK, I tried GtkPerf on my hardware "VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)". The best time I got was this one:
Total time: 15.61

Well, you need a comparison with the same hardware on, say, jaunty.  If you don't have a bootable jaunty around, then boot jaunty CD Live then sudo apt-get install gtkperf.

I get GtkPerf times ranging from 10 to 60 depending on which of the four pc's I use and what level of ubuntu and whether KMS is modeset=1 or 0.

Good luck, Jerry

---

### Post by Jim March on 2009-09-01
I just pulled a 13.92 with mine - just got ALL Karmic updates including the -9 kernel.

---

