---
title: "Evolution not importing all e-mail - tried but not working"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by thikrat on 2008-04-30
Hi,

I recently bought a new laptop and installed Hardy on it last week.  My old laptop was running Hardy Development build, so I applied all the upgrades via update manager to bring it up to speed.  I was basically able to move everything over (Tomboy notes, Pidgin, thunderbird) and I left evolution for last.  

I went into Evolution itself on my old laptop and did the whole backup procedure, everything seemed to work fine, no errors.  I then copied this file over to my new laptop, imported and it said everything was good.  It appeared my accounts were all in order, etc etc.  Then I went in and tried viewing my inbox for my exchange account.  It doesn't say there isn't any mail, in fact it says there is new mail, but the window that displays all the e-mails is blank!  I thought that was weird, so I tried going to another folder in exchange and the e-mails show up.  Another folder, they don't.  I don't have filters or search queries on, that I can see.

So i went into my archived offline mail and all of that seems to show up fine.  I worked on this for two days, no dice.  So I decided to copy (via rsync) the entire .evolution directory from my old laptop to the new laptop (i backed up .evoluton on my new laptop) and let it ride.  Same thing happened.  Any ideas on this one?  very weird...

Thanks

---

### Post by thikrat on 2008-05-06
anyone have any ideas on this one?

bump!

---

### Post by thikrat on 2008-05-06
Well, it seems i found a semi-fix... and it is an Evolution bug...

[https://answers.launchpad.net/ubuntu/+source/evolution/+question/16787](https://answers.launchpad.net/ubuntu/+source/evolution/+question/16787)

It worked for me, just tried it and all seems to be fine.

---

