---
title: "Where's that pointer?"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by smacky on 2012-09-20
I recently upgraded from 11.04 to 12.04.

I have a 1920xwhatever-it-is desktop and am *always* losing the pointer. In previous versions (using Gnome) I was able to set the pointer size and colour more or less independently of the theme. This didn't work 100% (it went back to the default over certain windows) but was good enough. So I had a nice big black pointer which was easy to spot.

I also set it so that Control would highlight the pointer. So if I did lose track of it a few quick taps on control would draw my eye to wherever it was hiding.

Now in Unity I can't find either of these options so I'm stuck with a tiny white pointer (and web page bgs are often white too, as here). So a significant part of my time is spent trying to spot the thing.

Do options to change the pointer colour, size, or highlighting exist now?

---

### Post by vasa1 on 2012-09-20
See if [this]("http://ubuntuforums.org/showpost.php?p=11929215&postcount=17") and the rest of the thread help.

---

### Post by smacky on 2012-09-20
Thanks. That got me *part* way there (I can change the cursor).

But there's no obvious way to resize it, so it's still tiny.

Perhaps I can use ImageMagick or something to batch resize the dozens of files in /usr/share/icons/DMZ-Black/cursors (although I don't know what type they are)?

---

### Post by JKyleOKC on 2012-09-20
Search for a program called "xeyes" (I found a version in the Debian repositories that might work for us) and see if it helps. It puts a pair of eyes on the desktop, that are always looking at the mouse pointer. It really helped when I had a problem similar to yours on a much much older distribution, even before I discovered the *buntu family...

EDIT: I found two packages in the Software Center for 10.04 Lucid LTS so you may not need to search far at all...

---

### Post by vasa1 on 2012-09-20
> **smacky said:**
> Thanks. That got me *part* way there (I can change the cursor).

But there's no obvious way to resize it, so it's still tiny.
...
Take a look at this video by **quidsup**: How to Change Mouse Cursor Size in Ubuntu 11.10 and 12.04 Unity Gnome 3.2 ([http://www.youtube.com/watch?v=Yxfa2fXJ1Wc](http://www.youtube.com/watch?v=Yxfa2fXJ1Wc)).
BTW, many of his videos are pretty decent.

---

### Post by smacky on 2012-09-21
Great! I remember xeyes as a novelty years and years ago but I can see it's utility now.

However, quidsup's video has (nearly) solved it for me. The ~/.Xresources doesn't seem to be working, but that's a minor point as I tend to just have one window maximized (ie, browser, terminal, etc) so the pointer is now at a decent size most of the time.

Changing the theme with galternatives doesn't seem to work with changing the size with dconf-editor though (ie, it reverts to the default theme, but bigger) ... ah, changiing theme in dconf-editor to DMZ-Black worked -- so galternatives is unnecessary.

This sort of thing should be an easy option via Customization>Appearance. Thanks.

---

### Post by vasa1 on 2012-09-21
If your question is solved, you could use the "Thread tools" near the top right of the page to mark it so.

---

### Post by smacky on 2012-09-21
Will do. It's nearly solved. I'll try to figure out why the Xresources stuff doesn't work tonight/tomorrow and then update the thread.

---

### Post by vasa1 on 2012-09-21
> **smacky said:**
> Will do. It's nearly solved. I'll try to figure out why the Xresources stuff doesn't work tonight/tomorrow and then update the thread.
Could you put up screenshots that illustrate your problem?

---

