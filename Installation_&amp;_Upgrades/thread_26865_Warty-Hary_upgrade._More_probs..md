---
title: "Warty-Hary upgrade. More probs."
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by lykoszine on 2005-04-14
Hi Guys

I upgraded Warty to Hoary, and totally screwed my dpkg. I changed repositories in sources.list, and then did

sudo apt-get update
sudo apt-get upgrade

(not dist-upgrade unfortunately).

After that apt, synaptic and dpkg stopped working. Have been through the forum, and tried the suggestions, including

sudo dpkg -C
sudo dpkg --configure -a
sudo apt-get -f install 
dpkg --clear-avail

and replacing .../dpkg/status with /dpkg/status-old

(not in that order).

I have a strange mix of stuff installed, which does not include gnome terminal, for ex, but I do have root terminal. What is installed works fine.

I am looking at damage limitation here, and do not mind trashing my package list and reinstalling everything, but would prefer not to reinstall.

Help appreciated. Cheers

---

### Post by heimo on 2005-04-14
One line that has helped me through several dependency problems is
```
 apt-get update -f
```
Maybe it could help you too?
 
EDIT: Hrmpf... I was sure you didn't list that one. Sorry. Hmm... And I think I got it wrong, it's probably the version you listed (install -f).
 
What I'd try to do is uninstall only the messed up stuff (or even the whole ubuntu-desktop meta package) and then reinstall those parts.

---

### Post by lykoszine on 2005-04-14
> What I'd try to do is uninstall only the messed up stuff (or even the whole ubuntu-desktop meta package) and then reinstall those parts.

That is the problem, apt is so dead that I can't install/uninstall ANYTHING. I just get DPKG errors.

---

### Post by heimo on 2005-04-14
Oh... :-\" In similar situation I have sometimes tried to force dpkg install everything that I've had in /var/apt/cache/arhive (or what-ever that directory is, can't verify at the moment). That's a long shot. :) Not very professional, but sometimes it helped.

---

### Post by lykoszine on 2005-04-14
[QUOTE=heimo]Oh... :-\" In similar situation I have sometimes tried to force dpkg install everything that I've had in /var/apt/cache/arhive (or what-ever that directory is, can't verify at the moment). That's a long shot. :) Not very professional, but sometimes it helped.[/QUOTE]

And what would the command be to do that? 

(don't think it is gonna work though. Doesn't dpkg --clear-avail get rid of the cache anyway?)

---

### Post by heimo on 2005-04-14
I'm not at my Linux box at the moment, so I can't give you the flags I used. But something like *dpkg -i *deb* (and some flag to force, probably -f?) And if you already flushed the cache, you wouldn't have any packages. I always use *apt-get clean* to do that.)
 
Of course you could try to manually uninstall and then reinstall the conflicting packages from install CD, if you have that one near you. I've once salvaged my Debian box from a situation where I no longer had commands like ls, rm or cp available (dpkg was working!). Used *cat ** for ls. :D EDIT: I think it was echo * (cat would be nasty)
  
I think you can do it, but maybe it can be easier to reinstall whole Ubuntu.

---

