---
title: "gtkperf gnome vs. kde/compiz vs kwin"
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-07-29
This will be a long post, but wanted to show detail.
All tests with gtkperf were done fullscreen and standard 100 count test.  
Not dual booted, just changed session at logon screen (same kernel, same drivers, etc)
Fresh install since a few days ago Karmic alpha 3, Updates current as of today.
Compiz settings between gnome and KDE are identical, it's the way I always set up compiz.

-------------------------------
Summary of results:
KDE fresh boot, no desktop effects enabled:  Total time: 12.94
KDE Compiz enabled:  Total time: 19.59
KDE after compiz turned off:  Total time: 13.26
KDE Kwin enabled:  Total time: 36.43 

Gnome fresh boot, no desktop effects enabled:   Total time: 12.59
Gnome Compiz enabled:  Total time: 47.76
Gnome after compiz turned off:  Total time: 35.41
-------------------------------

As you can see gnome with effects take a pretty hard hit on my system, as does KDE with kwin, (but no worried about kwin, I don't use it anyway.  Really just included it incase anyone wanted to know).  but KDE with compiz seems to do just fine.  It makes for a less than pleasant experience under gnome sesssion.  I've seen some posts about karmic being slow, might be this.

Does anyone else have any issues like this?  when enabling compiz in the terminal under gnome session I get no errors.  Is this a bug of sorts?

Laptop, intel i945m graphics.

__________________________________________
You can stop here if you don't want to see the dreary details  lol

> KDE fresh boot, no desktop effects
GtkPerf 0.40 - Starting testing: Wed Jul 29 20:11:15 2009

GtkEntry - time:  0.08
GtkComboBox - time:  1.95
GtkComboBoxEntry - time:  1.18
GtkSpinButton - time:  0.29
GtkProgressBar - time:  0.32
GtkToggleButton - time:  0.42
GtkCheckButton - time:  0.23
GtkRadioButton - time:  0.37
GtkTextView - Add text - time:  0.86
GtkTextView - Scroll - time:  0.03
GtkDrawingArea - Lines - time:  1.88
GtkDrawingArea - Circles - time:  4.19
GtkDrawingArea - Text - time:  1.03
GtkDrawingArea - Pixbufs - time:  0.13
 --- 
Total time: 12.94



KDE with compiz
GtkPerf 0.40 - Starting testing: Wed Jul 29 19:52:52 2009

GtkEntry - time:  0.09
GtkComboBox - time:  1.62
GtkComboBoxEntry - time:  1.28
GtkSpinButton - time:  0.34
GtkProgressBar - time:  0.38
GtkToggleButton - time:  0.44
GtkCheckButton - time:  0.27
GtkRadioButton - time:  0.39
GtkTextView - Add text - time:  0.99
GtkTextView - Scroll - time:  0.03
GtkDrawingArea - Lines - time:  5.18
GtkDrawingArea - Circles - time:  6.24
GtkDrawingArea - Text - time:  1.86
GtkDrawingArea - Pixbufs - time:  0.50
 --- 
Total time: 19.59


KDE after turning compiz off, no desktop effects
GtkPerf 0.40 - Starting testing: Wed Jul 29 19:54:55 2009

GtkEntry - time:  0.06
GtkComboBox - time:  1.99
GtkComboBoxEntry - time:  1.24
GtkSpinButton - time:  0.31
GtkProgressBar - time:  0.33
GtkToggleButton - time:  0.41
GtkCheckButton - time:  0.24
GtkRadioButton - time:  0.38
GtkTextView - Add text - time:  0.89
GtkTextView - Scroll - time:  0.03
GtkDrawingArea - Lines - time:  1.90
GtkDrawingArea - Circles - time:  4.30
GtkDrawingArea - Text - time:  1.03
GtkDrawingArea - Pixbufs - time:  0.14
 --- 
Total time: 13.26



KDE running KWIN
GtkPerf 0.40 - Starting testing: Wed Jul 29 19:56:12 2009

GtkEntry - time:  0.14
GtkComboBox - time:  3.90
GtkComboBoxEntry - time:  2.94
GtkSpinButton - time:  0.42
GtkProgressBar - time:  0.44
GtkToggleButton - time:  0.50
GtkCheckButton - time:  0.46
GtkRadioButton - time:  0.65
GtkTextView - Add text - time:  1.13
GtkTextView - Scroll - time:  0.03
GtkDrawingArea - Lines - time: 12.06
GtkDrawingArea - Circles - time: 10.64
GtkDrawingArea - Text - time:  2.63
GtkDrawingArea - Pixbufs - time:  0.50
 --- 
Total time: 36.43 



Gnome, fresh boot, no desktop effects
GtkPerf 0.40 - Starting testing: Wed Jul 29 20:03:26 2009

GtkEntry - time:  0.05
GtkComboBox - time:  1.67
GtkComboBoxEntry - time:  1.19
GtkSpinButton - time:  0.34
GtkProgressBar - time:  0.34
GtkToggleButton - time:  0.39
GtkCheckButton - time:  0.23
GtkRadioButton - time:  0.33
GtkTextView - Add text - time:  0.85
GtkTextView - Scroll - time:  0.03
GtkDrawingArea - Lines - time:  1.90
GtkDrawingArea - Circles - time:  4.15
GtkDrawingArea - Text - time:  1.00
GtkDrawingArea - Pixbufs - time:  0.13
 --- 
Total time: 12.59


Gnome with compiz enabled
GtkPerf 0.40 - Starting testing: Wed Jul 29 20:05:06 2009

GtkEntry - time:  0.08
GtkComboBox - time:  3.50
GtkComboBoxEntry - time:  2.06
GtkSpinButton - time:  0.37
GtkProgressBar - time:  0.79
GtkToggleButton - time:  0.91
GtkCheckButton - time:  0.68
GtkRadioButton - time:  1.04
GtkTextView - Add text - time:  3.27
GtkTextView - Scroll - time:  0.08
GtkDrawingArea - Lines - time: 14.28
GtkDrawingArea - Circles - time: 16.23
GtkDrawingArea - Text - time:  3.42
GtkDrawingArea - Pixbufs - time:  1.05
 --- 
Total time: 47.76


Gnome after turning off compiz
GtkPerf 0.40 - Starting testing: Wed Jul 29 20:06:45 2009

GtkEntry - time:  0.10
GtkComboBox - time:  4.54
GtkComboBoxEntry - time:  3.21
GtkSpinButton - time:  0.52
GtkProgressBar - time:  0.55
GtkToggleButton - time:  0.82
GtkCheckButton - time:  0.67
GtkRadioButton - time:  1.02
GtkTextView - Add text - time:  3.13
GtkTextView - Scroll - time:  0.07
GtkDrawingArea - Lines - time:  5.15
GtkDrawingArea - Circles - time: 12.64
GtkDrawingArea - Text - time:  2.55
GtkDrawingArea - Pixbufs - time:  0.43
 --- 
Total time: 35.41



---

### Post by psyke83 on 2009-07-29
There was a recent thread which talked about metacity taking 100% CPU when compiz was active - it seems quite likely to be the reason why compiz is so much slower in GNOME for you.

---

### Post by wayne_cat on 2009-07-29
> **psyke83 said:**
> There was a recent thread which talked about metacity taking 100% CPU when compiz was active - it seems quite likely to be the reason why compiz is so much slower in GNOME for you.

I had to delete the metacity key in gconf to fix this

```
/desktop/gnome/session/required_components/windowmanager = "metacity"
```My result (sorry ... no KDE on board)

gnome + compiz ... Total time:  9,47

System:

Macbook Pro - 2.0 GHz Core Duo - 2 GB RAM - ATI x1600 (radeon module)

---

### Post by ranch hand on 2009-07-29
Sorry just lurking, thought this may have to do with performance.

---

### Post by buzzmandt on 2009-07-29
> **wayne_cat said:**
> I had to delete the metacity key in gconf to fix this

```
/desktop/gnome/session/required_components/windowmanager = "metacity"
```My result (sorry ... no KDE on board)

gnome + compiz ... Total time:  9,47

System:

Macbook Pro - 2.0 GHz Core Duo - 2 GB RAM - ATI x1600 (radeon module)
lemme have the gksudo gedit line for this and I'll give it a try

Edit:  lemme rephrase that:  Please lemme have the gksudo gedit line for this and I'll give it a try, thanks

---

### Post by Darkshade on 2009-07-29
Gnome + Compiz = 8.99

AMD Sempron 1.8GHz, 1GB ram, GeForce 6800


```
GtkPerf 0.40 - Starting testing: Thu Jul 30 03:02:05 2009

GtkEntry - time:  0.17
GtkComboBox - time:  1.33
GtkComboBoxEntry - time:  1.07
GtkSpinButton - time:  0.18
GtkProgressBar - time:  0.14
GtkToggleButton - time:  0.26
GtkCheckButton - time:  0.20
GtkRadioButton - time:  0.34
GtkTextView - Add text - time:  0.65
GtkTextView - Scroll - time:  0.34
GtkDrawingArea - Lines - time:  1.20
GtkDrawingArea - Circles - time:  1.59
GtkDrawingArea - Text - time:  0.92
GtkDrawingArea - Pixbufs - time:  0.57
 --- 
Total time:  8.99
```

---

### Post by wayne_cat on 2009-07-29
> **buzzmandt said:**
> lemme have the gksudo gedit line for this and I'll give it a try

I did this because of this bug:

[http://ubuntuforums.org/showthread.php?t=1222849](http://ubuntuforums.org/showthread.php?t=1222849)

not fixed at the moment.

You can edit the entry with:

```

gconf-editor /desktop/gnome/session/required_components/windowmanager
```Delete the "Metacity" (see attached screenshot) entry and restart Gnome.

edit: not as the user root ... edit it as the user you use to login

---

### Post by buzzmandt on 2009-07-29
That was it, much much better
gtkperf with compiz enabled:
> GtkPerf 0.40 - Starting testing: Wed Jul 29 21:36:10 2009

GtkEntry - time:  0.04
GtkComboBox - time:  1.50
GtkComboBoxEntry - time:  1.26
GtkSpinButton - time:  0.36
GtkProgressBar - time:  0.35
GtkToggleButton - time:  0.43
GtkCheckButton - time:  0.26
GtkRadioButton - time:  0.37
GtkTextView - Add text - time:  0.93
GtkTextView - Scroll - time:  0.03
GtkDrawingArea - Lines - time:  5.03
GtkDrawingArea - Circles - time:  5.83
GtkDrawingArea - Text - time:  1.89
GtkDrawingArea - Pixbufs - time:  0.63
 --- 
Total time: 18.92


---

### Post by dentaku65 on 2009-07-30
My performance is quite terrible :D (gnome+compiz)

> GtkToggleButton - time:  1.08
GtkCheckButton - time:  0.41
GtkRadioButton - time:  1.04
GtkTextView - Add text - time:  3.84
GtkTextView - Scroll - time:  1.63
GtkDrawingArea - Lines - time:  6.90
GtkDrawingArea - Circles - time: 24.64
GtkDrawingArea - Text - time:  7.07
GtkDrawingArea - Pixbufs - time:  1.77
 --- 
**Total time: 57.94**

---

### Post by lithorus on 2009-07-30
> GtkEntry - time:  0,03
GtkComboBox - time:  0,42
GtkComboBoxEntry - time:  0,41
GtkSpinButton - time:  0,13
GtkProgressBar - time:  0,07
GtkToggleButton - time:  0,14
GtkCheckButton - time:  0,12
GtkRadioButton - time:  0,23
GtkTextView - Add text - time:  0,20
GtkTextView - Scroll - time:  0,01
GtkDrawingArea - Lines - time:  0,49
GtkDrawingArea - Circles - time:  2,67
GtkDrawingArea - Text - time:  0,52
GtkDrawingArea - Pixbufs - time:  0,11
 --- 
Total time:  5,56

Gnome+compiz :)
Fullscreen? At which resolution?

---

### Post by tekstr1der on 2009-07-30
Hmm. On my netbook (lenovo s10) gnome+compiz not so good, though compiz feels snappy enough and all games run well with all the Intel graphics improvements.

> GtkPerf 0.40 - Starting testing: Thu Jul 30 08:57:21 2009

GtkEntry - time:  0.16
GtkComboBox - time:  2.81
GtkComboBoxEntry - time:  2.22
GtkSpinButton - time:  0.64
GtkProgressBar - time:  0.63
GtkToggleButton - time:  0.81
GtkCheckButton - time:  0.34
GtkRadioButton - time:  0.67
GtkTextView - Add text - time:  1.77
GtkTextView - Scroll - time:  0.04
GtkDrawingArea - Lines - time:  7.03
GtkDrawingArea - Circles - time: 10.87
GtkDrawingArea - Text - time:  4.15
GtkDrawingArea - Pixbufs - time:  1.11
 --- 
Total time: 33.27

---

### Post by ssam on 2009-07-30
'[GTKperf is not a benchmark]("http://cworth.org/intel/performance_measurement/")' is the new '[glxgears is not a benchmark]("http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark")' :-)

