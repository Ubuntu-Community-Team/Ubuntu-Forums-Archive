---
title: "GMT setup - dpkg-reconfigure tzdata - Awkward behavior"
date: 2015-10-08
forum: Installation &amp; Upgrades
---

### Post by Wagner_Alves on 2015-10-08
Hi everyone,

I would like to update my Ubuntu 14 GMT, so I did the following steps:

1-
```

sudo dpkg-reconfigure tzdata

```

2- Chose my preferable GMT (in my case GMT-3 (Brazil/Sao Paulo) )
--

What I've noticed is that GMT-3 is actually adding up 3 hours in the GMT time! My date/time is now GMT plus 3 hours (totally wrong)!

I know that, to make it works, I have to setup GMT+3 in that old blue screen, but** I would like to understand why** the SO behaves that way.

See attached print screens that I've captured. 

PS: I'm using GMT setup instead of time zones due daylight savings issues that I have to deal with.

Thank you,

Wagner Alves

[ATTACH=CONFIG]264855[/ATTACH][ATTACH=CONFIG]264856[/ATTACH][ATTACH=CONFIG]264854[/ATTACH][ATTACH=CONFIG]264853[/ATTACH]

---

### Post by ian-weisser on 2015-10-10
> In order to conform with the POSIX style, those zone names beginning with "Etc/GMT" have their sign reversed from what most people expect[SUP]**[/SUP].  In this style, zones west of GMT have a positive sign and those east  have a negative sign in their name (e.g "Etc/GMT-14" is 14 hours  ahead/east of GMT.)

Source: [https://en.wikipedia.org/wiki/Tz_database](https://en.wikipedia.org/wiki/Tz_database)

---

