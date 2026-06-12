---
title: "Keyboard 'extra' buttone cause logout"
date: 2009-01-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ubername on 2009-01-11
HI

I have a logitech MX3000 keyboard. Whenever I use any of the extra buttons, like Volume Control dial, mute, My Documents, e-mail etc. I get logged out (See also the thread 'No sound in Jaunty (New problem)'. Can anyone help ?

TIA

---

### Post by klange on 2009-01-11
They're actually crashing X, and I get the same issue.

---

### Post by forumache on 2009-01-11
Same here, on a Cherry Master Linux keyboard. All buttons used to work great, until a couple of weeks ago. Whenever I press a special button (Volume Up, Volume Down, Mute, Back, Forward, whatever) X crashes.

It is not a logout for me, the X server is killed abruptly.

---

### Post by tawmas on 2009-01-11
I have the same with a Microsoft Natural keyboard. It looks like a restart of X (i.e. something like CTRL-ALT-BACKSPACE), so something might well be killing X.

I found this in syslog, and I believe it is related:

```
gdm[19359]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
```

Do any of you have the like?

---

### Post by olskar on 2009-01-11
I have the very same problem both in Intrepid and Jaunty..

---

### Post by forumache on 2009-01-12
> **tawmas said:**
> I have the same with a Microsoft Natural keyboard. It looks like a restart of X (i.e. something like CTRL-ALT-BACKSPACE), so something might well be killing X.

I found this in syslog, and I believe it is related:

```
gdm[19359]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
```

Do any of you have the like?

Yes, I have it in /var/log/daemon.log. I pressed again on a extra key (I learned to avoid them in the last month), X crashed and a new line like you described appeared in daemon.log

I don't know if this will help us to identify the problem, it might be just gdm detecting that X crashed and restarting it.

---

### Post by LordVeovis on 2009-01-12
I don't know enough about that to tell you how to go any farther.  I was hoping I'd find something more definitive in syslog or dmesg or whatever places it gets reported to.  I would suggest a bug on launchpad now and see if they ask for any debugging info.


EDIT: I tried to find any more info but it seems that this is just a general crash error.  I could not find anything useful.  Sever other people that had this error had their X-server messed up after getting it.  So, lucky I guess?

---

### Post by ubername on 2009-01-12
I only get this in Jaunty (but I am using a different Kernel in Jaunty 2.6.28-4 rather than 2.6.27-something in Intrepid). Don't know if this is significant.

---

### Post by ubername on 2009-01-12
Also wish I knew how to edit the title of  a thread. 'buttone' should of course read 'buttons' but it seems everyone has worked out what I meant!

---

### Post by tawmas on 2009-01-12
> **forumache said:**
> Yes, I have it in /var/log/daemon.log. I pressed again on a extra key (I learned to avoid them in the last month), X crashed and a new line like you described appeared in daemon.log

I don't know if this will help us to identify the problem, it might be just gdm detecting that X crashed and restarting it.

Yep, it IS just gdm detecting that X crashed. But at least we know that X is crashing and not, for example, that extended keys got suddenly remapped to CTRL-ALT-BACKSPACE... :-)

I'm going to bug this, although I have no clue as of the proper package. I asked twice on IRC, but nobody could reply.

---

### Post by ShirishAg75 on 2009-01-12
> **ubername said:**
> Also wish I knew how to edit the title of  a thread. 'buttone' should of course read 'buttons' but it seems everyone has worked out what I meant!

I don't think this can be done although you could try the following. 

Go to your first post. 

Click 'Edit'

Then click on 'Go Advanced' beneath your post. 

This would show the subject. Change 'buttone' to 'button'

Click save . 

It should get saved. 

Lemme know if that works or not.

---

### Post by ubername on 2009-01-15
> **ShirishAg75 said:**
> I don't think this can be done although you could try the following. 

Go to your first post. 

Click 'Edit'

Then click on 'Go Advanced' beneath your post. 

This would show the subject. Change 'buttone' to 'button'

Click save . 