---

### Post by wayne_cat on 2009-07-30
> **ssam said:**
> '[GTKperf is not a benchmark]("http://cworth.org/intel/performance_measurement/")' is the new '[glxgears is not a benchmark]("http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark")' :-)


Somebody has to edit 'glxgears is not a benchmark'

```
**Real Benchmarks**

<removed some text>

  **[[edit]("http://wiki.cchtml.com/index.php?title=Glxgears_is_not_a_Benchmark&action=edit&section=8")] GTK**

 
[LIST]
[*]Gtkperf - offered by any major distribution's repository.
[/LIST]

```and the funniest thing on this side ... Phoronix Test Suite ... 

"Phoronix Test Suite offers Unigine, **Gtkperf**, and a ton of other tests all in one"

---

### Post by mariner09 on 2009-07-30
So what is this really telling me?

The desktop environment is snappy?

GtkPerf 0.40 - Starting testing: Thu Jul 30 22:23:49 2009

GtkEntry - time:  0.05
GtkComboBox - time:  1.48
GtkComboBoxEntry - time:  1.17
GtkSpinButton - time:  0.51
GtkProgressBar - time:  0.65
GtkToggleButton - time:  0.46
GtkCheckButton - time:  0.15
GtkRadioButton - time:  0.49
GtkTextView - Add text - time:  0.58
GtkTextView - Scroll - time:  0.60
GtkDrawingArea - Lines - time:  1.70
GtkDrawingArea - Circles - time:  3.23
GtkDrawingArea - Text - time:  2.58
GtkDrawingArea - Pixbufs - time:  0.57
 --- 
