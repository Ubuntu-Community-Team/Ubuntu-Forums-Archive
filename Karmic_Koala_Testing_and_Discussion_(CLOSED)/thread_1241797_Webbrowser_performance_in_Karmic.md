---
title: "Webbrowser performance in Karmic"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TrueTom on 2009-08-16
Using [http://service.futuremark.com/peacekeeper]("http://service.futuremark.com/peacekeeper"):

[IMG]http://dl.getdropbox.com/u/963697/screenshot_001.png[/IMG]

---

### Post by taavikko on 2009-08-16
```
Your fastest score for Arora 0.8.0
3350 Points

Rendering 1428
Social networking 2283
Complex graphics 2365
Data 5493
DOM operations 4550
Text parsing 5182
```

---

### Post by rudenko_ruslan on 2009-08-16
> Firefox (v3.5.2) Scored: 1614 Points
> Chrome (v3.0.195.0) Scored: 7566 Points
:(

---

### Post by Merk42 on 2009-08-16
> **taavikko said:**
> ```
Your fastest score for Arora 0.8.0
3350 Points

Rendering 1428
Social networking 2283
Complex graphics 2365
Data 5493
DOM operations 4550
Text parsing 5182
```

You do know that peacekeeper is per computer right? So while Arora 0.8.0 may have scored 3350 on your computer that doesn't mean it's faster than Chrome.

Also, yes Chrome (and Safari, not shown) is faster than Firefox, Windows Firefox is faster than Linux Firefox.  All very unfortunate but not news to me.

---

### Post by anders_c_ on 2009-08-16
Chrome 4.0.202.0: 1930
Firefox 3.5.2: 872
not good...

---

### Post by scaine on 2009-08-16
> **anders_c_ said:**
> Chrome 4.0.202.0: 1930
Firefox 3.5.2: 872
not good...

But not really relevant either.  Unless you're running incredibly complex javascript applications, you won't notice any difference.  I don't even see any difference on Gmail or Reader between Firefox on Linux and Chrome on Windows.

It's just not noticeable.  Yet.

These tests will be useful in driving Firefox towards better performance though.  But frankly, unless there's a killer app that comes along that runs noticeably smoother on Chrome, there's no way I'm giving up on Firefox with my 5 must-have extensions.

---

### Post by Merk42 on 2009-08-16
> **scaine said:**
> But not really relevant either.  Unless you're running incredibly complex javascript applications, you won't notice any difference.  I don't even see any difference on Gmail or Reader between Firefox on Linux and Chrome on Windows.

It's just not noticeable.  Yet.

These tests will be useful in driving Firefox towards better performance though.  But frankly, unless there's a killer app that comes along that runs noticeably smoother on Chrome, there's no way I'm giving up on Firefox with my 5 must-have extensions.


Okay then how about that Firefox 3.5.2 in Jaunty only runs marginally faster than Firefox 3.5.2 in Windows XP **when Windows XP is being virtualized in Jaunty**

---

### Post by jppr on 2009-08-16
chromium 4.0.202 2063 p, ff 3.7a1pre 1136 p and ff 3.5.3pre 1032 p

---

### Post by cdEWoozy on 2009-08-16
> **scaine said:**
> But not really relevant either.  Unless you're running incredibly complex javascript applications, you won't notice any difference.  I don't even see any difference on Gmail or Reader between Firefox on Linux and Chrome on Windows.

It's just not noticeable.  Yet.

For me, it definitely is noticeable. If I use Google Reader with Firefox and scroll down the list of articles, it feels sluggish and is visibly slow.
I have tried Chrome for half a week now and noticed that everything suddenly feels smooth and responsive (including scrolling in Google Reader). Chrome may well become my default browser because of that.

---

### Post by oztrailrider on 2009-08-16
> **cdEWoozy said:**
> For me, it definitely is noticeable. If I use Google Reader with Firefox and scroll down the list of articles, it feels sluggish and is visibly slow.
I have tried Chrome for half a week now and noticed that everything suddenly feels smooth and responsive (including scrolling in Google Reader). Chrome may well become my default browser because of that.

This is something I have noticed as well, using Firefox to view Google Reader is a horrible experience. I feel like I am browsing on a 486. I think I am going to try out Chrome.

---

### Post by Mr. Picklesworth on 2009-08-16
> **anders_c_ said:**
> Chrome 4.0.202.0: 1930
Firefox 3.5.2: 872
not good...

How is this not good? There is a fast, free web browser available now called Chromium that is an awesome leap ahead from the already quite capable Firefox browser. Beyond speed, the Linux port of Chromium is doing great things for integration which will make the experience for new users much better! (In all ways except HIG compliance and having a normal looking UI, but even that is more consistent when you look at menus and dialogs).

It's progress.

---

### Post by cdEWoozy on 2009-08-16
I just ran the benchmark on Chrome and Firefox:

```
Your fastest score for Chrome 4.0.202.0
3188 Points

Rendering 3494
Social networking 2604
Complex graphics 4714
Data 2635
DOM operations 3365
Text parsing 4085


Your fastest score for Firefox 3.5.2
1393 Points

Rendering 1863
Social networking 1656
Complex graphics 2484
Data 1734
DOM operations 1411
Text parsing 695
```

@oztrailrider: I'm using [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by tghe-retford on 2009-08-16
My results using a wide range of browsers on Kubuntu Karmic with a Intel Core 2 Quad Q6600 @ 2.4GHz:
```

Chrome 4.0.202.0   &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608; 3562
Arora 0.8.0        &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;    2741
Minefield 3.7a1pre &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;        1771
Opera 10           &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;         1574
Konqueror 4.3      &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;         1535
Namoroka 3.6a2pre  &#9608;&#9608;&#9608;&#9608;&#9608;          1459
Firefox 3.5.2      &#9608;&#9608;&#9608;&#9608;           1238
```
Arora 0.8.0 looks very promising from a Kubuntu perspective, but really showed itself up against the other browsers in the complex graphic benchmarks. Chrome on Kubuntu is let down, away from the main browser window, by the fact that the GTK+ menus and windows don't follow the QtCurve theming applied to other Gnome applications.

---

### Post by klim8 on 2009-08-16
It looks like epiphany-webkit is even better :): 

Your fastest score for Chrome 4.0.202.0
3653 Points

SuiteResult
Rendering 3632
Social networking 3335
Complex graphics 6267
Data 2837
DOM operations 4108
Text parsing 4612

Your fastest score for Epiphany Webkit
3671 Points
SuiteResult
Rendering 1926
Social networking 2347
Complex graphics 4384
Data 5834
DOM operations 5284
Text parsing 4790

---

### Post by froggyswamp on 2009-08-16
Folks, Firefox is slower, but also keep in mind that the 64 bit version is even slower by about 30% than the 32 bit version (according to sunspider at least)

---

### Post by Merk42 on 2009-08-16
> **froggyswamp said:**
> Folks, Firefox is slower, but also keep in mind that the 64 bit version is even slower by about 30% than the 32 bit version (according to sunspider at least)

Add-ons tend to slow it down as well.

---

### Post by Seventh Reign on 2009-08-17
Speed is nice, but its not everything.  Only Firefox renders the code on my personal forum correctly.

All the other browsers are completely useless there.

---

### Post by scaine on 2009-08-17
> **cdEWoozy said:**
> For me, it definitely is noticeable. If I use Google Reader with Firefox and scroll down the list of articles, it feels sluggish and is visibly slow.
I have tried Chrome for half a week now and noticed that everything suddenly feels smooth and responsive (including scrolling in Google Reader). Chrome may well become my default browser because of that.

Yikes.  I use Reader VERY heavily and as I said in my earlier post, I see no difference.  At all.  Lists with 300+ items will scroll with only tiny pauses to read in the extra items, both browsers.  Either I have a very nippy Firefox/Ubuntu build, a very slow Firefox/Vista build, or you have an issue.

I'd like to hear if anyone has come across any apps which would really benefit from a faster javascript engine.  I suppose it would be good have youtube consume slightly less CPU (about 25% here, on a 2.7Ghz dual core), but really that's the only time I see web browsing hit my CPU.

---

### Post by inportb on 2009-08-17
> **Seventh Reign said:**
> Speed is nice, but its not everything.  Only Firefox renders the code on my personal forum correctly.

All the other browsers are completely useless there.

It might be time for a bugfix, on your part... or people who don't use Firefox would not stay to look at your pages. A real web developer knows not to discriminate (too much) ;p

---

### Post by NCLI on 2009-08-17
:guitar:

                                                                                                                                                                                                             **Firefox**(v3.5.2) Scored:
                                    [B]1973 Points
[/B]               Rendering
                  1495
              
               Social networking
                  2217
              
               Complex graphics
                  6129
              
               Data
                  2872
              
               DOM operations
                  1623
              
               Text parsing
                  1940
              
  

[B] 
Chrome[/B](v4.0.202.0) Scored:
[B]5472 Points
[/B]
Rendering
5011

Social networking
4959

Complex graphics
9306

Data
4268

DOM operations
6188

Text parsing
7482

---

### Post by fifth on 2009-08-17
I've never considered moving from Firefox, but reading this thread made me curious about Chrome. I'm now running the Linux developer release (3.0.198.1) and ... wow ...

I can't believe how much faster Chrome is over Firefox. Click a link, a quick screen flash and the new page is on screen. In firefox I'd see the statusbar progress for roughly 1 or 2 seconds before the new page loads.

Page scrolling is also very smooth and quick. I've noticed Firefox getting slower and jerky recently when scrolling large pages.

And the built-in Developer Tools are very neat - not checked them out thoroughly but looks like a decent alternative to Firebug.

Only problems I've noticed so far are the GTK menu's look ugly in Kubuntu and don't fit with the rest of the browser ui, but then this is only a dev (pre)release. Also still to check what plugins are available (if any).

Feeling really guilty after years of Firefox ...

---

### Post by phenest on 2009-08-17
> **klim8 said:**
> It looks like epiphany-webkit is even better :): 

