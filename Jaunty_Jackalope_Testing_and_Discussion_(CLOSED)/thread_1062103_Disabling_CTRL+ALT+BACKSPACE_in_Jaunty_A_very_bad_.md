---
title: "Disabling CTRL+ALT+BACKSPACE in Jaunty: A very bad idea?"
date: 2009-02-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nickpick on 2009-02-06
According to [http://www.ubuntu.com/testing/jaunty/alpha4]("this site"):

> Ctrl-Alt-Backspace is now disabled, to reduce issues experienced by users who accidentally trigger the key combo. Users who do want this function can enable it in their xorg.conf, or via the command dontzap --disable. 

Frankly, I think this is a terrible idea. For someone coming from Windows, i.e. the majority of Ubuntu users, CTRL+ALT+BACKSPACE is the standard alternative to CTRL+ALT+DELETE, in case something goes wrong. I don't know about other users, but if you ever run fullscreen applications, things tend to go wrong pretty often. Remove the said shortcut and you'll find yourself restarting your computer pretty often. (Yes, I know that we can switch to the terminal and kill the session from there, but it's not quite as straight forward as pressing a combination of buttons and loging in again; nor is re-enabling the shortcut through the terminal)

If the shortcut causes problems, replace it with a different one or, for example, force the user to hit it twice/press and hold the buttons for 3 seconds, but, for goodness sake, do not remove it!

---

### Post by jespdj on 2009-02-06
I think it is a good idea. Ctrl + Alt + Backspace stops the X server in quite a hard way, and it should not be used as a normal way to logout or stop badly behaving programs.

I guess the reason why they removed it is because it's nasty if you press this while you have a number of programs open and all your programs are killed with that single keypress, possibly leading to loss of data if you didn't save.

If you have a badly behaving program, just press Ctrl + Alt + F1 to go to a text login window, log in and use "kill ..." to stop the badly behaving program.

And no, I don't have any programs that run fullscreen and that go wrong pretty often.

---

### Post by nickpick on 2009-02-06
> **jespdj said:**
> If you have a badly behaving program, just press Ctrl + Alt + F1 to go to a text login window, log in and use "kill ..." to stop the badly behaving program.

Do you expect somebody, who just installed Ubuntu to know this sort of thing? Or should they Google it while their entire system refuses to repond?

CTRL+ALT+BACKSPACE is a straightforward way of dealing with this sort of problems. Sure, there might be more elegant ways, but I would not expect a normal user to know about them. Disabling it is like removing CTRL+ALT+DEL from Windows.

Frankly, [quite a few people]("http://ubuntuforums.org/showthread.php?t=1040988") seem to agree that this will end badly. Why is this getting implemented?

---

### Post by mb_webguy on 2009-02-06
There's a bit of a minor error in your logic.  While Windows users would probably be familiar with Ctrl-Alt-Delete, why would they be any more familiar with Ctrl-Alt-Backspace than they would Ctrl-Alt-F1?  AFAIK, there's nothing in Windows that corresponds to Ctrl-Alt-Backspace, so a Windows user new to Ubuntu would have no knowledge of this key combo.  Ctrl-Alt-Delete performs a similar function, and would be known to Windows users.

I can see the logic behind this decision.  As jespdj said, it's not a very graceful way to shut down X or log out.  The mention of accidentally activation of this combo aside, it will also prevent it's misuse.  I know I use this combo more often than I should, and I know better.

Since re-enabling the functionality is to be a single simple command, I don't think it's really a big deal.

---

### Post by nickpick on 2009-02-06
> **mb_webguy said:**
> Since re-enabling the functionality is to be a single simple command, I don't think it's really a big deal.

It is a big deal. Normal users do not know how to fix things with CTRL+ALT+1. They will never learn it. To put it simply, it's a process that requires more effort than a "user" would want to invest.

No, there's no error in my logic. I assume that there's a slight difference between learning how to press BACKSPACE instead of DELETE and killing processes through terminals? Somebody switching to Ubuntu from 9.04 onwards will simply begin to restart his computer every time something goes wrong. I've installed this system on half a dozen computers, belonging to people who are not exactly into programing, and all of them except one simply kept switching off the computer once some application froze. Sure, there might be a gentler way of fixing these issues, but, in all honesty, I simply can't imagine my grandmother killing sessions via terminal.

I'm all for giving the user the ability to disable this feature with one command or changing the combo (albeit I don't know how anybody could unconsciously press CTRL+ALT+BACKSPACE after seeing what it does once). I simply fail to find the words appropriate for this forum to describe the individual responsible for this. I understand why one might implement this sort of change, however, from my experience with computer-illiterate users, I can tell you that this will cause more harm than good.

---

### Post by HavocXphere on 2009-02-06
People trigger ctrl-alt-bckspace accidentally? Damn...

Surely those few people can disable it instead of it being disabled by default and then having 90% of the user just re-enabling it.:confused:

I'll tell you guys what will happen: Valiant noobster Joe will resort to hard-resetting the *nix box or literally pull the plug.

If a guy is on the brink of giving up because the new gfx drivers don't cooperate then the last thing one needs is something along the lines of "console login and type in...". :rolleyes: Sure its not elegant...but thats (one of) the points which could decide whether someone goes back to MS or becomes a nix convert.

I know I needed to use the combo quite a few times so far....and I'm *slowly* getting to the point where I can maybe fix it via console, but the first X days I couldn't.

---

### Post by nickpick on 2009-02-06
> **HavocXphere said:**
> I'll tell you guys what will happen: Valiant noobster Joe will resort to hard-resetting the *nix box or literally pull the plug.

This is PRECISELY what happened (and will happen) with a good deal of people I've installed Ubuntu for. I'd like to point out that all of them are academics and by no means stupid; however as non-IT people they simply couldn't bother to learn how to operate the terminals. Why would they, if all they want is to use the system?

---

### Post by mb_webguy on 2009-02-06
My point is that very rarely can you not hit Ctrl-Alt-Delete (a known Windows key combo) to log out gracefully rather than using Ctrl-Alt-Backspace.  If the system is locked up so badly that they can't use Ctrl-Alt-Delete, then they probably can't use Ctrl-Alt-Backspace either.  (And if it is locking up that badly on a regular basis, there's an underlying problem that needs to be fixed rather than continuing to you such a band-aid fix.)  Since these two key combos can produce the same result, but one is safe and the other potentially hazardous, it makes sense to disable the risky alternative.

Also, Windows users would not be any more familiar with the key combo Ctrl-Alt-Backspace than any other non-Windows key combo, such as Ctrl-Alt-F1 or Alt-F2.  They have to learn that Ctrl-Alt-Backspace exists and what it does, the same as any other key combo with which they're not familiar.  More than likely, this forum is the place where they would learn these things.  Since Windows users don't know about Ctrl-Alt-Backspace, they won't miss the functionality, and if they ever *do* need that functionality, we on this forum can advise them of the better way of doing things.

Ubuntu is designed to be friendly to non-Linux users.  Yes, it's easy to shut down X with Ctrl-Alt-Backspace.  It's easy to shut down your computer by holding down the power button.  I wouldn't recommend doing either, and for the same basic reasons.  Being friendly to non-Linux users doesn't just mean making things easier to do.  Sometimes it means making things more difficult, if those things could otherwise easily allow a new user to damage his system.  

It's generally a bad idea to let children play with matches.  The Ubuntu team is simply applying the same reasoning to the Ctrl-Alt-Backspace combo and newbies.  They're not getting rid of the matches entirely -- the functionality is still there if you need it.  They're just putting them out of reach of the kiddies.

---

### Post by xc1024 on 2009-02-07
why disable it? ctrl-alt-backspace is not something triggered by mistake very often. there are situations where you need to use it. Ubuntu team should first ask users IF they want it disabled, then make changes. perfect solution would be to ask user to turn it off/on during upgrade/install. that way everyone is happy.

alternatively, they should slightly change the way of triggering it, just as @nickpick said. my vote is to change it to pressing ctrl-alt-backspace 3 times.

---

### Post by sleepyjon on 2009-02-07
> **xc1024 said:**
> why disable it? ctrl-alt-backspace is not something triggered by mistake very often. there are situations where you need to use it. Ubuntu team should first ask users IF they want it disabled, then make changes. perfect solution would be to ask user to turn it off/on during upgrade/install. that way everyone is happy.

alternatively, they should slightly change the way of triggering it, just as @nickpick said. my vote is to change it to pressing ctrl-alt-backspace 3 times.

I agree. There are times where ctrl + alt + backspace is very useful. It's much easier to learn 3 keys than it is to learn:

ctrl + alt + f1
login
killall processname

---

