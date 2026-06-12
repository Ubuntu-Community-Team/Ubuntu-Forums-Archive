---
title: "Can I Customize the Install?"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by dewey1973 on 2007-06-15
I know one of the major advantages of Ubuntu is that it contains everything the typical user would need for their computing experience.  As a bit of an obsessive compulsive user, I was wondering if there was a way to choose what packages are installed during the initial setup of Ubuntu.  Other *nix OSs, like Fedora, allow you to customize the install.  If I only want the base OS and Firefox, can I make that happen?

I know you are able to uninstall, but the dependencies scare me a bit.  When I try to uninstall Evolution and its related packages and it tells me it will have to uninstall the Ubuntu Desktop, I get nervous.  I think it'd just be easier to start as clean as possible and choose my apps as I need them.

---

### Post by kerry_s on 2007-06-15
just do the minimal install and build up from there. grab the alternate cd or mini.iso, boot it up type server
then login
sudo su
apt-get install xorg gdm synaptic gnome-core
reboot
login
use synaptic to get what ever else you want.

ubuntu-desktop is just a metapackage to insure everything included in ubuntu gets updated, but if you remove some of the included apps you don't need it.

---

### Post by dewey1973 on 2007-06-15
Why "server?"  If it matters, I am installing on a laptop.

Will this base install include things like the network/wireless management that make Ubuntu the only distribution I've tied where my wireless works "out of the box?"

---

### Post by zvacet on 2007-06-15
[http://www.psychocats.net/ubuntu/minimal#barebones]("http://www.psychocats.net/ubuntu/minimal#barebones")

---

### Post by kerry_s on 2007-06-15
> **dewey1973 said:**
> Why "server?"  If it matters, I am installing on a laptop.

Will this base install include things like the network/wireless management that make Ubuntu the only distribution I've tied where my wireless works "out of the box?"

server is misleading, it is actually a barebones system, no gui nothing but the base. You apt-get what you want. the gnome network manager is> apt-get install gnome-system-tools netapplet < i think have'nt used it in a while. installing the gnome-core will get you the gui though from there you can look up what ever is not included in gnome-core and install it. i have not done a gnome-core install in a long time so i can't remeber what is part of that package, you'll just have to wing it and try different things till your happy.

---

### Post by dewey1973 on 2007-06-16
I tired both the mini.iso and the alternative iso and here is what happens.  With the mini.iso, I type in server and all of the command line stuff flies up the screen.  Then the screen goes blank, the CD drive stops, the hard drive is silent, and there is no network activity.

When I tried the alternate iso, I choose "Install a command-line system.  Same results as above.

Am I out of luck?

---

### Post by kerry_s on 2007-06-16
that's strange, does the live cd work? are you usung ubuntu now? have you tried pressing the f? keys and tried any of the boot options?

---

### Post by dewey1973 on 2007-06-16
The live CD worked in the past.  As far as boot options go, I wouldn't know what to do, so if you have any suggestions, let me know.

---

### Post by dewey1973 on 2007-06-16
Oh, and if it helps, I am trying to install Ubuntu on my [IBM T42 (2379-DXU.)]("http://www.thinkwiki.org/index.php?title=2379-DXU&printable=yes")

---

### Post by kerry_s on 2007-06-16
maybe your screen is just blanking/sleeping, try pressing the backspace to see if it wakes up.

You don't seem to be very familar with doing a custom install, are you sure thats really what you want to start with?

i think you should go xfce4

ubuntu xfce4-> [http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/xubuntu-7.04-desktop-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/xubuntu-7.04-desktop-i386.iso)
debian xfce4-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)


try the debian net installer, type> installgui
[http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

with debian unselect the desktop and standard when it come to that section, that will give you the base(nogui). then just do the regular apt-get

login
apt-get install xorg gdm synaptic gnome-core gnome-system-tools netapplet
reboot

---

### Post by dewey1973 on 2007-06-16
It's not sleeping or blanked.  And I know you probably didn't mean it this way, but I'm not an idiot.  I've been into computers for decades.  I tweak my windows boxes and mac boxes and now I'm exposing myself to the *nix world.  I can follow a guide like the one zvacet posted.

I got Ubuntu up and running with the Live CD and I learned how to install and uninstall programs.  I just don't want a lot of preloaded stuff on my machine because I'm finding that I can do just about everything I want to do with web apps.  That's the main reason I'm trying to make the switch in the first place.

I truly appreciate the help you all have offered and I'm still interested in making this work.  I'm sorry if I overreacted.

---

### Post by kerry_s on 2007-06-16
i don't think your an idiot, but i do think you need to get more familar with linux first. guide's are great but you need to read them and you at least need to know how to do the simple things with out a guide. For instance, like when i asked if you tried pressing the F1 through F8 keys, there's no guide for that and it's just something you need to try, basiacly when you press those keys to see the options you can use for problem systems, it shows the commands you can use to try and work past the problem. You also need to get familar with the apps you want to use, there are some 20,000+ apps to pick from you should not just jump in blindly. A custom install will start with no GUI so you want to at least be a little familar with the command line. With that guide you should already have a working minimal system, it has pic's and everything.

---

### Post by dewey1973 on 2007-06-18
> You also need to get familar with the apps you want to use, there are some 20,000+ apps to pick from you should not just jump in blindly.

Well that was my main point.  I don't want to just use what Ubuntu thinks I should use.  I want to start clean and decide for myself by reading articles, forums, blogs, etc.  I don't need an office suite or an email program.  Google has all of that.  So why not start clean?  Why not give your users a nice easy customization section of the install like Fedora or openSUSE?  It seems no better than the bloatware PC manufacturers put on your machine for you.

> ...it has pic's and everything.

That doesn't really help me when I have nothing on my screen and my laptop won't respond.

I'm all for slugging this out and making it work.  I want to learn and will do so.  I just came here because I thought it's be a nice friendly place to get some help.  Maybe you think people like me are ruining the Linux community.  Newbies.  There needs to be a middle ground between plug and play easy and entrenched super user difficult.  I'm totally impressed by the ease of the LiveCD install.  It is everything a non-geek needs to have a really great computing experience.  I also know that true geeks can get down and dirty and do incredible things with the OS.  But you have to get in somewhere!  And I wanted somewhere to jump in the was a little more manual than being given everything you could possibly need preinstalled.

---

### Post by dewey1973 on 2007-06-20
In case anyone wants to know, I got the minimal install to work using the mini iso and this boot command:

```
server floppy.floppy=thinkpad vga=771 noapic nolapic
```

---

