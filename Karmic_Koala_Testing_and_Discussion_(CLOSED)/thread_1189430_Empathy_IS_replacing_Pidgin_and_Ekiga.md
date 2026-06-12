---
title: "Empathy IS replacing Pidgin and Ekiga"
date: 2009-06-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DPic on 2009-06-16
There's another big thread right now with people arguing about why they prefer Empathy or Pidgin, but at UDS it was already decided that Empathy would ship with Karmic. 

I humbly request that we all stop bickering about any problems we may currently have with it, and start testing it and filing bug reports so that it will ready for Karmic. 14 pages of discussion about the current state of things does nothing. 

The concensus is that Empathy, by using the Telepathy framework and integrating with the GNOME desktop, is superior to Pidgin and should be included with Ubuntu by default eventually. Almost everyone who opposes it does so on the grounds that some bugs make it premature for such a thing to happen in Karmic, but since Karmic already has so many other major changes planned anyways and Karmic +1 will be an LTS, the decision has already been made for us. So let's make the best of it!

---

### Post by zekopeko on 2009-06-16
Question: What is the size difference when Pidgin and Ekiga (+ dep) are removed and empathy (+dep) are added?

---

### Post by TheBuzzSaw on 2009-06-16
I'll still be able to add Pidgin using the repos, yes?

---

### Post by zekopeko on 2009-06-16
> **TheBuzzSaw said:**
> I'll still be able to add Pidgin using the repos, yes?

yes. if you upgrade you will not install empathy. empathy will be the default only for new users.

---

### Post by super.rad on 2009-06-16
> **TheBuzzSaw said:**
> I'll still be able to add Pidgin using the repos, yes?
yes, pidgin won't be installed by default on new systems but you'll still be able to install it

EDIT: Beaten to it

---

### Post by TwiStEr55 on 2009-06-16
does empathy have OTR/encryption support? otherwise i will always stick with pidgin .....

otr integration should be a high priority if it becomes default

---

### Post by zekopeko on 2009-06-16
no OTR. and i doubt most users use it anyway.

---

### Post by TwiStEr55 on 2009-06-16
> **zekopeko said:**
> no OTR. and i doubt most users use it anyway.

their loss :P

i want/need it and therefore wont switch ....as long as it stays in the rpos .. fine with me

---

### Post by DPic on 2009-06-16
> **TwiStEr55 said:**
> does empathy have OTR/encryption support? otherwise i will always stick with pidgin .....

otr integration should be a high priority if it becomes default

It will have it, but either way, this isn't about what we use. Let's not start the same discussion again! You are free to use Pidgin and continue using it. Empathy is much nicer for new users. It's planned to ship with Karmic. We should be testing and working to improve it.

---

### Post by super.rad on 2009-06-16
I'm waiting until 2.27.3 is uploaded to the repo's as 2.27.2 has a bug where it shows my contacts as offline even when they aren't, supposed to be already fixed in 2.27.3 though.

---

### Post by TwiStEr55 on 2009-06-16
> **DPic said:**
> It will have it, but either way, this isn't about what we use. Let's not start the same discussion again! You are free to use Pidgin and continue using it. Empathy is much nicer for new users. It's planned to ship with Karmic. We should be testing and working to improve it.

1. good to know

2. sorry, just wanted to make sure, since I didnt hear much about empathy before ... didnt wanna start a flame war on which is better :)

---

### Post by MacUntu on 2009-06-16
> **DPic said:**
> Empathy [...] is superior to Pidgin

As long as Empathy isn't superior to Pidgin I'd stay away from such statements - unless you WANT another 10-20 pages about ppl proving you wrong. ;)

---

### Post by loell on 2009-06-16
I was one of the opposition back then, but a lot has changed in empathy since then. so aye for it's karmic default.

---

### Post by andrewabc on 2009-06-16
Did empathy replace pidgin/ekiga in alpha 2? Or is this something that will happen in later alpha?

I have alpha 2 downloaded and burned, want to know whether to test to see if it connects to my http msn.

---

### Post by geojorg on 2009-06-16
When will 2.27.3 be in Karmic ? We should have this right away to start testing. Many new features are in 2.27.3, I am very interested in this new release toward 2.28

---

### Post by meho_r on 2009-06-16
I'm not happy about this. And saying that Empathy is superior to Pidgin is ridiculous. I just installed 2.27.2 and guess what! It's totally unusable. However, I'm not gonna bash it, sure, but would like to know why should it replace Pidgin?

---

### Post by RAOF on 2009-06-16
Because many people, particularly the people who did a UI review & MIR, *didn't* find it unusable?  If you can break down the problems you found, they can be filed as bugs (many of them probably already are).  Until then a cry of "it's unusable!" isn't going to be persuasive or helpful.

