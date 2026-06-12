---
title: "Flock 2, the browser for people who like to be connected"
date: 2008-06-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ubulette on 2008-06-16
Hi,

it's been a while since I last posted Mozilla related stuff in here.

I recently packaged Flock 2, currently 2.0 beta 1 freshly released, and I'm working to get it in Intrepid.

In the meantime, preview packages are in my [PPA]("https://launchpad.net/~fta/+archive").

Feedbacks welcome.

---

### Post by ShirishAg75 on 2008-06-16
Looking forward for the same.

---

### Post by ronacc on 2008-06-16
I've got flock installed and it looks good ,thanks , I'll give ff4 a shot when you get the amd64 pkg built for intrepid .

---

### Post by durand on 2008-06-17
> **ronacc said:**
> I've got flock installed and it looks good ,thanks , I'll give ff4 a shot when you get the amd64 pkg built for intrepid .

ff4? Don't you mean ff3?

I really, really like ecoflock but the mozilla/gecko/whatever_it's_called engine doesn't appeal to me. Die hard opera fan here :lolflag:

---

### Post by ronacc on 2008-06-17
No I meant ff4 .  there were some packages in ubulette,s PPA labled ff4  yesterday , they are gone now though . I also am a diehard Opera fan , but I like to see what else is out there . BTW did flock import your opera bookmarks right ? it messed mine up a bit and didn't get all of them .

---

### Post by durand on 2008-06-17
I didn't really bother importing them cos I just wanted to try it out. I'll get it from the ppa now.

Have mozilla already started working on firefox 4?

---

### Post by ubulette on 2008-06-17
> **ronacc said:**
> No I meant ff4 .  there were some packages in ubulette,s PPA labled ff4  yesterday , they are gone now though . I also am a diehard Opera fan , but I like to see what else is out there . BTW did flock import your opera bookmarks right ? it messed mine up a bit and didn't get all of them .

I removed my FF4.0 / Xul2.0 packages because I worked on that before Mozilla decided that mozilla-central will first target FF3.1 / Xul 1.9.1 instead of the initially planed 4.0 / 2.0.
So you could say I've been tricked, but it's my own fault, noone asked me to work on that.

Sorry for the confusion. Those who used my PPA before are already aware that I like tracking the freshest thing possible. I plan to follow Gecko 2 as soon as it emerges.. a fork in mozilla-central is expected, probably later this year, but that would be upstream choice, i.e. only when they think it's the right time.

BTW, in case you wonder, mozilla-central is the name of the hg/Mercurial branch hosting gecko/xul and firefox right now (it used to be hosted in CVS).
Seamonkey and Thunderbird are working hard to move to hg too as they are tracking xul 1.9.1 (well so far, I've seen proofs on the Seamonkey side only, thanks to Kairo :)), but I'm puzzled as for how that whole VCS is organized. I have serious doubts regarding the initial choices. But again, who am I to discuss that..

If you care about acid3, CSS3, HTML5, <video> tag and such, XUL 1.9.1 is already active on those fronts so don't worry about XUL2 for now, it will come in time and there's plenty to come already.

---

### Post by ronacc on 2008-06-17
when you removed them I guessed that those were not ment for public eyes yet :) when you are free to put them back I'll be glad to test them .right now my intrepid install is stuck in vesa graphics due to the .26 kernel not liking any nvidia driver I have been able to throw at it :lolflag:

---

### Post by ace214 on 2008-07-27
Thanks for the upload, and I really hope you can get this into the repos. In case you're not aware, there is a new beta version out.

The previous versions from getdeb never worked with the ubuntustudio theme. The text was greyed out. This version works mostly.

I attached a screenshot. What is that bar below the menu bar? It's in the human theme too, it's just the same color as the backgrounds around it. Also the tab text is now the proper color but the menu bar text is not. Ideally all the toolbar backgrounds would be the black color as they are in other mozilla programs that integrate properly with this theme, and the text would be white.

Also, the browser never recognizes that it is the default. I had to turn off the check because it was saying it wasn't the default every time.

Lastly, the icon when the program is open is not the Flock icon. It's some globe with some gold thing at the top left corner. I don't even know what it is.

---

### Post by ubulette on 2008-08-10
> **ace214 said:**
> Thanks for the upload, and I really hope you can get this into the repos. In case you're not aware, there is a new beta version out.

I know but upstream never tagged b2: [http://svn-mirror.flock.com/trac/flock/browser/tags](http://svn-mirror.flock.com/trac/flock/browser/tags)
Instead, I just pushed a b3pre snapshot to my PPA.

> 
Lastly, the icon when the program is open is not the Flock icon. It's some globe with some gold thing at the top left corner. I don't even know what it is.

I'm aware of that. In b1, there was no flock icon for the window (top left), only the default Mozilla blue earth used for Minefield.
It has been fixed since.

---

### Post by ace214 on 2008-08-11
Cool. Thanks for all your hard work!

---

### Post by ace214 on 2008-08-14
Noticed one more issue: upgrading via your repo doesn't add the google live results in the search bar that came out in this release, but a new install from your repo does. Is this a packaging bug or just the way it works?

---

