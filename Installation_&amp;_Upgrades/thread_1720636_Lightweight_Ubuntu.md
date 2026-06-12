---
title: "Lightweight Ubuntu"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by Mr Stoozer on 2011-04-03
Hello to all.
I'm looking for a lightweight Ubuntu install. _For me_, Ubuntu 10.10 installs a lot of unnecessary applications and trying to uninstall them on a clean install is a nightmare and i just end up with too many breaks and unmet dependencies. I've had a look at the 10.10 mini iso available and have thus far not been able to install it (i suspect a hardware issue). Are there any other routes i can take or should i look into other distros? If other distros are the case, which do you recommend? Please bear in mind i am very new to *nix.
All i really want from the system is to be like a 'base' ubuntu with no applications, themes etc.
Thanks for any help.

---

### Post by beameup on 2011-04-03
"trying to uninstall them on a clean install is a nightmare"

I don't understand this. How are you uninstalling? Software center does that easily.

You looked at Lubuntu or Xubuntu for lightweights?

---

### Post by Dutch70 on 2011-04-03
This may be what you're looking for...
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1155961[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1155961")

If not, you'll find a lot of answers by googling "ubuntu minimal desktop"

---

### Post by galacticaboy on 2011-04-03
Try out Xubuntu, or Lubuntu. I am running Elementary OS Jupiter, it is great! Small and lightweight, not a lot of programs or anything!

---

### Post by snowpine on 2011-04-03
Here's the best tutorial I know of for building your own lightweight Ubuntu: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

If you are looking for "out of the box" then Lubuntu (LXDE desktkop) is the lightest. You can install LXDE on your current Ubuntu; you don't need to reinstall.

---

### Post by Mr Stoozer on 2011-04-03
> **beameup said:**
> "trying to uninstall them on a clean install is a nightmare"

I don't understand this. How are you uninstalling? Software center does that easily.

You looked at Lubuntu or Xubuntu for lightweights?

Not checked out L or X, will do, thanks. I'm doing it through synaptic. A basic example would be if i wanted to uninstall Totem player, i'd have to sacrifice Shotwell. The list goes on, and if i force it, i end up broken. Software center doesn't really have the functionality i'm looking for. TBH i think it's a bit naff. (they should go a la 'cydia').

@Dutch70
Reading through the thread now, looks quite interesting. Thanks.

@galacticaboy
I'm running elementary-jupiter too! That's how i became interested in slimming down Ubuntu. 

@snowpine
Thanks for the link. I had that page on my phone when i tried installing the ubuntu mini iso


So the consensus feels Lubuntu is most appropriate.  What are your thoughts on starting with a server install and building it up that way?

---

### Post by Dutch70 on 2011-04-03
I think this would be a good link for that, just change "ubuntu-desktop" to "lubuntu-desktop"
[[COLOR="RoyalBlue"]http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html[/COLOR]]("http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html")

---

### Post by Mr Stoozer on 2011-04-03
> **Dutch70 said:**
> I think this would be a good link for that, just change "ubuntu-desktop" to "lubuntu-desktop"
[[COLOR="RoyalBlue"]http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html[/COLOR]]("http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html")

Building from a server edition seems most appropriate based on my skill-set. Thank you again, i'll be sure to post how i get on.

I'd still be interested to hear of other alternatives.

---

### Post by snowpine on 2011-04-03
Don't start with a server install unless you actually plan to run a server. The Minimal CD is what you're looking for. See the tutorial I linked to in post #5.

---

### Post by galacticaboy on 2011-04-03
> **Mr Stoozer said:**
> Not checked out L or X, will do, thanks. I'm doing it through synaptic. A basic example would be if i wanted to uninstall Totem player, i'd have to sacrifice Shotwell. The list goes on, and if i force it, i end up broken. Software center doesn't really have the functionality i'm looking for. TBH i think it's a bit naff. (they should go a la 'cydia').

@Dutch70
Reading through the thread now, looks quite interesting. Thanks.

@galacticaboy
I'm running elementary-jupiter too! That's how i became interested in slimming down Ubuntu. 

@snowpine
Thanks for the link. I had that page on my phone when i tried installing the ubuntu mini iso


So the consensus feels Lubuntu is most appropriate.  What are your thoughts on starting with a server install and building it up that way?

Well, awesome! I thought Jupiter was as low as it got on Lightweightedness, it is running very very smooth on my PC.

---

### Post by Dutch70 on 2011-04-03
Alternatives to what exactly? I mean, what is it exactly that you'd like to accomplish?

---

### Post by Mr Stoozer on 2011-04-03
> **snowpine said:**
> Don't start with a server install unless you actually plan to run a server. The Minimal CD is what you're looking for. See the tutorial I linked to in post #5.

I cannot get the minimal CD to install as per my OP. ;)

---

### Post by Mr Stoozer on 2011-04-03
> **Dutch70 said:**
> Alternatives to what exactly? I mean, what is it exactly that you'd like to accomplish?

