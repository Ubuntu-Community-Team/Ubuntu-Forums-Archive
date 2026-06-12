---
title: "screenlets and cairo-clock broken?"
date: 2009-02-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by r.k.rafciol on 2009-02-24
Hey after yesterday's update screenlets are not starting any more, screenlet manager does not start also,
also i have this problem in cairo-clock:

[[IMG]http://img502.imageshack.us/img502/5693/zrzutekranu.th.png[/IMG]](http://img502.imageshack.us/my.php?image=zrzutekranu.png)

no transparency... 

i'm running Jaunty alpha 4 x64 with all updates

---

### Post by ronacc on 2009-02-24
It looks like a python update took out screenlets .

---

### Post by dBuster on 2009-02-24
Okay so the python update kicked out the screenlets...  any idea if this was intentional or has someone already reported it with a bug report?????

---

### Post by ronacc on 2009-02-24
here is the bug I filed . 
[https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/334113 ](https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/334113 )
if you are getting a crash report send it in .

---

### Post by dBuster on 2009-02-24
> **ronacc said:**
> here is the bug I filed . 
[https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/334113 ](https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/334113 )
if you are getting a crash report send it in .

No crash report here, at least not yet...

I can't seem to get to your bug report.. even though I am logged in it says I am not authorized... oh well at least there is a bug report entered.

I did run the update again tonight and it updated python again so I am going to restart and see what happens....  wish me luck.

---

### Post by ronacc on 2009-02-24
for some reason the report was set to private I changed it to public .see the triagers comment and check your libs .

---

### Post by plun on 2009-02-25
It just seg faults....

```
plun@plun:~$ **python -u /usr/share/screenlets-manager/screenlets-manager.py**
/home/plun/.themes/Carbon/gtk-2.0/gtkrc:85: Murrine configuration option "style" is not supported and will be ignored.
/home/plun/.themes/Carbon/gtk-2.0/gtkrc:92: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/plun/.themes/Carbon/gtk-2.0/gtkrc:93: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
**Segmentation fault (core dumped)**

```

I have a crash report with this command but its better that ronacc also verifies that apport catches the crash.

---

### Post by ronacc on 2009-02-25
go ahead and send yours in , they basicly rejected my crash report because I have some libs installed from a PPA and If I try to go back to the ubuntu "official" libs it wants to take out too much stuff , so it looks like I'll have to live without screenlets for awhile .

---

### Post by plun on 2009-02-25
> **ronacc said:**
> go ahead and send yours in , they basicly rejected my crash report because I have some libs installed from a PPA and If I try to go back to the ubuntu "official" libs it wants to take out too much stuff , so it looks like I'll have to live without screenlets for awhile .

@ronacc

There is a crash report within the bug earlier posted, so it must be enough.

Python seems to be a mess for the moment nevertheless....;)

---

### Post by ronacc on 2009-02-25
yes lots of updates to python the last 2 days , thats what started this mess . If you are refering to the crash report attached to my bug (334113) that is what they "rejected" . they say they can't get any useful information because of the libs from the PPA .

---

### Post by plun on 2009-02-25
> **ronacc said:**
> yes lots of updates to python the last 2 days , thats what started this mess . If you are refering to the crash report attached to my bug (334113) that is what they "rejected" . they say they can't get any useful information because of the libs from the PPA .

Well... "Apport retracing service"... a "bot" which writes  ?

Stone dead broken and nothing else...

---

### Post by Nullack on 2009-02-25
I dont agree - if a tester has a crash and has related binaries that are not part of the Ubuntu build its fully fair to dump the problem with no support.

---

### Post by plun on 2009-02-25
> **Nullack said:**
> I dont agree - if a tester has a crash and has related binaries that are not part of the Ubuntu build its fully fair to dump the problem with no support.

I have exactly the same crash with Ubuntus package... but I installed Screenlets from source just for a check (on top).

In this case its broken despite of what a "bot" writes   ):P

---

### Post by Nullack on 2009-02-25
So then the right path is for another apport report to show it with the correct ubuntu build config, then apport will deal with it.

---

### Post by plun on 2009-02-25
> **Nullack said:**
> So then the right path is for another apport report to show it with the correct ubuntu build config, then apport will deal with it.

No the correct path is a human being which just takes the bug.....):P

Otherwise we are lost to Redmonds ideas....:lolflag:

---

### Post by Nullack on 2009-02-25
Humans do look at it :)

Automation in crash reporting and diagnosis is an important part of any serious OS project. MS do, Apple do it and so on.

---

### Post by dBuster on 2009-02-25
> **ronacc said:**
> go ahead and send yours in , they basicly rejected my crash report because I have some libs installed from a PPA and If I try to go back to the ubuntu "official" libs it wants to take out too much stuff , so it looks like I'll have to live without screenlets for awhile .

Okay I start the screenlets from terminal window and I get a crash notification however I can not report it due to the following

