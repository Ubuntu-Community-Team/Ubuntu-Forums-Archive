---
title: "Lubuntu 10.04 Beta 1 - A couple questions..."
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Uncle Spellbinder on 2010-04-02
Unless there is somewhere else I should be posting, I'll post here Lucid Lynx Testing and Discussion. Hopefully there are some Lubuntu 10.04 testers that can help out -

Testing out Lubuntu 10.04 Beta 1, 32 bit. 

A few questions:

1) [s]Is there a way to get 'quick search' working is Synaptic?[/s]

2) [s]Is there a way to adjust font settings? I'm so use to system > preferences > appearance > fonts in Ubuntu, I see no way to do this in Lubuntu.[/s]

3) [s]I really like the speediness of PCManFM2. But it seems that thumbnail generation, for videos primarily, is not possible. Is there a way to do this in PCManFM2? If not, can Nautilus be made the default? If so, how?[/s]

4) [s]How can I change the clock in the panel from 24 hour to 12 hour. Not sure why it defaults to a 24 hour clock as I know nobody who uses it as such.[/s]

5) How can I change the desktop background (wallpaper)?

6) Though proprietary drivers were available to me in Lucid (nVidia), nothing shows up in Lubuntu.

---

### Post by Uncle Spellbinder on 2010-04-02
Took care of number 4. The clock format was %R by default. I changed it to %I:%M:%S which geve me the 12 hour clock I'm use to. Stumbled across it purely by accident [here](http://www.pclinuxos.com/forum/index.php?PHPSESSID=1fr9hcmknoj2fijkqfu8htclv3&topic=67039.msg545772#msg545772)

---

### Post by Uncle Spellbinder on 2010-04-02
Well, After about 3 days of regular use, I'm finding Lubuntu quite promising. But buggier that it's Lucid counterpart. I'll probably be installing Lucid beta again. Maybe re-visit Lubuntu at RC or final in hopes that some of the above issues (quick search in Synaptic and proprietary drivers in particular) will be addressed.

---

### Post by gilir on 2010-04-03
> **Uncle Spellbinder said:**
> 
1) Is there a way to get 'quick search' working is Synaptic? 

Install apt-xapian-index and reboot, it should work. 

> **Uncle Spellbinder said:**
> 
2) Is there a way to adjust font settings? I'm so use to system > preferences > appearance > fonts in Ubuntu, I see no way to do this in Lubuntu.

Go to Preferences > Apparence > Windows. It should in the corner left.

> **Uncle Spellbinder said:**
> 
3) I really like the speediness of PCManFM2. But it seems that thumbnail generation, for videos primarily, is not possible. In folders, external drives or the desktop. Is there a way to do this in PCManFM2? If not, can Nautilus be made the default? If so, how?

It should be a bug, you can report it here [http://sourceforge.net/tracker/?group_id=156956&atid=801864](http://sourceforge.net/tracker/?group_id=156956&atid=801864)
Installing nautilus instead of pcmanfm will kill most of the interest of LXDE and Lubuntu.


> **Uncle Spellbinder said:**
> 
5) How can I change the desktop background (wallpaper)?

Right click on the desktop to open the preference dialog.

> **Uncle Spellbinder said:**
> 
6) Though proprietary drivers were available to me in Lucid (nVidia), nothing shows up in Lubuntu.
You can manually install them via Preferences > Hardware Drivers

---

### Post by plun on 2010-04-03
[QUOTE=gilir;9069062]

Impossible to Quote a whole message with Lubuntu and Firefox.....

Change background is a mystery for myself.....;)

---

### Post by Uncle Spellbinder on 2010-04-03
> **gilir said:**
> Right click on the desktop to open the preference dialog.

You can manually install them via Preferences > Hardware Drivers

Appreciate the help. There is no dialog to change background/wallpaper.

Preferences > drivers shows nothing to install. On Lucid, I have 2 choices.

---

### Post by vredley on 2010-04-03
> **Uncle Spellbinder said:**
> Appreciate the help. There is no dialog to change background/wallpaper.

To change the wallpaper, right-click on the desktop and select 'Desktop Preferences'. The wallpaper options are in the 'Appearance' tab.

---

### Post by kerry_s on 2010-04-03
> **vredley said:**
> To change the wallpaper, right-click on the desktop and select 'Desktop Preferences'. The wallpaper options are in the 'Appearance' tab.

he's using lubuntu, it's the lxde version of ubuntu. 
no appearance tab, but it is right click the desktop.


@ Uncle Spellbinder,
 lubuntu is still work in progress & a lot of stuff is still incomplete, best thing is to use synaptic.
just find it & install it.

make sure you add the lubuntu ppa, there missing on a fresh install.
```
sudo add-apt-repository ppa:lubuntu-desktop/ppa
```

---

### Post by tcchris on 2010-04-03
UncleSpellbinder
I plan to install Lubuntu on a machine that just runs boxee , the media center .
It will rarely need the desktop . I will ssh in to update and movies etc will be on another networked computer using samba.

I would appreciate a review on how things go for you .
Installing hardware drivers or any other issues you run into

Thanks for blazing the trail !

---

### Post by vredley on 2010-04-03
> **kerry_s said:**
> he's using lubuntu, it's the lxde version of ubuntu.

