---
title: "Gnome login slow"
date: 2009-02-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-02-09
Gnome startup still seems a bit slow compared to Intrepid so I took two bootcharts of the login process.

1st one from a "cold" login after a boot, takes about 23 seconds:

[[IMG]http://img.xrmb2.net/images/689343.png[/IMG]]("http://img.xrmb2.net/images/283225.png")


2nd one from a "warm" login after a logout, takes about 17 seconds.

[[IMG]http://img.xrmb2.net/images/860564.png[/IMG]]("http://img.xrmb2.net/images/260274.png")


Notice the 6 second delay starting after the first bigger CPU load spike. I don't know what's happening there but I'm sure there's room for improvement.

Maybe someone knows about related bugs?

---

### Post by kj74 on 2009-02-09
Little slow? It's very slow.

There is massive racing condition in jaunty and also still in intrepid. Many bit's and pieces are racing, compiz, seahorse daemon, libcanberra, pulseaudio...

---

### Post by lazka on 2009-02-09
post your ~/.xsession-errors file...

if you see something like "timeout.. blahblah" or errors try to disable it in the session manager..

---

### Post by kj74 on 2009-02-09
> **lazka said:**
> post your ~/.xsession-errors file...

if you see something like "timeout.. blahblah" or errors try to disable it in the session manager..

Yes, that helps a lot but doesn't fully fix it and you loose functionality.

It's weird because they are trying to improve boot speed but seems to ignore this long standing racing mess. Who cares if it boots little bit faster? Because logging in can take longer than booting.

---

### Post by minisori on 2009-02-09
> **kj74 said:**
> yes, that helps a lot but doesn't fully fix it and you loose functionality.

It's weird because they are trying to improve boot speed but seems to ignore this long standing racing mess. Who cares if it boots little bit faster? Because logging in can take longer than booting.

+1

---

### Post by MacUntu on 2009-02-09
> **lazka said:**
>  try to disable it in the session manager..

Yeah, I know I can make login faster disabling some daemons etc. but as already stated that's not a fix.

> **kj74 said:**
> Because logging in can take longer than booting.

Actually it does for me. Boot time: 14-16 seconds, login time: 17-23 seconds. Weirdness!

---

### Post by salsafyren on 2009-02-09
> **kj74 said:**
> Little slow? It's very slow.

There is massive racing condition in jaunty and also still in intrepid. Many bit's and pieces are racing, compiz, seahorse daemon, libcanberra, pulseaudio...

Where are these race conditions? Any bugs filed?

---

### Post by kj74 on 2009-02-09
> **salsafyren said:**
> Where are these race conditions? Any bugs filed?

[324395]("https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/324395"), [310199]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/310199"), [291467]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/291467"), [322344]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/322344")

Yes and you can find more if you search, especially pulseaudio related.

---

### Post by MacUntu on 2009-02-09
Just removed seahorse-deamon from the session entries and bootcharted again.

Cold login: 23 -> 14 seconds
Warm login: 17 -> 8 seconds

Seems already fixed in SVN: [https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/324395](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/324395)

---

### Post by MacUntu on 2009-02-09
double post

---

### Post by plun on 2009-02-09
> **MacUntu said:**
> double post

Question !?....;)

I noticed that Debians version includes a real conf file for Bootchart.

Must it also be patched for logging a Gnome login..?  I cannot see any conf-entry for this ?

I am lazy today and just asks...;)

---

### Post by MacUntu on 2009-02-09
I installed the SVN version from bootchart.org and followed the INSTALL and README files. I then just did 

```
/sbin/bootchartd start; sleep 45; /sbin/bootchartd stop
```

on a VT and logged in during the 45 seconds of logging. I couldn't get it to chart the boot process, though. Maybe an Ubuntu thingy?

---

### Post by plun on 2009-02-09
> **MacUntu said:**
> I installed the SVN version from bootchart.org and followed the INSTALL and README files. I then just did 

```
/sbin/bootchartd start; sleep 45; /sbin/bootchartd stop
```

on a VT and logged in during the 45 seconds of logging. I couldn't get it to chart the boot process, though. Maybe an Ubuntu thingy?

No I took Sids package and just tested....

Testing your method... Thanks !  ;)

---

### Post by plun on 2009-02-12
Followup...  Gnome disaster..:)

