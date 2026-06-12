---
title: "Kde4?"
date: 2008-06-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rahulthewall3000 on 2008-06-07
Though I have used Ubuntu since the days of edgy, I have never tried tried KDE and have always stuck with gnome. Now what I would like to know is how to go about installing KDE-4 in Intrepid.
I want to have both KDE and Gnome - that I know is possible. gdm would provide me with the options for that.

Thanks in advance
Rahul

---

### Post by caryb on 2008-06-07
I find KDE4 great but don't try it just yet it has been broken for the last 10 days!


Cary

---

### Post by Eclipse. on 2008-06-07
Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main to your sources.list.

Then sudo apt-get update && sudo apt-get install kubuntu-kde4-desktop

That will install 4.0.80 (4.1 beta).

Choose which one you want to login to at the login screen in sessions.

---

### Post by rahulthewall3000 on 2008-06-07
> **caryb said:**
> I find KDE4 great but don't try it just yet it has been broken for the last 10 days!


Cary

Thanks for that! :)

---

### Post by Eclipse. on 2008-06-07
Meh, KDE has been fine with me using they packages.Not that I have used it alot though.

---

### Post by rahulthewall3000 on 2008-06-07
> **Eclipse. said:**
> Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main to your sources.list.

Then sudo apt-get update && sudo apt-get install kubuntu-kde4-desktop

That will install 4.0.80 (4.1 beta).

Choose which one you want to login to at the login screen in sessions.

Will give it a try, hard to decide whether to wait for it to get fixed or not, I like broken softwares. :P

---

### Post by ChameleonDave on 2008-06-07
> **Eclipse. said:**
> Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main to your sources.list.



You've really got to think about how cryptic that sounds to a new user.  Really.

---

There is a file located at */etc/apt/sources.list* which lists all the online repositories that your computer uses to get software packages from.  You need to add "http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu" to this list.  You can do so in a text editor, or else you can type the following on the command line:

```
sudo echo "deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main" >> /etc/apt/sources.list
```

---

### Post by rahulthewall3000 on 2008-06-07
> **ChameleonDave said:**
> You've really got to think about how cryptic that sounds to a new user.  Really.

---

There is a file located at */etc/apt/sources.list* which lists all the online repositories that your computer uses to get software packages from.  You need to add "http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu" to this list.  You can do so in a text editor, or else you can type the following on the command line:

```
sudo echo "deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu" >> /etc/apt/sources.list
```

Dude, thanks for the help, but I think as I mentioned that I have been an Ubuntu user since the days of edgy, it was understood that I know what Eclipse meant and I did. No offense meant, but I do not think that anyone trying Intrepid would not understand what that means.

---

### Post by ChameleonDave on 2008-06-07
> **rahulthewall3000 said:**
> Dude, thanks for the help, but I think as I mentioned that I have been an Ubuntu user since the days of edgy, it was understood that I know what Eclipse meant and I did. No offense meant, but I do not think that anyone trying Intrepid would not understand what that means.

I didn't read your life-story bit.  I went straight for the bit where you asked how to install a desktop environment, which is a newbie question.  ;-)

---

### Post by rahulthewall3000 on 2008-06-07
W: Failed to fetch [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by rahulthewall3000 on 2008-06-07
> **ChameleonDave said:**
> I didn't read your life-story bit.  I went straight for the bit where you asked how to install a desktop environment, which is a newbie question.  ;-)

Yup, no need to read the life story, and am quite a newbie when it comes to KDE, have never tried it. :D As for installing a desktop environment, I specifically asked because I anticipated that there would be a separate repo for 4.1 (beta).

However, that repo does not seem to work right now. :)

---

### Post by ChameleonDave on 2008-06-07
A look at [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/) shows that only packages for gutsy and hardy are available.  The hardy packages would no doubt suffice.

---

### Post by rahulthewall3000 on 2008-06-07
> **ChameleonDave said:**
> A look at [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/) shows that only packages for gutsy and hardy are available.  The hardy packages would no doubt suffice.

Thanks again. :)

---

### Post by MacUntu on 2008-06-07
Won't install because of unmet dependencies.

---

### Post by Eclipse. on 2008-06-07
> **ChameleonDave said:**
> You've really got to think about how cryptic that sounds to a new user.  Really.

---

There is a file located at */etc/apt/sources.list* which lists all the online repositories that your computer uses to get software packages from.  You need to add "http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu" to this list.  You can do so in a text editor, or else you can type the following on the command line:

```
sudo echo "deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main" >> /etc/apt/sources.list
```

If your running intrepid and being using ubuntu since edgy you dont need to baby them, you presume they have the knowledge to know what they are talking about otherwise they wouldnt be running intrepid for a start.

Obviously with a new user you go through everything and explain it all.

---

### Post by quickshade on 2008-06-07
It's not really worth it to try and fix all these problems. I suggest hitting up a live CD and using that for now. If you end up liking it then make the switch. Just remember it's going to be a bit slow.

[http://home.kde.org/~binner/kde-four-live/](http://home.kde.org/~binner/kde-four-live/)

---

### Post by Gina on 2008-06-09
I tried Hardy KDE4 and had lots of bugs so went back to Gnome.  OK I know there's KDE3 but I thought I'd try the latest version ;)

---

