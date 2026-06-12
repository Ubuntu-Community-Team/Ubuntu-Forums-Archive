---
title: "Successful Upgrade to 7.10 ? A Few Problems"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by slavojzizek on 2007-10-16
I upgraded from 7.04 to 7.10 using the official method two days ago.

Everything appears to work fine...except a few programs wont load.

System > Administration > Restricted Drivers Manager
System > Administration > Screens and Graphics
System > Administration > Software Sources
The GUI for my System Updates. The taskbar will let me know I have updates, but when I click to install them the GUI will not load.

I click on them and my hard drive ticks for a while and the programs fail to load.

NOTE: I was perhaps an idiot and installed the "Screens and Graphics" program on 7.04 to test it out (didn't work) and used synaptic to uninstall it before doing the upgrade to 7.10

Please help, as I would love to have two monitors work. I do not know what logs/additional information you need to see, so let me know and I'll promptly post it.

UPDATE1: I ran sudo apt-get update and sudo apt-get upgrade and it installed 111mb or so of updates. After restarting, I am still experiencing the aforementioned issues. In general, this is very disappointing, because I went from a rock solid 7.04 install with Beryl to a plain, less functional install of 7.10. Unlike the next poster, I would like to KEEP my installation and not have to reinstall my OS. If I am forced to do that, Fedora is looking rather attractive at the moment...

---

### Post by jimbo99 on 2007-10-16
I did the update over the web but now my box doesn't boot at all.  I get a kernel panic error on a previously solid working ubuntu 7.04 install.

I'd give people a solid word of warning on doing the upgrade now, or even till after the whole update thing calms down and people have a change to flesh out the issues and fixes.

In my situation the computer that is down was a secondary computer I had for serving some unimportant files.  So, I'll just back up the data and reinstall 7.10 from scratch.  I am unhappy that the update messed up the machine as I wasn't expecting it but then again I'm not too alarmed.  Most people would be and should be alarmed at what happened and question whether the 7.10 update is solid enough to do the update over the web.  Too many possible unaccounted for issues seem to be in place to trust it at this point.

---

### Post by fish2ways on 2007-10-16
Well, 7.10 is still 2 days away from official release, so what you've installed is either a Beta  or RC and not the final release.
Why then  be surprised when you encounter issues/bugs? They go with the territory if you choose to install pre-release software. Report them.
That's why you install pre-release software, to help the developers, not just to "see what it's like".
Upgrading a highly complex thing like an operating system is always going to be a risky thing to do, whether you use Linux or Windows and regardless of whether it's a pre or final release.

---

### Post by slavojzizek on 2007-10-16
True, however, is there any hope that my issues will be resolved in two days by doing another update?

Is there anyone who is technically inclined who can point me in the right direction to figure out the cause of these programs not loading?

---

### Post by urielka on 2007-10-18
try to run them in console and see the output.

---

### Post by karachuonyo on 2007-10-18
> **jimbo99 said:**
> I did the update over the web but now my box doesn't boot at all.  I get a kernel panic error on a previously solid working ubuntu 7.04 install.

I'd give people a solid word of warning on doing the upgrade now, or even till after the whole update thing calms down and people have a change to flesh out the issues and fixes.

In my situation the computer that is down was a secondary computer I had for serving some unimportant files.  So, I'll just back up the data and reinstall 7.10 from scratch.  I am unhappy that the update messed up the machine as I wasn't expecting it but then again I'm not too alarmed.  Most people would be and should be alarmed at what happened and question whether the 7.10 update is solid enough to do the update over the web.  Too many possible unaccounted for issues seem to be in place to trust it at this point.
I think it's a bit OTT to question the integrity of the update just because you have issues. You may just be one of the unlucky ones. Maybe you can detail the problems you have and your hardware and hopefully you will get pointers on here how to resolve them. 
P. S. You must have installed the RC which is not yet stable for normal use.

---

### Post by ljonesj on 2007-10-18
ok here is my thing. i have been running the rc and yesterday i updated 2 files because i use kwifi manger and wifi radar on ubuntu and those were the updates i installed. so right now i wonder that i updated everything i could update that know i have the full final release since yesterday but the final was released today thou but i have not been able to get anymore updates

---

### Post by slavojzizek on 2007-10-18
> **urielka said:**
> try to run them in console and see the output.

UPDATE MANAGER
```

zkrebs@Lenin:/usr/bin$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

```

RESTRICTED MANAGER
```

zkrebs@Lenin:/usr/bin$ restricted-manager
Traceback (most recent call last):
  File "/usr/bin/restricted-manager", line 40, in <module>
    from RestrictedManager.RestrictedManagerGtk import RestrictedManagerGtk as RestrictedManager
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

```


I don't know how to run the rest from console...but it looks like a common error. What do I do?

UPDATE WITH FIX
[https://bugs.launchpad.net/libcairo/+bug/129816](https://bugs.launchpad.net/libcairo/+bug/129816)

```

 Naldini Paolo wrote on 2007-08-25: (permalink)

I have solved the problem in this way:

I removed all the libraries present in /usr/local/lib and then I launched ldconfig command.(note: use sudo ldconfig)

```

---

### Post by ebichete on 2007-10-18
A quick glance suggests you have multiple versions of python installed and the system (or you) have set the wrong one as the default.

Try using the "altenatives" system to reset your default python setup. Something like:

update-alternatives --display python

- Edward -

---

### Post by slavojzizek on 2007-10-18
> **ebichete said:**
> A quick glance suggests you have multiple versions of python installed and the system (or you) have set the wrong one as the default.

Try using the "altenatives" system to reset your default python setup. Something like:

update-alternatives --display python

- Edward -

Should I do this even though the above post fixed my problem?

---

