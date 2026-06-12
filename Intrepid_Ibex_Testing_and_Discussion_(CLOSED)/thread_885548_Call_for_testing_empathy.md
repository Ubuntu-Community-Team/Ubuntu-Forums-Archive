---
title: "Call for testing empathy"
date: 2008-08-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bobbocanfly on 2008-08-10
This was posted to the Ubuntu Development mailing list a few days ago, but I thought I should re-post it here, as I think quite a few people will be interested in this:

> Hello everyone,

Empathy[1] will be part of the upcoming GNOME 2.24 desktop.
The ubuntu desktop team considers using it instead of Pidgin for
intrepid as default IM client. If you are running intrepid, please give
empathy a test and report bugs to launchpad[2]. It may be installed by
running synaptic and installing the empathy package or by running
"sudo apt-get install empathy".
If you experiment a bug have a look at [3] before reporting.

Empathy consists of a rich set of reusable instant messaging widgets,
and a GNOME client using those widgets. It uses Telepathy and Nokia's
Mission Control, and reuses Gossip's UI. The main goal is to permit
desktop integration by providing libempathy and libempathy-gtk
libraries. libempathy-gtk is a set of powerful widgets that can be
embeded into any GNOME application.

The Telepathy[4] project is building a unified framework for many
different kinds of real-time communications. It uses the D-Bus
messaging system to provide a simple interface for client applications,
allowing them to quickly take advantage of Telepathy's benefits.
Telepathy supports XMPP(jabber), MSN, ICQ, SIP, ...

Laurent Bigonville

