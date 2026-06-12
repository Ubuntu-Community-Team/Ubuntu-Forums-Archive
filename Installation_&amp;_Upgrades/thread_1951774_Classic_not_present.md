---
title: "Classic not present"
date: 2012-04-03
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2012-04-03
Nothing less than a gnome 2 interface will work for me.

Delighted to see "GNOME Classic in Ubuntu 12.04: It’s Like Nothing Ever Changed" at 

[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/)

All you have to do is "Open the Ubuntu Software Centre and search for ‘gnome-panel’, ..."

But it is not there. WTF!?

Never mind. Just "sudo apt-get install gnome-panel"
according to
[http://ubuntublog.org/gnome-classic-ubuntu-12-04.htm](http://ubuntublog.org/gnome-classic-ubuntu-12-04.htm)

NOPE. Package 'gnome-panel' has no installation candidate.

Would someone please tell me what's going on! Thanks.

---

### Post by zombifier25 on 2012-04-03
Are you using 12.04? If not, you must install the package gnome-session-fallback instead. If so, did you try to update the repo? It installs fine for me on my Precise. (In Precise Pangolin, gnome-panel and gnome-session-fallback is the same package)

---

### Post by triplemaya on 2012-04-04
Thanks zombifier. I am running 12.04 off the disk. 

ubuntu-12.04-beta2-desktop-amd64 to be specific

I ran apt-get update, but still no gnome-panel and no gnome-session-fallback either. Both give ... has no installation candidate.

---

### Post by darkod on 2012-04-04
I would say hold on for a few weeks until the final release is out.

If they say it will be there, it will be. Running a development version from the cd (not installed on the hdd) may be creating some unknown issues. Even though your logic that the package should be located in the repositories is correct.

---

### Post by triplemaya on 2012-04-04
Good point. Cheers. Hopefully all the old features will be there.

---

### Post by critin on 2012-04-04
I searched for gnome panel in SC and the results came back to "Launcher and docking facility for gnome"
which is the gnome panel.

---

### Post by gordintoronto on 2012-04-04
Funny, a couple of days ago I installed gnome-panel in the 12.04 beta. (I installed onto an 8 GB flash drive. Real install, not a LiveUSB.)

Perhaps you need to enable more repositories.

---

### Post by critin on 2012-04-05
Or run a distro update, it's definitely in SC now.

---

### Post by triplemaya on 2012-04-05
Thanks for all the replies.

"Or run a distro update, it's definitely in SC now."

As posted, I ran apt-get update as part of my initial attempt to get it running for evaluation. Do you mean something else critin?

---

### Post by critin on 2012-04-08
No, but I did search for gnome panel in SC and it wasn't there.   

Searched for something else and installed "**Launcher and docking facility for gnome**"

which turns out to be the gnome panel.  I'm running classic now. 
"gnome panel" is still not in SC (as of 5 min ago) under that name but is if you use the name above.

---

### Post by triplemaya on 2012-04-09
Thanks, but this does not seem to get me anywhere. There is nothing about launcher in available applications.

Google shows me this page
[http://packages.ubuntu.com/oneiric/gnome-panel](http://packages.ubuntu.com/oneiric/gnome-panel)
And this is part of universe, however, I have no idea how to even locate software sources in unity. Dash home has no results for 'software', let alone 'software sources'. (But I thought universe was included anyway.)

How did you install this package?

---

### Post by coffeecat on 2012-04-09
> **triplemaya said:**
> I am running 12.04 off the disk. 

Do you mean off a live CD? Universe is not enabled in the live session.

---

### Post by triplemaya on 2012-04-09
Thanks, yes. That's what I mean. Good to know.

So, I'll just wait for the full release.

---

### Post by coffeecat on 2012-04-09
> **triplemaya said:**
> 
So, I'll just wait for the full release.

I'm a bit puzzled by what you mean. If you want to install the package gnome-panel, you need to have a permanent installation. Not because you cannot enable the Universe repository in the live session - you can - but because there is not much point in installing the package in the live CD session. You will lose it when you power down. (You could, of course, install it to a live USB with persistence.)

Is it that you want to try out gnome-panel before you commit yourself to a permanent installation on a hard drive? I think the only way you could do that is with a live USB with persistence

---

### Post by triplemaya on 2012-04-10
"Is it that you want to try out gnome-panel before you commit yourself to a permanent installation on a hard drive?"

Yes, that was the idea. After the distro cast loose those of us who depend on features of g2 I went over to Debian - all hail! - and there is zero chance of my going back to the big U until I can make use of the features I am used to, which are by now required for me to function effectively on the pc. (I'm assuming that there is a sufficient number of us in this boat, and that we are sufficiently vociferous, that eventually all the missing functionality will be restored.)

---