Your fastest score for Chrome 4.0.202.0
3653 Points

SuiteResult
Rendering 3632
Social networking 3335
Complex graphics 6267
Data 2837
DOM operations 4108
Text parsing 4612

Your fastest score for Epiphany Webkit
3671 Points
SuiteResult
Rendering 1926
Social networking 2347
Complex graphics 4384
Data 5834
DOM operations 5284
Text parsing 4790

[epiphany ppa]("https://launchpad.net/~webkit-team/+archive/epiphany")
[webkit ppa]("https://launchpad.net/~webkit-team/+archive/ppa")
...in case anyone is interested.

---

### Post by phenest on 2009-08-17
Epiphany-gecko 2.22: 942
Firefox 3.0.13: 953
Epiphany webkit 2.27.90 ppa: 2623

---

### Post by xens on 2009-08-17
Will one day mozilla use webkit for firefox instead of geko ?

---

### Post by phenest on 2009-08-17
> **xens said:**
> Will one day mozilla use webkit for firefox instead of geko ?

Why wait? Epiphany-webkit is here. I'd like to see Epiphany webkit as default browser instead of Firefox someday. I've used Firefox for probably over 5 years (maybe more), Windows first, now Ubuntu, but now I'm losing interest. But I'd prefer a browser a bit more 'neutral'. I'm not a fan of Google either.

