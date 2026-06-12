---
title: "piding/empathy gnome integration is fantastic"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by syxbit on 2008-10-03
i installed the beta yesterday and i'm extremely impressed.

sure the delayed and ongoing promised theme changes still aren't up to much, but the gnome integration of pidgin and empathy are fantastic.

does anyone know if these improvements are ubuntu's doing, or part of gnome 2.24 ?
(cause i'd like that to carry over in my other distros)

(also, anyone know where conversation logs for empathy kept, i can't find them)

---

### Post by gnomeuser on 2008-10-03
I believe logs are in ~/.mission-control/accounts/<account name>/

---

### Post by stewacide on 2008-10-03
I don't understand the point of Empathy, when Pidgin does everything it does and more and better. Are there licensing issues why it isn't the official Gnome IM app?

---

### Post by syxbit on 2008-10-03
empathy (for starters) supports audio, which pidgin doesn't.
also, empathy integrated much better with gnome. it is because it uses libraries that can be shared and used by other programs.

as for chat history being in .mission-control, i just have avatar.bin :(

---

### Post by syko21 on 2008-10-03
logs are actually in ~/.gnome2/Empathy/logs

PS> is there anyway to import pidgin logs to Empathy?

---

### Post by gnomeuser on 2008-10-04
> **stewacide said:**
> I don't understand the point of Empathy, when Pidgin does everything it does and more and better. Are there licensing issues why it isn't the official Gnome IM app?

There are two main reasons, the underlying technology Telepathy which is much more modular than pidgin and will allow some cool stuff e.g. you can look up Telepathy Tubes. Empathy as such is about much more than im/voip/video. 

Then the fact that empathy is more than an im client, you see that now but what we get in addition is libempathy which will allow integration of relevant parts of the technology above into applications. You also get the ability to do dbus based interaction with the framework. 

One scenario empathy will allow e.g., you and I know each other, you see I am online so you start up the tetris game and invite me to play you. Empathy/Telepathy will then send an invitation, setup the connection (and handle firewall hole punching if required). All of that hard code that does the hole punching and connection establishment is now literally only requesting a tube and as an application programmer that is.. it. The same could be the case for collaborative simultaneous document editing (in fact you can look at the OLPC XO Write activity for an actual implementation using Tubes and AbiWord). Or sharing files with your friends directly in Nautilus with a single click.. one could go on.

So it's not about licensing, it's about being GNOME'y, it's about the technology underneath, it's about integration, it's about bringing im/voip/video/buddy networking deep into our platform and enable you to connect and interact with your friends in new ways.

What you see now is just a very clean well integrated IM client, but that is the tip of the iceberg. Give this technology some time and see it enable many new and exciting things in nicely integrated ways.

---

### Post by | MM | on 2008-10-04
The way i understand it, Telepathy is sort of like Gstreamer except for communications.  So its more a framework than a insular application like what pidgen is to IM.

---

### Post by gnomeuser on 2008-10-04
> **| MM | said:**
> The way i understand it, Telepathy is sort of like Gstreamer except for communications.  So its more a framework than a insular application like what pidgen is to IM.

That is a reasonable way to look at it, and like gstreamer wraps ffmpeg (the gstreamer-ffmpeg package) to get certain support which they don't have in well defined libraries, telepathy wraps libpurple to provide support for certain protocols for which there aren't clean implementations for yet (gadu-gadu and aim stands out here). 

So in terms of protocols empathy is in no way a step back, file transfer and voice/video support though are not (universally) supported (there is a SoC project but it isn't merged yet and can't be till the next GNOME cycle opens but in theory this work could then be found in a PPA till Jaunty comes out and delivers the code through the repos.. much like it is done with Banshee).

---

### Post by Lorenz on 2008-10-04
> **syxbit said:**
> i installed the beta yesterday and i'm extremely impressed.

sure the delayed and ongoing promised theme changes still aren't up to much, but the gnome integration of pidgin and empathy are fantastic.

does anyone know if these improvements are ubuntu's doing, or part of gnome 2.24 ?
(cause i'd like that to carry over in my other distros)

(also, anyone know where conversation logs for empathy kept, i can't find them)

What did you do to make the theme fit in firefox as well? It only makes the window borders dark for me, rest is in the bright normal color.

---

### Post by syxbit on 2008-10-04
i didn't do anything.
it's just the human dark theme.

so is this cool integration the work of Ubuntu devs, or Gnome?
It was interesting that the same integration works for both empathy and Pidgin.
Gnome 2.24 will hit in Arch Linux soon (my main OS) and I really hope this works there too :)

---

### Post by Mr. Picklesworth on 2008-10-04
> **syxbit said:**
> i didn't do anything.
it's just the human dark theme.

so is this cool integration the work of Ubuntu devs, or Gnome?
It was interesting that the same integration works for both empathy and Pidgin.
Gnome 2.24 will hit in Arch Linux soon (my main OS) and I really hope this works there too :)

One thing to keep in mind is that Canonical pays developers to work on GNOME; most of Ubuntu's changes to GNOME are applied upstream. Just some of them are too rough around the edges / Ubuntu-specific to fit in. So even if it is a change by Canonical, they are always sharing back upstream!

In this case, I believe the fancy Fast User Switcher was a patch to GNOME by a different party, but definitely present upstream. (It's even in their release notes).
I am not sure about the Pidgin end of things, though; as I understand it, the thing by default just plugs in to Telepathy's Presence stuff. I could be mistaken, however :)

Kudos for the excellent explanation of Empathy / Telepathy, gnomeuser!

---

### Post by BwackNinja on 2008-10-04
"busy" and "offline" don't work in pidgin from the fast-user-switcher, but away and available do. What works works well though.

---

### Post by jerome1232 on 2008-10-09
> **Lorenz said:**
> What did you do to make the theme fit in firefox as well? It only makes the window borders dark for me, rest is in the bright normal color.

Completely offtopic but if your talking about the dust theme (it does what your talking about) you can get a firefox theme that fixes it [here]("https://wiki.ubuntu.com/Artwork/Incoming/DustTheme")

---

### Post by igknighted on 2008-10-10
As neat as this integration is, for some reason with empathy when I set myself as away or busy, and then walk away from my computer (like to go to bed), I come back to find that I am no longer away/busy.  Anyone else notice this?  I am using AIM/Oscar and Google Talk when this happens.

---

### Post by stormtrooprdave on 2008-10-10
Is it mentioned in this thread that empathy can handle voice - does that mean if I log into empathy on my msn account I can voice chat to msn users in Windows?

---

### Post by gnomeuser on 2008-10-10
> **stormtrooprdave said:**
> Is it mentioned in this thread that empathy can handle voice - does that mean if I log into empathy on my msn account I can voice chat to msn users in Windows?

not currently, the code is mostly there but lacks merging, testing and polish. The project you want is called farsight2 and had a great deal of work done on it during Google' Summer of Code 2008. 

This support is on the roadmap for GNOME 2.26 (though in the hopeful category since there are other pressing issues to solve). 

So no, you can't do this with empathy today, you will soon though and till then amsn supposedly has an implementation that sorta works (I have never been able to make it work). One problem is that Microsoft is constantly changing their protocol and server authentication so it's an arms race for us to keep up.

What does work today is voice chat using Jingle so if you can convince your Windows using friends to try out google talk then you can talk to them today.

See: [http://live.gnome.org/Empathy/Roadmap](http://live.gnome.org/Empathy/Roadmap)

---

### Post by plun on 2008-10-10
> **gnomeuser said:**
> One problem is that Microsoft is constantly changing their protocol and server authentication so it's an arms race for us to keep up.

What does work today is voice chat using Jingle so if you can convince your Windows using friends to try out google talk then you can talk to them today.

See: [http://live.gnome.org/Empathy/Roadmap](http://live.gnome.org/Empathy/Roadmap)


Well, I tested Windows Live **Messenger 9** and this is a "mountain" to climb. IMHO

"Please Nokia,  we need money"...8-)

Empathy is just nothing for the moment.  "IMHO" again...

---

### Post by Ub1476 on 2008-10-10
Well, it's good that they focus on integration and stuff being logical in a smart way. I hope that's the future of Gnome 3.0 (2.30).

---

### Post by gnomeuser on 2008-10-10
> **plun said:**
> Well, I tested Windows Live **Messenger 9** and this is a "mountain" to climb. IMHO

"Please Nokia,  we need money"...8-)

Empathy is just nothing for the moment.  "IMHO" again...

you seem to expect perfection, but please remember perfection is the enemy of good. 

Empathy is better in so many ways underneath, it might just pay off in 6-12 month for all users. It will however never pay off if Empathy never gets tested or deployed so we can work out all the kinks.

Today Empathy provides us very good compatible support for every protocol with a minimal amount of regression from pidgin.

You cannot blame a Free Software project for issues imposed on it by an arms race with a proprietary project which controls the servers and the protocol. This will never work 100% as well as the official client, regardless of what alternative client you use, the solution to this problem could be asking people to also use an open standard like Jabber (here GoogleTalk is an excellent client for Windows). It's my experience that users are very willing to do this. Alternatively if you insist on being tied down by proprietary vendors or you are forced by unchangeable circumstances to do so (like myself), you will have to wait till we get that stuff implemented - sad facts of life.

You could level the same concern against Linux as a whole.. Windows and OS X are mountains to climb.. should we not encourage users to switch to Linux because we currently don't (and likely never will) cover all the use cases those alternative systems have. I would say no.

---

### Post by Merk42 on 2008-10-11
How do you even use Empathy? I installed it via add/remove.
It says I need to install a backend for each account I want to use, but doesn't tell how to go about doing that.

---

### Post by BARlotta on 2008-10-11
Does empathy have any sort of notification when another user is typing?  I haven't been able to notice any change in this regard.

---

### Post by Asraniel on 2008-10-11
Empathy is a little what kde 4 is for kde. Empathy is in it's base better than pidgin, and will allow cool new things in the future. But to get there, a rough time where things are not quite up to what they have been, has to be traversed. For kde that rough time was more or less a year, but now you can see the advantages of kde 4 over kde 3.

by the way, telepathy will also be used by kopete, which means, protocol improvements will be shared between gnome and kde, which means, better protocol support.

---

### Post by gnomeuser on 2008-10-11
> **BARlotta said:**
> Does empathy have any sort of notification when another user is typing?  I haven't been able to notice any change in this regard.

The status icon (normally the little green circle) in the chat window should transform into a keyboard typing icon when typing is happening on the other end.

---

### Post by MALEADt on 2008-10-11
I decided to give it a try myself, and indeed the integration is really beautifull :) Too bad some quite important features are still missing, but I'm sure this will improve in newer releases.

---

### Post by jblackhall on 2008-10-11
> **Merk42 said:**
> How do you even use Empathy? I installed it via add/remove.
It says I need to install a backend for each account I want to use, but doesn't tell how to go about doing that.

This sounds like you're using the version in Hardy.  If that's the case, I think that version is very old and doesn't work very well unless you know how to set it up (installing a bunch of telepathy packages basically).  I'd wait to test it out until Intrepid.

If you're working on Intrepid, then you may be experiencing a bug via add/remove.  Although I'm pretty sure that's how I installed it in Intrepid and it worked ootb.

---

### Post by Merk42 on 2008-10-11
> **jblackhall said:**
> This sounds like you're using the version in Hardy.  If that's the case, I think that version is very old and doesn't work very well unless you know how to set it up (installing a bunch of telepathy packages basically).  I'd wait to test it out until Intrepid.

If you're working on Intrepid, then you may be experiencing a bug via add/remove.  Although I'm pretty sure that's how I installed it in Intrepid and it worked ootb.

I am using the one in Hardy, so does that mean I'm SOL and need to wait for Intrepid?.

---

### Post by jblackhall on 2008-10-11
> **Merk42 said:**
> I am using the one in Hardy, so does that mean I'm SOL and need to wait for Intrepid?.

You can try adding the telepathy ppa:
[https://launchpad.net/~telepathy/+archive](https://launchpad.net/~telepathy/+archive)

I seem to recall that was not as well integrated in Hardy and there still might be some setup involved.  In Intrepid, it pretty much just works after install.  If you're wondering what packages you need to install to make it work (besides empathy), it's some of the ones like telepathy-*.  I couldn't tell you exactly which ones, but I think telepathy-haze is the most important.

You won't get the integration with the fast-user-switcher in Hardy, though, I don't think.  So besides that, it's not incredibly different from Pidgin at this point (a few things better, probably a few more worse).  Just has a lot of potential for Gnome, I think.

---

### Post by Merk42 on 2008-10-11
I was trying it out because of the possiblity of webcam support. I can't find any way to get my AIM friends to view my webcam


I've tried Kopete, and while it finds my cam I can't find a way to start a view, and receiving doesn't work either
I've Windows XP in Virtualbox, but I can't get it to detect my cam.
The Linux native AIM is a pitiful version 1.5
I tried AIM in WINE (1.1.6) and that wouldn't run at all

---

### Post by gnomeuser on 2008-10-12
> **Merk42 said:**
> I was trying it out because of the possiblity of webcam support. I can't find any way to get my AIM friends to view my webcam


Okay before more people try this because of webcam support and get disappointed. This support is not ready yet, it depends on the farsight2 project which has not been integrated yet.

It will not work yet. The magic moment we all wait for with regards to this is farsight2 reaching maturity.

Another issue is the fact that webcam support under Linux is currently really bad. We have drivers for more cams now but there is still the issue that only one application can use the camera at once. openSUSE have a project to build a frameserver that will share the output. Then we have to account for the existance of v4l as well as v4l2 both having different APIs, Fedora' Hans de Goede has been writing a compatibility layer to workaround this issue.

All in all before webcams really work in Linux we need a lot of work, to get them working in empathy (as the only app using them), farsight2 needs to get finalized and integrated. The Empathy roadmap has this as a hopeful item for GNOME 2.26 which means it's a Jaunty item as best.

This should not be taken as encouragement to wait with switching, run Empathy in parallel, use it as your primary client and help report problems. Everytime one of the other features is made more solid and development goes smoothly it will mean a higher probability that time will be present to allow for farsight2 work. Your work on this really does make a difference even if you can't code, you can help by testing.

I know this is a killer feature, I myself, wait for it but it's just not there yet.

---

