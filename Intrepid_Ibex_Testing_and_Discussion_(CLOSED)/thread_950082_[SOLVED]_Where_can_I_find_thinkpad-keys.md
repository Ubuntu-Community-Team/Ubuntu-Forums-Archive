---
title: "[SOLVED] Where can I find thinkpad-keys?"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wenuswilson on 2008-10-16
I just upgraded to Intrepid and I want to get my keyboard layout to work again i.e. the volume and media play on the arrow keys. I checked [this site]("http://www.thetacticalnuke.com/2008/ubuntu-810-intrepid-ibex-beta-on-t61/") to get somethings to work. I'm using a Lenovo Thinkpad T61 with Ibex with a x64 bit. Suggestions?

Thanks in advance.

---

### Post by wenuswilson on 2008-10-17
I bump my threads. Sue me. Help, Help, Help!

---

### Post by LinuxT60 on 2008-10-17
I have a T60 and I was able to get all mine working.  Have you tried:
System -> Preferences -> Keyboard -> Layouts

It has a couple different TP layouts.

You also may need to remap some keys using the "Keyboard Shortcut" tool located under the keyboard option in the preferences menu.  All my keys now work (Volume, back, play, pause, etc).

Nathan

P.S.  I did not install the Thinkpad Keys Program

---

### Post by wenuswilson on 2008-10-18
> **LinuxT60 said:**
> I have a T60 and I was able to get all mine working.  Have you tried:
System -> Preferences -> Keyboard -> Layouts

It has a couple different TP layouts.

You also may need to remap some keys using the "Keyboard Shortcut" tool located under the keyboard option in the preferences menu.  All my keys now work (Volume, back, play, pause, etc).

Nathan

P.S.  I did not install the Thinkpad Keys Program

I tried this initially and setting my keyboard to the IBM -> T61 option gave me the issue. The pc is a Lenovo and that may have something to do with it?

In pressing most / if not all of the buttons the only things that seem not to work (that I care about) are the volume keys and the play/next/back/stop keys (fn+arrow keys).

I can't get my trackpoint to scroll either, that in a different post but if you have any ideas regarding that post [here]("http://ubuntuforums.org/showthread.php?p=5986697#post5986697").

---

### Post by LinuxT60 on 2008-10-20
Hmm, yeah I have a T60 which is Lenovo / IBM branded too...I am pretty sure I did the following and it worked.

Initally Set the "Layout" to be T60.
Ctrl + Alt + Bkspc, re-logged in.

Went to "Keyboard Shortcuts" and then mapped the following:
Volume Up / Down - x86AudioRaiseVolume, x86AudioLowervolume
Mute-              x86AudioMute
Play-              x86AudioPlay
Previous-          x86AudioPrev
Next-              x86AudioNext

The back / forward buttons for the web seemed to work without mapping.

That should do it.

Nathan

---

### Post by FuturePilot on 2008-10-20
thinkpad-keys is part of the hotkey-setup package in /usr/sbin/thinkpad-keys

---

### Post by wenuswilson on 2008-10-21
Alright for those who may be in the same boat as I was -- I solved it.

In Admin -> Software Sources -> Third-party Updates -> Unsupported updates. Make sure it's checked. That was you can get all of the updates. And everything that I had problems with will go away. My mistake.

---

