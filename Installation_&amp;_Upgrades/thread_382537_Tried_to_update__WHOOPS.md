---
title: "Tried to update:  WHOOPS"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by thater on 2007-03-12
So last night I decided to update to 6.10.  I ran the gksu -c and everything was going well.  After downloading over 1.3 Gigs or so Ubuntu started installing and configuring everything.  Things were going swimingly when I got an IM from a friend of mine on GAIM.  I know I probably shouldn't have been doing other things while updating.  It's too late now.

Long story short, i was wunning Compiz and in the midst of chatting I hit "Shift + del" to try and delete a line of text and wound up restarting gnome.  Now Linux won't boot unless I go in Recovery mode.  I get an XServer configuration error but I know it's way worse than that.

So my question is this: Is there a way to restart the update process or recover Linux or do I have to download the 6.10 DVD image and just install from scratch?

Thanks in advance.  Sorry I'm such a n00b!

---

### Post by Kateikyoushi on 2007-03-12
Well you could try to update from recovery mode, post the output of this command.

```
cat /etc/apt/sources.list
```

---

### Post by thater on 2007-03-12
> **Kateikyoushi said:**
> Well you could try to update from recovery mode, post the output of this command.

```
cat /etc/apt/sources.list
```

Hey, the only way I could think to capture that output was with my digital camera.  And so here it is...

[[IMG]http://img156.imageshack.us/img156/5963/img0243rj8.th.jpg[/IMG]](http://img156.imageshack.us/my.php?image=img0243rj8.jpg)

---

### Post by Kateikyoushi on 2007-03-12
Okay what we really needed to know was that the file is updated to edgy.

Now let's try to continue the update as your sources.list

```
sudo aptitude update
sudo aptitude dist-upgrade
```

I think sudo is not necessary in recovery mode added it just in case.

---

### Post by thater on 2007-03-12
> **Kateikyoushi said:**
> Okay what we really needed to know was that the file is updated to edgy.

Now let's try to continue the update as your sources.list

```
sudo aptitude update
sudo aptitude dist-upgrade
```

I think sudo is not necessary in recovery mode added it just in case.

That's great, thanks a million for your help.  Everything appears to be working.  Still a few kinks to work out (wifi drivers, compiz) but you put me back in business.  much appreciated.

---

