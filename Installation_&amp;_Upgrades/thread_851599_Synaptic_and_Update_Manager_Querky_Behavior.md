---
title: "Synaptic and Update Manager Querky Behavior"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by arborrow on 2008-07-06
I have Ubuntu 8.04 running on a Dell XPS M1330.  Recently when I try to start synaptic from the menu it looks like it is attempting to start but then never does. Similarly, when I try to do an upgrade it looks like it is going to start and does not. I am attaching a screenshot showing the 'Starting Administration' program at the bottom of the screen which then disappears. Annoyingly, then I cannot close the Update Manager window (I have to manually go and kill it). I can also start synaptic from the command prompt with sudo synaptic and then it runs fine. Any clue what might be causing this annoying behavior? Peace - Anthony

---

### Post by iaculallad on 2008-07-06
> **arborrow said:**
> I have Ubuntu 8.04 running on a Dell XPS M1330.  Recently when I try to start synaptic from the menu it looks like it is attempting to start but then never does. Similarly, when I try to do an upgrade it looks like it is going to start and does not. I am attaching a screenshot showing the 'Starting Administration' program at the bottom of the screen which then disappears. Annoyingly, then I cannot close the Update Manager window (I have to manually go and kill it). I can also start synaptic from the command prompt with sudo synaptic and then it runs fine. Any clue what might be causing this annoying behavior? Peace - Anthony

What about running Update using the Terminal, does it give you similar problem?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by arborrow on 2008-07-07
Running apt-get update and upgrade through the terminal works fine which is what makes it more mysterious for me. I'm not sure what could be causing the gui not to work.

---

### Post by Bubba64 on 2008-07-07
Every thing should work now try opening synaptic, I have had this happen on occasion with Hardy, although it is usually just the update manager.

---

### Post by arborrow on 2008-07-07
It turns out that the issue was actually with gksudo. My /etc/hosts had been modified and was causing trouble. I followed the instructions at:
[https://answers.launchpad.net/ubuntu/+question/34350](https://answers.launchpad.net/ubuntu/+question/34350) and basically just fixed the line for 127.0.1.1 mycomputer, saved that and tried gksudo again and now all is working well. Thanks for the ideas and helping me to track this down. Peace - Anthony

---

