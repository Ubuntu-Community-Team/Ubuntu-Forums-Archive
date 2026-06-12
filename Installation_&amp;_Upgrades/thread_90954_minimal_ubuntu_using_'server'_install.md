---
title: "minimal ubuntu using 'server' install"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by jan-banan on 2005-11-16
i am tired of finding some stupid programs i never use, or cant use, or never will use, when i upgrade my system, so i want to flush it out and be able to choose asolutely everything in my system, as in windows (my windows xp is 150Mb installed...) so i am going to do a server installation and choose every package on my own, but! if i download "ubuntu-desktop" after doing the server installation (i did that once) i get a worthless system and all of the apps i want to e free from. 

so how am i supposed to do this, and get it right? 

to begin with, is it possible at all using ubuntu? do i have to use packages at any occasion, if i for example want open-office2, do i have to download the "ubuntu-desktop" and install everything else at the same time? can i avoid these packages?

should i maybe use another dist? :o

---

### Post by chris_andrew on 2005-11-16
Hi,

Select Server install.  When this is finished, 

apt-get xfce gdm xwindow-system and maybe firefox (browser).

Ubuntu is after all, just debian, with bells and whistles (that I love).

See this thread for better installation details.

Cheers,

Chris.

---

### Post by tomski on 2005-11-16
[QUOTE=chris_andrew]

See this thread for better installation details.

Cheers,

Chris.[/QUOTE]


er what thread????

---

### Post by jan-banan on 2005-11-16
[QUOTE=chris_andrew]Hi,

Select Server install.  When this is finished, 

apt-get xfce gdm xwindow-system and maybe firefox (browser).

Ubuntu is after all, just debian, with bells and whistles (that I love).

See this thread for better installation details.

Cheers,

Chris.[/QUOTE]

why xfce? and what thread?

---

### Post by jan-banan on 2005-11-18
*bump*

hey, any of you guys, is it possible? i'm really thinking about trying debian, but i want to give ubuntu a chance, i like ubuntu.

---

### Post by az on 2005-11-18
Well, what do you want to run?

Install the base system (using the server option) and log in and run

sudo apt-get install x-window-system-core gdm mozilla-firefox xterm synaptic icewm menu

or

sudo apt-get install xubuntu-desktop

or 

sudo apt-get install x-window-system-core gdm gnome  openoffice2

or
sudo dselect

and select ubuntu-desktop for installation.  It will show you a list of packages that depend on it.  You can then go down the list and "deselect" (press "-") the one's you do not need.  Using dselect, the other selected packages will stay selected.  Press g (for "go") to make it download and install those remaining packages.

There are even more options.  Do you need something else that is more specific?

---

### Post by Biased turkey on 2005-11-18
[QUOTE=jan-banan]

should i maybe use another dist? :o[/QUOTE]

You are the perfect candidate for installing Gentoo.
After installing the Gentoo universal install CD, you have  ... nothing , just the nano console editor lol.Then you can add anything you want on top of that: Xserver for the graphics, then an Xclient like xfce4, fluxbox or icewm.
You need a web browser? install firefox.
That's exactly what I did when I installed  Gentoo

The Ubuntu server install option just does the same .
As Azz says: **what do you want to run ? **

---

### Post by steeley on 2005-11-19
[QUOTE=azz]

Install the base system (using the server option) and log in and run

sudo apt-get install x-window-system-core gdm mozilla-firefox xterm synaptic icewm menu
[/QUOTE]
I've been looking at doing a similar thing and did try the above.
apt-get cannot find icewm, and throws an error for menu.

looked at dselect, but could not get to install ubuntu-desktop.
rebooted, and the machine hangs at "starting periodoc command scheduler"
This machine runs full desktop Ubuntu fine when I plug its original drive back in.
My advice is if you want a compact fast minimal Linux system for lower powered machines, use Damn Small Linux. I use this on an old laptop and it is very good.

---

### Post by az on 2005-11-19
[QUOTE=steeley]
apt-get cannot find icewm, and throws an error for menu.
...

looked at dselect, but could not get to install ubuntu-desktop.[/QUOTE]


You do not need anything other than the install disk to install ubuntu-desktop.  What was that problem?

As for icewm and menu, they are in universe.  You need to enable those repositories.

---

### Post by chris_andrew on 2005-11-26
jan-banan,

Thanks for the private message.  I've just seen it.  Hopefully the answers that followed in your thread will explain what you need.

Thanks,

Chris.

---

### Post by MetalMusicAddict on 2005-12-02
[QUOTE=jan-banan]i am tired of finding some stupid programs i never use, or cant use, or never will use, when i upgrade my system, so i want to flush it out and be able to choose asolutely everything in my system, as in windows (my windows xp is 150Mb installed...)[/QUOTE]
Thats sick! Best I could do with [nLite]("http://nuhi.msfn.org/") was 500megs installed.

---

### Post by christooss on 2005-12-02
Wait for my Ubutnu lite howto :) It hasnt been authorised yet :)

---

### Post by MetalMusicAddict on 2005-12-02
[QUOTE=christooss]Wait for my Ubutnu lite howto :) It hasnt been authorised yet :)[/QUOTE]
Cool. I didnt have much luck with UbuntuLite but Ill give it another look. :)

---

### Post by bwog on 2005-12-03
There is an xubuntu howto in the wiki, which shows how to install xcfe on top of a server install. This results in a licht installation: [https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29](https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29)

I tried it and found it easy to implement.

---

### Post by christooss on 2005-12-03
But xubununtu is starting twice as much time as Ubuntulite does. :)

---

### Post by MetalMusicAddict on 2005-12-03
[QUOTE=bwog]There is an xubuntu howto in the wiki, which shows how to install xcfe on top of a server install. This results in a licht installation: [https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29](https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29)

I tried it and found it easy to implement.[/QUOTE]
I have tried that out. Its nice but I want tools that are Ubuntu and mostly a familar enviorment.

---

### Post by christooss on 2005-12-03
[http://ubuntuforums.org/showthread.php?t=98233](http://ubuntuforums.org/showthread.php?t=98233)

---

