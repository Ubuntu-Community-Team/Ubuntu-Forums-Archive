---
title: "Latest Firefox Update completely messed it up"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by salukibob on 2008-11-18
Hi There,

After the latest firefox 3 update (I think it was last night) my version of firefox has lots of annoying little problems. They have all manifested themselves since the last updates. My version is 3.0.4, just installed straight from 'apt-get install firefox'.

The problems are:
1. Search bar doesn't redirect to google when you press enter, or even when you press on the magnifying glass. Again, nothing happens if I change search provider.
2. The back button doesn't work at all. It is permanently greyed out. I have previously enabled using the backspace key for moving back through pages, and this still works fine. But still very annoying.
3. Adobe flash seems to not want to play properly anymore. Using BBC iplayer, it just freezes, as soon as you try to play something. 
4. Sometime just exits itself for no apparent reason. 

Thats the list so far, but i'm wondering if i'll find anymore. I've tried uninstalling (apt-get remove) and re-installing, but no help. Has anyone had any of these problems before, or suffering the same as me after the update?

I've recently (4 days ago) also installed thunderbird. Don't know if that may have messed things up.

Any clues?

Thanks
salukibob

---

### Post by salukibob on 2008-11-18
Sorry, I meant to say also that i'm using Hardy Heron, 8.04

Cheers

---

### Post by Tsu Dho Nimh on 2008-11-18
Mine too: totally borked

UBUNTU 8.04 

CTRL-F doesn't open the FIND menu
Half my add-ons aren't working

All the usual dialog boxes open blank,and minimized so that I can't bookmark anything, edit my preferences, clear my cache or anything. 

