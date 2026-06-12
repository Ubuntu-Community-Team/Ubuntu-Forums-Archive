---
title: "dpkg-deb error on routine system update"
date: 2016-04-01
forum: Installation &amp; Upgrades
---

### Post by Kestreln8144 on 2016-04-01
I have 14.04 Trusty.

While running a routine *sudo apt-get update && sudo apt-get dist-upgrade*, I ran into this error:

```
Unpacking libefl (201603312131-31982~ubuntu14.04.1) over (201603242131-31876~ubuntu14.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libefl_201603312131-31982~ubuntu14.04.1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libelementary.so.1.17.99', which is also in package libelementary 201603242216-12490~ubuntu14.04.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libefl_201603312131-31982~ubuntu14.04.1_amd64.deb

```

Running *sudo apt-get -f install* gives the same error.

What might've caused this?

---

### Post by Kestreln8144 on 2016-04-01
I've fixed it.

I have elementary libs installed because I use Terminology. I don't know how this problem occurred, but here is what I did:
[LIST=1]
[*]*sudo dpkg -r libelementary*
[*]*sudo apt-get purge terminology*
[*]*sudo apt-get autoremove*
[*]Restart machine.
[*]*sudo apt-get install terminology*
[/LIST]

And the packages appear to have installed correctly. (And Terminology works.)

---

### Post by RobGoss on 2016-04-01
Glad you got it sorted out would you mind marking this thread as solved? Just view the Thread Toll option at the top right hand side of this post. Thanks so much

---

### Post by Kestreln8144 on 2016-04-01
> **RobGoss said:**
> Glad you got it sorted out would you mind marking this thread as solved? Just view the Thread Toll option at the top right hand side of this post. Thanks so much

I did immediately after posting my solution, and I can see it marked as solved. Is it not showing up for you?

---

### Post by RobGoss on 2016-04-01
Yes it is thank you very much

---

