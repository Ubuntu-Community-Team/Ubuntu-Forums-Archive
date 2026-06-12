---
title: "Feisty"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by quentinludwig on 2007-04-09
I hope this doesn't sound like a dumb question but how do I upgrade to feisty and keep all my upgrades that I have?  Is there a way to do that?

---

### Post by WiseElben on 2007-04-10
Once Feisty comes out of the Beta stage, Ubuntu will automatically download the upgrades for you through the usual update notifications. If you want to do it now (manually), edit your /etc/apt/sources.list and change everything from "edgy" to "feisty."

```

$ cd /etc/apt/
$ sudo cp sources.list sources.list.backup
$ gksudo gedit sources.list

```

Replace the string "edgy" with "feisty" and save. Then:

```

$ sudo apt-get update
$ sudo apt-get dist-upgrade

```

---

### Post by old_geekster on 2007-04-10
> **quentinludwig said:**
> I hope this doesn't sound like a dumb question but how do I upgrade to feisty and keep all my upgrades that I have?  Is there a way to do that?
The only version of Ubuntu that you can upgrade to Feisty is Edgy.   You won't actually be able to keep your updates because Feisty is a separate OS.  

So far I have received approximately 150 updates since upgrading to Feisty.

Here is a link to help you upgrade:

[http://www.howtogeek.com/howto/ubuntu/upgrade-ubuntu-edgy-to-feisty/](http://www.howtogeek.com/howto/ubuntu/upgrade-ubuntu-edgy-to-feisty/)

---

### Post by jetpeach on 2007-04-10
old_geekster may have jumped to conclusions when saying you can't keep your upgrades - it depends what "upgrades" you are talking about? do you mean program upgrades or application data for you programs, config files, or manually installed updates for specific programs? i guess the term updates is just a bit ambiguous to me in the context you've used it, if you clarify we might be able to make it more clear what is lost/kept during a dist-upgrade.

---

