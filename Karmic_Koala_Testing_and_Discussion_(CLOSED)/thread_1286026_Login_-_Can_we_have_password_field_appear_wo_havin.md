---
title: "Login - Can we have password field appear w/o having to hit &quot;Return&quot;?"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-08
On a single user login, one has to hit "Return" to get the Password Field.  I know it's trivial, but why is this?

---

### Post by meborc on 2009-10-08
the point is that if you have 5+ users on the machine, then you shouldn't have as many password fields... when a username is selected, the password field appears...

of course we could have the password field there all the time, but the user must still be selected

---

### Post by TrueJournals on 2009-10-08
Yes, but that's not the situation given.  I also use Ubuntu on a machine where I'm the only user.  I still want to have to enter my password to login, but it's a bit of a detour to have to hit Enter every time the computer boots up in order to actually select the only user.

---

### Post by emarkay on 2009-10-08
> **TrueJournals said:**
> Yes, but that's not the situation given.  I also use Ubuntu on a machine where I'm the only user.  I still want to have to enter my password to login, but it's a bit of a detour to have to hit Enter every time the computer boots up in order to actually select the only user.

Correct.  That's how Jaunty did it, and I am sure that the programmers are able to tell if there is only "one user, display field on page load"  :)

Bug report filed:
[https://bugs.launchpad.net/ubuntu/+bug/446783](https://bugs.launchpad.net/ubuntu/+bug/446783)

---

### Post by Zorael on 2009-10-08
No gdm.conf file you can tinker with?

From kdmrc;
```
# Specify, if/which user should be preselected for log in.
# "None" - do not preselect any user
# "Previous" - the user which successfully logged in last time
# "Default" - the user specified in the DefaultUser option
# Default is None
#PreselectUser=Previous
# If this is true, the password input line is focused automatically if
# a user is preselected.
# Default is false
#FocusPasswd=true

...

# Greeter config for 1st local display
[X-:0-Greeter]
# See above
#PreselectUser=Default
# The user to preselect if PreselectUser=Default.
# Default is ""
#DefaultUser=johndoe
```

---

### Post by narcus on 2009-10-20
In what way was this [solved]? I too really miss the 9.04 behaviour. I'm so used to just type the password right away, now I'm typing my password for anyone next to me to see because it goes into the username field in clear text instead.

I saw your Bug 447615 was marked invalid. I think it should be a candidate for One Hundred Papercuts instead.

---

### Post by cyberkilla on 2009-10-21
> **narcus said:**
> In what way was this [solved]? I too really miss the 9.04 behaviour. I'm so used to just type the password right away, now I'm typing my password for anyone next to me to see because it goes into the username field in clear text instead.

I saw your Bug 447615 was marked invalid. I think it should be a candidate for One Hundred Papercuts instead.

I keep doing that too:P

I agree, it's quite annoying - but then, the whole situation is annoying. There are almost no configuration options at all. 

You can't customise it very much, even with gconf trickery. The defaults are a bit unwieldy and serve to add a few extra steps to every login procedure.

---

### Post by mrboojive on 2009-10-27
I think this is a serious bug. Pressing enter every time is extremely annoying.

---

