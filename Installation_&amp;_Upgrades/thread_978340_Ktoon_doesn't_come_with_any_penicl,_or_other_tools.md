---
title: "Ktoon doesn't come with any penicl, or other tools?"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by CastilleV on 2008-11-11
Um, just curios but when I install it, it has no tools like that in it.
No pencil tool.
No brushes.
What the hell man?

---

### Post by Bondy_uk on 2009-03-28
Took me a while to work out what was going on and when I was searching forums it didn't seem like a lot of people came up with an answer / a lot of the time nobody answered to this specific problem.

But I finally found out why...

The directory is /usr/share/ktoon, however, there is a plugins directory in /usr/lib/ktoon/plugins/
Basically KToon needs this directory, but its looking for the plugins in /usr/share/ktoon instead!

So the simple fix is to create whats called a 'symbolic link' which is basically a system link file in the /usr/share/ktoon directory that tells the system when looking in one directory to also look in another (which allows a program to access files the second directory as if they are located in the first).

To do that, simply open up the terminal and type: 

sudo ln -s /usr/lib/ktoon/plugins/ /usr/share/ktoon/
and enter your password.

Then open KToon and the tools are there 8-)

I hope this helps anyone having trouble with KToon!

---

### Post by BCtom on 2009-07-06
> **Bondy_uk said:**
> Took me a while to work out what was going on and when I was searching forums it didn't seem like a lot of people came up with an answer / a lot of the time nobody answered to this specific problem. ...

To do that, simply open up the terminal and type: 

sudo ln -s /usr/lib/ktoon/plugins/ /usr/share/ktoon/
and enter your password.

Then open KToon and the tools are there 8-)

I hope this helps anyone having trouble with KToon!

Bondy_uk, Thank you. I would have spent hours working on this. I thank you very much for posting this very nice fix. Tools are nice for drawing cartoons with.

Tom. :p

---

### Post by Bondy_uk on 2009-07-06
No problem mate ;)

I can only assume its a bug in the program... they made it look in the wrong directory! lol

---

### Post by varunendra on 2010-04-30
> **Bondy_uk said:**
> Took me a while to work out what was going on and when I was searching forums it didn't seem like a lot of people came up with an answer / a lot of the time nobody answered to this specific problem.

But I finally found out why...

The directory is /usr/share/ktoon, however, there is a plugins directory in /usr/lib/ktoon/plugins/
Basically KToon needs this directory, but its looking for the plugins in /usr/share/ktoon instead!

So the simple fix is to create whats called a 'symbolic link' which is basically a system link file in the /usr/share/ktoon directory that tells the system when looking in one directory to also look in another (which allows a program to access files the second directory as if they are located in the first).

To do that, simply open up the terminal and type: 

sudo ln -s /usr/lib/ktoon/plugins/ /usr/share/ktoon/
and enter your password.

Then open KToon and the tools are there 8-)

I hope this helps anyone having trouble with KToon!
Thanx man ! I searched about half an hour on google with keywords "ktoon tutorial" in hope of getting some hint on this. It didn't come up with anything real. Then I tried keyword "ktoon guide" & got a link to this thread.
Their official "tips  page"> [http://ktoon.toonka.com/documentation/index.php?title=Tips](http://ktoon.toonka.com/documentation/index.php?title=Tips)also  returns "Not Found" error.
You just saved me from removing ktoon & wasting time in search of some other alternate.
Thanx again

---

### Post by Bondy_uk on 2010-05-04
No problem mate.

Linux/Ubuntu is full of quirky little things like that to keep you on your toes! lol

---

### Post by GrindStreet on 2010-06-28
Well, I put the code into the terminal, and nothing. KToon still does not do anything for me. Can't get it to do one single thing. No pens, no tools. When I click "Import bitmap" it does nothing. Drag the cursor around and nothing shows up. I really want to use this to work on a short cartoon for my girlfriend.

And, when I click for help, the help does not work either. All I get are two texts that say "How to draw?" and "How to animate?". 

I feel like the software is making fun of me, and it is dumb frustrating... Should I give up on this and try learning something different??

---

### Post by varunendra on 2010-06-28
post here exactly what you type in the terminal.

(mind that in 'ln', it is "small L" not "capital I")


_**PS:**_ By the way, have you crosschecked that these two directories do exist in their respective places? (**/usr/lib/ktoon/plugins** and **/usr/share/ktoon**)

---

