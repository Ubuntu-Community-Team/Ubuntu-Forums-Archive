---
title: "Chromium rendering problems - Screenshot"
date: 2009-12-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-12-07
Has anyone been having these problems ? been this way on my machine for the last 4 updated versions or so. I have disabled desktop effects, but it does not seem to be related to the problem.

---

### Post by rtalcott on 2009-12-07
I have the same problem...same timeframe too.
rt

---

### Post by alexmurray on 2009-12-07
Same here on karmic - this is on an Nvidia GPU w/ binary restricted driver BTW too.

---

### Post by VMC on 2009-12-07
I have the same issues, and because of it I have started using Seamonkey. Sad because I was very impressed with Chromium until this started happening.

---

### Post by sliketymo on 2009-12-07
I had the same thing start up after todays most recent update.oh well,back to the fox.:lolflag:

---

### Post by cariboo on 2009-12-07
I just installed chromium and I get the same thing. I also have a whole lot of xorg files in the queue waiting for dependencies to catch up.

---

### Post by kylehase on 2009-12-07
Same here on Xubuntu 9.10.

Scrolling or resizing the window seems to fix it for the current page.

Has anyone submitted this to the chromium team?

---

### Post by darco on 2009-12-07
nm


d

---

### Post by Regenweald on 2009-12-07
> **alexmurray said:**
> Same here on karmic - this is on an Nvidia GPU w/ binary restricted driver BTW too.

Lucid here. on board graphics. I noticed some libwebkit 1.0 updates in recent days, may be something there. But I really have no idea where to start ;). Such is testing :) Checking for updates now.

---

### Post by zekopeko on 2009-12-08
> **Regenweald said:**
> Lucid here. on board graphics. I noticed some libwebkit 1.0 updates in recent days, may be something there. But I really have no idea where to start ;). Such is testing :) Checking for updates now.

If you are using Chromium from the PPA then you should know that they package their own webkit AFAIK. So the problem is purely on the Chromium side.

---

### Post by jbernardo on 2009-12-08
> **zekopeko said:**
> If you are using Chromium from the PPA then you should know that they package their own webkit AFAIK. So the problem is purely on the Chromium side.
It's on Chromium side, as it also shows after today's update on karmic.

---

### Post by Revik on 2009-12-08
Facing same issue. Intel graphics, today update on karmic

---

### Post by Yes_It's_Me on 2009-12-08
The latest update (came out an hour or two ago) fixes it.

---

### Post by TobiasTheViking on 2009-12-08
> **Yes_It's_Me said:**
> The latest update (came out an hour or two ago) fixes it.

Hm, i just ran an update, upgrade, and it didn't find a new version.  Where did you get the update from?

ETA: I don't think it is building correctly for karmic i386.

[https://launchpad.net/~chromium-daily/+archive/ppa/+build/1384961]("https://launchpad.net/%7Echromium-daily/+archive/ppa/+build/1384961")

[https://launchpad.net/~chromium-daily/+archive/ppa/+packages](https://launchpad.net/~chromium-daily/+archive/ppa/+packages) <- this link says all i386 builds are still building.

Guess i'll just have to wait. I can do that.

---

### Post by speakman on 2009-12-08
Same here, running from the PPA. Really hope this will be fixed with next build. It's quite unusable right now. :(

---

### Post by speakman on 2009-12-08
New build done!! And using it for over 30 secs, it seems to fix the rendering issues. Yes!

---

### Post by nxt on 2009-12-08
> **Yes_It's_Me said:**
> The latest update (came out an hour or two ago) fixes it.

i can confirm this. I just upgraded and the problem's gone. That was fast....

---

### Post by TobiasTheViking on 2009-12-08
And now it works in i386 as well, woohoo :)

---

### Post by andresv on 2009-12-08
same problem with rendering - using the latest update I see on the channels (Dec 8, 6.32 am, EST)

---

### Post by speakman on 2009-12-08
> **andresv said:**
> same problem with rendering - using the latest update I see on the channels (Dec 8, 6.32 am, EST)

Are you really using r34029? Could you double check that?

---

### Post by Neon Lights on 2009-12-08
All clear here after updating as well.
In other news, an official Google Chrome beta has been released for linux.. :D All clear there too. haha.
[http://www.google.com/chrome](http://www.google.com/chrome)

---

### Post by JohnJackson on 2009-12-08
It is a daily build you know, you should expect problems such as these :P.

---

### Post by nanog on 2009-12-08
> It is a daily build you know, you should expect problems such as these.

Yep. The TB 3 daily build recently filled up my / quota (700 gb). LOL!

---

### Post by JohnJackson on 2009-12-08
> **nanog said:**
> Yep. The TB 3 daily build recently filled up my / quota (700 gb). LOL!

Nice. I have been wanting to try out the new TB but have been put off by potential issues just like that. Hopefully we'll see TB in the Ubuntu repositories soon though and I just might use it.

---

### Post by kylehase on 2009-12-08
This is the first time I've seen a problem like this.  Is this common for Chromium?

I've since switched to Google Chrome beta which was just released today but I'm wondering what the Ubuntu community thinks of Chrome.

---

### Post by Regenweald on 2009-12-08
> **kylehase said:**
> This is the first time I've seen a problem like this.  Is this common for Chromium?
Not really, but remember chromium-daily is basically a rolling release.
> 
I've since switched to Google Chrome beta which was just released today but I'm wondering what the Ubuntu community thinks of Chrome.
I can't speak for the community, but Chromium is the default browser on my machine. It wins for me on UI design and speed, as for extensions, I only need adblock and flashblock. For many, lacking in key extensions seems to be the deal breaker.

---

### Post by Felliph3 on 2009-12-08
Had the same problem and did a sudo apt-get update and its fixed.

---

### Post by cariboo on 2009-12-09
> **Regenweald said:**
> Not really, but remember chromium-daily is basically a rolling release.

I can't speak for the community, but Chromium is the default browser on my machine. It wins for me on UI design and speed, as for extensions, I only need adblock and flashblock. For many, lacking in key extensions seems to be the deal breaker.

The Chrome extensions are available [here]("https://chrome.google.com/extensions/?utm_campaign=en&utm_source=en-ha-na-us-bk-ext&utm_medium=ha"). I just installed adblock, and saw flashblock in the list of extensions

---

### Post by Regenweald on 2009-12-09
> **cariboo907 said:**
> The Chrome extensions are available [here]("https://chrome.google.com/extensions/?utm_campaign=en&utm_source=en-ha-na-us-bk-ext&utm_medium=ha"). I just installed adblock, and saw flashblock in the list of extensions

Yes, I already use them in chromium and just upgraded Chrome in win7 so that i could use them also :) The [Cooliris](https://chrome.google.com/extensions/search?q=cooliris) extension is fantasmical :D although I really don't do much flash video viewing....

---

### Post by Felliph3 on 2009-12-09
cooliris has no linux support what do you mean?

---

### Post by Regenweald on 2009-12-09
> **Felliph3 said:**
> cooliris has no linux support what do you mean?

I mean I'm using it in win7. Hope to see it in linux, but our 3D support is a many tangled web ;)

---

### Post by Felliph3 on 2009-12-09
For some reason it started working on mine lol!

---

### Post by Enk on 2009-12-09
I can confirm that updating fix the problem :)

---

