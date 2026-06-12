---
title: "cant find KDE with apt-get or on Synaptic"
date: 2004-10-24
forum: Installation &amp; Upgrades
---

### Post by nyx on 2004-10-24
Hey,
I'm new to ubuntu, another member of my linux user group reccomended it over gentoo, so I figured "why not". 
But I personally really really dislike gnome.
So when I did a search for KDE, I couldn't find it anywhere on the list.
Nor any other GUI's such as enlightnment or any of them!
Why is this?  
Am I doing something wrong?
i'm currently not logged into root, should I be to find them?   
BTW, thanks for the other FAQs, they were quite helpful for us ubuntu newbies.

---

### Post by Seti on 2004-10-25
Ubuntu only supports Gnome at this time I think, which is a fine window-manager if you give it a chance. Remember, this is an early release only; KDE and Fluxbox may come L8R.

---

### Post by nyx on 2004-10-25
ok I can be patient with gnome for awhile
Could you please help me though?
I truly can't stand the default way gnome makes you browse the file system through gui.
You click on a folder and it opens another window.  I want to go to root and access my other hard drive but it wont let me go back into root.
I'm new with linux so bear with me, this is probably incredibly simple but I dont even see it in gnome documentation.
Perhaps ubuntu isn't quite yet for me, although it seems quite stable at this point, but I really need to access my other HD so I can transfer some files over to this hard drive from it.

---

### Post by jmings on 2004-10-25
[QUOTE=nyx]ok I can be patient with gnome for awhile
Could you please help me though?
I truly can't stand the default way gnome makes you browse the file system through gui.
You click on a folder and it opens another window.  I want to go to root and access my other hard drive but it wont let me go back into root.
I'm new with linux so bear with me, this is probably incredibly simple but I dont even see it in gnome documentation.
Perhaps ubuntu isn't quite yet for me, although it seems quite stable at this point, but I really need to access my other HD so I can transfer some files over to this hard drive from it.[/QUOTE]

Open nautiuls -> Edit -> Prefernces -> Behaviour -> Check "Always open
in browser windows"

---

### Post by JProgrammer on 2004-10-25
Ok to turn off spatial browser I belive in Gnome 2.8 it's in the options for nautilus.

As for KDE it's in Universe so just enable that and apt-get install kde

---

### Post by nyx on 2004-10-25
[QUOTE=jmings]Open nautiuls -> Edit -> Prefernces -> Behaviour -> Check "Always open
in browser windows"[/QUOTE]

lol that worked!  I tried every option on there before I swear!

JProgrammer, how do I enable universe?  I'm not familiar with it yet.

---

### Post by JProgrammer on 2004-10-25
See [here](http://wiki.ubuntu.com/UniversePackages)

---

### Post by nyx on 2004-10-25
Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by JProgrammer on 2004-10-25
[QUOTE=nyx]Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) - stat (2 No such file or directory)[/QUOTE]
 You have a space in between bin and ary

---

### Post by nyx on 2004-10-25
[QUOTE=JProgrammer]You have a space in between bin and ary[/QUOTE]
And how do I fix that?
They dont give me an option to edit that part.

---

### Post by JProgrammer on 2004-10-25
sudo gedit /etc/apt/sources.conf

---

### Post by Seti on 2004-10-25
NEVERMIND!!
Just installed KDE no problem.
Added universal to the sources through synaptic, then did apt-get install kde...
and presto! Now have KDE working fine. But what is this about it not being supported by Ubuntu yet? I don't udnerstand.

---

### Post by JProgrammer on 2004-10-25
Some of the developers paid by Canonical are also Gnome developers and Ubuntu is a Gnome distribution with their release cycle tied closely to that of stable releases of Gnome. Which also has a 6 month release cycle unlike KDE

---

### Post by nyx on 2004-10-26
[QUOTE=JProgrammer]Some of the developers paid by Canonical are also Gnome developers and Ubuntu is a Gnome distribution with their release cycle tied closely to that of stable releases of Gnome. Which also has a 6 month release cycle unlike KDE[/QUOTE]
 My sources.conf seems to be blank?  I don't understand why this is?  
Nothings simple.  lol

---