Also, because:
[list]
[*] It's the official GNOME IM client
[*] It can do voice+video, including SIP, and so can replace Ekiga
[*] The Telepathy framework it uses can be (and is being) used by other applications to provide collaboration features - cf: the Banshee music library sharing to contacts work.
[*] Some cool features like geolocation & supporting Adium themes.
[/list]

---

### Post by DPic on 2009-06-16
> **meho_r said:**
> I'm not happy about this. And saying that Empathy is superior to Pidgin is ridiculous. I just installed 2.27.2 and guess what! It's totally unusable. However, I'm not gonna bash it, sure, but would like to know why should it replace Pidgin?

Take it up on the other thread. 
[http://ubuntuforums.org/showthread.php?t=1154769](http://ubuntuforums.org/showthread.php?t=1154769)

---

### Post by CoreyB. on 2009-06-16
> **RAOF said:**
> Also, because:
[list]
[*] It's the official GNOME IM client
[/list]

I hope no one is thinking about replacing Firefox because Epiphany is the official GNOME web browser...

---

### Post by RAOF on 2009-06-16
> **CoreyB. said:**
> I hope no one is thinking about replacing Firefox because Epiphany is the official GNOME web browser...

No, but it *is* a point in Epiphany's favour.  If Firefox and Epiphany were otherwise feature-equivalent, then we'd be picking Epiphany.

---

### Post by ghindo on 2009-06-16
Why are there two threads for Empathy v. Pidgin?

---

### Post by DPic on 2009-06-17
> **ghindo said:**
> Why are there two threads for Empathy v. Pidgin?

There aren't. There is some thread that is hopefully dead at this point which was a pointless debate of pet IM clients. This thread is here to say, "Everyone stop bickering and start helping!".

---

### Post by michaelzap on 2009-06-17
> **TwiStEr55 said:**
> 1. good to know

Very good to know. Unfortunately I can't test Empathy until it has OTR support, since that's an essential feature to me. Unless perhaps I could install both clients and use them simultaneously (which seems like a recipe for frustration and bug reports due to improper use).

---

### Post by RAOF on 2009-06-17
> **michaelzap said:**
> Very good to know. Unfortunately I can't test Empathy until it has OTR support, since that's an essential feature to me. Unless perhaps I could install both clients and use them simultaneously (which seems like a recipe for frustration and bug reports due to improper use).

You certainly can have both installed simultaneously without problems; any problems that come up in that situation are bugs that should be fixed anyway.

You should also be able to run both simultaneously, for those IM protocols which support multiple login (MSN doesn't, so either Pidgin or Empathy but not both could be connected to your MSN account).  Jabber/gTalk, at least, supports multiple login.

---

### Post by DPic on 2009-06-17
I'm noticing that in the latest daily build of Ubuntu, Pidgin in still included, who makes the actual change and when will that happen?

---

### Post by hexsel on 2009-06-17
This new thread is the one that is ridiculous.  As much as it was predetermined that Empathy was indeed decided to be default for now, if any serious issues are found in it, I would bet the decision would be reversed.

If the intent was just to announce the decision, the whole undertone of this thread (a la "lol suckrz take empathay") is the wrong approach for it.

Recapping:
1) the announcement should have been done on the other thread
2) the tone should have been concilliatory, not flaming (not that the message was wrong, just the envelope in which it was delivered)

---

### Post by ELD on 2009-06-17
I'm glad it is being changed, fedup of the pidgin devs not listening to the users, remember the "you can't change the textarea size" fiasco! What a load of rubbish!

---

### Post by meho_r on 2009-06-17
> **RAOF said:**
> Because many people, particularly the people who did a UI review & MIR, *didn't* find it unusable?  If you can break down the problems you found, they can be filed as bugs (many of them probably already are).  Until then a cry of "it's unusable!" isn't going to be persuasive or helpful.

Also, because:
[list]
[*] It's the official GNOME IM client
[*] It can do voice+video, including SIP, and so can replace Ekiga
[*] The Telepathy framework it uses can be (and is being) used by other applications to provide collaboration features - cf: the Banshee music library sharing to contacts work.
[*] Some cool features like geolocation & supporting Adium themes.
[/list]

I didn't intend to be "persuasive" or "helpful", but only to tell the fact (which was mentioned before me: all contacts are displayed as offline in 2.72.2) and ask why should it replace pidgin which works. So, I requested some info in this regard which you provided, thanks. That's all.

