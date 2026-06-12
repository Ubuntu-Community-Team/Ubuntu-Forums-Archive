---
title: "upgrade from Warthy problems ?"
date: 2005-05-04
forum: Installation &amp; Upgrades
---

### Post by seti@tquadrado.com on 2005-05-04
Hi,
i am about to do a:

sudo apt-get update
sudo apt-get upgrade

Will this install me Hoary ?
What about Evolution ? Will it upgrade it from 2.0.2 to 2.2.2 or will it maintain the older  and add the newer one ?
The same with mysql, ...

Is it safe ? I'd not like to loose things.... <g>

Thanks,
pedro mg

---

### Post by kvidell on 2005-05-04
Only part of your question I can answer is whether or not apt-get upgrade will get you hoary: I don't believe so.
For something that big Iyou have to go ahead and tell it:
apt-get dist-upgrade

As for breaking things? I'm not sure. I'd probably guess it "shouldn't" but I have no idea.

I like taking big risks though, so maybe I'm not the best one to answer that question, I'd probably just go ahead and do it. hah.

That's one question down, sorry I couldn't be of more help.

---