Total time: 14.21

---

### Post by budluva04 on 2009-07-30
xfce4 + compiz
~20% cpu usage & 50% mem usage

GtkPerf 0.40 - Starting testing: Thu Jul 30 21:15:56 2009

GtkEntry - time:  0.02
GtkComboBox - time:  0.60
GtkComboBoxEntry - time:  0.50
GtkSpinButton - time:  0.13
GtkProgressBar - time:  0.03
GtkToggleButton - time:  0.11
GtkCheckButton - time:  0.05
GtkRadioButton - time:  0.09
GtkTextView - Add text - time:  0.40
GtkTextView - Scroll - time:  0.07
GtkDrawingArea - Lines - time:  0.22
GtkDrawingArea - Circles - time:  0.36
GtkDrawingArea - Text - time:  0.34
GtkDrawingArea - Pixbufs - time:  0.07
 --- 
Total time:  3.00

gnome + compiz
fresh startup
1% cpu usage 14% mem usage

GtkPerf 0.40 - Starting testing: Thu Jul 30 21:23:12 2009

GtkEntry - time:  0.01
GtkComboBox - time:  0.57
GtkComboBoxEntry - time:  0.45
GtkSpinButton - time:  0.06
GtkProgressBar - time:  0.09
GtkToggleButton - time:  0.06
GtkCheckButton - time:  0.05
GtkRadioButton - time:  0.09
GtkTextView - Add text - time:  0.31
GtkTextView - Scroll - time:  0.09
GtkDrawingArea - Lines - time:  0.21
GtkDrawingArea - Circles - time:  0.29
GtkDrawingArea - Text - time:  0.15
GtkDrawingArea - Pixbufs - time:  0.04
 --- 
Total time:  2.48


xfce + compiz
fresh startup
3% cpu %17 mem usage

GtkPerf 0.40 - Starting testing: Thu Jul 30 21:26:06 2009

GtkEntry - time:  0.02
GtkComboBox - time:  0.53
GtkComboBoxEntry - time:  0.41
GtkSpinButton - time:  0.13
GtkProgressBar - time:  0.03
GtkToggleButton - time:  0.10
GtkCheckButton - time:  0.08
GtkRadioButton - time:  0.09
GtkTextView - Add text - time:  0.31
GtkTextView - Scroll - time:  0.07
GtkDrawingArea - Lines - time:  0.20
GtkDrawingArea - Circles - time:  0.30
GtkDrawingArea - Text - time:  0.22
GtkDrawingArea - Pixbufs - time:  0.07
 --- 
Total time:  2.56

---

