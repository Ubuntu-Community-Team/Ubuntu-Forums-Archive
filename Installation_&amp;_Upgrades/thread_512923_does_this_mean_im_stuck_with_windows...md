---
title: "does this mean im stuck with windows?.."
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by Likenota on 2007-07-29
i just installed compiz-fusion and it freezes everytime i type in password and username what do i to make the default theme beryl ?  through the console? please give me more then one command to try because it takes forever to get another response after the first. im tired of booting in windows... i miss ubuntu.  thanks.

---

### Post by kelly.seay on 2007-07-30
I don't know about the freezing part, but if you want to start compiz-fusion when you login in, this is what I did:

Go to System, Preferences, Session.
Add a new start-up program, call it whatever you want
for the command use this:

compiz --replace -c emerald & (if you have emerald)
compiz --replace (if you do not have emerald)

for beryl, do the same thing except for the command, just put beryl

---

### Post by Likenota on 2007-07-30
umm i cant even boot up... anyways the funny thing is i used the command to remove compiz fusion...




i used these commands

```

sudo apt-get autoremove compiz*

sudo apt-get install ubuntu-desktop
```



and guess what... i ended up being able to boot in ubuntu and logged in and this is the great part it ended up giving me the compiz fusion!!! :). how wierd is that?! compiz is amazing people. it really is.

note i had to do the compiz -- replace stuff i believe..

---

### Post by HarshReality on 2007-07-30
So do I misunderstand or were you willing to scrap the whole of it because you couldnt run CF?

---

### Post by Likenota on 2007-07-30
yes i was trying to remove the compiz fusion completely because it wasnt allowing me to even boot how lame is that. i had vmware files setup and everything i didnt wanna restart my ubuntu..

---

