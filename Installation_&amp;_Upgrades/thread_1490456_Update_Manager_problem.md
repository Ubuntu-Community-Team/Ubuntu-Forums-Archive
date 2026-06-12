---
title: "Update Manager problem"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by WanderingSnake on 2010-05-22
I've looked around on the forums at issues that other users were having with the update manager, but no one seemed to be having the same problem as I have. Basically, I am able to open update manager just fine, it gets its list of updates, but when I click install, or indeed any other button in the window it freezes before it even prompts me for my password.

Synaptic package manager seems to be having some problems as well. The only way that I can open it is through terminal, otherwise nothing happens when I click on it. I'm also unable to send crash reports, when I click on it, the cursor changes to busy for a few seconds, then nothing happens.

---

### Post by wojox on 2010-05-22
Have you tried running all updates through the terminal?

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by WanderingSnake on 2010-05-22
Yes, but those updates still show up in the update manager, which makes me unsure of whether or not they were installed, or if update manager isn't updating its list when it starts

---

### Post by baz19 on 2010-07-27
This too is happening, on my side I will give it a shot in the terminal

---

### Post by Nolind on 2010-08-02
Yes....I'm getting the same problem too. Update manager lists 56 updates. Downloads them then returns to the main screen without apparently installing them. I tried in terminal using the code in the previous post and it reports 0 changed 0 updated etc.   Is this a problem on the server?

---

### Post by Nolind on 2010-08-02
Done that. Still doesn't install.

---

