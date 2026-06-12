---
title: "Ubuntu--&gt;Kubuntu failure."
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by Rxke on 2005-11-07
I run Ubuntu Breezy on an iBook, using only the usual repo's. (Up to Universe) 
I apt-get installed kubuntu-desktop, then logged out and tried to start a KDE session via gdm.
However, I got a blue screen, and after some seconds a window in the upper left hand corner saying: "Could not start kdeinit. Check your system."
with a button saying "okay"
When pressing that button, I go back to gdm.

Now, I do not really know where to look. Check your system is a bit broad, no?

(Afterwards, I also installed a ream of KDE-related stuff, via synaptic, thinking it was a dependency issue, but to no avail. Rebooting didn't help either. )

---

### Post by lorenco on 2005-11-07
Have you tried installing KDM ???

---

### Post by Rxke on 2005-11-07
Is it really neccesary to use KDM? When installing, I was asked whether I wanted to use GDM or KDM, and I chose GDM... If this is the problem, then why didn't the install warn me about that?

---

### Post by lorenco on 2005-11-07
Not really needed... If you want to run KDE, KDM is the better option... But It could be that if you run KDM your problem goes away :???:

---

### Post by tseliot on 2005-11-07
[QUOTE=Rxke]Is it really neccesary to use KDM? When installing, I was asked whether I wanted to use GDM or KDM, and I chose GDM... If this is the problem, then why didn't the install warn me about that?[/QUOTE]

No, KDM is not necessary. Try to "Mark for Complete removal" kubuntu desktop and KDE in Synaptic. Then install the package "KDE"  (the kubuntu one maybe doesn't work for you and I find it buggy)

---

### Post by Rxke on 2005-11-07
Thanks, but didn't solve it.

I did complete removal of kubuntu desktop and kde-core and kdebase
Then reinstall of kde-core and kdebase, but problem persists.

---

### Post by tseliot on 2005-11-07
[QUOTE=Rxke]Thanks, but didn't solve it.

I did complete removal of kubuntu desktop and kde-core and kdebase
Then reinstall of kde-core and kdebase, but problem persists.[/QUOTE]

Ok, if you want to try KDM (so as to see if it solves the problem) type this:

sudo dpkg-reconfigure kdm

and select kdm

If it doesn't work then use GNOME and type the same command again (and select "gdm"

---

### Post by Rxke on 2005-11-07
No joy. Had to manually startx after that; and got a lot of warnings... 
Weird thing is, I rebooted, just to be double sure after choosing kdm, and then when I did startx... eventually everything looked ok (took a bit longer for the wallpaper to come up) except for the stuff I have in my sessions auto-start (or what it's called in English.) Afterwards I reconfigured to gdm again, and stuff is back to normal, as far as I can tell... 

Oh well, one day I'll figure it out.

---

### Post by tseliot on 2005-11-08
[QUOTE=Rxke]Oh well, one day I'll figure it out.[/QUOTE]
Perhaps a fresh installation is required (I suggest you to use GNOME though)

---

### Post by Rxke on 2005-11-08
A fresh install? Over my dead body! :p 

I just wanted to check out the KDE desktop, been more than two years since I last worked with it (Debian)... Wanted to see the new stuff etc... 
But it's no biggie I can't get it to work, I mean, I have everything I need already, so it was just curiosity, heh.

---

### Post by lorenco on 2005-11-08
I would suggest download the Kubuntu Live CD and boot that.  I can surely reccomend KDE (Works great) but that is my humble pie oppinion..:)

---

