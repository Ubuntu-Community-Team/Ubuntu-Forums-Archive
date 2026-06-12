---
title: "Failed windows installer version"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by cocodamol on 2012-12-04
Hi guys, having had enough of windows Ive decided to join the Linux crew. 

This is my first time with Linux so please be gentle with me!

Ok, Ive downloaded the Ubuntu 12.10 windows installer.
Installed > restarted > select ubuntu > black error screen

[IMG]http://s8.postimage.org/6e4r7rymt/photo_20.jpg[/IMG]

My current set up was/is Windows 7 64
True crypt harddrive encryption upon boot.

As you can see I haven't got very far, could someone please advise what my next step is. Ive tried downloading and re installing again but the same problem happens.

Thanks in advance.

---

### Post by mikewhatever on 2012-12-04
Don't think you can use the Windows installer with disk encryption, sorry.

---

### Post by Mark Phelps on 2012-12-05
The Windows Installer version (known as Wubi) is NOT giving up  on windows; on the contrary, it is keeping you DEPENDENT on Windows because it relies on the Windows boot loader to launch the selection menu.

If you really want to get rid of Windows you need to wipe the drive of the OS partitions.

---

### Post by cocodamol on 2012-12-06
The idea really was to leave windows as a worst case backup in case I need to run windows only software for business. I suppose  I could always just have a separate HD for each OS as its only a laptop to plug and play when windows might be needed. Wont be able to go without encryption as its for business.

Is it possible I could  > remove truecrypt > run wubi installer again > then truecrypt the entire disk or do you think its going to causes issues again by having dual boot. But thinking about it Ive probably answered my own question better to have a clean single version of Linux on its own HD hey?

thank you

---

### Post by Carlefot on 2012-12-06
I have the same problem. My machine also runs Win 7 64, but no encryption is switched on.

---

### Post by black veils on 2012-12-06
i have seen there are different ways truecrypt can be installed and run, so i dont know how deep this thing goes on your system.

really looks like you will need to try leaving windows as is (but remove ubuntu/wubi in program and features).

then try installing ubuntu properly to another hard drive. if you want that encrypted, you can use trucrypt, but LVM full disk encryption would be less complicated i think. if using an external hard drive, probably best to go for a lighter system like Xubuntu or Lubuntu, they are based on Ubuntu, you can use the same applications.

if trucrypt is in the mbr or GPT equivalent, then i dont think you can have ubuntu on that computer, unless you play with it in a virtual machine inside Windows, as if you were running any other application.

---

### Post by cocodamol on 2012-12-06
I didn't realize Ubuntu had its own secure encryption system much easier to just turn it on and select a PW than setting up truecrypt.

I've swapped the HD, and done a clean install from the iso.

Set up and running perfectly without any trouble.  Its the first time tonight Ive set eyes on Ubuntu / Linux and I have to say I'm very impressed.  I was worried I was going to struggle to work my way around it but its very intuitive. The layout is a breath of fresh air, Im converted after just playing around with it for an hour. Just wish i'd thought of using it sooner!

---

### Post by mastablasta on 2012-12-07
you can also install truecrypt on ubuntu.
 
yeah the system is really easy to use. the only downside is that many hardware remains unsupported (manufacturers do not provide drivers) and also many games and certain enterprise software doesn't work in it (they do not make linux ports). however for everything else system is great. it is also very fast.

---

### Post by black veils on 2012-12-07
there are also different desktop environments which can be used instead of the ubuntu default (unity). xfce, gnome shell, kde and cinnamon. there are light options too.

just mentioning in case you need to navigate your computer with a different graphical user interface and configured layout. xfce and kde can be tweaked a lot to have 'taskbars' (panels) anywhere you want, and any size. personally i think xfce is the most customisable environment.

---

