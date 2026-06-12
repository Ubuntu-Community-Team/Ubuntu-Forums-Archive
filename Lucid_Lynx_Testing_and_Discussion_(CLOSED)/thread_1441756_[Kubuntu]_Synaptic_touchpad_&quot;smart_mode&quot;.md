---
title: "[Kubuntu] Synaptic touchpad &quot;smart mode&quot; grayed out"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Chareos on 2010-03-29
Hi guys,

as per topic title,
on lucid (updated yesterday)
my synaptic touchpad works fine, except for the "Smart Mode" feature (the one that stops touchpad for X seconds while writing on keyboard)

I know my very hardware (dell mini 9) is capable of that, cause I used it in a previous ubuntu release.
BUT
in KDE control panel it's grayed out.

Am  missing something here ? I'm the only one having this ?

---

### Post by Chareos on 2010-03-29
(from terminal) systemsettings 

QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: Nessun file o directory
QFileSystemWatcher: failed to add paths: /home/mini/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
mini@mini-laptop:~$ Recognized device: "SynPS/2 Synaptics TouchPad"

---

### Post by SushiR on 2010-03-29
> **Chareos said:**
> Hi guys,

as per topic title,
on lucid (updated yesterday)
my synaptic touchpad works fine, except for the "Smart Mode" feature (the one that stops touchpad for X seconds while writing on keyboard)

I know my very hardware (dell mini 9) is capable of that, cause I used it in a previous ubuntu release.
BUT
in KDE control panel it's grayed out.

Am  missing something here ? I'm the only one having this ?

Same here on my Eee 901

---

### Post by Chareos on 2010-03-30
I also filed
[https://bugs.kde.org/show_bug.cgi?id=232560](https://bugs.kde.org/show_bug.cgi?id=232560)

KDE folks say this problem is per-distribution, cause it's not a KDE module

so I filed also
[https://bugs.launchpad.net/ubuntu/+bug/551467](https://bugs.launchpad.net/ubuntu/+bug/551467)

---

### Post by Chareos on 2010-03-30
Also tried to enable SHM this way
( [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) )


(for KDE/Kubuntu):

kdesudo kate /etc/hal/fdi/policy/shmconfig.fdi
Put this into the file:

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
    </match>
  </device>
</deviceinfo>
Save and close that file, reboot,

same problem !

---

### Post by miegiel on 2010-03-31
> **Chareos said:**
> Also tried to enable SHM this way
( [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) )


(for KDE/Kubuntu):

kdesudo kate /etc/hal/fdi/policy/shmconfig.fdi
Put this into the file:

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
    </match>
  </device>
</deviceinfo>
Save and close that file, reboot,

same problem !

That way is obsolete since lucid (has to do with hal). I used the .fdi file to _simulate_ two finger scrolling. Now I'm using *xinput --set-prop --type=int .... etc. etc.* commands in a script that auto-runs when X starts.

Your problem is different, so you can't just use my script, but maybe it does give you some inspiration. [http://ubuntuforums.org/showthread.php?p=8904748](http://ubuntuforums.org/showthread.php?p=8904748)

---

### Post by SushiR on 2010-03-31
Just update, there's a new xserver-xorg-input-synaptics version, that fixes it.

---

### Post by Chareos on 2010-04-02
1.2.2-1ubuntu1 here, still same problem

---

### Post by miegiel on 2010-04-02
> **Chareos said:**
> 1.2.2-1ubuntu1 here, still same problem

*SHMConfig* (*<merge key="input.x11_options.SHMConfig" type="string">on</merge>*) was used to grab the input of touchpads (among other things I assume). It has been obsolete since karmic at least, though you could still use the function if you wanted to. In lucid *SHMConfig* is completely gone. If the *"disable touchpad while typing"* function relies on *SHMConfig* being turned on , then I think the function needs to be reimplemented in some otherway.

---

### Post by Starks on 2010-04-02
I'm using vanilla Ubuntu and two finger scrolling is suddenly grayed out. Is this the same issue?

---

### Post by miegiel on 2010-04-02
> **Starks said:**
> I'm using vanilla Ubuntu and two finger scrolling is suddenly grayed out. Is this the same issue?

Not really, but check [this thread]("http://ubuntuforums.org/showthread.php?t=1435663").

---

### Post by TheNessus on 2010-04-08
any chance this gets fixed on official release?

---

### Post by miegiel on 2010-04-08
> **TheNessus said:**
> any chance this gets fixed on official release?

bug report >> [https://bugs.launchpad.net/ubuntu/+bug/551467](https://bugs.launchpad.net/ubuntu/+bug/551467)
Only 3 people effected so far.

---

### Post by TheNessus on 2010-04-08
> **miegiel said:**
> bug report >> [https://bugs.launchpad.net/ubuntu/+bug/551467](https://bugs.launchpad.net/ubuntu/+bug/551467)
Only 3 people effected so far.
That's not true. the fact that only 3 people reported does not mean only three people are affected.

I haven't reported and effected, for example. Google it, you'd see its pretty widespread, too.

---

### Post by miegiel on 2010-04-08
> **TheNessus said:**
> That's not true. the fact that only 3 people reported does not mean only three people are affected.

I haven't reported and effected, for example. Google it, you'd see its pretty widespread, too.

Oh, sorry I didn't know the devs use google to keep track of bugs. Well, I guess the next time I have a bug in an ubuntu release under development, I'll just post something somewhere where google will find it. :twisted:

Dude! The devs don't even visit this subforum. They get their info on what needs to be fixed from launchpad. And if they can't (re)produce the bug themselves because, for example, they don't have the hardware, they ask users there to test fixes.

Google is pretty damn irrelevant!

Btw it feels great when you report a bug, a dev pokes around in the code (or what ever they do), asks you to test it, you get to report is't ½ fixed ½ unfixed, more poking code, you get to test it again and can report back it's fixed. All before the official release.

---

### Post by TheNessus on 2010-04-09
> **miegiel said:**
> Oh, sorry I didn't know the devs use google to keep track of bugs. Well, I guess the next time I have a bug in an ubuntu release under development, I'll just post something somewhere where google will find it. :twisted:


Well aren't you a smart alec. Allow me to hold my breath and not not join you in useless pathetic condescending.

---

