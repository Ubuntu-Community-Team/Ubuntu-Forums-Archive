---
title: "NEW to Ubuntu. How do I install &quot;Cairo Dock&quot;??"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xwat17x on 2008-10-13
okay. i just got ubuntu 8.10 a few days ago and dont know much about it yet.

But i was trying to download and install the cairo dock, but i have no idea how.

I went to a site and it said to use deb or repository, but when i do...

This comes up in the terminal:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I dont know what to do.

---

### Post by overdrank on 2008-10-13
> **xwat17x said:**
> okay. i just got ubuntu 8.10 a few days ago and dont know much about it yet.

But i was trying to download and install the cairo dock, but i have no idea how.

I went to a site and it said to use deb or repository, but when i do...

This comes up in the terminal:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I dont know what to do.

Hi and moved to  Intrepid Ibex Testing and Discussion
Intrepid is still testing stage, you can use the command in the terminal
```
sudo dpkg --configure -a
```

---

### Post by SpenceMakesSense on 2008-10-13
also to install with repository you must go to a terminal and type
```
sudo apt-get install cairo-dock
``` you could also look around synaptic

---

### Post by raymose on 2008-10-15
administrator@Ubuntu-desktop:~$ sudo apt-get install cairo-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cairo-dock

why??

---

### Post by talkingwires on 2008-10-15
> **raymose said:**
> administrator@Ubuntu-desktop:~$ sudo apt-get install cairo-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cairo-dock

why??You probably don't have the Universe repositories enabled. Launch Synaptic, Select Package/Repositories from the menu bar. Now select "Community-maintained Open Source software (universe)". Synaptic will prompt you to refresh your package lists, and now you should be able to install it.

---

### Post by mrgnash on 2008-10-15
If you're new to Ubuntu, what are you doing using a development version? That is a really bad idea...

---

### Post by talkingwires on 2008-10-16
> **mrgnash said:**
> If you're new to Ubuntu, what are you doing using a development version? That is a really bad idea...Maybe they heard that the latest version of a distro with considerable hype surrounding it is shipping in two weeks and wanted to see what the fuss was about? My first experience was with the Warty beta, Ubuntu didn't even *have* a stable release. I liked it enough to keep using it all these years.

---

### Post by mnwr on 2008-10-18
Hi,

I'm pretty new to Ubuntu but not a complete newbie, I had gutsy before I installed Intrepid. I wanted to install a dock apparently cairo dock so I just copied the command line syntax which spencer gave,to a terminal and it promted for my password so I input the password and it started downloading and completed the installation but my problem is where can I find the dock? It's not in under the accesories, (thats where AWN was when I installed that). Any suggestions pls?

Thanks

---

### Post by Hairy_Palms on 2008-10-18
just press alt-f2 to bring up a run dialog and enter cairo-dock should run it

---

### Post by owenll on 2008-10-18
> **mnwr said:**
> Hi,

..my problem is where can I find the dock? It's not in under the accesories, (thats where AWN was when I installed that). Any suggestions pls?

Thanks It's under system tools on my computer

---

### Post by ronacc on 2008-10-18
It dosent show up anywhere in my applications menu either ( anywhere ) but you can start it from terminal or create a launcher . I'm 64bit here , not sure if that makes a difference .

---

### Post by mnwr on 2008-10-19
Hi,

Hey that worked. thanks guys, I have one more question. Does anyone know where i can get themes for the dock? And also I'd appreciate it if someone points me to some nice GTK 2.0 themes for gnome, ones with progress animations and the whole glossy effects. Where can i find the best themes?

Thanks

---

### Post by ronacc on 2008-10-19
try here [http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by plun on 2008-10-19
There are 3 excellent new community themes within Intrepids repo

**Dust, Kin, New Wav**e 

```
sudo apt-get install community-themes
```

Prefs > Appearance


Info
[http://packages.ubuntu.com/intrepid/community-themes](http://packages.ubuntu.com/intrepid/community-themes)

:)

---

### Post by hardhu on 2008-10-19
> **SpenceMakesSense said:**
> also to install with repository you must go to a terminal and type
```
sudo apt-get install cairo-dock
``` you could also look around synaptic

Am I wrong, or isn't the cairo-dock package in Intrepid  (1.5.5.3) quite older than the one available from cairo repository (1.6.2.3)?
And also the package cairo-dock-plug-ins is not available in intrepid.

---

### Post by fabounet on 2008-10-20
you're right, and that's why we're maintaing our own repository
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")
1.6.3 will be out soon, so here is an excellent reason to use it from now ;-)

---

### Post by hardhu on 2008-10-22
> **fabounet said:**
> you're right, and that's why we're maintaing our own repository
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")
1.6.3 will be out soon, so here is an excellent reason to use it from now ;-)

Ok, since the forum on the site is only in French, I try to post my question here to see if you're still reading this thread. I have installed the two packages (cairo-dock and cairo-dock-plug-ins) form your repository, but I have this problem: when I set it to auto-hide, after a random amount of time the dock becomes invisible, that is I can see the process running, but I don't see it any more on the bottom panel of Gnome desktop.

---

### Post by fabounet on 2008-10-22
you can post on the forum, you wouldn't be the first one to do this ;-)
random = ? which actions do you do before it happens ?
isn't it under the gnome-panel ?

---

### Post by hardhu on 2008-10-22
> **fabounet said:**
> you can post on the forum, you wouldn't be the first one to do this ;-)
random = ? which actions do you do before it happens ?
isn't it under the gnome-panel ?

Yes, you're right. That is, when I launch cairo-dock, it stays above the gnome-panel, but after a random amount of time it disappears to my eyes, because it goes under the gnome-panel, and since in its properties I set the panel to expand, I couldn't see the dock anymore. After disabling the "expand" property of the panel, I have been able to see again the dock, and to use it. Thanks for your suggestion.

Since you're reading this thread, I take the chance to remark this possible bug: I have set the views of the dock to curved, and to parabolic for the sub-docks. Then I set the position of the dock to right, and then again back to bottom. That worked for the dock, but the sub docks keeps on showing on the right edge of the screen, as you can see in the attached screenshot:
[IMG]http://img151.imageshack.us/img151/8466/screenshotvh9.png[/IMG]

---

### Post by fabounet on 2008-10-23
try with cairo-dock --keep-above, but I would suggest to remove your gnome-panel (at least, the most possible) and use the dock only. :-)

for your problem, it's probably a refresh bug, sorry ^_^
I think it may work fine after you restart the dock.

---

### Post by fab.head on 2008-10-23
Hi fabounet!

Great news! Thanks for the 64-bit version :)

I'll try it first thing tomorrow morning

Cheers

---

