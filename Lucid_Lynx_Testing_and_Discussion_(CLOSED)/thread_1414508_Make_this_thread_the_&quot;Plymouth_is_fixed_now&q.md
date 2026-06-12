---
title: "Make this thread the &quot;Plymouth is fixed now&quot; one, for all to know."
date: 2010-02-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-02-23
Looks like it's getting better, but it's been such an Alpha problem it would be nice to know it's finally ready to test.

However, I will more than likely keep it uninstalled permanently - seems like "Fluff" that is unessential to productivity.

---

### Post by katie-xx on 2010-02-23
[SIZE=2][COLOR=Blue]Ive never managed to persuade Plymouth to run trouble free on Fedora ..and it hasnt been for want of trying.

Kate[/COLOR][/SIZE]

---

### Post by xebian on 2010-02-23
Just did a fresh install and it's a huge disappointment.  Out goes the plymouth and nouveau* to the crap bin.  It's so bad keyboard is pretty much dead, blank screen except for the little square with "..No Digital Signal..'.

Having a much better results with the plain xorg-video-nv.

```
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
```

---

### Post by VMC on 2010-02-23
I'm almost afraid to say this, but since installing the latest daily-live (Feb23), I have re-booted several times and Plymouth (Version: 0.8.0~-10ubuntu1), is preforming well.
 I hope I haven't jinxed myself...

---

### Post by ranch hand on 2010-02-23
Plymouth acts just like it has for weeks here.  I still have the one install on the same hardware as the rest that plymouth works on every time.  The rest work only after a initramfs update and then there are still random failures.

---

### Post by emarkay on 2010-02-23
> **xebian said:**
> ...  Out goes the plymouth and nouveau* to the crap bin.


May be a new thread, but what's wrong with Nouveau?

---

### Post by dagrump on 2010-02-24
It is far from fixed! It doesn't lock up now, it just kicks you back to the log in screen. I removed it & it reappeared, kinda like a bad penny.
If all this thing does is some stupid blue stripes across the bottom of the screen during boot, Thanks you can keep it I'll pass.
Try getting some bugs fixed, this is a waste of effort. The old cylon eye slit looked better then this.

---

### Post by drs305 on 2010-02-24
My results mirror dagrump's. The only improvement seems to be that after crashing the first time I press <ENTER> (I now just go directly to the search window to try it) it seems to work ok after logging back in.

---

### Post by VMC on 2010-02-24
> **drs305 said:**
> My results mirror dagrump's. The only improvement seems to be that after crashing the first time I press <ENTER> (I now just go directly to the search window to try it) it seems to work ok after logging back in.

This is indeed strange. It works perfect for me, but then I use auto login feature. Never thought of trying the login option.

Maybe I'll try it and see what happens. After all this is testing.

---

### Post by drs305 on 2010-02-24
> **VMC said:**
> This is indeed strange. It works perfect for me, but then I use auto login feature. Never thought of trying the login option.

Maybe I'll try it and see what happens. After all this is testing.

My system also logs on automatically. Once at the desktop, I put the cursor in the FF search window, hit ENTER, and it crashes. It would also crash the first time I hit ENTER somewhere else, the FF search window is just my fastest access.  The system reboots to the log on screen, after which it runs without problems for the rest of the session.

64-bit, nvidia GS 7600. Interestingly, when I went to check the driver version it shows both "current version" and "nVidia riva/TNT/GeForce"  activated.

---

### Post by VMC on 2010-02-24
Ok I tried this using login screen, nothing changed. Plymouth still works, but I'm using 32-bit, P4, Intel i865.

Also, FF is the first thing I remove, and replace it with chrome.

But I have another Lucid install that I now leave untouched, to test it that way: FF, and no chrome and all the trimmings. Seeing if I now notice a difference. After all the Plymouth problems I've had I want to make sure it works every time.

I've read about the "enter" problems, and now wonder if its graphics related only and not Plymouth related.

---

### Post by ranch hand on 2010-02-24
Plymouth seems to be getting worse to me.  Maybe I am just tired of booting through recovery after trying the normal boot.

I have both auto and login installs.  Five are very similar and should all work the same as they are on the same hardware.  One does not act like the rest.  Plymouth works on it every time.  Beats me.

It does seem like a very big waste of time just to avoid a black screen for a few seconds.  I would just as soon see text.  I do anyway when I have to reboot about 80% of the time to recovery to get in.  This is not good for a grumpy geezer.

---

