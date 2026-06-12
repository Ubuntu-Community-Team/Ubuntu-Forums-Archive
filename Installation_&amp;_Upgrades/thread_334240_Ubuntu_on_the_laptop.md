---
title: "Ubuntu on the laptop"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by JermainWijnhard on 2007-01-08
Hi,

I'd like to put ubuntu on my laptop but i'd like to know a few things before i start with it

 - if new updates come, will it work if i just download them from the net and put them on my laptop from my USB disk?
 - Will i have to uninstall all win apps before starting, or will everything be cleaned out at the install?
 - What will i have to keep in mind
 - What are the most common mistakes that i would have to watch out for?
 
Note, all files have been backed up, so there isnt much to lose for me.

---

### Post by pebo on 2007-01-08
> 
 - if new updates come, will it work if i just download them from the net and put them on my laptop from my USB disk?

I believe it can be done but it's not a straightforward process - a broadband connection is a big bonus

> 
- Will i have to uninstall all win apps before starting, or will everything be cleaned out at the install?

Not if you partition your hard drive so as to dual boot - read [this]("http://www.psychocats.net/ubuntu/partitioning") tutorial for info. No need to lose your windows

> 
- What will i have to keep in mind

That there is good documentation in the wikis and at psychocats, and failing that good support on the forum
That the most frustrating part will be setting up your hardware
That all the pain and suffering of learning a new OS will reap its rewards in the end:) 

> 
- What are the most common mistakes that i would have to watch out for?

Well one would be to think that linux works like "that other OS"

Cheers and good luck;)

---

### Post by JermainWijnhard on 2007-01-09
Im having a slight panic attack here..

booted my laptop from ubuntu and double clicked install. After a long a time of loosing speed (because it was reading the cd) it just decided to quit reading the cd and just froze.

Please help,.. :(

---

### Post by JermainWijnhard on 2007-01-09
i managed to reset. ignore the above post ^^

The brick bashing treatment worked and my screen doesnt show the ubuntu screen anymore. Time for a 2nd attempt.

---

### Post by Rhubarb on 2007-01-09
If you don't get any success, try running "Check CD for defects" option (this comes up just after you boot up your PC on the Ubuntu live CD).

---

### Post by skinny on 2007-01-09
> **JermainWijnhard said:**
> i managed to reset. ignore the above post ^^

The brick bashing treatment worked and my screen doesnt show the ubuntu screen anymore. Time for a 2nd attempt.

Similar thing happened to me when I installed Dapper 6.06 onto my laptop. I tried using the LiveCD, that failed, then tried using an Alternative cd, and that produced problems like you're describing - the install would get so far, and then just appear to hang [with a blank screen]. I retried a couple of times with the Alternative cd, checked for defects etc but nothing appeared faulty.  Decided to give it one last go, and when it produced the blank screen once again and then appeared to hang, I just desperately pressed Enter a couple of times on the keyboard.  Whirring started again (the cd-rom sounds like a hoover on my old Toshiba), and then the cd-rom popped out and it rebooted.:mrgreen: 

If it works it works...

good luck,

$

---

### Post by JermainWijnhard on 2007-01-09
Thanks Rhubarb,

The 2nd attempt failed aswell and i just checked the finish. It seems i'll have to try something else ^^


Skinny,

I'm gonna try your advice right now, desperate times call for desperate measures. As you said, if it works it works, I'm gonna bash that enterkey like it burned down my temple and disgraced my family :twisted:


Edit: The Enter key was a no-go :(

---

### Post by Rhubarb on 2007-01-09
You might have a bad burn of your Edgy CD there.
Try burning the iso at a slower speed (4x or 8x) and try again.

---

### Post by skinny on 2007-01-09
Are you using a LiveCD or an Alternate CD?

---

### Post by JermainWijnhard on 2007-01-09
You know,.. thats actually a good question ><

I went to this page [http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download) and and just downloaded '**Ubuntu 6.10, The Newest Ubuntu Release**' without paying attention. :-k

---

### Post by skinny on 2007-01-09
Alternate cd : No GUI available here, its terminal stylee installation
Live cd : Boots to a GUI, point and click style installation

Both are normally available from whichever mirror you choose to download from, although Alternate cd is often found under "Other installation options" links.

Assuming you've not downloaded a different cd than earlier, you mention "double-clicking install" indicating you're trying to install from a Live cd.  If its not tooooo much of a pain I'd really suggest trying to install from an Alternate cd. A number of people complain of problems when attempting installs from the Live cd, but the Alternate cd normally works ok for them.

My earlier advice of whacking the Enter key a couple of times [at a blank screen] only worked with the Alternate cd, which may just work fine for you.  The Live cd totally froze on me.

If the specs of your laptop are not tremendous, I would recommend looking into installing Xubuntu (however this can always be done after installing any Ubuntu flavour and then installing the Xubuntu desktop environment once everything is fine).  It is somewhat lighter on resources than Gnome or KDE (the other main desktop environments - basically the look and feel of the system).

Hope this helps :)

$

---

### Post by JermainWijnhard on 2007-01-09
Ooh ive never done terminal style inatallations before, sounds fun. I have faith in my laptop, so i went for Kubuntu alternate. Its dl-ing as im typing this. But i just wanted to say thanks for your patience. I'm gonna go do some reading on how to install the alternate rather than making you guys write the whole thing out for me. I'll post again later, when ive started the installation.

Edit:

Okay,.. its probably me but i cant find an installation guide for the alternate cd, i tried the upper right search function and google without succes. Is it about the same as the LiveCD or is there a man page out there that can help me? If someone can link me up it's much appreciated


Just some notes to myself, they may also come handy when i have another question (rather than "this thingy doesnt like.. do stuff")

It has C and D partitions, I plan to dedicate the D partition to Kubuntu on installation, assuming i can always safely partition afterwards.

---

### Post by skinny on 2007-01-09
The Alternate cd installer leads you through the process in much the same way as the graphical installer on the Live cd would, so hopefully it should be fairly straightforward to install.

However, as usual (and I totally recommend as a bookmark [psychocats.net]("http://www.psychocats.net/ubuntu/index.php")), aysiu links to a guide which can be found [here]("http://users.bigpond.net.au/hermanzone/").

$

---

### Post by JermainWijnhard on 2007-01-10
Ive installed kubuntu, but then the loging didnt work. Then i thought i was being dumb and miss typed / forgot my own login and pass en installed all over. the second time i left the login name 'ubuntu' (default) and made my pass 'jermain' purpusely not using caps (my laptop is never online so it doesnt matter if my loging and pass are written in the forum). I followed this guide:

[https://wiki.kubuntu.org/KubuntuOEMInstaller](https://wiki.kubuntu.org/KubuntuOEMInstaller)

difference being that i chose not to dual boot, but formatted the whole HD (2nd option in the partitioning menu). Does anyone have advice or a solution?

Edit: problem solved had to log in as OEM, i spoke before i thought -.-

Installation complete! I am now a proud user of Kubuntu!

Thank you guys for your help, i hope i can help someone in the same time :)

---

### Post by Rhubarb on 2007-01-10
Uh, why did you install as OEM for?
Doesn't make a lot of sense, unless you're an OEM computer company.

Doesn't matter too much anyway, you end up on the Kubuntu desktop either way.
If there is a next time you install (K)ubuntu, and you have to use the alternate CD, then choose the "Install in text mode" option.
The OEM step is just unnecessary.

---

