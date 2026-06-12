---
title: "'True' hybrid-suspend / suspend-to-both / suspend-and-hibernate?"
date: 2020-09-19
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2020-09-19
I have hibernate working, and I can also trigger 'true' hybrid-suspend from the command line or my power menu, but I want to configure Ubuntu 20.04 to hybrid-suspend when idle rather than just suspend or hibernate.

When I say 'true' hyrbrid-suspend I mean 'true' hybrid-sleep, suspend-and-hibernate, suspend-to-both, where my desktop will suspend and hibernate at the same time - if it has power when I turn it back on it will resume from RAM, if not it will resume from disk. There is some confusion around this as hybrid-sleep is sometimes used to refer to suspend-then-hibernate, suspend first and hibernate after a set period of time, and why the former, and my desired setup, is often denoted 'true'.

There are several articles explaining how to do this, like [How to Use Hybrid Suspend in Ubuntu]("http://www.webupd8.org/2012/11/how-to-use-hybrid-suspend-in-ubuntu.html") but that method references a directory that does not exist: ```
/etc/pm/config.d/
```

Similarly, [How do I use pm-suspend-hybrid by default instead of pm-suspend?]("https://askubuntu.com/a/781957/913523") has a section for 18.04 but reports:

> In the hybrid-sleep mode, the hibernate part gets effective only when the battery is critically low and the system shuts down.

Whereas I want it to suspend to both from the beginning. In the same post there is a section for 16.04 which references hybrid-sleep but it has already said that hybrid-sleep but as quoted this hybrid-sleep will only hibernate when the battery is critically low.

How can I set this up please?

---

