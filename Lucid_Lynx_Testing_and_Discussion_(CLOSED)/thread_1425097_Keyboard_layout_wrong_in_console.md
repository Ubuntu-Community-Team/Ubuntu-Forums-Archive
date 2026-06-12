---
title: "Keyboard layout wrong in console"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phenest on 2010-03-08
I use a GB Dvorak keyboard. I setup this layout during installation, and it's exactly what I get in X. When I switch to tty1-6, I get Qwerty instead. Checking /etc/default/console-setup, it shows GB Dvorak.

Clearly a bug which needs reporting, but what I need to know is how to change the layout on the fly, or what a workaround is.

---

### Post by gwenn on 2010-03-08
Same problem for me

---

### Post by ASchweitzer on 2010-03-08
See the last post here:

[http://ubuntuforums.org/showthread.php?t=329369&highlight=boot+console+font](http://ubuntuforums.org/showthread.php?t=329369&highlight=boot+console+font)

Run
```
sudo dpkg-reconfigure console-setup
```

Hope that works for you.

---

### Post by phenest on 2010-03-09
Thanks. It did work, but it doesn't survive a reboot.

---

### Post by QwUo173Hy on 2010-03-09
I've bugged it here - please 'me too' it.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/533047](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/533047)

---

### Post by phenest on 2010-03-09
> **jarlath said:**
> I've bugged it here - please 'me too' it.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/533047](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/533047)

Marked as 'me too', and left a comment.

---

### Post by ASchweitzer on 2010-03-09
Is this a Lucid specific thing?

---

### Post by cyberkilla on 2010-03-09
Same here. US layout on console, but my computer uses a UK layout.

This has happened for a few days now. It is because of the way they've changed the boot process.

[http://ubuntuforums.org/showthread.php?t=1422297](http://ubuntuforums.org/showthread.php?t=1422297)

---

### Post by QwUo173Hy on 2010-03-09
And I see that there was an existing report (with a title I don't understand!). [https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/524439](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/524439)

I've marked mine as a dupe. Nice to see a fix is on the way. Interesting that it doesn't adopt the 'me too's of the duplicates though.

---

### Post by QwUo173Hy on 2010-03-09
Cyberkilla - thanks for the heads up on launchpad ;)

---

### Post by cyberkilla on 2010-03-09
> **jarlath said:**
> Cyberkilla - thanks for the heads up on launchpad ;)

No problem. I just managed to get native resolution TTYs and they're useless because of a keyboard layout problem!

Typical:p

---

