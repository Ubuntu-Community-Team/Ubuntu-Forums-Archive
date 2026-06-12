---
title: "after todays update, some websites show jagged fonts"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jwork123nl on 2009-03-17
On some websites, fonts show ragged, as if for (some fonts on those) websites subpixel rendering and/or aliasing is switched off.

The problem occurred after the update of today
I updated this system to jaunty from a freshly installed ubuntu 8.10
and I NEVER edited any config files.

I included a picture of the ubuntu website.
Problem also occurs with several other websites, e.g.
tweakers.net, nu.nl etc.


For sports I tried 
dpkg --purge -allow-force fontconfig
dpkg --purge -allow-force fontconfig-config
 
and reinstalled the packages.
Does not help, and I did not expect it to help either, since I run
with a default install.

So I think we have a problem.

Take a look at the enclosed screenshot to see what I mean.

Here's for hoping this problem will be solved quickly...

---

### Post by nyarnon on 2009-03-17
There are a lot of updates going on at the moment and I think that you better wait a while becouse it probably will solve itself soon. In the mean time you might try some of the stuff in 

[http://ubuntuforums.org/showthread.php?t=1094867&highlight=fonts](http://ubuntuforums.org/showthread.php?t=1094867&highlight=fonts)

Have fun.

---

### Post by jwork123nl on 2009-03-17
I installed ttf-mscorefonts-installer
This seems to solve the problem.

I read somewhere that it might be a fallback problem with a
missing font. Perhaps now my fallback is better :-)

Nyarnon, thx!

---

### Post by David Tomic on 2009-03-17
> **jwork123nl said:**
> I installed ttf-mscorefonts-installer
This seems to solve the problem.


Same here ... seemed to do the trick for me as well! ;)

---

### Post by rudenko_ruslan on 2009-03-17
Yeah, ttf-mscorefonts-installer "solved" this issue, but what about those people, who don't want to use that fonts? :-k

---

### Post by nyarnon on 2009-03-17
> **rudenko_ruslan said:**
> Yeah, ttf-mscorefonts-installer "solved" this issue, but what about those people, who don't want to use that fonts? :-k

Replace with [http://www.fontsquirrel.com/foundry/Google-Android](http://www.fontsquirrel.com/foundry/Google-Android) :popcorn:

---

### Post by hugmenot on 2009-03-17
What I did:

```
cd /etc/fonts/conf.d/
sudo ln -sf ../conf.avail/70-no-bitmaps.conf .
```

Somehow that link got removed. Not sure why.

---

### Post by taavikko on 2009-03-17
> **nyarnon said:**
> Replace with [http://www.fontsquirrel.com/foundry/Google-Android](http://www.fontsquirrel.com/foundry/Google-Android) :popcorn:

These can be installed via apt

```
apt-cache policy ttf-droid 
ttf-droid:
  Installed: 1.00~b112+dfsg-0ubuntu1
  Candidate: 1.00~b112+dfsg-0ubuntu1
  Version table:
 *** 1.00~b112+dfsg-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
        100 /var/lib/dpkg/status
```

check out liberation fonts, ttf-liberation

---

### Post by dbulante on 2009-03-17
This worked well for me.  Thanks.

> **hugmenot said:**
> What I did:

```
cd /etc/fonts/conf.d/
sudo ln -sf ../conf.avail/70-no-bitmaps.conf .
```

Somehow that link got removed. Not sure why.

---

### Post by rudenko_ruslan on 2009-03-17
I have already installed Liberation Fonts & Google Droid. But even with them, I was affected with that bug.

Well, I will use those mscorefonts for some time, I think.

By the way, **nyarnon**, on "Font Squirrel" I can see horrible fonts again #-o

UPD: Tip from hugmenot did the trick. Thanks!

---

### Post by jmmL on 2009-03-17
> **hugmenot said:**
> What I did:

```
cd /etc/fonts/conf.d/
sudo ln -sf ../conf.avail/70-no-bitmaps.conf .
```Somehow that link got removed. Not sure why.

This works like a charm for me. I really don't want to install the ms fonts.

---

### Post by jwork123nl on 2009-03-17
Well let's hope that this gets repaired by an update so indeed we do not have to resort to installing parts of MS windows, free or not :-(

BTW how do I remove these core fonts again? 
Stuff installed by .exe files - not my preferred way to install stuff....
I guess that removing the installer does not remove the actually installed fonts?

thx for any advice

John

---

### Post by rudenko_ruslan on 2009-03-17
> **jwork123nl said:**
> Well let's hope that this gets repaired by an update so indeed we do not have to resort to installing parts of MS windows, free or not :-(

BTW how do I remove these core fonts again? 
Stuff installed by .exe files - not my preferred way to install stuff....
I guess that removing the installer does not remove the actually installed fonts?

thx for any advice

John
Well, John, I just removed that package (mscorefonts) through Synaptic, so this simple method works, I believe ;)

---

### Post by Halow on 2009-03-17
Yep, I had it too. Installed ttf-droid and ttf-liberation (because I sure wasn't going for the ms ones). FIxed!
I had tried the ln fix first, and it didn't help me.

---

### Post by Polygon on 2009-03-17
i noticed the package 'font-config' or whatever cannot be installed, and it asked me to do a partial upgrade cause that one has dependency problems...so i assume once that gets fixed all will be well.

---

### Post by jwork123nl on 2009-03-17
@rudenko_ruslan:
Ah, I guess I should have just tried it! Works and uninstalls the fonts.
Just tried adding the the link with (as root, I do not use sudo)
ln -s ../conf.avail/70-no-bitmaps.conf .

And it works for me!

great :-) :-):popcorn:

---

