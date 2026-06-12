---
title: "How do I prevent upgrades?"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by dtlinker on 2006-06-27
I have found that the latest version of wine doesn't seem to work, at least for me, so I installed 0.9.3.

Now, I constantly have the indicator on the menu bar saying that there is an update available. It is wine. I uncheck the box, and close the window, but it keeps coming back!

I edited /etc/apt and commented out the line:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

but it still comes back!

What can I do to keep it away?

---

### Post by rcarring on 2006-06-27
You need to remove it from the repository list in synaptic. If you use adept I can't advise as i don't have kubuntu installed anywhere.

---

