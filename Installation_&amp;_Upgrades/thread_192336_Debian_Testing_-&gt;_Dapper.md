---
title: "Debian Testing -&gt; Dapper"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by Mauvaisours on 2006-06-08
I have a server, debian testing based, running apache2 + mysql + bind9
I plan to upgrade it to DapperDrake.
Is there anything I should pay special attention to (beyond personal data backup) ?
Will just editing sources.list / apt-get update / apt-get dist-upgrade do the trick ?

---

### Post by pyromithrandir on 2006-06-08
That sounds like a pretty dangerous idea. There's a chance it could work, but I would be really surprised. While Ubuntu is based on Debian, an they have the same package manager, they're still different distros, and there are quite a few changes under the hood. 

Maybe someone will come along and tell you some more details about what might break, and what could go wrong, or about how it might work, but for now, I'm posting to say that it's probably not such a great idea.

---

### Post by matthew on 2006-06-08
I have done this...a while back going from Debian Sarge (when it was testing) to Ubuntu Breezy when it was where Dapper is now. The big thing you may have trouble with are your x server (I can't remember, does Etch use Xorg or is it still XFree86 like Sarge?)...wait, I just noticed you are doing this on a server. You ***should*** be fine...no guarantees, though so like you said, backup your data and make sure the backup worked in case you need to do a fresh install.

Then, just change your sources.list to the base Ubuntu Dapper repos (I recommend doing this without the universe and multiverse repos at first...always seems to work better for me to do the upgrade without them, then add them in and upgrade again...I don't know why.) and do an apt-get update then an apt-get dist-upgrade.

My advice, if that isn't painfully clear and easy sounding to you, don't do it. Do a fresh install (that was mainly for others reading this thread later, you seem to know what you're talking about and are just asking about expreiences).

EDIT: Oh, anyone asking a question like this is probably like me and thinks minor breakage once in a while is fun because it gives you a chance to learn something new...if that's not you, take the first responder's advice. :)

---

### Post by metoo on 2006-06-09
What's the package state of Testing?
I once tried it with sid/unstable and breezy. Too bad that many versions in sid where newer than the once in breezy.
It was a pita because the newer packages where not properly updated.
So that's something you should look at. Development for drapper took a long time ...
But probably Testing isn't too up to date either? :-)

---

### Post by Mauvaisours on 2006-06-09
Thanks all, especially matthew.
You were right, I don't mind the breakage, just wanted to know if I better keep some coffee around and an install DVD too (seems so).
I will backup everything tonight and start upgrading tomorrow (reminds me I need a fresh HD, so backup will be tomorrow). I'll post results when it's done.

Re state of testing : quite up to date actually. Xserver moved to xorg when I did my last dist-upgrade. 

And you are right : KIDS DON'T DO THIS AT HOME ! PEOPLE DOING THIS ARE HIGHLY TRAINED PROFESSIONALS :D

---

### Post by matthew on 2006-06-09
When you finish, let us know how it goes. Good luck and have fun!

---

### Post by Mauvaisours on 2006-06-19
So, after a bit of fiddling, I reinstalled from CD. The problem being that libc6 in testing is more recent than in dapper (well, not really, but version numbers are misleading apt/dpkg).

---

