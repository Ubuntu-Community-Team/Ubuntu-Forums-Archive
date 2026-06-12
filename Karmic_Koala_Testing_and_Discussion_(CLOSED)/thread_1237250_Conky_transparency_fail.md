---
title: "Conky transparency fail"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-08-11
Conky appears to be messing up a lot more than it used to. For example, if I load gnome-do, the transparency turns opaque.

[Example video (only ~400k)http://i.thepcspy.com/oli/conkyfail.avi]("http://i.thepcspy.com/oli/conkyfail.avi")

Any idea how to stop it doing that? I've played around with a lot of settings but I'm not getting anywhere fast.

---

### Post by taavikko on 2009-08-11
What's the .conkyrc like?
just snip the variables of and paste the config-part only.

---

### Post by OliW on 2009-08-11
```
background yes
use_xft yes
xftfont Sans:size=8
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 12
gap_y 12
no_buffers no
uppercase no
cpu_avg_samples 2
override_utf8_locale no

on_bottom yes
```

---

### Post by taavikko on 2009-08-11
Test if setting "own_window_type desktop" helps.

It's been a long time since last played with conky.
It could be that compiz/GPU is messing with conky

---

### Post by OliW on 2009-08-11
> **taavikko said:**
> Test if setting "own_window_type desktop" helps.

It's been a long time since last played with conky.
It could be that compiz/GPU is messing with conky

It does but it also means compiz (or whatever's giving my windows shadows)  tries to give it a drop-shadow.

---

### Post by tekstr1der on 2009-08-11
There's a bug filed about this. [https://bugs.launchpad.net/ubuntu/+source/conky/+bug/405340](https://bugs.launchpad.net/ubuntu/+source/conky/+bug/405340)

It's fixed in the PPA mentioned in the report.

---

### Post by OliW on 2009-08-11
> **tekstr1der said:**
> There's a bug filed about this. [https://bugs.launchpad.net/ubuntu/+source/conky/+bug/405340](https://bugs.launchpad.net/ubuntu/+source/conky/+bug/405340)

It's fixed in the PPA mentioned in the report.

Oh yes, that's much better. Thank you.

---