[[img]http://ubuntu-pics.de/thumb/9639/jaunty_20090212_2_TMW2FN.png[/img]](http://ubuntu-pics.de/bild/9639/jaunty_20090212_2_TMW2FN.png)


Approx **65 seconds** for a start.   (after 65s its manual starts)


EDIT   Automagic login AND Compiz disabled,   **50 sec**

Compiz takes approx 10s.....    starting later with fusion-icon

[[img]http://ubuntu-pics.de/thumb/9640/jaunty_20090212_4_1DakBR.png[/img]](http://ubuntu-pics.de/bild/9640/jaunty_20090212_4_1DakBR.png)


------------------------------------------------------


Bootchart was updated twice yesterday for Jaunty.


Solution from Martin Pitt howto add a gnome login to Bootchart
```

- Install the package 'bootchart'
- sudo rm /etc/rc2.d/S99stop-bootchart
- Reboot your system
- sudo /etc/init.d/stop-bootchart start
```

NOTE!!!  Last command used every time


**_EDIT/EDIT_**

```
gksudo gedit /etc/bootchartd.conf
```



> #
# Configuration for bootchartd, the bootchart logger script.
#

# tmpfs size
# (32 MB should suffice for ~20 minutes worth of log data, but YMMV)
**TMPFS_SIZE=5m**

# Sampling period (in seconds)
SAMPLE_PERIOD=0.2



Smaller size must also be OK....:)

---

### Post by walmis on 2009-02-14
On archlinux warm login takes about 3-4 seconds on my laptop (with compiz enabled). Ubuntu clearly has some room for improvement.

---

### Post by syko21 on 2009-02-14
Feisty used to be a lot faster than intrepid or jaunty, how did we accumulate so much bloat in between?

---

### Post by cl333r on 2009-02-14
> **syko21 said:**
> Feisty used to be a lot faster than intrepid or jaunty, how did we accumulate so much bloat in between?

It's not bloat, it's developers not caring (enough) among Gnome devel teams - most of them are paid for issuing patches to keep it more or less stable for their distro, if you don't have your man there you know how hard is to push something that you know is better and would benefit anyone, they call it "that's how open source works", I call it "that's how YOU work". This happens in many other devel places, Gnome is not alone.
Of course there are ppl who work a lot and care a lot, but such ppl are much less. Many contributors don't get to write this, they just leave:
> 
I did everything I could, worked hard but in the end I did not even find
somebody looking into my code. I did not even get a response to the bug report.
I asked on IRC, on the mailing list and even on the bug-reporter - nobody told
me it was nonsence I was doing, or I should not care or whatever.
So yes, I am angry and that rant is personal in nature of course.
... wait ... it seems there is just nobody there.

[http://bugzilla.gnome.org/show_bug.cgi?id=515600](http://bugzilla.gnome.org/show_bug.cgi?id=515600)

---

### Post by plun on 2009-02-14
2.6.29-RC5 is a little faster.....:)

[[img]http://ubuntu-pics.de/thumb/9761/jaunty_20090214_3_eG4gU2.png[/img]](http://ubuntu-pics.de/bild/9761/jaunty_20090214_3_eG4gU2.png)


approx 55 seconds for a total boot with automagic Gnome login.

---

### Post by MacUntu on 2009-02-17
The issue with the seahorse daemon seems fixed with the latest updates - making login a lot faster (like when I disabled it).

> **plun said:**
> - Install the package 'bootchart'
- sudo rm /etc/rc2.d/S99stop-bootchart
- Reboot your system
- sudo /etc/init.d/stop-bootchart start

Just found this by accident:
> 
bootchart (0.9-0ubuntu8) jaunty; urgency=low
* Allow people to disable the stop script with bootchart=nostop (so you can chart login time).

Not tested yet.

---

### Post by plun on 2009-02-19
> **MacUntu said:**
> The issue with the seahorse daemon seems fixed with the latest updates - making login a lot faster (like when I disabled it).

Just found this by accident:

Not tested yet.

Took a new total bootchart today....  51-52 sec  ;)


[[img]http://ubuntu-pics.de/thumb/9940/jaunty_20090219_1_XbNyDW.png[/img]](http://ubuntu-pics.de/bild/9940/jaunty_20090219_1_XbNyDW.png)

---

### Post by MacUntu on 2009-02-19
Strange, system specs? You have far more I/O than me (Do, python).

28-8, autologin: 35 seconds (BIOS-bug causes an eight seconds long delay)
[[img]http://ubuntu-pics.de/thumb/9945/jaunty_20090219_3_Zr10PY.png[/img]](http://ubuntu-pics.de/bild/9945/jaunty_20090219_3_Zr10PY.png)

29-rc5, autologin: 35 seconds (BIOS-bug delay patched)
[[img]http://ubuntu-pics.de/thumb/9944/jaunty_20090219_2_UK1t3o.png[/img]](http://ubuntu-pics.de/bild/9944/jaunty_20090219_2_UK1t3o.png)

---

### Post by taavikko on 2009-02-19
Haven't used bootchart for ages, decided to test on new hardware...
Pretty good...

---

### Post by plun on 2009-02-19
> **MacUntu said:**
> Strange, system specs? You have far more I/O than me (Do, python).



OK... python is broken for the moment but I took away Gnome-do, Screenlets, PackageKit and Kerneloops

44 sec  ;)

[[img]http://ubuntu-pics.de/thumb/9948/jaunty_20090219_2_us9u12.png[/img]](http://ubuntu-pics.de/bild/9948/jaunty_20090219_2_us9u12.png)

@tavikko

Well, I must overclock more.... just a moderate for the moment and a 1000Hz kernel.

MacUntu and I also measure total time including Gnome login...;)

---

### Post by MacUntu on 2009-02-19
As you can see it's not an easy task to reasonably compare different systems.

Bottom line: 2.6.28 and 2.6.29 are fast to boot, Gnome still needs too much time to load (at least for my taste).

---

### Post by taavikko on 2009-02-19
> **plun said:**
> 
@tavikko

Well, I must overclock more.... just a moderate for the moment and a 1000Hz kernel.

MacUntu and I also measure total time including Gnome login...;)

Considering the amount of stuff you have autostarting, your time is decent;)

My comp, havent done any OC. stock setup.
I could add 20sec for my asus p6t dlx-v2 MB bios problems before startup :D
And havent enabled automated login. (security security)

Only disabled "usplash" from menu.lst since it gives me headache...

Sorry for pointless message, too many usplashes...

---

### Post by MacUntu on 2009-02-19
> **taavikko said:**
> 
And havent enabled automated login. (security security)
Just activated it for easier measurement. :)
> **taavikko said:**
> Only disabled "usplash" from menu.lst since it gives me headache...
I understand. ;)

---

### Post by plun on 2009-02-19
> **MacUntu said:**
> As you can see it's not an easy task to reasonably compare different systems.

Bottom line: 2.6.28 and 2.6.29 are fast to boot, Gnome still needs too much time to load (at least for my taste).

Yup...  Gnome-do seems to be the slow one....;)

But we are indeed within reasonable boot times as also "taavikko" wrote

Lets see within a couple of days again...:D

---

