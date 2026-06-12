---
title: "Where is sunbird?"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-04-28
Having been testing lucid for a while I'm about to settle down and try using it as my main OS but when I went to setup my calendar I found sunbird is no longer in the repos.
What happened?
I have my profile with many calendar entries but no sunbird :(

---

### Post by andrewabc on 2010-04-28
Argh they don't have it. Reason is probably because debian no longer has it.

Sunbird is no longer going to be around for 1.0 final. The last sunbird release will be 1.0 beta1.

You can get it by installing thunderbird 3 and [Lightning](http://www.mozilla.org/projects/calendar/) addon.

[calendar blog](http://weblogs.mozillazine.org/calendar/) shows up to date info and why they got rid of new sunbird releases.

---

### Post by 23meg on 2010-04-28
[QUOTE=andrewabc]Argh they don't have it. Reason is probably because debian no longer has it.[/QUOTE]

The reason is documented in [bug #571134]("https://bugs.launchpad.net/ubuntu/+source/lightning-sunbird/+bug/571134").

---

### Post by andrewabc on 2010-04-28
> **23meg said:**
> The reason is documented in [bug #571134]("https://bugs.launchpad.net/ubuntu/+source/lightning-sunbird/+bug/571134").

I read the bug report and are a bit confused (since they say *lightning-sunbird doesn't work with the current thunderbird version*.

sunbird is gone (not sure how it doesn't work with thunderbird since it never relied on it).
But lightning extension will work with thunderbird 3.x correct?

---

### Post by x-shaney-x on 2010-04-28
Hmm, strange thing is, I am preparing to move over to evolution's calendar because I was concerned something like this might happen.

I figured thunderbird's popularity would mean lightning would supersede and obsolete sunbird.
But despite thunderbird's popularity, I do not want something as important as my calender stuff to rely on an extension which could also be discontinued at any time.

Problem is getting all the sunbird stuff into evolution...

---

### Post by 23meg on 2010-04-28
> **andrewabc said:**
> I read the bug report and are a bit confused (since they say *lightning-sunbird doesn't work with the current thunderbird version*.

sunbird is gone (not sure how it doesn't work with thunderbird since it never relied on it).

*lightning-sunbird* is the source package that provides the binary packages for both the *lightning-extension* and *sunbird* packages. Since bugs are tracked per source package in Launchpad, the bug is against *lightning-sunbird*.

[QUOTE=andrewabc]But lightning extension will work with thunderbird 3.x correct?[/QUOTE]

When you install it from addons.mozilla.org, yes.

---

### Post by chrisccoulson on 2010-04-28
> **andrewabc said:**
> I read the bug report and are a bit confused (since they say *lightning-sunbird doesn't work with the current thunderbird version*.

sunbird is gone (not sure how it doesn't work with thunderbird since it never relied on it).
But lightning extension will work with thunderbird 3.x correct?

No, both the lightning extension and sunbird are built from the same source package. The version of lightning in the archive was too old for our current version of thunderbird, and sunbird is no longer supported upstream. As I said in the bug report, at some point we will build just the lightning extension from the lightning-sunbird source, but that requires some packaging changes that we just didn't have time to finish in time for release

---

### Post by x-shaney-x on 2010-04-28
Well I installed sunbird from the karmic repos, works fine for now.
I can't for the life of me figure out how to import the calendars into evolution though.
Is there an easy way?

<EDIT>
Hehe, actually it was easy.  So looks like I'm switched to evolution for now.  Never got along with it but it seems the best option now.

---

### Post by andrewabc on 2010-04-28
> **x-shaney-x said:**
> Well I installed sunbird from the karmic repos, works fine for now.
I can't for the life of me figure out how to import the calendars into evolution though.
Is there an easy way?

<EDIT>
Hehe, actually it was easy.  So looks like I'm switched to evolution for now.  Never got along with it but it seems the best option now.

Hmm, looks like I'll have to look into evolution. I just input fake email address info to see what it looks like in ubuntu 9.10.

Not bad looking.

---