Me too.

> **kerry_s said:**
> no appearance tab, but it is right click the desktop.

Trust me. 'Desktop Preferences' has two tabs - 'Appearance' and 'Advanced'. :)

---

### Post by kerry_s on 2010-04-03
> **vredley said:**
> Me too.



Trust me. 'Desktop Preferences' has two tabs - 'Appearance' and 'Advanced'. :)

my bag, i was still half a sleep, i wasn't even concentrating, was still waiting for the coffee. :lolflag:
anyways it's right there in the screenshot so he can see it.

sorry!

---

### Post by Uncle Spellbinder on 2010-04-03
> **vredley said:**
> Trust me. 'Desktop Preferences' has two tabs - 'Appearance' and 'Advanced'. :)
Unless I'm beyond blind, inept or just a fool - I see no option to change the background via *Desktop Preferences > Appearance and/or Advanced*. My wife has the Lubuntu Beta (fully updated) on her laptop. Same issue. Neither of us can change the background.

I'll admit to this being a minor issue in the grand scheme of things, bit an issue nonetheless.

---

### Post by vredley on 2010-04-03
> **kerry_s said:**
> my bag, i was still half a sleep, i wasn't even concentrating, was still waiting for the coffee. :lolflag:
anyways it's right there in the screenshot so he can see it.

sorry!

You had me worried there for a minute. Thought I'd installed the wrong distro. :lol:

---

### Post by vredley on 2010-04-03
> **Uncle Spellbinder said:**
> Unless I'm beyond blind, inept or just a fool - I see no option to change the background via *Desktop Preferences > Appearance and/or Advanced*. My wife has the Lubuntu Beta (fully updated) on her laptop. Same issue. Neither of us can change the background.

I'll admit to this being a minor issue in the grand scheme of things, bit an issue nonetheless.

Could you post a screenshot of 'Desktop Preferences'?

---

### Post by Uncle Spellbinder on 2010-04-03
No I cannot. I've since reformatted and reinstalled Lucid on my desktop. And though my wife was dual-booting Lucid/Lubuntu, she's since returned to Lucid. 

I'll be waiting for the RC before making any snap judgments.

---

### Post by seeker5528 on 2010-04-05
I'm not using the PPA, have not updated for a couple of weeks either.

The way it show up for me when I go to change the wall paper is....

Right click the desktop.

Choose 'Desktop Settings'

Click on the 'Desktop' tab

Updating.......

Rebooting......

Yup, same stuff. 

Are they expecting to get some stuff from the PPA into Lucid? It seems a bit late at this point.

Later, Seeker

---

### Post by RTrev on 2010-04-05
Wow.  I have to say that I haven't been this impressed with a distro for some time.  Lubuntu, unlike any of the other "lightweight" distros I've tried, is completely comfortable for me.  I installed it mainly just to see, but I haven't booted anything else since.

What I find interesting is that I can see using this on any computer.  Right now I have it on an AMD 3800+ dual core with 4G of RAM and over a Terrabye of disk.  That would seem like overkill for a lightweight distro, but it isn't.  It's working better than it ever has.  The 64-bit Ubuntu sees 3.9G of my memory, and this 32-bit one sees 3.6G.  It uses so much less, that I come out ahead anyway.  Besides, there will probably be a 64-bit version as soon as Canonical officially adopts Lubuntu.

I notice that it has a netbook remix option on login, and I plan to try this on a Dell Mini-9 when I get a chance.

It seems to do everything I want, so far.  I'll use it for a while and see how it wears. <g>

---

### Post by stinger30au on 2010-04-06
to change background


system

preferences

appearance

then click background and change away till your little heart is content

---

### Post by seeker5528 on 2010-04-07
OK, re-reading my earlier post, I see it probably is a bit confusing.

The 3 steps to get to a place where it allows me change the wall paper, that works for me.

Right click the desktop.

Choose 'Desktop Settings'

Click on the 'Desktop' tab

I'm installing the Lubuntu stuff from the Lucid repositories, not the PPA. 

The updating and rebooting thing was to see if anything had changed in the couple of weeks since I had updated the machine I have the Lubuntu stuff on, again not from the PPA. None of the updates changed anything with the stuff relating to changing the wall paper. Leading to the question about whether stuff from the PPA is expected to make it into Lucid since it is into the beta part of the development cycle.

Later, Seeker

---

### Post by vredley on 2010-04-07
> **seeker5528 said:**
> Leading to the question about whether stuff from the PPA is expected to make it into Lucid since it is into the beta part of the development cycle.

I don't think it is, if this message from the mailing list is anything to go by: [https://lists.launchpad.net/lubuntu-desktop/msg01055.html](https://lists.launchpad.net/lubuntu-desktop/msg01055.html) .

---

### Post by seeker5528 on 2010-04-08
> **vredley said:**
> I don't think it is, if this message from the mailing list is anything to go by: [https://lists.launchpad.net/lubuntu-desktop/msg01055.html](https://lists.launchpad.net/lubuntu-desktop/msg01055.html) .

Reading that gives me more incentive to pull form the PPA.

EDIT: OK, installed from the PPA, looks like pcfm2 is the only significant thing being provided, which sounded iffy for Lucid anyway, so I guess that is good to know. 

Later, Seeker

---

