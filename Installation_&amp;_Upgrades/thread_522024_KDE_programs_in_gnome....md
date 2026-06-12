---
title: "KDE programs in gnome..."
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by myk.dinis on 2007-08-10
I like certain kde programs...
amarok, k3b, and ktorrent (especially ktorrent)...

I want them to run in Gnome. I like Gnome better than KDE...I like it's simplicity...

Is there anything I can do (short of running both WM's) to make this work...

I want to go back to gnome, it felt comfortable and nice...

It had a lot of the stuff I like except those three items...

I used adept manager to install gnome-desktop...

I set GDm a my default Wm...I haven't rebooted yet but my divers and xorg.conf et al are all good to go...

BTW my /home is on a separate partition...will my access to these files be affected negativelyby this switch...

I fully plan on removing KDE in it's entorety )except for those 3 programs....) 

Is this do-able and safe?

thanks 
myk

---

### Post by Rondonjin on 2007-08-10
> **myk.dinis said:**
> I like certain kde programs...
amarok, k3b, and ktorrent (especially ktorrent)...

I want them to run in Gnome. I like Gnome better than KDE...I like it's simplicity...

Is there anything I can do (short of running both WM's) to make this work...

I want to go back to gnome, it felt comfortable and nice...

It had a lot of the stuff I like except those three items...

I used adept manager to install gnome-desktop...

I set GDm a my default Wm...I haven't rebooted yet but my divers and xorg.conf et al are all good to go...

BTW my /home is on a separate partition...will my access to these files be affected negativelyby this switch...

I fully plan on removing KDE in it's entorety )except for those 3 programs....) 

Is this do-able and safe?

thanks 
myk

You don't have to install all of KDE to run one or two programs in Gnome. Just select the programs you want to install with Synaptic and it will install the required dependencies for you, at minimum kdelibs.

Wayne

---

### Post by merlinus on 2007-08-10
You can remove kde following these instructions, and then use Synaptic to install the three apps:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

-merlin

---

### Post by forestpixie on 2007-08-10
I run all 3 of those in my setup - just install them, you can sometimes get a few problems but there not unsurmountable 

Have you just got Kubuntu on your PC or do you have both and choose at login - because you can if you want. When I started with Ubuntu I wanted to have a look at all 3 - so had Xubuntu as well. I did in the do a reinstall.

If you Kubuntu and want Ubuntu you can do

sudo aptitude install ubuntu-desktop 

it will then ask which you want as default, or as you are saying you can reinstall Ubuntu

I beleive the way to do it is to go for amnual partitioning and when you get the choice install root to its partition and format , point the install at your existing /home partition and DON'T cliclk the format box and that should be fine.

Edit - as they both said !!  :D

---

### Post by myk.dinis on 2007-08-10
if I sudo aptitude update does that change synaptic to aptitude?

I like the gui...

Any thoughts?

---

### Post by forestpixie on 2007-08-10
not quite sure what you mean, I've used both apt-get and aptitude and nothing GUI wise has changed for me.

I think aptitude is the same as apt-get but can sometimes deal with dependencies better (could be wrong - that's from memory)

Edit - Synaptic isn't a different thing to aptitude - it's the GUI for both

---

