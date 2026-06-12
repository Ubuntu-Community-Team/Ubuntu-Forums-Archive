---
title: "Update information is outdated"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by Crazy K on 2010-12-31
Hey there, I have a small error I'd like to fix. I got the yellow caution triangle is showing up. When I clicked it I'm brought to the update manager and when I click on check for updates, I get this: 


[IMG]http://i.imgur.com/7jJL0l.jpg[/IMG]

---

### Post by tommcd on 2011-01-01
This is yet another problem with those all too problematic PPA repos that so many Ubuntu users seem so compelled to add to their sources.list.
Try commenting out (put a # in front of) any third party PPA repos in your 
/etc/apt/sources.list, or in your /etc/apt/sources.list.d/ directory, and then run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
And you should be good to go.
For the best and most trouble free results, avoid *all* third party repos in Ubuntu, and you will never again have problems like this.

Third party repos, including those all too problematic PPA repos, are unsupported by the Ubuntu developers.

It is possible that your problematic PPA repo is temporally unavailable. You may try using it again at a later time.

---

### Post by Crazy K on 2011-01-01
I just unchecked the ppa that the error was with. So yeah, seems to be working fine now.

---

### Post by jcolyn on 2011-01-01
Adding untrusted ppa's is playing a dangerous game.

You could end up with a root kit on your computer.

If a ppa is not directly connected with a Ubuntu developer I'd stay away. If the software you want is not in the repos there usually is an alternative.

---

