---
title: "Firefox"
date: 2008-12-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2008-12-16
Has anybody noticed slow access to web pages ?
It takes 10-15 seconds to go from one page to another and sometimes I get web site not found if it takes too long.
It only seems to happen with the 2.6.28 kernel.

---

### Post by Gina on 2008-12-16
Firefox 3.04 is working fine for me - pages loading in about a second.  I'm running 2.6.28.2 kernel. 64 bit.

EDIT :- Now running Firefox 3.1 and that's OK too - about the same speed.

I think your problem is likely to be internet speed or the server for the site you're looking at.

---

### Post by cecilpierce on 2008-12-16
Thanks Gina for the reply. I don't have a problem with Hardy Intreped or Mandriva just Jaunty and the only differance I can see is the 28 kernel. I'm running 32 bit system and Firefox 3.0.4.

---

### Post by Gina on 2008-12-16
I didn't notice any problem with my laptop (32bit Jaunty F3.04 28.2 kernel) but I'll check again later,

---

### Post by dakkar9999 on 2008-12-16
Yes, I do find browsing to be slower than when running windows. Not sure why.

---

### Post by autocrosser on 2008-12-16
I've not had problems--running the new kernel (.3) & the newest Firefox beta 3.1 release.....

---

### Post by forumache on 2008-12-16
cecil, do you have a nvidia card?

it "seems" that since I changed from nvidia to nv driver I have no problems with Firefox anymore.

I say "it seems" because at the same time I changed the firmware on the router.

It would seem the router firmware update solved the problem, but the problem manifested itself only on my computer, the other computers were ok, although using the same router.

Firefox was waiting with "Looking for <hostname>" about 10 seconds. I seemed sluggish.

---

### Post by cecilpierce on 2008-12-16
Yes I have FX5200 in this machine with seven OS's and all have the nvidia driver except one, that is Ubuntu Ultimate Edition that uses nv driver. The only systems that run slow are Fedora 10 and Ubuntu Jaunty all the others are like lightening, by the time you take your finger off the mouse its there ! Can't figure it out, I even tried going back to the 2.6.27 kernel, no change. Oh well thanks for the input, I'll keep messing with it till it blows up ! Cecil

---

### Post by Slug71 on 2008-12-16
I would actually like if Opera just replaced Firefox in Ubuntu.

---

### Post by curtis on 2008-12-17
> **Slug71 said:**
> I would actually like if Opera just replaced Firefox in Ubuntu.

Opera will never replace Firefox because Opera is closed source. I think Firefox is a lot better anyway.

---

### Post by super.rad on 2008-12-17
Since updating to version 3.0.5 this morning this keeps happening on a lot of websites (see pic attatched)

---

### Post by jfernyhough on 2008-12-17
I knew E17 was beta, but I didn't know it was so unstable that just by thinking about it Firefox breaks.

:)

Looks like a Cairo issue, but in reality I've no idea.

---

### Post by super.rad on 2008-12-17
I'm using the experimental kubuntu PPA for KDE 4.2 beta on intrepid and I just did a load of updates which included firefox 3.0.5 and it doesnt have any problems with the same websites that mess up when using jaunty

---

### Post by knarf on 2008-12-17
Yes, Firefox seems to be slow as molasses these days. Once of the potential culprits is the new (sqlite-based) bookmark/history/etc system ('places') in combination with a slow disk or near capacity filesystem.

One of the ways of getting a faster - albeit less stable - browser is to download the latest Firefox 'tracemonkey' nightly (currently firefox-3.2a1pre, new builds appear every day, the name won't change, the bugs might... get them at [ftp://ftp.mozilla.org/pub/firefox/nightly](ftp://ftp.mozilla.org/pub/firefox/nightly)) to an alternative location [SIZE=1](1)[/SIZE], open it up, go to *about:config*, change '*javascript.options.jit.chrome*' to '*true*' and restart firefox. The speed difference here is remarkable: on a 1.2 GHz T23 with 768MB it feels nearly instantaneous where its siblings crawl using the same profile directory (!) with a 25 MB 'places' sqlite file.

[SIZE=1]1) I use /opt/APPfirefox/firefox with /opt/APPfirefox/bin linked to /opt/APPfirefox/firefox, optionally add some scripting (eg. in /etc/profile.d/path.sh) to add all /opt/APPsomething/bin directories to $PATH[/SIZE]

---

### Post by cecilpierce on 2008-12-17
Just reinstalled Jaunty and its even slower than the first one ! Twenty seconds just to load my home page (Google).
I tried Opera and its fast but I like FF more. Guess I will use it till something turns up with FF.

---

### Post by gjoellee on 2008-12-18
> **Gina said:**
> 
EDIT :- Now running Firefox 3.1 and that's OK too - about the same speed.


hmmmm..... for me Firefox 3.1 is more the double as fast, not changes int he internet connection. I've heard Fiefox 3.1/Opera10 alpha1 are currently the worlds fastest web browsers

---

### Post by gjoellee on 2008-12-18
> **super.rad said:**
> Since updating to version 3.0.5 this morning this keeps happening on a lot of websites (see pic attatched)

the KsHoster team registered that bug yesterday. This bug does not appear in other web browsers, this bug is known to appear in Fiefox 3 or greater (3.1 Alpha is included). Versions below 3 are not tested.

---

### Post by Slug71 on 2008-12-18
Firefox 3.1 should just be default already.

---

