---
title: "New default theme for Lucid :)"
date: 2010-02-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lais on 2010-02-20
I read that the Human theme will no longer be the default theme in Ubuntu 10.04. While I consider that as a good news, I have also been hearing that Elementary theme will most probably be the default.

[http://digitizor.com/2010/02/20/ubuntu-getting-a-new-default-theme-for-lucid-finall]("http://digitizor.com/2010/02/20/ubuntu-getting-a-new-default-theme-for-lucid-finally/")y/

Honestly, I don't like the Elementary Theme very much either.
Any thoughts?

Here is the interview where Mark Shuttleworth revealed the dropping of Human. [http://www.youtube.com/watch?v=7yNW4fnGPDk]("http://www.youtube.com/watch?v=7yNW4fnGPDk")

---

### Post by Simon17 on 2010-02-20
NO!

They can pry the [feces-colored] brown from my cold, dead hands!

---

### Post by HarshReality on 2010-02-20
Could be a bit more complete there..

[https://wiki.ubuntu.com/Artwork/Incoming/Lucid/UbuntuSun](https://wiki.ubuntu.com/Artwork/Incoming/Lucid/UbuntuSun)

---

### Post by lais on 2010-02-20
Is it going to be Ubuntu Sun? It isn't exactly a "light theme".

---

### Post by Islington on 2010-02-20
> **HarshReality said:**
> Could be a bit more complete there..

[https://wiki.ubuntu.com/Artwork/Incoming/Lucid/UbuntuSun](https://wiki.ubuntu.com/Artwork/Incoming/Lucid/UbuntuSun)

Facepalm, the wiki is just a place to contribute artwork. The official decision lies completely with canonical's design team.

---

### Post by Ric_NYC on 2010-02-20
Freud can explain that fixation on brown and orange.

---

### Post by Kenny_Strawn on 2010-02-20
Ubuntu Sun is much more compatible with RGBA than the Elementary theme is, so it is more likely to be included in Lucid by default.

However, that aside, when "sudo apt-get upgrade"-ing my packages, here's what I found in the Daily Live build:

[ATTACH]147676[/ATTACH]

As you see, the icons have changed, and look like they will be more intertwined with RGBA.

As far as the freezes, the "FeatureFreeze" has already passed, according to the [Lucid Release Schedule]('https://wiki.ubuntu.com/LucidReleaseSchedule') and the "UserInterfaceFreeze" is coming on the 4th, before any Beta comes out.

Conclusion: Rewrite of the Human theme, as I saw. Take a look at these GTKRC in Gedit screenshots:

[ATTACH]147678[/ATTACH]

[ATTACH]147679[/ATTACH]

[ATTACH]147680[/ATTACH]

[ATTACH]147681[/ATTACH]

They indicate that Murrine has completely replaced the traditional GNOME theme engine for the Human theme. Evidence that our "theme" we are talking about here is really a theme rewrite.

---

### Post by Woolio1 on 2010-02-20
So... We'll still have the optional Human theme, correct? Because I use it as a base for most of my themes...

---

### Post by ETbluez on 2010-02-20
Here's the chosen theme.
[Screenshot.png]("http://ubuntuforums.org/attachment.php?attachmentid=147687&stc=1&d=1266698524")

---

### Post by ETbluez on 2010-02-20
> **ETbluez said:**
> Here's the chosen theme.
[Screenshot.png]("http://ubuntuforums.org/attachment.php?attachmentid=147687&stc=1&d=1266698524")

Well it's the one i chose.

---

### Post by Islington on 2010-02-20
> **Kenny_Strawn said:**
> 
They indicate that Murrine has completely replaced the traditional GNOME theme engine for the Human theme. Evidence that our "theme" we are talking about here is really a theme rewrite.

Human used to use the ubuntulooks engine not the traditional Gnome engine, the progression to murrine is nothing new.

---

### Post by dragos240 on 2010-02-20
What would be cool is if the dawn day and dusk themes alternated depending on the time of day.

---

### Post by ETbluez on 2010-02-20
Doesn't matter. which theme is default some one won't like it and we'll tweak are own theme any ways. I never kept the ubuntu default theme.

---

### Post by Sashin on 2010-02-20
I think impression would be the best possible candidate if they made a few changes... however it doesn't match his description of "light orientated".

---

### Post by zekopeko on 2010-02-20
Shuttleworth didn't say that the theme will come in 10.04. So to all of you, stop acting like you have some inside info. 
You don't. You are all trafficing in rumours. Speculating is fine but don't go around spreading rumours.

---

### Post by Sashin on 2010-02-20
He said new stylings, that's close enough to new theme. And he said human orientated to light orientated. And human is a theme.

---

### Post by zekopeko on 2010-02-20
> **Sashin said:**
> He said new stylings, that's close enough to new theme. And he said human orientated to light orientated. And human is a theme.

He said new styling and that it will be a STARTING point for later releases. Not that there is a new theme. He said, and I'm paraphrasing, "we were human and now we are going light".

Styling can easily include the new monochrome icons and similar tweaks.

---

### Post by MasterNetra on 2010-02-20
> **zekopeko said:**
> He said new styling and that it will be a STARTING point for later releases. Not that there is a new theme. He said, and I'm paraphrasing, "we were human and no we are going light".

Styling can easily include the new monochrome icons and similar tweaks.

Correction: "we were human and **now** we are going light"

---

### Post by Frem on 2010-02-21
He also said that Human has been used for the past five years, and that this new theme will be used for the next five years. It sounded like a clear break from the Human theme in the interview.

> **Kenny_Strawn said:**
> They indicate that Murrine has completely replaced the traditional GNOME theme engine for the Human theme. Evidence that our "theme" we are talking about here is really a theme rewrite.
If you'll look at /usr/share/themes/Human/gtk-2.0/gtkrc in Karmic, you'll see that Human being based on Murrine isn't new to Lucid.

---

### Post by V for Vincent on 2010-02-21
Zekopeko is right. Shuttleworth has not explicitly stated that *Lucid* will have a new theme. Just that they're going to move towards one.

---

### Post by k3lt01 on 2010-02-21
> **Kenny_Strawn said:**
> As you see, the icons have changed, and look like they will be more intertwined with RGBA.

They indicate that Murrine has completely replaced the traditional GNOME theme engine for the Human theme. Evidence that our "theme" we are talking about here is really a theme rewrite.Um, my Karmic install looked like that from the beginning, there is nothing new there at all. Methinks some are getting excited about nothing much.

---

### Post by Viva on 2010-02-21
Good theming is all about proper use of gradients. At least that is what many on this forum seem to think.

---

### Post by murderslastcrow on 2010-02-21
I think even if they just kept Human (they likely will) and made Dust the default, people would shout for joy. Orange (Brown especially) isn't exactly a middle-of-the-road, most people like me color. Sure, it's earthy and very expressive, and fits the idea of Ubuntu well, but people don't love it. Hopefully they can keep the image of human-ness alive, despite these changes. I'd hate to see Ubuntu getting all CLEAN all of a sudden. Polished, sure. Sterile? No.

---

### Post by ctrlmd on 2010-02-21
if there is going to be new theme i think it will be new and different from anything available at the moment

anyway good luck with the new theme

---

### Post by ad_267 on 2010-02-21
I highly doubt it will be Elementary, or any of the incoming proposed themes.

And I hope they stick with the brown and they use the Homosapien metacity, or at least use the Homosapien metacity with whatever colours they go with :)

---

### Post by cariboo on 2010-02-21
There is no need to speculate now, on if Lucid will have a new theme. Wait for an official announcement to avoid disappointment, instead of reading rumors.

This thread is closed.

---

