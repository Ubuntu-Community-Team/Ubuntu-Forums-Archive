---
title: "[SOLVED] spamassassin required?"
date: 2008-05-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by scradock on 2008-05-21
I don't have/use a mail server, only use web-mail. Somehow, my Intrepid install had spamassassin and spamc installed, after starting from a clone of a Hardy install that didn't have them.

I have removed them using Synaptic. I noticed that both were marked "Automatically installed", so I removed the mark.

Even so, Update Manager insists that they need to be installed every day. They don't get dropped from the list if I uncheck the entries. UM still insists that I have two updates available, and presents the list with them checked for install next time I run it.

Is this now required? Is Ubuntu telling me I HAVE to run spamassassin? As far as I know, it's only useful if your machine actively sends/receives/distributes email, which mine doesn't.

Has anyone else seen this behavior? Can anyone suggest how to get rid of a (minor) annoyance?

---

### Post by scradock on 2008-05-25
OK, it sorted itself out after unchecking "Automatically installed" in Synaptic, then removing spamassassin and spamc, then refusing to allow Update Manager to reinstall them, then updating software sources, then checking Updat Manager again - finally the two packages were not offered again. Oh, and at least a couple of system re-boots in between.....

I'll mark the thread solved...

---

### Post by scradock on 2008-05-28
Nope - happened again!

What is going on? If I don't have spamassassin installed, it should NOT be installed behind my back! What's going to be next? The Ubuntu Malicious Software Removal Tool, TM BillG?

Seriously, if Ubuntu is going to decide what protection I need, I might as well be allowing Bill Gates to decide what software I can/must run.

If I don't have spamassassin installed, WTF would Update manager think it had to be added? Again, it shows up in the list of updates, and Synaptic shows it as having been Automatically installed. I unchecked it and spamc in Update manager, but it still updated/installed. This is crazy!

Same thing happens with gnome-pilot. I don't have a Palm Pilot, so I don't want it installed. I remove it, and Update Manager puts it back..... GRRRRR!!!

---

### Post by meborc on 2008-05-28
> **scradock said:**
> Nope - happened again!

What is going on? If I don't have spamassassin installed, it should NOT be installed behind my back! What's going to be next? The Ubuntu Malicious Software Removal Tool, TM BillG?

Seriously, if Ubuntu is going to decide what protection I need, I might as well be allowing Bill Gates to decide what software I can/must run.

If I don't have spamassassin installed, WTF would Update manager think it had to be added? Again, it shows up in the list of updates, and Synaptic shows it as having been Automatically installed. I unchecked it and spamc in Update manager, but it still updated/installed. This is crazy!

Same thing happens with gnome-pilot. I don't have a Palm Pilot, so I don't want it installed. I remove it, and Update Manager puts it back..... GRRRRR!!!

dude relax... take a walk or a cup of tea... did you report this? it sounds more like a mistake then a feature... talk to the devs... 

again like in the other thread :) people should not get frustrated over pre-alpha software

---

### Post by ronacc on 2008-05-29
probably got drug in by one of the "meta packages" , they insist on reinstalling anything they think is "missing" at each update .

---

### Post by scradock on 2008-05-31
Yes, well, mebbe I was being a trifle melodramatic.

