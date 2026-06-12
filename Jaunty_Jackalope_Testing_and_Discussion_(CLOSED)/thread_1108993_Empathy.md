---
title: "Empathy"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lee_connell on 2009-03-28
Does empathy still not support audio/video out of the box? I have it setup in jaunty and 'send file' and 'call' are disabled, i'm assuming call does both video and audio?

---

### Post by Yfrwlf on 2009-04-10
> **lee_connell said:**
> Does empathy still not support audio/video out of the box? I have it setup in jaunty and 'send file' and 'call' are disabled, i'm assuming call does both video and audio?

Was wondering the same.  I tried installing a few various telepathy packages but that didn't do anything.  I can't do file transfers or calling with any user on any protocol, including Jabber via Google as well as AIM, Yahoo, ICQ, and MSN.

From their website:
Current features:
Voice and Video call using SIP and Jingle

So, yeah...a current feature for someone else maybe.

Am also running the latest Empathy in Jaunty (tho like that matters) like you are.  It's the latest Empathy, so, it should work.

---

### Post by ubuntu27 on 2009-04-10
From Gnome 2.26 Release Note:

"The Empathy instant messaging application, which uses the Telepathy communications framework, has taken another step forward with features including file transfer where supported by Telepathy (**currently Jabber and link-local XMPP**), chat room invite support, sound themes and notifications, and an improved VoIP experience."

[http://library.gnome.org/misc/release-notes/2.26/](http://library.gnome.org/misc/release-notes/2.26/)

---

### Post by Yfrwlf on 2009-04-11
> **ubuntu27 said:**
> From Gnome 2.26 Release Note:

"The Empathy instant messaging application, which uses the Telepathy communications framework, has taken another step forward with features including file transfer where supported by Telepathy (**currently Jabber and link-local XMPP**), chat room invite support, sound themes and notifications, and an improved VoIP experience."

[http://library.gnome.org/misc/release-notes/2.26/](http://library.gnome.org/misc/release-notes/2.26/)

Yeah, Jabber, that's what I'm using and that's what isn't working, unless there is some other Jabber server I need to use other than Google's to make this work.  If by the "link-local" part it means it won't work except...on your home network?  Then that's pretty useless of course, not that the developers care because even that would be a great step forward for them which is fine and dandy.

The problem here is that it says on their website it currently has voice and video implemented with SIP and Jingle aka part of Jabber, and I'm failing to see how any of this is implemented at all yet.  I don't think I'm going to be the only one who's going to be deceived by this, so, that's not a very good thing to note on your site.

Regardless, I have yet to get this working with Jabber, though I have not tried SIP.  I am not sure whether or not Google's Jabber server is Jingle-compliant, nor am aware of any Jabber servers that are.

Does anyone know of a Jingle-enabled Jabber server, if that is indeed the problem?

---

### Post by aamukahvi on 2009-04-11
> **Yfrwlf said:**
> The problem here is that it says on their website it currently has voice and video implemented with SIP and Jingle aka part of Jabber, and I'm failing to see how any of this is implemented at all yet.
Have you installed all the telepathy stuff for farsight and sofiasip?

---

### Post by Yfrwlf on 2009-04-14
> **aamukahvi said:**
> Have you installed all the telepathy stuff for farsight and sofiasip?

All is installed yep, everything except for the developer packages basically.  But of course, if it were the case of installing certain packages, which it may be, then of course the dependencies should be changed so that users can fully use Empathy.  I'm pretty sure voice and video isn't some side little enhancement, but a pretty important part of the program, along with being able to send files, so it should be the default.

What I haven't yet tested is to see if it's just Google's Jabber server that is the problem, because I read someplace else that you have to enable voice chat in your gmail settings.  Since I couldn't find an option to do so, I haven't tested this out, so I was going to look for some other Jabber server.

---