[1] [http://live.gnome.org/Empathy](http://live.gnome.org/Empathy)
[2] [https://bugs.launchpad.net/ubuntu/+source/empathy](https://bugs.launchpad.net/ubuntu/+source/empathy)
[3] [http://live.gnome.org/Empathy/Debugging](http://live.gnome.org/Empathy/Debugging)
[4] [http://telepathy.freedesktop.org/](http://telepathy.freedesktop.org/)



---

### Post by rockin_goliath on 2008-08-10
I will definitely participate in this when I get back to the US. I've been following the Empathy and Telepathy development very closely, and I am very excited for easier, open source video chat. Finally, an open alternative to Skype!!!!

---

### Post by Neon Lights on 2008-08-10
Empathy shows people as Online when they're Mobile, which is annoying. Thanks for reminding me to file a bug. [:

---

### Post by InfinityCircuit on 2008-08-10
Thanks for the heads-up.  Right away I see that there is something seriously wrong with the icons, but it looks like a nice client.

Since it doesn't seem to support IRC out of the box, it would seem that inclusion of this might require including XChat as well or other changes.

---

### Post by RAOF on 2008-08-10
> **InfinityCircuit said:**
> Thanks for the heads-up.  Right away I see that there is something seriously wrong with the icons, but it looks like a nice client.

Since it doesn't seem to support IRC out of the box, it would seem that inclusion of this might require including XChat as well or other changes.

That would be a lack of an installed IRC backend.  You might want to file a bug saying that empathy should Recommend: telepathy-idle (the IRC backend) in some way.

---

### Post by InfinityCircuit on 2008-08-10
Thank you for the quick reply. I will file the bugs promptly.

---

### Post by Mr. Picklesworth on 2008-08-11
Backend or not, Empathy's IRC support is currently a bit odd. The lack of password authentication (aimed at happening for GNOME 2.26 hopefully) breaks a lot of functionality users expect. Joining a room involves a surprising ammount of fiddling.

Not that XChat is easy, of course.
A solid IRC client would be a nice thing to have packaged. I don't think that IRC *needs* to be here out of the box, but I was mentioning somewhere that I think it would be nice if said IRC client was tuned by default to the Ubuntu support channels.

I, too, love Empathy :)
Anyone looking to run a recent version on Hardy, check out the Telepathy team PPA on Launchpad: [https://launchpad.net/~telepathy/+archive](https://launchpad.net/~telepathy/+archive)

---

### Post by yelo3 on 2008-08-11
I've just installed empathy. In my opinion it looks to bad to replace pidgin. The UI is really ugly.

---

### Post by Benjamin_Lebsanft on 2008-08-11
I'm also missing the option to group contacts in a meta contact as I can do with pidgin.

edit: seems a while off, so no empathy for me:
[http://bugzilla.gnome.org/show_bug.cgi?id=460647](http://bugzilla.gnome.org/show_bug.cgi?id=460647)

---

### Post by jethro10 on 2008-08-11
:)
When I read this, I though someone was gonna shout at us for being too hard on the developers during testing.

Phew,
J

---

### Post by Iceni on 2008-08-11
I will test. I do think emesene should replace pidgin as the msn client.

---

### Post by bobbocanfly on 2008-08-11
> **Iceni said:**
> I will test. I do think emesene should replace pidgin as the msn client.

I very much doubt that the core developers will even consider using emsene (or asmn etc.) due to the fact that they only support a single (closed) protocol. I think we should be pushing more and more towards using open protocols like Jabber (which means using Pidgin, Empathy or any other IM client that supports these), not sidling out into a single, closed protocol.

A big change like this is always going to meet with objections ("Its ugly, no we cant move"), but is it honestly too difficult to fire up synaptic or gnome-terminal and install the app of your choice? I know a lot of people that are for the shift and a lot of people that are against the move.

Unfortunately Empathy has seemed quite buggy for me (started using it in Intrepid last night) and it has crashed 3/4 times, all of which have been picked up by apport and sent to Launchpad (where there are quite a lot of (tele|em)pathy bugs.

---

### Post by bobbocanfly on 2008-08-11
> **InfinityCircuit said:**
> Since it doesn't seem to support IRC out of the box, it would seem that inclusion of this might require including XChat as well or other changes.

Uploaded a fix for the IRC bug. Will be in your next empathy update.

---

### Post by ViRMiN on 2008-08-11
Just got an update to Empathy...

---

### Post by Iceni on 2008-08-12
> **bobbocanfly said:**
> I very much doubt that the core developers will even consider using emsene (or asmn etc.) due to the fact that they only support a single (closed) protocol. I think we should be pushing more and more towards using open protocols like Jabber (which means using Pidgin, Empathy or any other IM client that supports these), not sidling out into a single, closed protocol.

While I agree to this (was also on my mind) there is the fact that the vast majority of users are windows-based. Ideally we should all use an open protocol, but then ideally linux should have a much greater market share as well. Msn is the standard for im, and because of the user base it will remain the standard for im for the forseeable future. Pidgin is .. adequate at best, buggy at worst to the extent that several people I've helped with ubuntu complained about the problems with their "msn". 

Yes, installing emesene is a 10-second job, but for a new user it is more of a 30-minute research job. And, as im clients are something a majority of the younger demographic uses a lot, ubuntu should be shipped with a working, effective and simple one.

---

### Post by zombiepig on 2008-08-12
I'm reserving my judgement until I see how empathy handles file transfer (which I think is coming soon). For me, pidgin has never worked properly with transfer over xmpp, so if empathy works with this, it will definitely get my vote! :P

---

### Post by DPic on 2008-08-12
> **Iceni said:**
> While I agree to this (was also on my mind) there is the fact that the vast majority of users are windows-based. Ideally we should all use an open protocol, but then ideally linux should have a much greater market share as well. Msn is the standard for im, and because of the user base it will remain the standard for im for the forseeable future. Pidgin is .. adequate at best, buggy at worst to the extent that several people I've helped with ubuntu complained about the problems with their "msn". 

Yes, installing emesene is a 10-second job, but for a new user it is more of a 30-minute research job. And, as im clients are something a majority of the younger demographic uses a lot, ubuntu should be shipped with a working, effective and simple one.

Woah woah woah there-- MSN is NOT the standard for IM. It may be in your area, but in other places that isn't true. I know that in the USA almost everyone uses AIM, and in other places almost everyone uses Yahoo. Multi-protocol client is the way to go.

---

### Post by h2gofast on 2008-08-12
I feel your pain

---

### Post by Gina on 2008-08-13
> **DPic said:**
> Woah woah woah there-- MSN is NOT the standard for IM. It may be in your area, but in other places that isn't true. I know that in the USA almost everyone uses AIM, and in other places almost everyone uses Yahoo. Multi-protocol client is the way to go.Definitely!  In fact most of my friends seem to use Yahoo!  But multi-protocol is definitely the way to go IMO.

---

### Post by ViRMiN on 2008-08-13
Serious fault in Empathy!

I have a chat open with contact A, and all went quiet until I get a message from B on the same conversation... "I'm confused"

Please try this out, I'm going to raise a bug!  Will have to edit the convo though! :redface:

---

### Post by ViRMiN on 2008-08-13
> **ViRMiN said:**
> Serious fault in Empathy!

I have a chat open with contact A, and all went quiet until I get a message from B on the same conversation... "I'm confused"

Please try this out, I'm going to raise a bug!  Will have to edit the convo though! :redface:

Filed - #257705 - Screenshots (once desensitised!) to follow...

---

### Post by slsolaris on 2008-10-30
> **yelo3 said:**
> I've just installed empathy. In my opinion it looks to bad to replace pidgin. The UI is really ugly.

yes, thats tru, but empathy could be improved!

---

