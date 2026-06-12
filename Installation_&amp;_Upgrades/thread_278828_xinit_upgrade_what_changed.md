---
title: "xinit upgrade: what changed?"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2006-10-16
It seems a xinit upgrade is available for Dapper but, as usual, the changelog isn't uploaded to the server (bug filed for ubuntu general, no news; will file bug for xinit now). 

does anyone know what changed/ why they updated it? 

thanks :)

ps. bug filed: [https://launchpad.net/distros/ubuntu/+source/xinit/+bug/66504](https://launchpad.net/distros/ubuntu/+source/xinit/+bug/66504)

---

### Post by wiggum26 on 2006-10-17
Whatever it did has pooched X on my machine and a friends machine. He trotted up to me this morning saying he'd written off his machine and he had no idea how he did it. I laughed at him and an apt-get upgrade pooched mine at lunch time (then he laughed at me).

His problem is that gnome logs him out when he logs in.
My problem is that it busted my screen/desktop settings. My monitor complains about an unsupported mode.

Both happened directly from the xinit update.

---

### Post by towsonu2003 on 2006-10-17
I'd file a bug report for xinit and open a support request for it as well. for both, see launchpad.net

---

### Post by Stephen Howard on 2006-10-17
Hmmm, think I'll wait and see some more feedback before upgrading...

Thinking of the turmoil the last time X was upgraded, and I don't want to go through that again.

---

### Post by The Pinny Parlour on 2006-10-17
I have mixed feeling about this thread.  If this update is hosing machines, I will be bitterly dissapointed that ANOTHER DODGEY update has managed to slip through.  If I'm wrong, disregard everything I said.

Having said all that, I too, and going to wait till I see what others experience.

---

### Post by wiggum26 on 2006-10-17
It was definately the update.

I did a "dpkg-reconfigure xserver-xorg" and all was well again.

---

### Post by wiggum26 on 2006-10-17
I did a diff on the xorg.conf's from before and after the reconfigure. It's odd, there's nothing really that stands out as something that would be causing a problem.

---

### Post by MKR. on 2006-10-17
> **wiggum26 said:**
> I did a diff on the xorg.conf's from before and after the reconfigure. It's odd, there's nothing really that stands out as something that would be causing a problem.

Then maybe the users experiencing problems had something custom in their config (proprietary display driver settings, maybe?) that were not preserved in the update.

---

### Post by towsonu2003 on 2006-10-17
just an update on the issue: the changelog is now available.

---

### Post by paradj on 2006-10-17
you mean this?
 [found here]("http://www.ubuntu.com/usn/usn-364-1")

> 
=========================================================== 
Ubuntu Security Notice USN-364-1           October 16, 2006
xinit vulnerability
CVE-2006-5214
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 5.10
Ubuntu 6.06 LTS

This advisory also applies to the corresponding versions of
Kubuntu, Edubuntu, and Xubuntu.

The problem can be corrected by upgrading your system to the
following package versions:

Ubuntu 5.10:
  xinit                                    1.0+0.99.1-4ubuntu0.1

Ubuntu 6.06 LTS:
  xinit                                    1.0.1-0ubuntu3.1

After a standard system upgrade you need to restart your session to
effect the necessary changes.

Details follow:

A race condition existed that would allow other local users to see error 
messages generated during another user's X session.  This could allow 
potentially sensitive information to be leaked.




how hard could it be to place this in the changes text of the update "before" its made available?
:-k 



:mrgreen: ...just 'cause i'm paranoid, doesn't mean they're NOT out to get me...:mrgreen:

---

### Post by BackInTimeMan on 2006-10-17
Where will I find the changelog?

---

### Post by BackInTimeMan on 2006-10-17
OK, I see it now in paradj's post. I would still like to know where it is published though.

---

### Post by towsonu2003 on 2006-10-17
nope, this one: [http://changelogs.ubuntu.com/changelogs/pool/main/x/xinit/xinit_1.0.1-0ubuntu3.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/x/xinit/xinit_1.0.1-0ubuntu3.1/changelog) :) but thanks

paradj's post is published here [http://www.ubuntu.com/usn/usn-364-1](http://www.ubuntu.com/usn/usn-364-1) and distributed thru this emil list: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce) -also accessible thru [www.ubuntu.com](www.ubuntu.com) > click on "Security Notices" on the right side. 

ps. to find the changelog, open synaptic,select a package, and do Package -> Download Changelog from the menu. Changelog is also accessible using update-notifier (the little star on the upper right corner of your screen when there is an update available). 

pss. of course, to access the changelog, te changelog itself should be uploaded to the servers ;)

---

### Post by BackInTimeMan on 2006-10-17
Ah thanks for the links and tips, I missed the link in paradj's post. There is no changlog visible in my update-notifier though.

---

### Post by paradj on 2006-10-17
yes, it would be nice to those us who like the "warm~n~fuzzy" feeling of being informed as to what is "Really" goin on... :D

---

### Post by towsonu2003 on 2006-10-17
> **BackInTimeMan said:**
> Ah thanks for the links and tips, I missed the link in paradj's post. There is no changlog visible in my update-notifier though.

try sudo apt-get update
and check it out again when the star comes back... 

if it doesn't can you attach a screenshot? I wonder why you're not seeing a changelog even though it's now uploaded.

---

### Post by BackInTimeMan on 2006-10-17
Did the update but still nothing in Changes.

Not quite "warm~n~fuzzy" yet paradj  :)

Here's the screenshot.

---

### Post by towsonu2003 on 2006-10-17
> **BackInTimeMan said:**
> Did the update but still nothing in Changes.

Not quite "warm~n~fuzzy" yet paradj  :)

Here's the screenshot.

what happens when you click on the "Check" button on that screenshot? I wish I didn't upgrade so I could help you / confirm your issue...

---

### Post by BackInTimeMan on 2006-10-17
It still doesn't show a changlog. No matter, maybe it will show after I've next logged out/in my session.

---

### Post by paradj on 2006-10-18
i single-right-click 'ed on the update "star" and chose one of the options there.
....wish i could remember which choice tho...
:-k


[posted a similar note here]("http://www.ubuntuforums.org/showthread.php?p=1523633#post1523633")

---

### Post by beerorkid on 2006-10-18
BTW mine worked fine.  I was worried and found another [thread](http://ubuntuforums.org/showthread.php?t=279188) which told me how to revert to the orig package.

well seeing how there was not a major uproar I figured what the heck.  Had no issues.  Using beryl BTW.

---

### Post by neymac on 2006-10-18
> **beerorkid said:**
> BTW mine worked fine.  I was worried and found another [thread](http://ubuntuforums.org/showthread.php?t=279188) which told me how to revert to the orig package.

well seeing how there was not a major uproar I figured what the heck.  Had no issues.  Using beryl BTW.

+1
no problem
using Beryl

---

