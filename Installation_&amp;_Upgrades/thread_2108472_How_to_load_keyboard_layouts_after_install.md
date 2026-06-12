---
title: "How to load keyboard layouts after install"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by bcm37 on 2013-01-24
I'm even a bit confused with the terminology right now -- input source, keyboard layout, language support -- so please forgive me if I've missed something due to a badly worded search.

I'm running 12.04LTS.

It was installed with just the US layout.

I'd like to switch to Dvorak.

I cannot find any layouts at all, and cannot figure out where to get them. My screen appears as such:

[IMG]http://i.imgur.com/fMkZZIk.png[/IMG]

There is just nothing listed, and I'm not sure how to proceed from here.

Thank you for your time

---

### Post by gifford on 2013-01-24
Your in the correct area to change it..just click on the + sign in the left hand column and you will get choose a layout, scroll down to English(Dvorak) and select it.

Sorry, I didn't read your post more carefully..when I go to my settings it is English(US) instead of your us. Did you fully install all the language settings? I think on your initial install you were given the choice of keyboard and English(US).

---

### Post by matt_symes on 2013-01-24
Hi

As the previous poster said, is dvorak installed on your machine. You can make a quick test by opening a terminal and typing

```
setxkbmap dvorak
```Does it throw an error or does it change the keyboard mapping ?

This will not persist after a reboot if it does change it.

Kind regards

---

### Post by gifford on 2013-01-24
In my file /etc/default/keyboard lists:
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

What does yours list?

---

### Post by bcm37 on 2013-01-28
> **gifford said:**
> Your in the correct area to change it..just click on the + sign in the left hand column and you will get choose a layout, scroll down to English(Dvorak) and select it.

Sorry, I didn't read your post more carefully..when I go to my settings it is English(US) instead of your us. Did you fully install all the language settings? I think on your initial install you were given the choice of keyboard and English(US).

No, I don't believe they were installed. Someone else set it up.

How would I go about installing them?

---

### Post by bcm37 on 2013-01-28
> **gifford said:**
> In my file /etc/default/keyboard lists:
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

What does yours list?

Only that.

setxkbmap returns:
```
XKB extension not present on :10.0
```

---

### Post by matt_symes on 2013-01-30
Hi

> **bcm37 said:**
> Only that.

setxkbmap returns:
```
XKB extension not present on :10.0
```

That's a surprise.I take it that
```

setxkbmap -print
```

gives the same error then.

Open a terminal and type

```
grep -i xkb /var/log/Xorg.0.log
```

The above command is case sensitive. Please post the output back here.

Is this any kind of special install such as a wubi install or a VM install ?

Kind regards

---

### Post by bcm37 on 2013-01-30
> **matt_symes said:**
> Hi



That's a surprise.I take it that
```

setxkbmap -print
```gives the same error then.

Yes.
```
XKB extension not present on :10.0
```> 
Open a terminal and type

```
grep -i xkb /var/log/Xorg.0.log
```The above command is case sensitive. Please post the output back here.

Is this any kind of special install such as a wubi install or a VM install ?

Kind regardsIt's on a VM, and I was told it was "Minimal".

I apologize, cut and paste don't work on over the odd configuration of Remote Desktop I'm using right now, screencaps are quicker.

[IMG]http://i.imgur.com/J5tgFU1.png[/IMG]

---

### Post by matt_symes on 2013-02-02
Hi

> It's on a VM, and I was told it was "Minimal".

That would make sense. It sounds like you have a minimal install and that would explain why you are missing various functionality.

I'll take a look in a moment.

Kind regards

---