---

### Post by Merk42 on 2009-08-17
> **phenest said:**
> Why wait? Epiphany-webkit is here. I'd like to see Epiphany webkit as default browser instead of Firefox someday. I've used Firefox for probably over 5 years (maybe more), Windows first, now Ubuntu, but now I'm losing interest. But I'd prefer a browser a bit more 'neutral'. I'm not a fan of Google either.

I'm going to guess because of the advantage Firefox has (right now) over Epiphany and Chrome/Chromium, extensions.

---

### Post by phenest on 2009-08-17
My results for Jaunty:
> **phenest said:**
> Epiphany-gecko 2.22: 942
Firefox 3.0.13: 953
Epiphany webkit 2.27.90 ppa: 2623

My results for Karmic (64 bit VM):
Firefox 3.5.2: 996
Epiphany webkit 2.27.90 ppa: 2201

---

### Post by xens on 2009-08-17
> **phenest said:**
> Why wait? Epiphany-webkit is here. I'd like to see Epiphany webkit as default browser instead of Firefox someday. I've used Firefox for probably over 5 years (maybe more), Windows first, now Ubuntu, but now I'm losing interest. But I'd prefer a browser a bit more 'neutral'. I'm not a fan of Google either.

I'll try it :)

---

### Post by CoreyB. on 2009-08-17
> **froggyswamp said:**
> Folks, Firefox is slower, but also keep in mind that the 64 bit version is even slower by about 30% than the 32 bit version (according to sunspider at least)

According to Google's V8 Benchmark, Firefox has a 13% performance boost under 64-bit.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by hetx on 2009-08-17
Anyone mind trying Midori for me? (don't have a Karmic installation)

Want to see how it ranks vs the other webkit based browsers.

---

### Post by ceramicm on 2009-08-17
I read about epiphany-webkit here and decided to try it, but I can't figure out how to use extensions. I don't have a tools menu. Any ideas?

(using karmic, installed epiphany-webkit and epiphany-webkit-extensions from the ppa)

---

### Post by Merk42 on 2009-08-17
> **ceramicm said:**
> I read about epiphany-webkit here and decided to try it, but I can't figure out how to use extensions. I don't have a tools menu. Any ideas?

(using karmic, installed epiphany-webkit and epiphany-webkit-extensions from the ppa)

As I said before:

> **Merk42 said:**
> I'm going to guess because of the advantage Firefox has (right now) over Epiphany and Chrome/Chromium, extensions.

So the reason you can't figure out how to do it, is because you can't do it.

---

### Post by ceramicm on 2009-08-17
> **Merk42 said:**
> So the reason you can't figure out how to do it, is because you can't do it.

Oh, OK. Thanks for the reply! Seems strange though that there is an epiphany-webkit-extensions ppa package if there aren't any working epiphany-webkit extensions. :confused:

---

### Post by Merk42 on 2009-08-17
> **ceramicm said:**
> Oh, OK. Thanks for the reply! Seems strange though that there is an epiphany-webkit-extensions ppa package if there aren't any working epiphany-webkit extensions. :confused:

Oh didn't realize there were extensions specific to epiphany, I don't know then.

---

### Post by phenest on 2009-08-18
My results for Jaunty 64 bit:
Epiphany-gecko 2.22: 942
Firefox 3.0.13: 953
Epiphany webkit 2.27.90 ppa: 2623

My results for Karmic (64 bit virtual machine):
Firefox 3.5.2: 996
Epiphany webkit 2.27.90 ppa: 2201

My results for Karmic (64 bit regular install):
Firefox 3.5.2: 1369
Epiphany webkit 2.27.90 ppa: 3302

---

