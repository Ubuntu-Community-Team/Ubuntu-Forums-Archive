---
title: "Did I just lose all my saved emails?"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by 98cwitr on 2010-03-20
Just upgraded from 9.10 to 10.04, and it uses Thunderbird instead of Evolution. I had a folder in evolution for my saved emails. Tell me they are still somewhere and I can import them.

---

### Post by jobix on 2010-03-20
Maybe I'm not understanding this, but why can't you use Evolution on your new 10.4 setup? That way it should be able to pick up your old email. Usually, there should be a directory named .evolution in your home directory and that should have all your data. Also, for thunderbird, this should be .mozilla-thunderbird.

I hope you take away an important lesson from this. Whenever you do a major upgrade, make sure you have backed up all your important data.

---

### Post by RTrev on 2010-03-20
I'm kind of puzzled.  As far as I can tell, Thunderbird isn't installed by default, and Evolution still is.  Something weird must have happened?

---

### Post by PRC09 on 2010-03-20
I upgraded from 8.04 last night and I have Thunderbird default as well....

---

### Post by RTrev on 2010-03-20
> **PRC09 said:**
> I upgraded from 8.04 last night and I have Thunderbird default as well....

And I did a fresh install from the beta1.

---

### Post by PRC09 on 2010-03-20
Hmmm,,,Just checked another system and the same on that one as well.I checked in Synaptic and it shows as installed but it doesnt appear in Applications > Internet.I opened a terminal and typed evolution and it gave an error, secret service operation failed and then the Evolution set-up screen opened as usual.......Strange......

---

### Post by RTrev on 2010-03-20
> **98cwitr said:**
> Just upgraded from 9.10 to 10.4, and it uses Thunderbird instead of Evolution. I had a folder in evolution for my saved emails. Tell me they are still somewhere and I can import them.

Have you looked in your home directory for the .evolution folder?  It's a hidden file, so you have to set Nautilus to "Show hidden files" under the View menu.

In there should, I believe, be your mail.  I've never used Evolution except to try it once or twice, so maybe someone will jump in with better advice.  Good luck!

---

### Post by 98cwitr on 2010-03-21
yep it's there...and my folder is there. Importing is as simple as copy and pasting the folder from evolution to the thunderbird folder. Sweet....solved. Yet I still wanted Evolution, so I had to manually add a custom app back to my top panel for evolution and back into the Applications menu. 


[http://maketecheasier.com/how-to-migrate-from-evolution-to-thunderbird-in-ubuntu-intrepid/2008/12/04](http://maketecheasier.com/how-to-migrate-from-evolution-to-thunderbird-in-ubuntu-intrepid/2008/12/04)

Now if I could just get these damn window controls back on the right side and get a few crashes to correct themselves (not system critcal, but a serious kernel error keeps occurring) :(

---

### Post by RTrev on 2010-03-21
> **98cwitr said:**
> yep it's there...and my folder is there. Importing is as simple as copy and pasting the folder from evolution to the thunderbird folder. Sweet....solved.

Super!

> Yet I still wanted Evolution, so I had to manually add a custom app back to my top panel for evolution and back into the Applications menu.

Yeah, the menus are still messed up, with various programs not showing up in them.  I'm sure they'll clean that up shortly.

> 
[http://maketecheasier.com/how-to-migrate-from-evolution-to-thunderbird-in-ubuntu-intrepid/2008/12/04](http://maketecheasier.com/how-to-migrate-from-evolution-to-thunderbird-in-ubuntu-intrepid/2008/12/04)


Remember, you don't *have* to switch to Thunderbird unless you want to.  Linux is all about choice.  Evolution should still work, I believe, and should still be able to access that mail.  Your call.

> 
Now if I could just get these damn window controls back on the right side and get a few crashes to correct themselves (not system critcal, but a serious kernel error keeps occurring) :(

I saw somewhere, and of course can't remember where, instructions for changing the controls back to the right.  I think it involved running gconf-editor, and going into the metacity settings.  My thought is that it's still a beta, so I'll just see where they go with it.  When it goes final, if I don't like something about it I can change it then.  In the meantime, I'm curious.  They may come up with something I'd never thought of which works really well. :D

As for the errors, I think you're probably seeing the Plymouth crashes that a lot of us are seeing.  It's nothing to worry about.  It's just eye-candy for the boot process, if I understand it correctly.  And it doesn't work very well for a lot of us.  I'm sure that will also be fixed.  Don't forget, Ubuntu's beta code is amazingly stable and well-done, but we *are* running beta (TEST) code.  We can't expect it to be perfect yet, or it would already have gone final. ;)

---

### Post by 98cwitr on 2010-03-21
so that's why it looked like a pink windows 98SE boot :p

Got my window controls moved back using this command:

```
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close" 
```

---