```
The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

libgail-common, libgtk2.0-0, libgail18, libhal1, libhal-storage1, libgtk2.0-common
```

Not sure if they are related to the screenlet issue or the apport issue...

---

### Post by plun on 2009-02-25
> **Nullack said:**
> Humans do look at it :)

Automation in crash reporting and diagnosis is an important part of any serious OS project. MS do, Apple do it and so on.

Yes I knows that but Screenlets is rather special and rather unmaintained for the moment, also a popular application. 

In this case a "human" must check this package.  !!!

You can use automagic Boolean algebra for everything but sometimes is rather stupid...:lolflag:

---

### Post by dBuster on 2009-02-25
Just updated for the morning and rebooted and tried to run from terminal the screenlets and I segfaulted.  But in the same note I then from the startup options received a crash report that clearcalendar has crashed and I am sending the crash report now.  or I should....

Okay new report filed:  [https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/334287]("https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/334287")

Also the screenlets manager just crashed also and I will append the previous crash report...

---

### Post by ronacc on 2009-02-25
@dBuster  thanks , your report it set to private like mine was so I cannot get to it  , set it to public and I'll confirm it and add comments .

---

### Post by dBuster on 2009-02-25
> **ronacc said:**
> @dBuster  thanks , your report it set to private like mine was so I cannot get to it  , set it to public and I'll confirm it and add comments .

DOH!  I did not realize that it was set private either.  Sorry about that.  It is changed now.  However, they have told me to update to the latest package as well...  What package though???

---

### Post by ronacc on 2009-02-25
apport retrace service wants you to install ttf-dejavu , it has obviously gone nuts as Plun indicated . Lets just hope that a human looks at these bug reports . That kind of  response from a bot really makes one feel all warm and fuzzy about sending in bug reports .

---

### Post by dBuster on 2009-02-26
Installed that ttf-dejavu as I was directed to and upon updating this morning I thought to restart.  So I did and now two crashes!  Submitted both of them and lets hope this isn't dismissed as a missing font again.

[https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/334833](https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/334833)

That was for the screenlets manager crash. and the following for the clear calendar.

[https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/334834](https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/334834)

---

### Post by ronacc on 2009-02-26
if apport retrace bounces those I'll file a bug against it and also post a nastygram here to try to get their attention .

---

### Post by perlluver on 2009-02-26
Screenlets bug is effecting me too, using clearweather, I added a comment to your bug.  I also installed ttf-dejavu, and now nothing at all is happening.  Not even an error.  I had these same problems in Intrepid, and now it is doing it on Jaunty.

---

### Post by plun on 2009-02-26
> **ronacc said:**
> apport retrace service wants you to install ttf-dejavu , it has obviously gone nuts as Plun indicated . Lets just hope that a human looks at these bug reports . That kind of  response from a bot really makes one feel all warm and fuzzy about sending in bug reports .

Well...  a dirty hack for time being...;)

```
gksudo nautilus
```

**/usr/lib/python2.5/site-packages**

copy the screenlets folder and paste to **/usr/lib/python2.6/dist-packages**

copy screenlets-0.1.2.egg-info to the same


Open 

```
sudo gedit /usr/lib/python2.6/dist-packages/screenlets/options.py
```

Gnomekeyring is broken somehow and must be dismissed

Line 216
```
#import gnomekeyring
class AccountOption (Option):
```

Example for terminal test

```
python2.6 -u /usr/share/screenlets/Sysmonitor/SysmonitorScreenlet.py

```

and so on... the manager is also probably fixable...

---

### Post by ronacc on 2009-02-26
Thanks for the workaround , for right now I'm going to leave as is so I can test any fixes they come up with , and also getting their attention about apport retrace giving bizzare responses , for the moment I think that is more important than me having some eyecandy .

---

### Post by dBuster on 2009-02-28
Okay my screenlets are back!  By miracle they are!  

I upgraded to Alpha 5 and in doing so it brought my screenlets back.  However with the post of : **[Heads up: Jaunty upgrades will be broken]("http://ubuntuforums.org/showthread.php?t=1082102")**

I was not sure if upgrading was a good idea.  I still did it and in the end I was broken like everyone else with a package that would not repair.  Although following the steps in that post I was able to take care of the broken package however, isn't there always a however, I have some apps that were removed like all the games, bitpim and so on.  Nothing that is a show stopper though and the best thing, SCREENLETS work!

---

### Post by r.k.rafciol on 2009-03-05
ok so the screenlets are back after all updates, few days after everything is still working so the problem have been solved:) And someone can close this topic

---

### Post by dBuster on 2009-03-05
> **r.k.rafciol said:**
> ok so the screenlets are back after all updates, few days after everything is still working so the problem have been solved:) And someone can close this topic

Actually Clearweather is not starting on its own when it should and needs to be manually started but that is not a biggie...

---

### Post by r.k.rafciol on 2009-03-08
Actually, i can it run, and it works... although i prefer wide weather

---