It should get saved. 

Lemme know if that works or not.

Thanks. It doesn't work, but looks like it should! I edited the title as you recommended above. Preview post worked fine, but when I clicked Submit (or whatever it's called) I got a 'Database Error'. This could be transient so I'll try again later, but if not it looks like a bug in whatever package powers these forums.

---

### Post by ubername on 2009-01-15
Off topic but - Just to add to the 'edit the title' bit: When I 'Go advanced' and edit the body of the post I don't get the 'Database Error' (I added a space in the body before the question mark and it has saved nicely)

---

### Post by marmuta on 2009-01-16
> **ubername said:**
> HI

I have a logitech MX3000 keyboard. Whenever I use any of the extra buttons, like Volume Control dial, mute, My Documents, e-mail etc. I get logged out...


Maybe this is another trigger for the CopyKeyClass crashes. Have a look at [#309785]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/309785") or [#311254]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/311254").

Do the crashes stop when you press any normal key before the extra buttons? This works for me, that is, if I think of it every time, which I don't #-o.

---

### Post by ubername on 2009-01-16
> **marmuta said:**
> Maybe this is another trigger for the CopyKeyClass crashes. Have a look at [#309785]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/309785") or [#311254]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/311254").

Do the crashes stop when you press any normal key before the extra buttons? This works for me, that is, if I think of it every time, which I don't #-o.

Do you mean that I should press and hold a normal button before using the 'extra' buttons. Obviously I have typically pressed a normal button sometime before using the extra buttons (e.g. typing this!)

---

### Post by marmuta on 2009-01-16
> **ubername said:**
> Do you mean that I should press and hold a normal button before using the 'extra' buttons. 
No, I really meant pressing and releasing any letter on the keyboard. Typing replies does count :). If X still crashes then this is probably a different problem. Better file a new bug. A [X backtrace]("https://wiki.ubuntu.com/X/Backtracing") would be very helpful too, to narrow down the cause.

---

### Post by ubername on 2009-01-16
> **marmuta said:**
> No, I really meant pressing and releasing any letter on the keyboard. Typing replies does count :). If X still crashes then this is probably a different problem. Better file a new bug. A [X backtrace]("https://wiki.ubuntu.com/X/Backtracing") would be very helpful too, to narrow down the cause.

Ooh, X backtrace looks scary (having to remotely logon from another machine) I think I will leave that to more competent folk for now.

---

### Post by tawmas on 2009-01-16
> **marmuta said:**
> No, I really meant pressing and releasing any letter on the keyboard. Typing replies does count :). If X still crashes then this is probably a different problem. Better file a new bug. A [X backtrace]("https://wiki.ubuntu.com/X/Backtracing") would be very helpful too, to narrow down the cause.

I'm a bit sleepy right now, so let's see if I got it right. I type a letter, say R, and release it, and then I type one of the special keys right away; and if X crashes, this is likely NOT to be the same bug already reported?

I just did the above, and it crashed for me. I had a quick glance at the instruction for an X backtrace, and they don't seem much worse than a regular backtrace (well, I use SSH a lot). I'm going to bed now, but I'll try to get a backtrace tomorrow. I don't use those keys all that often, but this is a bug I want squashed by release time! :-)

---

### Post by marmuta on 2009-01-17
> **ubername said:**
> Ooh, X backtrace looks scary (having to remotely logon from another machine) I think I will leave that to more competent folk for now.
I've tried to find an easier way but no luck, sorry.
Apport or core dumps should have been just as helpful, but I somehow couldn't get them to trigger with X-crashes. Dunno why, I think it should work but maybe I'm wrong. I'm going to file a bug against apport.
> **tawmas]
I'm a bit sleepy right now, so let's see if I got it right. I type a letter, say R, and release it, and then I type one of the special keys right away said:**
> 
Yes, that's about what I meant to say, thank you. Without a backtrace it's hard to be sure what's really going on though.

[QUOTE=tawmas]I'll try to get a backtrace tomorrow. I don't use those keys all that often, but this is a bug I want squashed by release time!
great!