BUT .. what's testing all about? If I try out Intrepid and something doesn't work as I expect, do I have to rush straight to Launchpad and possibly clutter up the list of Ubuntu bugs (for ever, if no-one gets around to weeding the list out)? Or can I ask in this specific forum if anyone else has seen the same behavior, and if anyone knows whether this is a bug or a feature (AKA new policy decision that hasn't been effectively notified)?

I know the official line is that the developers cannot be relied on to see comments here .... but we all know that some developers do actually lurk here, and even sometimes make sensible and informative responses. I certainly don't feel "entitled" to join the UD mailing list as a simple but rash user; this forum is as close as I care to get to being part of the mind-blowing flood of conversation that developers have to keep up with.

I agree with ronacc - it's probably some other package that is bringing spamassassin in again and again - now if anyone else showed an interest we could maybe work out which and tell the developers through launchpad....I can't find any clues through Synaptic, and I don't know where/how I would look in the apt logs.

BTW, I have reported this through Launchpad. No response yet.....

---

### Post by scradock on 2008-05-31
So, responding to the sensible suggestion made in the last post, I have checked the apt log.

Spamassassin is indeed being brought in along with evolution and/or evolution-common, along with a whole horde of other libs and applications. I can understand that if evolution is being used to send and receive email it is reasonable to include a spam filter...

BUT I don't use evolution that way. in fact I don't use any of the declared functions of evolution:

```
Evolution is a groupware suite which integrates mail, calendar,
address book, to-do list and memo tools.

Additional features include integration with Exchange and Groupwise
servers, newsgroup client, LDAP support, web calendars and
synchronization with Palm devices.
```

I believe in the freedom arguments for FOSS, including my freedom to choose NOT to use any application - one of my gripes with M$, which requires so many of its products if I choose to use Windows.

BUT if I try to remove evolution, it threatens to remove other parts of my system that I DO use, which I find inconsistent with my free use of the Ubuntu OS.

I guess I'll just have to go on finding out how to use the programs I want without being locked into running stuff I don't want or need.

Anyone got ideas about how to purge evolution from the system without wrecking it?

---

### Post by meborc on 2008-05-31
if i try to remove evolution, it tries to remove **evolution evolution-exchange evolution-plugins**... so you use exchange or some of the plugins?

i don't see how you can remove evolution without not being able to use them

---

### Post by scradock on 2008-05-31
You're right - I can remove evolution itself, and its plugins, and evolution-common, and even evolution-data-server, without affecting other stuff. 

BUT - if I try to take out the last evolution package, evolution-data-server-common, it says it's going to take a bunch of other stuff including gnome-panel and gnome-applets, which I know I use and don't want to lose.

I guess I could try removing the whole lot and putting back the panel and applets, but I haven't gone that far yet.

I have also established that the introduction of spamassassin as a requirement is new to Intrepid - 8.04 allows evolution and all its parts WITHOUT spamassassin. I still think that is worth noting, and it's worth asking why now?

---

### Post by meborc on 2008-05-31
true... but you are asking in the wrong place :) contact evolution package maintainer, or any MOTU with access to better information on the subject

i found this from packages.ubuntu.com:> The data server, called "Evolution Data Server" is responsible for managing calendar and addressbook information. might be that is why you can't remove it... the gnome panel calendar is using it

---

### Post by Ripfox on 2008-05-31
Maybe off topic, but I wish they would nuke Evolution. Seriously. :)

---

### Post by meborc on 2008-05-31
> **Ripfox said:**
> Maybe off topic, but I wish they would nuke Evolution. Seriously. :)

i never use mail clients... so i feel you 100%, BUT i recently converted a person to use ubuntu, and she was very happy with evolution, making different filters for the incoming mail etc etc... and it is a gnome project... AND there should be at least 1 mail client included for those who actually use them

---

### Post by scradock on 2008-05-31
> **meborc said:**
> true... but you are asking in the wrong place :) contact evolution package maintainer, or any MOTU with access to better information on the subject

i found this from packages.ubuntu.com:might be that is why you can't remove it... the gnome panel calendar is using it
yes, that's possible. Seems kind of risky, making a panel applet that anyone might want to use depend on a part fo an elaborate package that some people don't need/want.

---

### Post by Ripfox on 2008-05-31
> **meborc said:**
> i never use mail clients... so i feel you 100%, BUT i recently converted a person to use ubuntu, and she was very happy with evolution, making different filters for the incoming mail etc etc... and it is a gnome project... AND there should be at least 1 mail client included for those who actually use them

Yes it's called ThunderBird :lolflag:

I do use mail clients, I just hate Evolution. Too many dependancies, very annoying. And I think it sucks. Do you want to hear how I REALLY feel?

:lolflag:

---

### Post by meborc on 2008-05-31
> **Ripfox said:**
> Yes it's called ThunderBird :lolflag:

I do use mail clients, I just hate Evolution. Too many dependancies, very annoying. And I think it sucks. Do you want to hear how I REALLY feel?

:lolflag:

not really :) ... why is thunderbird better then evolution? i have never used any so i would like to know

---

### Post by 23meg on 2008-05-31
> **scradock said:**
> yes, that's possible. Seems kind of risky, making a panel applet that anyone might want to use depend on a part fo an elaborate package that some people don't need/want.

The applets are meant to work with the GNOME panel, which is part of GNOME, and isn't really meant to be 100% usable outside a GNOME environment. Desktop environments and other projects of their size and complexity tend to have project-wide dependencies that multiple components rely on, and you need to bear with them if you don't use one component that relies on a certain package, but do (or may) use others. It's a small cost that you may have to pay if you want the benefits of DE integration and package management.

---

### Post by scradock on 2008-05-31
The bug against evolution brought a response from Sebastian Bacher.

The reason for the new behavior in Intrepid is that update-manager is now installing all recommends for updated packages, rather than required stuff only.

We shall probably see a lot more stuff coming in this way.

