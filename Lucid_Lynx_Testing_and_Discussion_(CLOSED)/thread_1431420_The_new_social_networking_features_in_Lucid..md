---
title: "The new social networking features in Lucid."
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by beatme101 on 2010-03-16
[QUOTE="http://www.h-online.com/open/news/item/Canonical-releases-Ubuntu-10-04-LTS-Alpha-3-941337.html"]built-in social networking integration now includes support for Twitter, identi.ca and Facebook.[/QUOTE]

Is this really as bad as I'm hearing? Where will this new bloat feature be, and how easy is it to disable?

I thought the copying of mac style window buttons was bad enough. Heck, I thought switching from the well-supported alsa to pulseaudio was bad enough. This is quickly becoming a distro I don't want to recommend to people. I don't want people to think I'm someone who would ever use those social networking sites.

---

### Post by Psumi on 2010-03-16
too bad identi.ca requires your posts/work to be GPL/CC. Which some of my work cannot be.

---

### Post by graabein on 2010-03-16
They'd better make it easy to uninstall all that social stuff without screwing up Ubuntu desktop package n'stuff. 

It's okay for the average user I suppose but opting out should be ***very*** easy (compared to those sites).

---

### Post by doas777 on 2010-03-16
horray! now they can sell our details like myspace!
[http://yro.slashdot.org/story/10/03/16/1317228/MySpace-To-Sell-User-Data](http://yro.slashdot.org/story/10/03/16/1317228/MySpace-To-Sell-User-Data)

---

### Post by Psumi on 2010-03-16
> **graabein said:**
> They'd better make it easy to uninstall all that social stuff without screwing up Ubuntu desktop package n'stuff. 

It's okay for the average user I suppose but opting out should be ***very*** easy (compared to those sites).

Follow this post: [http://ubuntuforums.org/showpost.php?p=8754516&postcount=3](http://ubuntuforums.org/showpost.php?p=8754516&postcount=3)

---

### Post by FuturePilot on 2010-03-16
> **beatme101 said:**
> Is this really as bad as I'm hearing? Where will this new bloat feature be, and how easy is it to disable?

I thought the copying of mac style window buttons was bad enough. Heck, I thought switching from the well-supported alsa to pulseaudio was bad enough. This is quickly becoming a distro I don't want to recommend to people. I don't want people to think I'm someone who would ever use those social networking sites.

Right click on the panel applet > Remove. Done.

I don't get why people are freaking out over this.

---

### Post by Psumi on 2010-03-16
> **FuturePilot said:**
> Right click on the panel applet > Remove. Done.

I don't get why people are freaking out over this.

What if it's also a daemon?

---

### Post by FuturePilot on 2010-03-16
> **Psumi said:**
> What if it's also a daemon?

It's not.

---

### Post by zekopeko on 2010-03-16
> **Psumi said:**
> too bad identi.ca requires your posts/work to be GPL/CC. Which some of my work cannot be.

You got it wrong. Identi.ca runs on StatusNet which is A-GPL. Content and data that belong to Identi.ca are under CC-BY-3.0 .
You still own copyright on everything you wrote.

EDIT: It appears I was half-right. By posting on Identi.ca you are giving every reader your content under CC-BY-3.0 .

---

### Post by Psumi on 2010-03-16
> **zekopeko said:**
> You got it wrong. Identi.ca runs on StatusNet which is A-GPL. Content and data that belong to Identi.ca are under CC-BY-3.0 .
You still own copyright on everything you wrote.

There's this checkbox that won't allow me to register unless checked:

> My text and files are available under Creative Commons Attribution 3.0  except this private data: password, email address, IM address, and phone number.

I cannot check this box if some of my works/text are not available under Creative Commons. Leaving this unchecked disallows me an account.

---

### Post by beatme101 on 2010-03-16
> **FuturePilot said:**
> Right click on the panel applet > Remove. Done.

I don't get why people are freaking out over this.

> **FuturePilot said:**
> It's not.

Well then this is good to hear, it's hard to find information about it without installing it myself.

---

### Post by swoll1980 on 2010-03-16
It's a panel applet. If you think Ubuntu is bloated why not try something else. Ubuntu exist because of it's user friendliness. This is just another feature that helps achieve that goal.

---

### Post by zekopeko on 2010-03-16
> **Psumi said:**
> There's this checkbox that won't allow me to register unless checked:

> My text and files are available under Creative Commons Attribution 3.0 except this private data: password, email address, IM address, and phone number.


I cannot check this box if some of my works/text are not available under Creative Commons. Leaving this unchecked disallows me an account.

From the wording I would say it only applies to things you own. If you post stuff that is from your employer I don't think it would apply since you never owned the content. But IANAL.

---

### Post by coolbrook on 2010-03-16
> **swoll1980 said:**
> If you think Ubuntu is bloated why not try......a [minimal](https://help.ubuntu.com/community/Installation/MinimalCD) install sans 'Ubuntu Desktop' (package.)

---

### Post by supershin on 2010-04-24
They should put a note stating the feature can be easily uninstalled, if it can. It does raise some privacy concerns with many users.

---

### Post by Universal344 on 2010-04-24
Actually there is a daemon.  Gwibber-daemon provides the services for all the "broadcast" sites (aka, Facebook, Myspace, Twitter, etc.) and Epiphany (which I don't think is a daemon) provides services for any chat accounts.  So to remove social networking, you would uninstall gwibber and epiphany and then just delete the panel applet (which would be useless anyways after uninstalling gwibber).  Of course if you dont associate any accounts with these applications they will have no power and simply removing the applet would suffice.

---

### Post by tokyobadger on 2010-04-24
I think you mean Empathy, not Epiphany

---

### Post by ToxicBurn on 2010-04-24
thats the great thing about Linux distros if Ubuntu does not work for you then i am sure you will find a distro that you will like over at [www.distrowatch.com](www.distrowatch.com)

have a nice day .

---

### Post by x-shaney-x on 2010-04-24
I like the idea of all this social networking stuff.  Or should I say **LIKED**.
With just a few days left til release, the social networking just doesn't work properly.

With facebook at least, gwibber doesn't work properly at all, replies to posts not updated in the window yet it shows replies from 5 and 7 days ago and nothing in between.
The only time I have EVER seen a notification from gwibber in the much fabled new notification area it was informing me that I had clicked on "like" on a status.
The envelope still didn't change colour, I just got a bubble.

What is the point of notifying me that I have just clicked on something?
I KNOW I have just clicked on something, it should be notifying me when somebody replies to one of my statuses or adds a reply to some other wall post I have posted on or what's the point?

I'm afraid "social from the start" is more like "social not quite ready yet".
Along with the whole new notification menus all this stuff is just not finished and not ready and should have maybe been held off from a final release.

---

