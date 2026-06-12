---
title: "java not working"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by 12katia34 on 2012-05-13
dear all,
I have now tried several times to download Java for either vpn connections or use of digital photoprinting software and other things, I have gone over the links from the official java homepage, the ubuntu wiki page and different online terminal codes, ...

but it seems there still is no working java applet on my computer, i cannot activate java in my browser and don't know if there is any java installed after all or not.

Q1: How do I delete old Java versions from my computer?

Q2: How can I know what version of ubuntu my computer is currently running?

Q3: What "type" of Java do I (ordinary user with no IT-knowledge whatsoever) need for my daily business and

Q4: How do I activate it in my browser?

THANK YOU!
Kate.

---

### Post by spcwingo on 2012-05-13
> **12katia34 said:**
> Q1: How do I delete old Java versions from my computer?

That according to how you installed the other versions.

> **12katia34 said:**
> Q2: How can I know what version of ubuntu my computer is currently running?

In a terminal run:
```
lsb_release -a
```

> **12katia34 said:**
> Q3: What "type" of Java do I (ordinary user with no IT-knowledge whatsoever) need for my daily business?

That is according to what, exactly, your needs are.

> **12katia34 said:**
> Q4: How do I activate it in my browser?

There should be no activation whatsoever...just install.  Here is the way that I install Java:

In a terminal run this command (after removing previously installed versions)

```
sudo add-apt-repository ppa:webupd8team/java && sudo apt-get update && sudo apt-get install oracle-java7-installer
```

---

