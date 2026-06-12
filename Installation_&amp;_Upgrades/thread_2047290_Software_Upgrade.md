---
title: "Software Upgrade"
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by Wer Bn on 2012-08-24
I got a new problem... *sigh* here I was trying to get my Ubuntu nice  and shinny, I installed a few packages for Gnome 3 and tried to get some  new themes.

God damnit, never more...

Now, a "Prohibited" sign shows at the top of the screen (near those icons, at the top bar)
It says

"E:Type 'ain' not known in line 3 at font list /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list"

And Ubuntu software center doesn't work
Help, please

---

### Post by cortman on 2012-08-24
> **Wer Bn said:**
> I got a new problem... *sigh* here I was trying to get my Ubuntu nice  and shinny, I installed a few packages for Gnome 3 and tried to get some  new themes.

God -*-it, never more...

Now, a "Prohibited" sign shows at the top of the screen (near those icons, at the top bar)
It says

"E:Type 'ain' not known in line 3 at font list /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list"

And Ubuntu software center doesn't work
Help, please

Please post output of

```
cat /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list
```

---

### Post by Wer Bn on 2012-08-24
Here you go

> deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main
deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main
ain

---

### Post by cortman on 2012-08-24
> **Wer Bn said:**
> Here you go

Hi, you just need to remove the "ain" from the bottom of the file. Run

```
gksu gedit /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list
```

to open it in a text editor. Remove the offending "ain", save and close, and run

```
sudo apt-get update
```

and that should fix it!

---

### Post by Wer Bn on 2012-08-25
Clean and effective.
Thank you very much

---

