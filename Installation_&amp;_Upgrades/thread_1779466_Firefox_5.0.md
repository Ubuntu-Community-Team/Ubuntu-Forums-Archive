---
title: "Firefox 5.0??"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by saphil on 2011-06-10
I am running Natty.  I just did a weekly update and the system installed something called firefox 5.0 - canonical 1.0 
It lost all my bookmarks and is not compatible with my add-ons and toolbars for 4.x

Is this a bug or a feature?

Attached is a picture of the "about firefox" dialog

---

### Post by lightstream on 2011-06-14
I just belatedly upgraded to Natty and yes, I've also been upgraded to Firefox 5.

A lot of add-ons seem to be OK - such as FireFTP (it's awesome), Greasemonkey, Web Developer.

However Google Toolbar is not supported, nor is All-in-One gestures, and in fact no gesture add-ons appear to be available in the Add On manager.

Gestures are a show stopper for me, so now I'm gonna have to find out how to switch back to Firefox 4...

---

### Post by lightstream on 2011-06-14
and strangely, the Add Ins Manager seems to be confused as to whether it's FF4 or FF5, as it shows FF5 Add Ins but has a big FF4 thingie at the top:

[IMG]http://www.kuxas.com/images/firefox-schizo.jpg[/IMG]

---

### Post by saphil on 2011-06-14
I got the reason from a member of [http://ale.org](http://ale.org).  They suggested I check whether I had the proposed repository enabled. Proposed is where future packages live. Apparently the developers needed firefox 5 for ubuntu 11.10 for coding security patches.
When I checked my repositories (synaptic has the link in a menu), I did have proposed checked.
So I made a copy of the hidden folder /home/~/.mozilla/ and deleted firefox 5.0.
When it was gone, I reinstalled firefox 4.0. All my addons work again, and I didn't lose any profile data.

---

### Post by lightstream on 2011-06-14
Found out that you can run FF4 addons in FF5. Install the [Nightly Tester Tools]("https://addons.mozilla.org/en-US/firefox/addon/nightly-tester-tools/") add on, then go to Tools > Nightly Tester Tools > Force Addon Compatibility

This disables compatibility checking for add ons, so add ons which are not marked as FF5 compatible will still run, and the two I mentioned both seem to work OK.

---

### Post by lightstream on 2011-06-14
> **saphil said:**
> I got the reason from a member of [http://ale.org](http://ale.org).  They suggested I check whether I had the proposed repository enabled. Proposed is where future packages live. Apparently the developers needed firefox 5 for ubuntu 11.10 for coding security patches.
When I checked my repositories (synaptic has the link in a menu), I did have proposed checked.
So I made a copy of the hidden folder /home/~/.mozilla/ and deleted firefox 5.0.
When it was gone, I reinstalled firefox 4.0. All my addons work again, and I didn't lose any profile data.

yes I discovered that too, however I didn't want to disable proposed just for this one app (although internet is a pretty important app!)

Also, my bookmarks were not affected...

---

### Post by saphil on 2011-06-14
I will try that. I don't think proposed has ever caused me any trouble before. I use these addons all time so I guess I reacted too strongly. :-)

Yesterday firefox 5 appeared in the standard repositories, so I installed it.  the FF4 extensions still didn't play, so I added the nightly tester tools and everything was peachy.  Now I can turn the 'proposed' repo back on.

Thanks again, Lightstream!

---

