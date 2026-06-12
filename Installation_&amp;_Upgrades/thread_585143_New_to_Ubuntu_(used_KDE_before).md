---
title: "New to Ubuntu (used KDE before)"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Kdar on 2007-10-21
Ok.
Since trying to update Kubuntu from 7.04 to 7.10 didn't go well.

I decided to do clean install of Ubuntu (which I didn't tried before, but wanted to).

So it is installed now. Everything seem to work fine. I got my wireless connection working.

But there few problems and questions.
-------------------
1) In Kubuntu I used "Adept".. What do I use Ubuntu.

2) I tried to enable nvidia drivers in "Restricted Drivers". But when I try to do that.. I see this "The software source for the package nvidia-glx-new is not enabled"

Is it not installed yet? or....

Also. By using "Add/Remove..." (which I guess is like adept.. But I could be wrong..)
When I try to install anything it would not do it..  and I get something like this 
"The list of applications is not available....."

Can any one help? I kind of like how Gnome looks and feel. But I guess I have few problems at the moment.

--

Also.
After I will get my Add/Remove working.
What kind of packages do I need to install.
Since, just now I tried to play some video, DVDs.. and it didn't played any of them.

---

### Post by Kdar on 2007-10-21
bump..
Its already on page 3...

Can any one help?

---

### Post by atlfalcons866 on 2007-10-21
use synaptic in ubuntu. system tools>administration>synaptic package manager

---

### Post by benerivo on 2007-10-21
The package manager in Ubuntu is Synaptic (in the main menu). Also open Software Sources from the main menu and check that you have all the repositories ticked.

---

### Post by Kdar on 2007-10-21
Ah.. ok. thks.

And how can I enable my Nvidia drivers?
It still doesn't work..

---

### Post by benerivo on 2007-10-21
Do you definitely have 'Proprietary  drivers' enabled in Software Sources?

---

### Post by Kdar on 2007-10-21
Ah.. I see it now.
Sorry about it.


Right now, I am can't seem to get my resolution right...

When I set it to my default monitor resolution, its too big.

But 1280 X 1024 is not correct. (but its fit to my monitor for some reason)

My monitor is wide-screen.

1600 by 1000
or something like that..

(I already have my NVIDIA drivers working... But is there some special NVIDIA setting menu? or I need to use Ubuntu settings? if so.. Which one.. Since.. I saw like two.)


------------

Do I need to make changes in "Screens and Graphics"  or in "Screen Resolution"  ?

---

### Post by shad0w_walker on 2007-10-21
You should be able to setup custom monitor resolutions using the new Xorg config tool, goto:

System > Administrations > Screens and graphics

You should have an option to choose your monitor type (The generics work fine for most cases. Only advantage of specifics is it knows all your limits precisely)
Select a monitor that suits your needs, by the sounds of things you need something like

```

Manufacturer: Generic
Model: LCD Panel 1600 x 1200

```

You probably also want to tick the 'Widescreen monitor' box on the monitor selection window. When you are done it will ask you logout to apply the changes.

---

### Post by Kdar on 2007-10-21
oh cool.
Thanks for explaining!! Its sure different from KDE, well at list a little. I guess I just need to get used to it, but I like it.


Few more questions.....

Since I installed it just today.

What kind of packages are "must have"? I am not really talking about software.. But more about things like drivers.. etc..
I have "build-essential" installed. What other to get?

Also.
In KDE.. I remember. I was able to get new Wallpapers online (but not going to the XXX-look.org page). It was in the monitor settings.
Is there something like this for Gnome?

---

### Post by shad0w_walker on 2007-10-21
I guess you got the monitor issue sorted out? If so awesome. 

As for 'must  have' packages, that's mostly a matter of opinion, I would personally have Amarok on my must have list along with wine and pmplib (For my Iriver) and in terms of drivers, the only thing i needed was the Nvidia drivers (Easily sorted using restricted drivers manager)

P.S. It will take some getting used to after using KDE for a while. I quite like the gnome environment (I like KDE as well but Kubuntu just didn't feel right to me for some reason)

---

### Post by Kdar on 2007-10-21
yes.. I getting to like Gnome too.

Its more mini and clean.

I don't know.. One of my friends always say bad things about Gnome. Like, its not for development, its pretty much dead, it use old development language.. etc..

But I am not sure about that, its maybe just a rant..

As for me.. I think I feel better with using Gnome then KDE.

--------
Almost forgot to ask one more thing, that kind of bugs me.

I had a NTFS external hard-drive.
When I had Kubuntu 7.04 it would not read it.

But when I installed Ubuntu 7.10, it was able read this external just find, play music, movies.. whatever... (without having to do anything)

The question is :   Is it save to write anything to this external hard-drive? I don't want to damage it, or information in it.

---

### Post by Kdar on 2007-10-21
Any one know about hard-drive question?

---

### Post by mistergq on 2007-10-21
the ability to write to NTFS was included with 7.10 for the first time (although, the ability has been around for awhile).  I am writing to NTFS partition without a problem.

---