> **DPic said:**
> Take it up on the other thread. 
[http://ubuntuforums.org/showthread.php?t=1154769](http://ubuntuforums.org/showthread.php?t=1154769)

No need for that. Just tell us if 2.72.3 hits some PPA so we can test it.

---

### Post by Joe_Bishop on 2009-06-17
Hahaha! You can't change input height in Empathy too lol

---

### Post by darthmob on 2009-06-17
I do not really care as long as there will be a gnome-do plugin for it!
(a plugin that searches the contact list and starts a new chat when you enter the contact name)

---

### Post by SunnyRabbiera on 2009-06-17
Yes but what about all that is needed to make Empathy work?
To make empathy work with all my IM clients I had to install many dependencies to make it work.
There better be a way to make empathy more ready for those who want ease of use, its bad enough that Ubuntu has already been made complicated to set up a monitor/graphics card setup with the loss of displayconfig-gtk.

---

### Post by ELD on 2009-06-17
> **SunnyRabbiera said:**
> Yes but what about all that is needed to make Empathy work?
To make empathy work with all my IM clients I had to install many dependencies to make it work.
There better be a way to make empathy more ready for those who want ease of use, its bad enough that Ubuntu has already been made complicated to set up a monitor/graphics card setup with the loss of displayconfig-gtk.

If it is included by default dependencies obviously should be taken care of.

I also fail to see how graphics cards are hard to setup...hardware drivers (restricted manager), seems pish easy to me (and i set a lot of ubuntu machines up!).

---

### Post by pferraro on 2009-06-17
> **DPic said:**
> I'm noticing that in the latest daily build of Ubuntu, Pidgin in still included, who makes the actual change and when will that happen?

[http://launchpad.net/distros/ubuntu/karmic/+source/ubuntu-meta/1.146](http://launchpad.net/distros/ubuntu/karmic/+source/ubuntu-meta/1.146)

---

### Post by rajeev1204 on 2009-06-17
> **DPic said:**
> There's another big thread right now with people arguing about why they prefer Empathy or Pidgin, but at UDS it was already decided that Empathy would ship with Karmic. 

I humbly request that we all stop bickering about any problems we may currently have with it, and start testing it and filing bug reports so that it will ready for Karmic. 14 pages of discussion about the current state of things does nothing. 

The concensus is that Empathy, by using the Telepathy framework and integrating with the GNOME desktop, is superior to Pidgin and should be included with Ubuntu by default eventually. Almost everyone who opposes it does so on the grounds that some bugs make it premature for such a thing to happen in Karmic, but since Karmic already has so many other major changes planned anyways and Karmic +1 will be an LTS, the decision has already been made for us. So let's make the best of it!


Where is this link ?

On another note- i just installed empathy ,couldnt see any yahoo users,uninstalled it again.And how to make a call on gtalk? I cant seem to find it yet.Maybe there is another vresion of empathy floating around probably a PPA.Iam using 2.26.1.

I prefer pidgin still.The UI is much nicer looking.And also more easy to understand.At least for me.

When it ships by default in karmic,this thread title will be justified.Till then we shall see.

---

### Post by super.rad on 2009-06-17
Hopefully we get 2.27.3 before tomorrow as it has loads of bug fixes and then I can join in the hug day (2.27.2 has a bug that shows all my contacts as offline)

---

### Post by yelo3 on 2009-06-17
If you are using MSN the contacts offline problem is fixed in telepathy-butterfly 0.3.4 not empathy.

---

### Post by DPic on 2009-06-17
> **rajeev1204 said:**
> Where is this link ?

On another note- i just installed empathy ,couldnt see any yahoo users,uninstalled it again.And how to make a call on gtalk? I cant seem to find it yet.Maybe there is another vresion of empathy floating around probably a PPA.Iam using 2.26.1.

I prefer pidgin still.The UI is much nicer looking.And also more easy to understand.At least for me.

When it ships by default in karmic,this thread title will be justified.Till then we shall see.

Funny how all the people complaining about bugs are using an outdated version of empathy. Please do not complain unless you are using the PPA

Anyways, this thread isn't about which IM client we prefer! This is to END that kind of discussion. As of today, Empathy is default in Karmic and we should be working on testing and bugfixing!

---

### Post by 23meg on 2009-06-17
[QUOTE=DPic]Anyways, this thread isn't about which IM client we prefer! This is to END that kind of discussion. As of today, Empathy is default in Karmic and we should be working on testing and bugfixing![/QUOTE]

I think you've delivered that point well enough, thus this thread has served its purpose.

People who want to test and improve Empathy by filing good bug reports may find [http://live.gnome.org/Empathy/Debugging](http://live.gnome.org/Empathy/Debugging) and [https://wiki.ubuntu.com/DebuggingTelepathy](https://wiki.ubuntu.com/DebuggingTelepathy) useful. Those who want to help triage Empathy bugs may want to join [the Hug Day]("http://ubuntuforums.org/showthread.php?t=1188976") tomorrow (June 18th). 

People who want to keep discussing whether Empathy is ready to replace Pidgin can continue in [the other thread]("http://ubuntuforums.org/showthread.php?p=7469297").

---