### Post by Didius Falco on 2010-02-24
I'm with you, Ranch Hand. I actually kind of like watching the text scroll by to make sure everything is doing what it is supposed to, though these days it moves too fast to do more than catch little bits and pieces of what it says.

 My problem is that now I can't seem to remove just plymouth anymore. Now it wants to remove the following packages along with plymouth:

```
cryptsetup remastersys ubiquity ubiquity-frontend-debconf

```

I use Remastersys (which uses Ubiquity) quite often. I actually tried letting it remove those packages, thinking I'd just reinstall them after, but the reinstallation then required plymouth.

Catch-22!!

Now plymouth seems to go to the black screen nearly all the time, while playing the drum sound. On the plus side, pressing enter will replay the drum sound and take me to the log in screen.

---

### Post by emarkay on 2010-02-24
[URL="http://www.geekconnection.org/remastersys/remastersystool.html"][COLOR=Black]May want to look at the Remastersys Forums for workarounds. [/COLOR]
[/URL]

---

### Post by ranch hand on 2010-02-25
> **Didius Falco said:**
> I'm with you, Ranch Hand. I actually kind of like watching the text scroll by to make sure everything is doing what it is supposed to, though these days it moves too fast to do more than catch little bits and pieces of what it says.

 My problem is that now I can't seem to remove just plymouth anymore. Now it wants to remove the following packages along with plymouth:

```
cryptsetup remastersys ubiquity ubiquity-frontend-debconf

```I use Remastersys (which uses Ubiquity) quite often. I actually tried letting it remove those packages, thinking I'd just reinstall them after, but the reinstallation then required plymouth.

Catch-22!!

Now plymouth seems to go to the black screen nearly all the time, while playing the drum sound. On the plus side, pressing enter will replay the drum sound and take me to the log in screen.
Another good reason for a clean install come release time.  Go with the minimal and don't install any meta packages.

Ah geeze I'll have to pick all the packages.  Yup.

You can even have Gimp, gthumb and gparted.  I think I like the gnome DE better anyway.

I am not sure what I am going to do but if plymouth doesn't start to behave pretty quick it will not be on my "real" install of the new LTS.

---

### Post by Didius Falco on 2010-02-25
Thanks for the link, Emarkay. I actually already have that link in my sig, but it was nice of you to take the time to post it.

As an experiment, I went to /bin and renamed plymouth to noplymouth and rebooted a few times. It worked just like plymouth was uninstalled, without having to remove the other stuff.

Then I did a backup with Remastersys and tested it and it worked fine too. So I at least have a workaround I can use for now.

I'm not discouraged about plymouth at this stage - after all, there is one more round of Alpha testing and 2 rounds of Beta testing before we get to the RC.

---

### Post by ranch hand on 2010-02-25
I am sure that the dependency is not on each other but the meta package that they are included in.

---

### Post by zika on 2010-02-25
> **ranch hand said:**
> I am not sure what I am going to do but if plymouth doesn't start to behave pretty quick it will not be on my "real" install of the new LTS.Give me one good reason why You would need it anyway... To see splash while booting...? I'd like to see nice screen while booting but the price looks to high... Seriously, what is the other, more important benefit of plymputh aside from splash screen?

---

### Post by philinux on 2010-02-25
I get 3 fsck messages then a blue white, corrupted graphics, progress bar.

This is only on screen for about 6 seconds. Then I get the login. I have to login twice to get to the desktop.

nVidia 8600gt 64 bit install

So it's getting removed until it's fixed.

---

### Post by ranch hand on 2010-02-25
> **zika said:**
> Give me one good reason why You would need it anyway... To see splash while booting...? I'd like to see nice screen while booting but the price looks to high... Seriously, what is the other, more important benefit of plymputh aside from splash screen?
I get the impression that it is important because Fedora uses it.  Got to keep up with the Jones.

Maybe it is needed to entertain the folks with a really short attention span.

---

### Post by zika on 2010-02-25
> **ranch hand said:**
> I get the impression that it is important because Fedora uses it.  Got to keep up with the Jones.

Maybe it is needed to entertain the folks with a really short attention span.As always, You're even more cynical than I am, You radical hard-working man...

---

### Post by emarkay on 2010-03-06
So, is it "fixed" yet?  :)

---

### Post by Uncle Spellbinder on 2010-03-06
> **emarkay said:**
> So, is it "fixed" yet?  :)

[Whats happening with Plymouth? ](http://ubuntuforums.org/showthread.php?t=1416872)

---