23meg - yes, I expect the panels to need a full gnome environment. But I don't think evolution should be regarded as an essential part of that. As other people have pointed out, it isn't everyone's favorite mail client, and not all of us even need/want a mail client. In my view, the basic gnome environment (which I really like) should be self-contained without needing optional packages that are supposed to be doing something else.

A bit like the OS/application distinction that M$ has been obfuscating to make it difficult to use alternatives to their chosen apps......

---

### Post by meborc on 2008-05-31
:)

i totally forgot that... there was a discussion about this a while ago...

i don't remember whether there was an option to turn it "off"... some conf file somewhere

---

### Post by MALEADt on 2008-05-31
> **Ripfox said:**
> Yes it's called ThunderBird :lolflag:

I do use mail clients, I just hate Evolution. Too many dependancies, very annoying. And I think it sucks. Do you want to hear how I REALLY feel?

:lolflag:

I prefer Evolution above Thunderbird... Everybody got his personal taste, so at least let the user choose (and don't nuke evolution :P)

---

### Post by plun on 2008-05-31
> **MALEADt said:**
> I prefer Evolution above Thunderbird... Everybody got his personal taste, so at least let the user choose (and don't nuke evolution :P)

Well... Mozilla Messaging...

[http://www.mozillamessaging.com/en-US/](http://www.mozillamessaging.com/en-US/)

I am also testing [Weave]("http://labs.mozilla.com/2008/03/performance-and-stability-update-to-weave-prototype/") for online backups.

So I nuke Evolution and for sure Epiphany if Gnomes tries
to "trick" it to a standard.

---

### Post by scradock on 2008-05-31
I think the message we all might agree on is that we want to be able to CHOOSE our apps - for whatever we want them to do. Sure, our choices will differ, so lots of stuff needs to be available. Great.

What I don't appreciate is when evolution, or whatever app, is allowed to become essential to other unrelated stuff, like Internet Explorer did in Windows. That put a whole bunch of us off M$, and got them into a bunch of trouble - billion dollar fines, for instance.

I hope Ubuntu goes on being free and open, in the above sense - it should be open to me to have a completely different collection of functional apps running from your chosen set - in the same Gnome environment. That way we can all be interested users, making whatever contributions we are able to to the development of the FOSS world.

---

### Post by meborc on 2008-05-31
well... actually you CAN remove evolution, it will also remove evolution-exchange and evolution-plugins

you can't remove evolution-data-server-common, which does all the calendar thing... if the name of that package was gnome-data-server-common you would not feel it as a problem, would you? :)

i think we are a bit ahead with saying evolution=explorer :)

---

### Post by scradock on 2008-05-31
> **meborc said:**
> well... actually you CAN remove evolution, it will also remove evolution-exchange and evolution-plugins

you can't remove evolution-data-server-common, which does all the calendar thing... if the name of that package was gnome-data-server-common you would not feel it as a problem, would you? :)


I agree - I would prefer such shared functionality to be split into "bits that are useful enough to be part of the gnome base" and "bits that really are only needed if you're using evolution". Renaming it would simply shift all the bits into the first category. If there is no need for the package name to refer to evolution unless for historical reasons, let's shift the more generally-useful functionality into the gnome environment base.

> i think we are a bit ahead with saying evolution=explorer :)
As you will have noticed, I do have a slight tendency to exaggerate - but I think it has been a useful conversation, and I've certainly learned new things from it.

---

### Post by meborc on 2008-06-01
> **scradock said:**
> as You Will Have Noticed, I Do Have A Slight Tendency To Exaggerate - But I Think It Has Been A Useful Conversation, And I've Certainly Learned New Things From It.

+1 ;)

---

### Post by scradock on 2008-06-03
Returning to my original complaint(!), I have tracked down the miscreant - the package which was requiring Update manager to keep telling me to install spamassassin, gnome-pilot, and evolution-data-server.

It was nautilus-sendto, whose function is to provide a "send-to Evolution" option in nautilus. As I don't use evolution, this is unnecessary, so I have removed it. Now Update Manager has stopped insisting that I install spamassassin, spamc, gnome-pilot, gnome-pilot-conduit, and evolution-data-server.

I found this using "aptitude why spamassassin", which conveniently lists the reason(s) why aptitude wants to install the package. It shows a 2-step recommend -  nautilus-sendto > evolution > spamassassin. Even without evolution installed, this is apparently enough to require spamassassin....

I'll mark this as SOLVED.

---

### Post by Ripfox on 2008-06-03
Alright then! Use the thread tools and actually mark it as solved :lolflag:

---

