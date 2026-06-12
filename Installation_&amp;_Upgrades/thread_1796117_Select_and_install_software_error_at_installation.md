---
title: "Select and install software error at installation"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by Neraste on 2011-07-03
Hello everyone!

I'm trying to install **Ubuntu Studio 11.04** on my **EeePC** laptop, but I have a problem at the *Select and install software* step: it can't be achieved correctly and I have to go on the next step.

Then, when I boot my computer, after choosing the right OS in GRUB menu, I have a black screen where nothing happens. I have access to the terminal mode, but not to the GUI; this seems normal because nothing but the kernel has been installed due to the error, isn't it?

If I try to install the Ubuntu Studio packages manually with *apt-get*, I receive an error message like: "following packages have unsatisfied dependencies," then a list of the packages and "E:defective packages."

Where I am wrong? Or is there a problem with the Ubuntu Studio packages?

Thank you a lot for your help!

---

### Post by dino99 on 2011-07-03
so from the terminal, run:

sudo apt-get update
sudo apt-get install -f
sudo apt-get install ubuntustudio-desktop

sudo dpkg --configure -a

note: check about installed graphic driver with synaptic

sudo synaptic

as synaptic is opened, check the repo tab and select "main server", the different repos need to be checked too to get all the packages

---

### Post by Neraste on 2011-07-03
Thank you for this quick answer!

Ok, I'll try it and tell you how does it like.

---

### Post by Neraste on 2011-07-03
Well, it wasn't very successful...

Here are the result details of your instructions:

[LIST]
[*]*apt-get update* : list of 17 items, mostly translations (I use a French version of Ubuntu Studio).
[*]*apt-get install -f* : no package were installed.
[*]*apt-get install ubuntustudio-desktop* : same previous error.
[*]*dpkg --configure -a *: nothing shown (but I guess it's regular).
[*]*synaptic* : command not found.
[/LIST]
T.T What should I do?

**Edit :**
My */etc/apt/source.list* file contains only one line: *deb cdrom:[Ubuntu-Studio 11.04 _Matty Marwhal_ - Release amd64 (20110426.1)]/ natty main multiverse restricted universe*.

---

### Post by Neraste on 2011-07-05
Up!

No one can help me? T_T

According to [this mailing list archive]("https://lists.ubuntu.com/archives/ubuntu-studio-devel/2010-September/002622.html"), it seems that the same error has occur for other versions of Ubuntu Studio, which were due to internal bugs.

I have re-downloaded an ISO and re-try to install it, but the error is still there.

I (hope to) use the French x64 version of Ubuntu Studio 11.04.

What may I do?

Thanks for your your advices.

---

### Post by dino99 on 2011-07-05
sudo gedit /etc/apt/sources.list might looks like:

(copy & paste)
  
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates restricted main multiverse universe
  
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security restricted main multiverse universe
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) natty main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-proposed restricted main multiverse universe

and you should stay with 32 bits version (less headaches :))

note: as you can see , the cdrom is deactivated (normal if you want to get updates from the net)

---

### Post by Neraste on 2011-07-05
OK, I will add those lines to *sources.list* and then, I will install the 32 bits version if it doesn't work (but I will be able to do this last one this evening only).

But currently, my only text editor is *vi*! I have neither *gedit*, nor *nano *(nor *man*, furthermore) and when I want to install one of them, I am asked to put the Ubuntu Studio CD; that's weird because I don't have that kind of stuff in my notebook...

---

### Post by Neraste on 2011-07-08
Well, I've added those lines to my */etc/apt/sources.list*, but then each time I wanted to use *apt-get install*, I'm told that the package can't be found (even for *man*)...

So, I've downloaded a fresh version of Ubuntu Studio (still x64... for a last test...) via the torrent link and I've installed it. This time I've chosen an us mirror because I'm currently in the USA and things has been a little bit different. Even if the *select and install software *step has failed again, I've been able to install all the needed packages with *apt-get* after rebooting my computer.

Now, my system is running, *apt-get* has a good behave and my */etc/apt/sources.list* is correct. All is fine! But I don't know what happened during the install of Ubuntu Studio... Problem solved, but with bypass.

Anyway, thank you **dino99** for your help!

---

