---
title: "Boot screen goes blank."
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by CrankyGeek71 on 2007-09-07
I am extremely new at linux and ubuntu, the whole thing, but I am very skilled wit windows, macs, and general workings of computers.

I was bored and decided I would see what linux was all about, a friend reccommended ubuntu, and so i downloaded it, made it into a cd on 2x burn, booted it, installed it, wala.

Now i still have windows as my boot drive, and so when I boot up it gives me the option to load windows or ubuntu.

I chose ubuntu, and a few lines of text stream by really fast, I can't read them, but I know they have something to do with the kernel.

then, a pretty ubuntu logo pops up, and it gets about 85% loaded according to the bar.

Then, it switches to more text, and the screen starts scrolling and listing things that are being loaded.
it looks like this


ITEM NAME BLAH BLAH...                                                                                                     [OK]
NEXT ITEM...                                                                                                                         [OK]

Then it stops at one, for about half a second, and the whole screen goes blank the backlight of my lcd is on, so i know it hasnt shut down or gone into some sleep-like state.

I left it there for about 20 minutes, and restarted, same thing. I did this about 6 times.
I then booted into windows, it works fine, and I started typing this post.

any ideas?

---

### Post by confused57 on 2007-09-07
Can you boot into "Recovery" mode?  If you can, it might be a video driver issue.

---

### Post by CrankyGeek71 on 2007-09-07
Well, if i chose recovery mode, there is a bit more code and no graphics, but the end result is the same.

I did manage to use a cannon camera i have that can take 2 pictures per second and i just kept taking pics during the boot

I noticed the object it ended on, i only caught part of it as it was moving, but the part i can read says

Starting HP Print Server....................................................


where the ...'s are text i cannot read

it then goes totally blank, no interface, nothing

i end up having to push my reset button

it could also be stopping server, or service, or spooler, it is really hard to read.

---

### Post by confused57 on 2007-09-07
You could try pressing the "Scroll Lock" key, see if it freezes the text on the boot screen so you can read it.

You might boot up the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
lspci
```
sounds like there is hardware incompatibility?

I assume you had no problems booting the Ubuntu live cd.

---

### Post by silent the spy on 2008-02-29
mine does the same. Its working.I wait for the screen to go blank, leave it........ type in my log in name, hit enter, type in my password, hit enter and it boots. Sometimes when I turn on my lcd last after the pc has had a chance to boot I can see the screen. Weird huh

---

