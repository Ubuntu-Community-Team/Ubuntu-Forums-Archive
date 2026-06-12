---
title: "Apache uninstalled but ti's still there"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by TheChaos0 on 2011-08-04
So, I needed to get rid of apache2 on my Ubuntu. apt-get remove apache2

All looked successful but... ps aux... Oh look it's still running. No matter, I thought, maybe I'll just restart (restart on Linux!? I must be mad!) and it'll just disappear. Nope, it still starts up like it always has.

I could of course just manually remove it.... but it feels so untidy.

Any ideas?

---

### Post by dinu90 on 2011-08-04
Hi,

Try purging the package:
apt-get purge apache2

I hope that helps

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

