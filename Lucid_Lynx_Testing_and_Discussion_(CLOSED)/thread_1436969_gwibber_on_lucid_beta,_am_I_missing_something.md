---
title: "gwibber on lucid beta, am I missing something ?"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by techno-mole on 2010-03-23
Hello, me again.

I was trying to use the social features of lucid, I have a twitter account and thought I would attempt to use gwibber for sending tweets etc, however nothing is happening.

I have entered the account details, but gwibber isnt retrieving the tweets, and nothing happens when I send a tweet with it either ? am I meant to do something else ? or is it not actually working yet ?

cheers

---

### Post by descendent87 on 2010-03-23
Been working fine for me posting to twitter, identi.ca and facebook. Maybe try starting from the terminal and see if there's any errors?

---

### Post by Uncle Spellbinder on 2010-03-23
Same here. Gwibbler doesn't do anything. Credentials added for twitter and facebook and nothing happens. No error messages.

---

### Post by VMC on 2010-03-23
Same here. Try to add my Facebook account and got nowhere.

---

### Post by zekopeko on 2010-03-23
Perhaps one of you gentelmen/ladies could either find the bug or report it and link it back here?

---

### Post by techno-mole on 2010-03-24
I logged a bug report on launchpad, as yet I have had no feed back, I have read that the twitter problem might be down to certificates or something.
[bug report]("https://bugs.launchpad.net/gwibber/+bug/545235")

cheers

---

### Post by Whitby on 2010-03-25
This wasn't working for me either, for both Twitter and Identica.  I just got no messages at all, as reported by others here.  

Tried it again last night, and it now seems to be working.  I didn't change anything, and hadn't applied any updates, so I don't know what changed.  If it fails again, I'll post back here.

---

### Post by techno-mole on 2010-03-25
gwibber still isn't working for me, it still won't show the time line for twitter of allow me to post messages, I have applied a few updates to gwibber over the last few days, but still no joy.

---

### Post by Wiebelhaus on 2010-03-25
It's been working fine here , let me see if I can't find something for out something for you. Sorry about this.

---

### Post by jjcv on 2010-03-25
Qwibber has not worked for me for the last few weeks.  Client kept crashing

I removed the following two directories and bingo... it works.

.gconf/apps/gwibber
.cache/gwibber

---

### Post by Whitby on 2010-03-26
Further to my post above, it isn't working again.  

Last night, I did get a group of posts from Twitter and Identica appearing in Gwibber, but now those are still the only ones displayed.  I've tried refreshing many times, left it running for some time to see what happened, and deleted and re-added the accounts.  None of this worked - I don't get anything new.

The app doesn't crash or anything, it just isn't getting any updates from the accounts it is subscribed to.

---

### Post by godhika on 2010-03-26
Just a stupid idea, but maybe the options recieve and send messages is disabled in the accounts setup?Go in the Me menu to broadcast accounts and the to advanced settings.

---

### Post by Whitby on 2010-03-26
The receive and send options are definitely turned on for both Twitter and Identica.  I checked them each time, and they are on by default anyway.

As a further update, I did get some messages through from both accounts just after I posted last time, so I then left Lucid and gwibber running all night to see if anything else turned up.  The accounts are set to automatically update each 15 minutes.  Nothing more appeared, even though I know there were many messages to receive during that time.  Updating manually in the morning also did not get anything.

Gwibber seems to update sometimes, and then do nothing for hours and hours.  I can't find any pattern to what is happening, which is probably going to make this difficult to fix.  Don't you hate intermittent faults!!!

---

### Post by techno-mole on 2010-03-27
I have tried various things, but gwibber still won't do anything, I did get it to receive some messages, but they are from 20 days ago ? but thats as far as its got, it doesnt do anything when I select refresh, Ive tried removing it and re-installing, Ive tried the ppa version from launchpad, this just crashes when I try and add an account.

I guess they will fix it before the rc is due out ?

---

### Post by Whitby on 2010-03-27
Hi techno-mole,

It sounds like your experience is exactly the same as mine.  I had a look at the bug on launchpad, and when I run gwibber from a terminal I get exactly the same output as listed there (Updating.... but nothing happens).

I'm surprised this isn't affecting more people - I added myself as being also affected by the bug, but there are only 2 people affected so far.  This isn't going to sound warning bells with the developers, I imagine.

Maybe the fact there is a new ppa version gives hope this will get fixed?

---

### Post by zeroseven0183 on 2010-03-28
> **Whitby said:**
> I'm surprised this isn't affecting more people - I added myself as being also affected by the bug, but there are only 2 people affected so far.  This isn't going to sound warning bells with the developers, I imagine.

I'm also having the same problem and confirmed it in Launchpad. Other people, perhaps, tend to not to report the problem and "ignore the crash next time" instead.

[ Having problems with Gwibber? Check if it's a bug at [https://bugs.launchpad.net/gwibber](https://bugs.launchpad.net/gwibber) ] :-)

---

### Post by kwaanens on 2010-04-10
Same problem here. This *needs* to be fixed, if Gwibber is supposed to be so tightly integrated into Lucid.
No feeds received (ever on Lucid), not able to post to either Twitter or Identi.ca, not able to add FB account.

---

