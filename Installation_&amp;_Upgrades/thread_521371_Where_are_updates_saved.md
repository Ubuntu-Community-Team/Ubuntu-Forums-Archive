---
title: "Where are updates saved?"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by xlinuks on 2007-08-09
Hi,
I have the standard Ubuntu 7.04 install CD. After I install it on some computer I have to download about 200 MB of new updates!! Is there a specific location where Ubuntu saves the downloaded updates (files) so I can copy them to a new CD and apply them later I install Ubuntu on another computer?

---

### Post by Irony on 2007-08-09
[PHP]/var/cache/apt/archives[/PHP]

Note the command to clear the archive is;

[PHP]sudo apt-get clean[/PHP]

---

### Post by mdebusk on 2007-08-09
> **xlinuks said:**
> Is there a specific location where Ubuntu saves the downloaded updates (files) so I can copy them to a new CD and apply them later I install Ubuntu on another computer?

Their location has already been mentioned, as was the command to clear the archive. I'll add that you'll probably want to use the following to purge the archive of anything you no longer need:

```

sudo apt-get autoclean

```

You'll also want to consider the aptoncd package. This answers your second request.

---

### Post by xlinuks on 2007-08-09
I'm impressed that there's such a user-friendly and smart app like aptoncd.
It actually did everything I expected and it was easier than I thought... another case when Ubuntu is smarter than windows
thanks to both of you!

---

