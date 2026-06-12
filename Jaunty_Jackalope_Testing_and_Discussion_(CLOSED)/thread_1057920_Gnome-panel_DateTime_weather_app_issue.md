---
title: "Gnome-panel Date/Time weather app issue"
date: 2009-02-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zaomaster on 2009-02-02
Since upgrading to Jaunty a while back I've been unable to set the "home" for the computer so that the weather is shown in the Date/Time app. I can use the separate "Weather Report" app and it works fine, but when I try to use the Date/Time app I get an error popup saying:

"Failed to set the system timezone, Launch helper exited with unknown return code 1"

Any thoughts?

---

### Post by deresh on 2009-02-02
i had the same problem.

this has worked for me:

1. go to system -> Administration -> Time and date
2. Unlock 
3. Select your time zone
4. Turn on NTP to sync with time with internet servers ( optional )
5. close

Now i have weather in my panel for my location automaticaly set ;)

---

### Post by zaomaster on 2009-02-03
Thanks for the advice, but it still doesn't work after setting that up (but the automatic update of the clock does! ;) )

---

### Post by pressureman on 2009-02-07
I notice that there aren't so many locations to choose from anymore. Previously, for Berlin, Germany, there were three locations (Tegel, Tempelhof, and Schoenefeld, which are the three airports here). Now there is just "Berlin".

I don't think it's working, because it's apparently been 4° C and the same weather conditions, day and night, for about the last week. :???:

---

### Post by chichilalescu on 2009-02-09
I'm using intrepid, and I have the same issue: temperature, wind speed and "feels like" have been stuck for more than a month I think. I realize this is not the best place to post this, but since it's the same problem... Sunrise and sunset times do change, and I assume the actual time is also synchronized with the servers.

---

### Post by zaomaster on 2009-02-09
Well, I did a fresh install of alpha 4 and that issue is fixed. I've got another one now, though it might have more to do with evolution and my "tasks" not meshing well with no connection.

So, it must have just been some borked code... who knows.

---

### Post by awam66 on 2009-02-09
Hi folks,

I have a similar but different problem with the Date/Time.
If I click on the Date/Time in the panel (top right) the gnome panel hangs and I can't access any of the items/menus on the panel.
Have to log out and in again.
Any ideas?

---

### Post by MaX on 2009-02-09
> **awam66 said:**
> Hi folks,

I have a similar but different problem with the Date/Time.
If I click on the Date/Time in the panel (top right) the gnome panel hangs and I can't access any of the items/menus on the panel.
Have to log out and in again.
Any ideas?

Yeah something is wrong with your evolution install. There should be a bug about it (probably fixed and closed already) in the gnome bugzilla.

I had this problem a year or two ago.

---

### Post by pressureman on 2009-02-09
> **awam66 said:**
> Hi folks,

I have a similar but different problem with the Date/Time.
If I click on the Date/Time in the panel (top right) the gnome panel hangs and I can't access any of the items/menus on the panel.
Have to log out and in again.
Any ideas?

I'm seeing that problem too. If you keep a gnome-terminal open, you save yourself having to logout/login if you ```
kill `pidof gnome-panel`
```

---

### Post by awam66 on 2009-02-09
> **pressureman said:**
> I'm seeing that problem too. If you keep a gnome-terminal open, you save yourself having to logout/login if you ```
kill `pidof gnome-panel`
```

Thanks I'll try that next time I'm in Jaunty.

---

### Post by pressureman on 2009-02-15
I at least figured out why it's been reporting 4° C round the clock for the last few weeks in Berlin. Libgweather is hitting a METAR URL for the Tempelhof weather station, which stopped updating on the same day that Tempelhof airport was closed, Oct 30 last year.

I only noticed this recently, because previously I had my location set to Berlin Tegel. Now with the "improved" version of the applet, we only get one choice for Berlin, instead of three (Schoenefeld was the other previous option)... and it just happens to be hitting an obsolete station.

LP bug filed here [https://bugs.launchpad.net/ubuntu/+source/libgweather/+bug/329881](https://bugs.launchpad.net/ubuntu/+source/libgweather/+bug/329881)

Pity that it still crashes and locks up gnome-panel if I try to expand the Locations tree though. Anyone have any ideas on that one?

---

### Post by bruce89 on 2009-02-15
> **pressureman said:**
> Pity that it still crashes and locks up gnome-panel if I try to expand the Locations tree though. Anyone have any ideas on that one?

[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-panel/+bug/328378](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-panel/+bug/328378)

---