The type-ahead for the browser bar errors out so I can't get to the sites:

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias([http://www.pinktruth.com/](http://www.pinktruth.com/))
7:getEngineByAlias([http://www.pinktruth.com/](http://www.pinktruth.com/))
8:getShortcutOrURI([http://www.pinktruth.com/](http://www.pinktruth.com/),[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:()
12:([object KeyboardEvent])
13:anonymous(textentered,[object KeyboardEvent])
14:fireEvent(textentered,[object KeyboardEvent])
15:onTextEntered()
16:handleEnter(false)
17:onKeyPress([object KeyboardEvent])
18:onxblkeypress([object KeyboardEvent])

*****************
There's more,lots more.

How can we back out of this "upgrade"?

---

### Post by tipiglen on 2008-11-18
Mine works fine so far as I can tell but it keeps telling me it's been updated and must be re-started....and when I did re-start it, it told me again, and again...

ctrl-f gets me find, searches Ok, add-ons ok, but what's with the re-start notification?

btw, I'm on intrepid.

Using quite a bit of cpu for a "lightweight" browser...```
ed@ubuntu:~$ pidstat 2
Linux 2.6.27-7-generic (ubuntu) 	11/19/2008 	_i686_

12:05:12 AM       PID   %user %system    %CPU   CPU  Command
12:05:14 AM      5232    1.47    0.98    2.45     1  Xorg
12:05:14 AM      5543    5.88    2.45    8.33     0  pulseaudio
12:05:14 AM      5955   53.43    4.90   58.33     0  firefox
12:05:14 AM      6358    0.00    0.98    0.98     1  gnome-terminal
12:05:14 AM      6418    0.00    0.98    0.98     1  pidstat

12:05:14 AM       PID   %user %system    %CPU   CPU  Command
12:05:16 AM      4645    1.00    0.00    1.00     1  kondemand/1
12:05:16 AM      5232    2.00    0.00    2.00     1  Xorg
12:05:16 AM      5543    7.00    1.50    8.50     0  pulseaudio
12:05:16 AM      5955   51.50    5.50   57.00     1  firefox
12:05:16 AM      6418    1.00    1.00    2.00     1  pidstat

12:05:16 AM       PID   %user %system    %CPU   CPU  Command
12:05:18 AM      5232    1.50    1.00    2.50     1  Xorg
12:05:18 AM      5543    7.00    1.00    8.00     0  pulseaudio
12:05:18 AM      5955   50.00    6.00   56.00     0  firefox
12:05:18 AM      6358    1.00    0.00    1.00     1  gnome-terminal
12:05:18 AM      6418    0.00    1.00    1.00     1  pidstat

12:05:18 AM       PID   %user %system    %CPU   CPU  Command
12:05:20 AM       183    0.00    1.00    1.00     0  pdflush
12:05:20 AM      5232    1.50    1.00    2.50     1  Xorg
12:05:20 AM      5543    6.00    2.00    8.00     1  pulseaudio
12:05:20 AM      5955   70.00    5.50   75.50     0  firefox
12:05:20 AM      6418    1.00    0.00    1.00     1  pidstat

12:05:20 AM       PID   %user %system    %CPU   CPU  Command
12:05:22 AM      5232    2.00    1.00    3.00     0  Xorg
12:05:22 AM      5543    5.00    3.00    8.00     1  pulseaudio
12:05:22 AM      5955   72.50    5.50   78.00     0  firefox
12:05:22 AM      6418    0.00    1.00    1.00     1  pidstat

12:05:22 AM       PID   %user %system    %CPU   CPU  Command
12:05:24 AM      1157    0.00    1.00    1.00     1  ata/1
12:05:24 AM      5232    1.00    1.00    2.00     0  Xorg
12:05:24 AM      5543    7.00    2.00    9.00     0  pulseaudio
12:05:24 AM      5548    1.00    0.00    1.00     0  gconfd-2
12:05:24 AM      5955   53.50    4.00   57.50     1  firefox
12:05:24 AM      6358    0.00    1.00    1.00     0  gnome-terminal
12:05:24 AM      6418    0.00    1.00    1.00     1  pidstat

12:05:24 AM       PID   %user %system    %CPU   CPU  Command
12:05:26 AM      5232    1.50    1.00    2.50     1  Xorg
12:05:26 AM      5543    6.50    3.00    9.50     0  pulseaudio
12:05:26 AM      5955   65.00    7.00   72.00     1  firefox
12:05:26 AM      6358    1.00    0.00    1.00     1  gnome-terminal
12:05:26 AM      6418    0.00    2.00    2.00     0  pidstat
q
12:05:26 AM       PID   %user %system    %CPU   CPU  Command
12:05:28 AM      5086    0.00    1.00    1.00     0  hald-addon-stor
12:05:28 AM      5232    1.50    1.00    2.50     0  Xorg
12:05:28 AM      5543    5.50    2.00    7.50     0  pulseaudio
12:05:28 AM      5567    0.00    1.00    1.00     0  metacity
12:05:28 AM      5632    0.00    1.00    1.00     1  mixer_applet2
12:05:28 AM      5955   64.50    7.00   71.50     0  firefox
12:05:28 AM      6418    1.00    0.00    1.00     1  pidstat


``````
top - 00:16:29 up 47 min,  2 users,  load average: 0.52, 0.77, 0.71
Tasks: 116 total,   2 running, 110 sleeping,   4 stopped,   0 zombie
Cpu(s): 16.1%us,  3.1%sy,  0.0%ni, 80.6%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:    514112k total,   505472k used,     8640k free,    10044k buffers
Swap:  2088440k total,     4796k used,  2083644k free,   155756k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5955 ed        20   0  329m 155m  29m S   35 30.9  15:16.84 firefox            
 5543 ed        20   0 31032 4560 3504 R    8  0.9   1:08.17 pulseaudio         
 5232 root      20   0  358m  28m 8204 S    3  5.6   1:32.51 Xorg               
 6358 ed        20   0 98.9m  24m  12m S    2  4.9   0:06.44 gnome-terminal     
 4643 root      15  -5     0    0    0 S    1  0.0   0:00.80 kondemand/0        
 5602 ed        20   0 21212 3080 1752 S    1  0.6   0:03.54 gnome-screensav    
    1 root      20   0  3056 1884  564 S    0  0.4   0:05.62 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.20 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.26 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper         
```

Otherwise OK
ed

---

### Post by strider22 on 2008-11-19
Here is a work-a-round. If you have google in your favourites, I seem to be able to search for a site, click the link and then it works fine.

If you don't have google in your favorites then right click your desktop, create a document. Call it google.html
Insert <a href="http://google.com">Google</a>
and save the file. Double click on it, then click on the google link. Yuck, I know but you may be desperate. (how did you get here?)

If I type in the site or select it from the type-ahead browser bar it fails with the above assert.

Fortunately, all my usual sites are on tabs that were restored after the upgrade. Those sites work fine too, so does my back button.

---

### Post by salukibob on 2008-11-20
Ok, so thankfully i've managed to fix it, although its a bit of an embarrasing reason why it was broken. Basically, I had totally run out of disk space. All fixed now though, so its all good. 

Sorry thats not much help for anyone else.

Cheers
salukibob

---

### Post by steveneddy on 2008-11-20
Can we mark this as solved please?

---

### Post by strider22 on 2008-11-20
I have 34GB (not KB) on the main filesystem and
55GB on the second partition where vista sleeps its long sleep.
I am not out of disk space.

The problem started when I upgraded. The upgrade required a reboot. I reloaded the previous sessions. Then I got the assert. I rebooted and the problem did not go away. I have now rebooted for the 3rd time since upgrading and yes the problem has now gone away.

---

### Post by Tsu Dho Nimh on 2008-11-21
steven - 
Several people have found work-arounds, but it's not what I would call solved.  

Something went wrong during the update process. My roommate walked me though how to reinstall FF, but that's not the same as fixing the update so it's not borked after an update. 

I think this is what I did ... just said YES to everything. 

$ sudo apt-get install firefox –reinstall

---