---

### Post by marmuta on 2009-01-18
Yay, [#309785]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/309785") and probably [#311254]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/311254")have been fixed!
My Xorg crashes are gone. Better update your systems and retest before digging any further.```
xorg-server (2:1.5.99.901-0ubuntu1) jaunty; urgency=low

  [ Timo Aaltonen ]
  * debian/rules: Enable dbus-support.
  * Merge current server-1.6-branch.
  * Disable patch 107 for now, to see what kind of a performance hit 
    it'll be. The problem it causes is random garbage on windows
    while apps are being loaded.
    (LP: #254468)
  * Remove patches 150, 151, 152, 154, applied upstream.

  [B][ Bryce Harrington ]
  * 156_exevents_copykeyclass_nullptrcheck.patch: Add several NULL pointer
    checks in CopyKeyClass to prevent SEGFAULT seen when pressing button
    on an ATI USB remote control.
    (LP: #311254)[/B]

 -- Timo Aaltonen <tjaalton@ubuntu.com>  Sat, 17 Jan 2009 16:17:58 +0200

```

---

### Post by forumache on 2009-01-18
marmuta,

my crashes are gone too, but now the extra buttons are ignored completely. They used to work.

How is it on your keyboard?

I joined [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/318261](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/318261) because it seams to me that Matt is hit by a similar problem. His ATI USB remote used to crash X, now it just doesn't work.

---

### Post by tawmas on 2009-01-18
> **forumache said:**
> marmuta,

my crashes are gone too, but now the extra buttons are ignored completely. They used to work.

How is it on your keyboard?

I joined [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/318261](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/318261) because it seams to me that Matt is hit by a similar problem. His ATI USB remote used to crash X, now it just doesn't work.

Same here with my Microsoft wireless keyboard. Crashes are gone, but now they keys are totally ignored.

Fact is, there are now NULL checks in place to prevent NULLs from crashing X, but the real problem is that there are NULL values in the first place. We can't get this fixed until we understand where those are coming from, but I just don't know how to help in that.

---

### Post by ubername on 2009-01-18
My crashes also gone (although I had to change to the main update server in software sources as these fixes hadn't replicated to my local one yet!)

---

### Post by marmuta on 2009-01-18
forumache, no extra keyboard buttons here, sorry. My beef was with onboard crashing X and that is fixed now with all the keys still working. I just thought all those crashes could be related and apparently they were.

I remember my old wireless pointer doubles as a HID keyboard. I'll try to find all the pieces and add to the bug if it does something funny.

> **tawmas said:**
> Fact is, there are now NULL checks in place to prevent NULLs from crashing X, but the real problem is that there are NULL values in the first place. We can't get this fixed until we understand where those are coming from, but I just don't know how to help in that.
I don't understand half of that keyboard code either, but the patch came from upstream. They will get it right eventually. 
The last discussion I found is here: 
[https://bugs.freedesktop.org/show_bug.cgi?id=19048](https://bugs.freedesktop.org/show_bug.cgi?id=19048)
I'd say, apart from becoming a xorg insider, the best way forward is to keep reporting the problems.

---

### Post by ubername on 2009-02-20
Hooray - my extra buttons now seem to work. One small, but bearable, snag is that when I adjust the volume a little grey box appears top right of the screen, but it doesn't actually show any level / slide bar.

---

### Post by ubername on 2009-02-20
> **ubername said:**
> Hooray - my extra buttons now seem to work. One small, but bearable, snag is that when I adjust the volume a little grey box appears top right of the screen, but it doesn't actually show any level / slide bar.

The strange behaviour of the 'slider' being a grey box could well be something to do with the 'Pop-up Notifications' option found under System > Preferences. I think it is new but it may be that I had not noticed it before. In any case, it is not yet fully functional as it always appears in the top right of the screen even when I change the settings to top left, bottom right, or bottom left. I'll wait and see. Maybe when the position is sirted so will be the content.

---

