---
title: "can I change flavours of Ubuntu, without starting from scratch?"
date: 2020-01-15
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2020-01-15
I have somehow wound up running Ubuntu 18.04.3 LTS
and I am having overall trouble with various programs (Thunderbird, Kolourpaint) being able to access various external and secondary HDDS.
LTS I am being told is really not suitable for private individual users.

can I change to a different version of Ubuntu without blowing away my system and all my installed software?
Kubuntu has been suggested (though I don't know why)

---

### Post by CatKiller on 2020-01-15
LTS releases are best for home users unless they're running very new hardware. We've seen many cases of new users being stranded on the intermediate releases because they didn't realise that they needed to upgrade to keep getting updates and support.

Those applications not being able to access external drives is likely nothing to do with which desktop environment you're using, but caused by being snaps. 

The different flavours just give you a different desktop environment and different applications. It's pretty easy to just install the metapackage for the new flavour and (optionally) remove the applications from the old flavour. I did exactly that switching my laptop from Cinnamon to KDE. 

Kubuntu is awesome.

---

### Post by pjstock on 2020-01-15
thank you.
so I can ignore this advice (from the makers of Kolourpaint. I had asked them how I could install a Non-Snap version of Kolourpaint. She could not help me there.)? 
"Using an LTS version makes only sense in a corporate multi-seat installation, not really for a private user. "

I am perfectly happy with my LTS setup. (but then I am not fussy and my hardware is pretty old. Intel® Core&#8482; i7-2600 CPU @ 3.40GHz × 8 )

---

### Post by CatKiller on 2020-01-15
> **pjstock said:**
> so I can ignore this advice (from the makers of Kolourpaint. I had asked them how I could install a Non-Snap version of Kolourpaint. She could not help me there.)? 
"Using an LTS version makes only sense in a corporate multi-seat installation, not really for a private user. "

I would, yes. 

The use case of software developers are much different from the use cases of end users. I'm sure that person has some definite reason for preferring the latest-and-greatest.

We're just end users helping each other out here.

The LTS releases get updates for five years; the interim releases only get updates for nine months. Third parties generally target the latest LTS release if they can only target one thing. 

The interim releases do contain newer versions of software, so they might contain some new features, or some bug fixes, or support newer hardware, so sometimes that might be just what a user needs. And obviously we need *some* users to be using non-LTS releases to test things and provide feedback on features, and so on.

To install the non-snap version of Kolourpaint you could just use ```
sudo apt install kolourpaint
```

---

### Post by pjstock on 2020-01-15
I tried that command line install:
"sudo apt install kolourpaint"

but it pickedup an older version of kolourpaint Version 17.12.3 that was missing the colour palette. I don't know why. But that renders the program very clumsy or useless for me.
but in order to get the colour palette I had to install a newer version of Kolourpaint 19.x but i only know how to do that via Ubuntu Software and that only offers me a Snap version (which prevents me from importing images from various locations on my various HDDs). 

This Snap is driving me crazy.

---

### Post by crip720 on 2020-01-15
Changing favours to try to fix problem in a program will usually not help and/or make it worst.  Installing different desktops sometimes work well, but other times can make a mess.  Test in a VM or get advice saying desktop you are using will work well with desktop you want to install.

---

### Post by CelticWarrior on 2020-01-15
When installing snaps from the Software Ubuntu always make sure to open the permissions button and adjust accordingly. That alone should solve the problem.

---

### Post by crip720 on 2020-01-15
Snaps are not full feature yet.  I would google kolourpaint and see if there is a a newer version as ppa.  Also see if there are any permissions you check in software store that will allow more features.

---

### Post by Dennis N on 2020-01-15
Gimp, Inkscape, and gthumb fit well with Ubuntu. Have you looked into those? I have all three installed, and they meet all my needs for graphics software.

Kolourpaint also has a flatpak version (19.12.1):
[https://flathub.org/apps/details/org.kde.kolourpaint](https://flathub.org/apps/details/org.kde.kolourpaint)

I've yet to install a flatpak application, so can't comment further - but I've been meaning to try one as a test, maybe this.

Installation information for flatpak:
[https://flatpak.org/setup/Ubuntu/](https://flatpak.org/setup/Ubuntu/)

---

### Post by Dennis N on 2020-01-15
OK, I installed the Flatpak of Kolourpaint and find I can save/load a file to/from a USB or another partition. Also just looks a lot nicer than the Snap version, and uses the user's selected cursor rather than it's own. So you can go with that. The Flatpak setup and install took about 10 minutes time.

---

