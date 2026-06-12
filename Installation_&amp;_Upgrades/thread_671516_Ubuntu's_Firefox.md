---
title: "Ubuntu's Firefox"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by awhite on 2008-01-18
Why is Ubuntu introducing all these customizations to Firefox?  The whole Ubuntu addons thing is stupid.  The Firefox devs have done a perfectly fine job creating an addon management interface.

What makes things worse are the other issues that arise from Ubuntu's customizations.  My experiences today has led me to remove all of Ubuntu's Firefox packages and install Firefox from the official distribution.

It all started with ColorZilla...

I wanted a color picker that actually worked.  After a quick search I found that only Ubuntu's Firefox didn't work with ColorZilla.  People on the forums suggested getting the official release and copying the libs over Ubuntu's Firefox libs.

This worked for ColorZilla...

A little while later I was using a Web Application that wasn't submitting correctly.  I reinstalled Firefox via synaptic and the issue resolved, however now ColorZilla was broken again.

After this adventure I decided to ditch Ubuntu's Firefox,  it's not like it's hard to install:
tar -xvzf firefox-2.0.0.11.tar.gz /opt
ln -s /opt/firefox/firefox /usr/bin/firefox

As I write this the "similar threads" hint of other problems with Ubuntu's Firefox distribution:

"Google in Ubuntu's Firefox is showing me a strange language!"
"Either Flash 9 or Ubuntu's FIREFOX is BROKEN in Linux"
"Wow, Ubuntu's Firefox is sloooooooooooooow"

I really hate seeing Linux distributions customize open source applications this way.  It just introduces more bugs that end up frustrating the application's developers.  I can see some value in it if you're backporting security patches or possibly enabling features beyond the default, but introducing the number of bugs Ubuntu has is unacceptable.

At the very least, have a firefox-ubuntu package and a firefox-vanilla package and document for users why they should use the ubuntu package.


-Arlo

---

### Post by sports fan Matt on 2008-01-18
I stopped using firefox and use swiftweasel..im not sure if all those packages are prominent with swiftweasel though....

---

### Post by Emerzen on 2008-01-18
While the points you raise may be valid, I think you could present them in a less offensive way.  Ask yourself, if this is important and you really would like to see it changed, what would be the best way to go about it?  A rant on the forums or a cool-headed post to the bug tracker?

---

### Post by sports fan Matt on 2008-01-18
Funny thing is everytime I try FF3 I cant run it, it automatically freezes (cant add new bookmarks, nothing imports, etc) thats why I went with swiftweasel...:)

---

### Post by argraff on 2008-01-18
I'm with awhite - it's terrible. I switched to Opera out of laziness...

---

### Post by awhite on 2008-01-23
> **Emerzen said:**
> While the points you raise may be valid, I think you could present them in a less offensive way.  Ask yourself, if this is important and you really would like to see it changed, what would be the best way to go about it?  A rant on the forums or a cool-headed post to the bug tracker?

Although my post was a bit of a rant and showed some of my frustration I thought I kept it fairly civil.  I wrote it hoping to get some details on Ubuntu's customizations to Firefox and the reason for them.

Since switching to the vanilla Firefox I've noticed one difference in Ubuntu's version.  Ubuntu does something with the fonts and default display of websites that makes them appear better at the resolution I'm running.  With vanilla Firefox some site's text is incredibly small and setting the minimum font size distorts portions of the page.  So I'm guessing Ubuntu did some work in this area to improve user experience, which is good.

I really appreciate the fact that I'm able to run an entirely open-source operating system that does everything I need.  I've been using Linux for almost 10 years.  Ubuntu is one of the best user-friendly distributions I've seen.

I just feel that it really hurts open-source to create forks or customizations of projects that aren't justified.  By justified I mean that the changes:
[LIST]
[*]Enhance/Improve the software in ways that are difficult to do with the official branch and that your users desire
[*]Backport security patches that the official branch will not backport
[/LIST]

Now you might comment that it's open-source, if people want to fork they can.  More choices are better.  Now this is true to an extent.  But the more choices there are the more confused users will be.  The bigger issue though, is the one I mentioned above.  Users will report bugs related to the fork to the developers of the official branch.  This wastes their time and slows down their own development.

Now I'll admit that I'm ignorant of the history of Ubuntu's Firefox package but from a user's perspective this is what I've seen:
[LIST]
[*][COLOR="Red"]Ubuntu's Addons - Duplicates functionality of Firefox's own addon manager.  Appears to be an attempt at integrating Firefox addons with Synaptic.  Seems unnecessary.[/COLOR]
[*][COLOR="Red"]Ubuntu's Firefox has introduced a number of bugs, Colorzilla was one I found, a quick search of the forums hints at others.[/COLOR]
[*][COLOR="SeaGreen"]Ubuntu's Firefox appears to improve font and website scaling issues.[/COLOR]
[/LIST]

I'm guessing there are other improvements, maybe flash is installed by default or embedded movies work correctly.  However, from what I've seen Ubuntu's changes to Firefox do more harm to the users and Firefox developers than good.  As for action, I'll make a bug report on ColorZilla, but my conclusion as a user was to abandon the customized version of Firefox.


-Arlo


Edit:  The bug already exists:  Bug #126940, first reported on 2007-07-19  by  ceverett

---