What i'd like is a usable ubuntu + gnome desktop system with none of the apps installed. A blank canvas if you will. (if you want an exhaustive list of my needs i can provide)

I've had a go at the server edition to which i build upon. I've got the system installed, and i've just installed xorg xterm gdm & metacity, rebooted and got a kernel panic! lol.
I'll have a tinker with it for now but doubt it'll be a usable system any time soon. -- all part of the learning curve i guess. :)

---

### Post by snowpine on 2011-04-03
> **Mr Stoozer said:**
> I cannot get the minimal CD to install as per my OP. ;)

Do you want some help with that or are you giving up? ;)

If you want assistance, follow along with the tutorial in my post #5 and let me know which step you're stuck at, along with any specific error messages.

---

### Post by Mr Stoozer on 2011-04-03
> **snowpine said:**
> Do you want some help with that or are you giving up? ;)

If you want assistance, follow along with the tutorial in my post #5 and let me know which step you're stuck at, along with any specific error messages.

Thanks. I followed the tut on that site, when i got to here ([www.psychocats.net/ubuntu/images/minimallucid12.png](www.psychocats.net/ubuntu/images/minimallucid12.png)) and chose continue (blank entry) the screen goes blank (blue) with a grey line at the bottom, no errors, no disk activity, no nothing. I left it overnight *in-case* it was downloading/doing something in the background but nothing happened....

---

### Post by snowpine on 2011-04-03
> **Mr Stoozer said:**
> Thanks. I followed the tut on that site, when i got to [here]("http://www.psychocats.net/ubuntu/images/minimallucid12.png") the screen goes blank (blue) with a grey line at the bottom, no errors, no disk activity, no nothing. I left it overnight *in-case* it was downloading/doing something in the background but nothing happened....

Perhaps an obvious question, but are you connected to the Internet with a wired connection, and does your ethernet card require a restricted driver?

---

### Post by mörgæs on 2011-04-03
This script can help you to install without a lot of unnecessary apps:

[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by Mr Stoozer on 2011-04-03
> **snowpine said:**
> Perhaps an obvious question, but are you connected to the Internet with a wired connection, and does your ethernet card require a restricted driver?

Connected via Ethernet, when i get to here ([http://www.psychocats.net/ubuntu/images/minimallucid08.png](http://www.psychocats.net/ubuntu/images/minimallucid08.png)) it completes 100% successfully without complaint.
I'm not sure if my card requires a restricted driver or not, how would i find out? I only get my GPU drivers pop up on the list of restricted drivers available on first install. If that helps!

---

### Post by Mr Stoozer on 2011-04-03
> **mörgæs said:**
> This script can help you to install without a lot of unnecessary apps:

[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

No disrespect to you Sir, but i have no idea what that does! One of the first lines says "trap" & "reset" !!!!!! lol :)

---

### Post by snowpine on 2011-04-03
I believe you can also do a minimal command-line install from the Alternate CD even if you don't have internet connectivity, that might be worth a try.

Another alternative is to buy a larger hard drive; they are very cheap these days so getting the 5gb required for a full install should be no big deal. :)

---

### Post by Mr Stoozer on 2011-04-03
> **snowpine said:**
> I believe you can also do a minimal command-line install from the Alternate CD even if you don't have internet connectivity, that might be worth a try.

Another alternative is to buy a larger hard drive; they are very cheap these days so getting the 5gb required for a full install should be no big deal. :)

I'll give the CLI with no networking a go and report. Not sure where the HDD came into it. I have plenty of spare gigs. I just don't like bloat.

---

### Post by snowpine on 2011-04-03
> **Mr Stoozer said:**
> I'll give the CLI with no networking a go and report. Not sure where the HDD came into it. I have plenty of spare gigs. I just don't like bloat.

Well, you can always edit your Gnome menus so the application(s) you don't use do not appear in the menus. This is quicker and easier than a custom minimal install. Out of sight, out of mind. :)

Apart from saving a very small amount of HDD space, there is no benefit to removing an end-user application such as Totem.

---

### Post by Mr Stoozer on 2011-04-03
> **snowpine said:**
> Well, you can always edit your Gnome menus so the application(s) you don't use do not appear in the menus. This is quicker and easier than a custom minimal install. Out of sight, out of mind. :)

Apart from saving a very small amount of HDD space, there is no benefit to removing an end-user application such as Totem.

Nice idea, but not what i'm after really.
I just can't get past that screen on the mini installation.
With that said, I've opted for the server route.  I've been fiddling with that and have a usable GUI.  Just updating GRUB for the new server kernels, then remastersys'ing its current state before i break it! 

For anyone interested; once the base server is installed i ran:
sudo apt-get install xorg xterm gnome-core syanptic

This provided the bare-bones to start building (bare enough for me anyways!)

Thank you for all of your valuable input. :KS

---

