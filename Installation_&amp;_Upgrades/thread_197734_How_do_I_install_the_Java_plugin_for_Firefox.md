---
title: "How do I install the Java plugin for Firefox?"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2006-06-16
I am trying to play "Go" on the following web site:

  [http://kgs.kiseido.com/en_US/applet.jsp]("http://kgs.kiseido.com/en_US/applet.jsp")

But, instead, I get an empy box that says "Click here to download plugin".

I clicked it, but then it says that the Java plugin is not available.

How do I install the Java plugin for Firefox?

Thanks!
Alex

P.S. I am running Ubuntu 6.06

---

### Post by frodon on 2006-06-16
The answer is there : [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) 
(link at the bottom of this wiki page)

---

### Post by l4v4_f10w on 2006-06-16
im sure this shud get u on ur way.
[https://wiki.ubuntu.com/Java?action=show&redirect=Java15](https://wiki.ubuntu.com/Java?action=show&redirect=Java15)

---

### Post by xp_newbie on 2006-06-16
Well... in the referenced page it says:

> [SIZE="3"]**Installing Java**[/SIZE]
[SIZE="2"]Ubuntu 6.06[/SIZE]

*   Sun Java5: Install it from the Applications -> Add/Remove... menu, or install the sun-java5-bin package.


I invoked Applications -> Add/Remove, but there is no mention of any java package.

I tried Synaptic as well and sun-java5-bin is nowhere to be found.

How do I find this package?

Thanks!
Alex

---

### Post by xp_newbie on 2006-06-16
[QUOTE=xp_newbie]I tried Synaptic as well and sun-java5-bin is nowhere to be found.

How do I find this package?
[/QUOTE]

OK - solved the problem.

All I had to do in Synaptic was to 

 > Settings > Repositories > 
    > Select Ubuntu 6.06 LTS (Binary) > Edit > check "Non-free (Multiverse)"
 > Reload

And then sun-java5-plugin was available.

BTW, why isn't sun-java5-plugin considered free? From the end user license it seems that I can re-install and/or redistribute it as many time as I wish.

Or have I misunderstood it?

---

