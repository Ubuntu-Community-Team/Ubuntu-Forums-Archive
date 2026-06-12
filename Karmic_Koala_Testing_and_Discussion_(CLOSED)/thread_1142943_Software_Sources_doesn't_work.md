---
title: "Software Sources doesn't work?"
date: 2009-04-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ebeckhusen on 2009-04-29
After upgrading to Karmic the Software Sources gui doesn't work.  It will ask for my password but then nothing happens.  I know I can edit sources manually, but I get lazy and like to c&p sometimes.

Any way to check out what's happening and fix it?

---

### Post by skierkyles on 2009-04-29
Im getting the exact same problem.

---

### Post by Ubuntu Terrier on 2009-04-29
Same here. :confused:

---

### Post by miwaypet on 2009-04-29
Can confirm also.

---

### Post by taavikko on 2009-04-29
start the app in CLI
```
gksudo software-properties-gtk
```
what does it say?

---

### Post by FraggedLocust on 2009-04-29
Haven't tried the sources window lately. It was working when I went to check after upgrading from jaunty.

---

### Post by skierkyles on 2009-04-29
> **taavikko said:**
> start the app in CLI
```
gksudo software-properties-gtk
```
what does it say?

```
Traceback (most recent call last):  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 83, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 521, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)   
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
```

---

### Post by autocrosser on 2009-04-29
Hmmm---I really tend to do a manual edit, so didn't see this one---time for a bugreport?

---

### Post by DougieFresh4U on 2009-04-29
> **ebeckhusen said:**
> After upgrading to Karmic the Software Sources gui doesn't work.  It will ask for my password but then nothing happens.  I know I can edit sources manually, but I get lazy and like to c&p sometimes.

Any way to check out what's happening and fix it?

This has happened at the begining of every testing version for the last 2 years. It will resolve eventually, but I expect not soon :):)
"Happyy Testing"

---

### Post by Gina on 2009-04-29
Does it work in Synaptic?

---

### Post by gnomeuser on 2009-04-29
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/364092](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/364092)

---

### Post by Nullack on 2009-04-29
Good stuff gnomeuser

---

### Post by cariboo on 2009-04-30
Clicking Package-->Repositories in synaptic, just brings up a window saying the repositories have changed.

---

### Post by zenithdave on 2009-04-30
Same here !

---

### Post by MacUntu on 2009-04-30
> **DougieFresh4U said:**
> This has happened at the begining of every testing version for the last 2 years. It will resolve eventually, but I expect not soon :):)
"Happyy Testing"

Hehe, yeah. I'm having a déjà-vu of a déjà-vu. :lolflag:

---

### Post by plun on 2009-04-30
> **MacUntu said:**
> Hehe, yeah. I'm having a déjà-vu of a déjà-vu. :lolflag:

Just a reminder.....:popcorn:

```
sudo gedit /etc/apt/sources.list
```


Some users maybe needs to refresh old fashioned terminal ways....:lolflag:

---

### Post by Gina on 2009-04-30
Yes, terminal is good for testing and sorting out problems :)

BTW... I think we're supposed to use gksudo (gksu) for gedit :lolflag:

---

### Post by Gina on 2009-04-30
I've just jumped aboard :lolflag:

Installed a new jaunty plus separate home partition (all new) ext4 and edited sources.list and server to karmic and main server.  Used Synaptic to Reload and Apply all updates.

I now get the same thing - Synaptic only says Repositories changed - use Reload.  No edit available.  Reload works :)

Now there are a few more updates which I'm now applying.

---

### Post by chrisccoulson on 2009-04-30
> **DougieFresh4U said:**
> This has happened at the begining of every testing version for the last 2 years. It will resolve eventually, but I expect not soon :):)
"Happyy Testing"

DougieFresh4U is absolutely correct here. This happens at the beginning of every cycle. When the floodgates to Debian open, things like this will break until everything settle down, and there is no need to report bugs for things like this at this stage.

---

### Post by DougieFresh4U on 2009-04-30
> **Gina said:**
> 

BTW... I think we're supposed to use gksudo (gksu) for gedit :lolflag:
Thanks for the reminder to all that don't know.
Correct you are, That's what I have always used.

---

### Post by Kevbert on 2009-05-01
> **cariboo907 said:**
> Clicking Package-->Repositories in synaptic, just brings up a window saying the repositories have changed.

[[COLOR="Red"]This[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/369910") is related to gnomeusers' [[COLOR="Red"]bug report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/364092") and is fixed by the editing the Ubuntu.info file mentioned.

---

### Post by Unhban on 2009-05-04
Sorry, wrong thread....

Unh.

---

### Post by DougieFresh4U on 2009-05-04
> **Kevbert said:**
> [[COLOR="Red"]This[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/369910") is related to gnomeusers' [[COLOR="Red"]bug report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/364092") and is fixed by the editing the Ubuntu.info file mentioned.

Thanks, all is good on that 'issue' :)

---

### Post by davideotape on 2009-05-04
> **DougieFresh4U said:**
> Thanks for the reminder to all that don't know.
Correct you are, That's what I have always used.

May I ask why? I've always used sudo for gedit, and nothing's gone wrong so far....

---

### Post by taavikko on 2009-05-04
> **davideotape said:**
> May I ask why? I've always used sudo for gedit, and nothing's gone wrong so far....

sudo uses users config files with root privileges, so might mess up permissions.

gksu uses root's config files with root privileges, so doesn't affect user.

See the difference.

---

### Post by davideotape on 2009-05-04
> **taavikko said:**
> sudo uses users config files with root privileges, so might mess up permissions.

gksu uses root's config files with root privileges, so doesn't affect user.

See the difference.

Thanks for that. You learn something new every day I guess :D

---

