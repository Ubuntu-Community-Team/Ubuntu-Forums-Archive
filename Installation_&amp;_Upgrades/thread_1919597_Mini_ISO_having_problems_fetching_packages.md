---
title: "Mini ISO having problems fetching packages"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by Cadmus on 2012-02-03
Hello there,

I'm trying to use the [Mini ISO]("https://help.ubuntu.com/community/Installation/MinimalCD") for 11.10 amd64 in a VM but I keep hitting the same problem.

After partitioning it goes off to try and fetch the packages but it always fails, even if I choose different mirrors (based in UK, have tried US, NL and FR mirrors so far). I would normally put it down to my VM configuration, but the same VM can be installed from the server CD and post install updates itself fine.

Any ideas what may be amiss? Has something changed and the Mini ISO needs updating? If so how do I make this change?

---

### Post by satanselbow on 2012-02-03
Is this what you mean?

[IMG]http://i39.tinypic.com/2vsnvrb.jpg[/IMG]

Had the same thing last might (32bit guest on 32bit pae host btw) - I immediately thought it was a dodgy net connection at my end... not had a chance to look any further... 

hmmm...

---

### Post by Cadmus on 2012-02-03
It's reassuring to know it's not just me

I've seen it go on the following packages:
```
eject
libplymouth
libpcre3
```

But I guess that's down to a semi-random order for package downloading.

---

### Post by Cadmus on 2012-02-06
Still having the same issue today.

Any ideas what could be causing this?

---

### Post by Bucky Ball on 2012-02-06
You probably needed to install a package manager. Didi you do this by installing a bunch of packages and apps like a CLI install, if you follow me? If so, perhaps you should have installed a desktop environment also, or aren't you there yet (at that stage of the install I mean, been awhile since I did a mini.iso)?

---

### Post by Cadmus on 2012-02-06
> **Bucky Ball said:**
> You probably needed to install a package manager. Didi you do this by installing a bunch of packages and apps like a CLI install, if you follow me? If so, perhaps you should have installed a desktop environment also, or aren't you there yet (at that stage of the install I mean, been awhile since I did a mini.iso)?

I'm booting the mini ISO with the 'Command Line Install' option, we get through the locale and partitioning stuff, then it goes wrong as above. It does seem to install apt beforehand (guessing that's on the disc). We're not making it to user creation or task/package selection.

---

### Post by Bucky Ball on 2012-02-06
A CLI install from the mini.iso should get to that though. You will need to input what packages you want installed (ie DE, Firefox, Synaptics, whatever). Slightly off track but that is the way ...

Best to prepare for that first so you know what you are going to need to manually type in to download into the base install. All the base install will do is get the hardware devices and internet up. You will be working from a shell after that. ;)

---

### Post by satanselbow on 2012-02-06
Hi Bucky - 

The problem is not with *installing* the packages - it is the *download* of the packages in the 1st place ;)

@OP

Are you using wifi or ethernet? I experienced problems with wifi but will be unable try it on an ethernet cable until tomorrow ;) Might be worth a whirl to narrow it down to ropey wifi :(

---

### Post by Cadmus on 2012-02-10
I'm on a cable (so to speak), it's a VM inside Virtualbox. If I use a standard live CD it can connect out fine.

---

### Post by Cadmus on 2012-02-10
Hmm, I'm trying it with a few different mirrors (from [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)).

Still the same issue, it can contact the mirror as if I type in a junk mirror address it gives up.

It seems to get through the initial packages fine, but it's on the libraries it just... stops.

---

### Post by Cadmus on 2012-02-10
Hmm, well, if I ignore the message and plow on it does start (there is a pre-existing bug where you need to do a ctrl+alt+F2 to get to a logon prompt)it does seem ok. I'd be happier if someone else had a try of this before putting anything important on it.

---

### Post by Cadmus on 2012-02-14
Well I'm calling it solved for now.

---

