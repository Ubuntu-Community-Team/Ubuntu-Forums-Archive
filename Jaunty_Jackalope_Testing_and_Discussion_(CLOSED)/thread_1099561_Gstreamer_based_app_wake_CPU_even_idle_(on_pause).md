---
title: "Gstreamer based app wake CPU even idle (on pause)"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yanns on 2009-03-18
I tested this with Totem and Rhythmbox that both use Gstreamer.

If I pause the song, the application (Totem or Rhythmbox) is idle. But PowerTOP still complains that the application wakes up the CPU too often:
```
Wakeups-from-idle per second : 35.0     interval: 3.0s
no ACPI power usage estimate available

Top causes for wakeups:
  60.2% ( 19.7)             totem : do_nanosleep (hrtimer_wakeup) 
   9.2% (  3.0)             totem : schedule_hrtimeout_range (hrtimer_wakeup)
```

I found some posts relative to this problem:
[http://mail.gnome.org/archives/rhythmbox-devel/2007-May/msg00020.html](http://mail.gnome.org/archives/rhythmbox-devel/2007-May/msg00020.html)

See [http://bugzilla.gnome.org/show_bug.cgi?id=399012](http://bugzilla.gnome.org/show_bug.cgi?id=399012) too.

Does somebody have the same experience?

---

### Post by yanns on 2009-03-19
With gnome-mplayer, this situation is worst:


on pause:
```
Wakeups-from-idle per second : 99.2     interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  34.7% ( 27.4)           mplayer : schedule_hrtimeout_range (hrtimer_wakeup) 
  30.8% ( 24.3)           mplayer : do_nanosleep (hrtimer_wakeup) 
  13.9% ( 11.0)     gnome-mplayer : schedule_hrtimeout_range (hrtimer_wakeup)
```

on stop:
```
Wakeups-from-idle per second : 68.4     interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  42.0% ( 27.4)           mplayer : schedule_hrtimeout_range (hrtimer_wakeup) 
  37.4% ( 24.4)           mplayer : do_nanosleep (hrtimer_wakeup)
```

---

