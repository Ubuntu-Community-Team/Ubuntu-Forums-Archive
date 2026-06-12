---
title: "Tomboy Notes broken since the weekend"
date: 2010-02-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by the.scarecrow on 2010-02-02
Since doing the updates last weekend Tomboy Notes wont start. I decided to rebuild my USB stick nice and fresh but Tomboy still refuses to work.

Are any of you having the same problem, It was working fine until last Friday 29jan.

---

### Post by afluth on 2010-02-02
Yep, I noticed the same thing.

When I attempt to start it from the terminal:
```
Unhandled Exception: System.ArgumentNullException: Argument cannot be null.
Parameter name: source
  at System.Linq.Check.SourceAndPredicate (System.Object source, System.Object predicate) [0x00000] 
  at System.Linq.Enumerable.Where[Note] (IEnumerable`1 source, System.Func`2 predicate) [0x00000] 
  at Tomboy.TomboyIndicatorTray+<CurrentMenuItems>c__Iterator1.MoveNext () [0x00000] 
  at Tomboy.TomboyIndicatorTray.SetMenuItems () [0x00000] 
  at Tomboy.TomboyIndicatorTray..ctor (Tomboy.NoteManager manager) [0x00000] 
  at Tomboy.Tomboy.StartTrayIcon () [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000]
```

---

### Post by xc3RnbFO8P on 2010-02-03
I got this problem if I try to start Tomboy Notes from Application> Accessories , but it works if add Tomboy Notes to the panel.

---

### Post by sharm on 2010-02-03
Yeah, the bug is filed here:

[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/516210](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/516210)

Basically, Ubuntu applies a patch to Tomboy to support their app indicator spec, but Tomboy 1.1.1 is not compatible with that patch at runtime.

The work-around is to add Tomboy to your panel as an applet instead.  We (upstream Tomboy) maintain a PPA with working (unpatched) packages, but we don't have Lucid packages yet.  In the future that will be another good source:

[https://launchpad.net/~tomboy-packagers/+archive/development](https://launchpad.net/~tomboy-packagers/+archive/development)

---

### Post by the.scarecrow on 2010-02-03
OKay, however adding Tomboy to my panel makes no difference as it doesn't work launched from there either.

Hope its fixed soon cos its one of my favorite apps.

---

### Post by phillw on 2010-02-03
> **the.scarecrow said:**
> OKay, however adding Tomboy to my panel makes no difference as it doesn't work launched from there either.


+1  

Added myself as an affects also to the bug report.

Phill.

---

### Post by phillw on 2010-02-05
I saw the update coming through on the email listing & sure enough, on my next update all is well with Tomboy :D

Regards,

Phill.

---

### Post by Knatchwa on 2010-02-06
On the updates today, 02/06 after about 101 updates, now I am unable to run Tomboy at all and when I try and add it to my panel all I get is the error that there is an error on the panel and the only options are to delete or don't delete.

Sorry to hear that there is nothing really setup for Lucid as of yet, or perhaps by the time this message is sent it will be different. I truly enjoy working with Tomboy and found it to be an important tool, which is why I would like to see this resolved.

There was also another question, though it may not be quite in line with the OP, is there still a way to import the notes to gnote if you are unable to run Tomboy?

Also as a side note, gnote the C++ Version seems to work with the recent updates while the original Tomboy is not working, just a bit of extra information.

---

### Post by pomnikus on 2010-02-06
It's a good day to switch to gnote :D

---

### Post by phillw on 2010-02-06
> **Knatchwa said:**
> On the updates today, 02/06 after about 101 updates, now I am unable to run Tomboy at all and when I try and add it to my panel all I get is the error that there is an error on the panel and the only options are to delete or don't delete.

Sorry to hear that there is nothing really setup for Lucid as of yet, or perhaps by the time this message is sent it will be different. I truly enjoy working with Tomboy and found it to be an important tool, which is why I would like to see this resolved.

There was also another question, though it may not be quite in line with the OP, is there still a way to import the notes to gnote if you are unable to run Tomboy?

Also as a side note, gnote the C++ Version seems to work with the recent updates while the original Tomboy is not working, just a bit of extra information.

Can you raise it as a bug. v1.1.1 is running fine on my 10.04 system. (I've even done another update since then & the requested re-boot always a 'hold my breath' moment')

Regards,

Phill.

---

### Post by hugmenot on 2010-02-06
Fully broken here too. No way to start it. System is up-to-date.

---

### Post by dimeotane on 2010-02-06
Can't run tomboy through applications menu, add to panel, or from terminal command.  Fully updated lucid system.  Here's the terminal output.

> desktop:~$ tomboy
/usr/share/themes/Human/gtk-2.0/gtkrc:85: Murrine configuration option "gradients" is no longer supported and will be ignored.

Unhandled Exception: System.DllNotFoundException: liblaunchpad-integration.so
  at (wrapper managed-to-native) LaunchpadIntegration.LaunchpadIntegration:launchpad_integration_set_sourcepackagename (string)
  at LaunchpadIntegration.LaunchpadIntegration.SetSourcePackageName (System.String name) [0x00000] 
  at Tomboy.ActionManager.LoadInterface () [0x00000] 
  at Tomboy.Application.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000]  

---

### Post by dimeotane on 2010-02-06
> **pomnikus said:**
> It's a good day to switch to gnote :D

Gnote doesn't seem to have the ability to sync... All my notes across several systems are synced using Tomboy... a really cool and useful feature.

I did however find this workaround for getting gnote to sync:
[http://ubuntuforums.org/showthread.php?t=1182584](http://ubuntuforums.org/showthread.php?t=1182584)

---

### Post by xc3RnbFO8P on 2010-02-06
Did you try to search **liblaunchpad-integration.so**
or check if you got it installed?

---

### Post by dimeotane on 2010-02-06
It isn't a package found in synaptic when I search.

---

### Post by phillw on 2010-02-06
Still works fine here, from Application --> Accessories --> Tomboy Notes.

I also tried ```
gksudo tomboy
```To see what it would it would say - started off as if it was a new installaion, no problems - puzzled.....

Anyways, I've just popped into Synaptics, it says I have 1.1.1-0Ubuntu2 and that 1.1.1-0Ubuntu3 is available, that requires that I load > liblaunchpad-integration1-cli  also

So ..... here goes !!!

/edit - yup - that borked it :(
::sigh::

Regards,

Phill.

---

### Post by phillw on 2010-02-06
Any one be kind enough to tell me how make apt-get go and re-install the older version, i know about the force command, but cannot work out how to tell it go get the ~Ubuntu2 variant.

thanks,

Phill.

---

### Post by phillw on 2010-02-09
It's back !!!

> Tomboy 1.1.2
1.1.2-0ubuntu1

If it doesn't update automatically  :D

Regards,

Phill.

---

