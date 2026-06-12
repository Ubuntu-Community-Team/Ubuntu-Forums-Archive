---
title: "Upgrade to 10.10 boots only in text mode"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by lonewolf88 on 2011-02-20
Hi all,

Upgraded (?) my Toshiba T110 laptop from 10.04 LTS to 10.10 via update manager.

Previously booted on kernel 2.6.32-28 in 10.04;  all worked fine.

Now I have the option of 2.6.32-28, or 2.6.35-25, both of which boot only in text mode, ask for my user name and password; finally finishing with prompt "john@jp-laptop:~$"

After some research I tried running at this prompt "startx" which failed;  I then tried "sudo aptitude install ubuntu-desktop", which went through a screen of text, then reverted to the prompt as above.

I then tried "startx" again, with no luck.

Bit of a loss what to do next, as I am still fairly new to all of this;  can some kind person advise please?

And as usual, Thanks in Advance!

---

### Post by dino99 on 2011-02-20
step by step:

into synaptic repo tab: check you only have genuine maverick repo (uncheck if necessary)

sudo rm /var/cache/apt/archives/*
sudo rm /etc/X11/xorg.conf
sudo apt-get update
sudo apt-get install -f
sudo dpkg --reconfigure -a

then reboot

---

### Post by lonewolf88 on 2011-02-20
> **dino99 said:**
> step by step:

into synaptic repo tab: check you only have genuine maverick repo (uncheck if necessary)

sudo rm /var/cache/apt/archives/*
sudo rm /etc/X11/xorg.conf
sudo apt-get update
sudo apt-get install -f
sudo dpkg --reconfigure -a

then reboot

Thanks for prompt reply!

Not sure how to do the first "into synaptic repo tab" bit on the text screen, in fact not sure how to do it all!  :(.

Running the first command ".../archives?*" brings up error message "Argument list too long"..

Also tried apt-get update again; an error comes up the the Debian repostory could not be accessed - bad name extension.

Errors when trying "startx" previously, which I should have posted,  (my bad, sorry) were :-

(EE) No kernel modesetting driver detected

(EE) Screen(s) found, but none have a usuable congig.

Fatal server error: No screens found.

---

### Post by Heliguy on 2011-02-20
Hi

I don't know if this will help but when I upgraded my server to 10.10 the package manager booted the grub installer behind the package manager. I found this was a bug with the manager and I had to restart a half updated system into SSH (Text Mode). So I restarted and ran sudo dpkg --reconfigure -a. Thats slightly off the subject though. It looks like Xserver isn't starting because you have no graphics card drivers.

---

### Post by lonewolf88 on 2011-02-20
> **Heliguy said:**
> Hi

I don't know if this will help but when I upgraded my server to 10.10 the package manager booted the grub installer behind the package manager. I found this was a bug with the manager and I had to restart a half updated system into SSH (Text Mode). So I restarted and ran sudo dpkg --reconfigure -a. Thats slightly off the subject though. It looks like Xserver isn't starting because you have no graphics card drivers.

Thanks for the help.

No luck, unfortunately!

Is it usual, or possible, to lose graphics drivers on an upgrade?

Anyway to get them back, or revert back to 10.04, which worked ok?

---

### Post by Heliguy on 2011-02-20
I would say it isint but then again its Linux after a few months with it i would say to really make things work you have to really work at it for example compiling PHP through source code to run on a kernel that wasn't actually supported that was a sleepless night :P. It worked in the end that was a real buzz :) Anyho if you want your GDI back i would suggest a reinstall uncomfortably and on the update search to see if any problems arise unless someone else "techier" then me says then i would say i have exhausted my knowledge. Remember logic is the key it really does help in other words have a good think :).

---

### Post by lonewolf88 on 2011-02-20
> **Heliguy said:**
> I would say it isint but then again its Linux after a few months with it i would say to really make things work you have to really work at it for example compiling PHP through source code to run on a kernel that wasn't actually supported that was a sleepless night :P. It worked in the end that was a real buzz :) Anyho if you want your GDI back i would suggest a reinstall uncomfortably and on the update search to see if any problems arise unless someone else "techier" then me says then i would say i have exhausted my knowledge. Remember logic is the key it really does help in other words have a good think :).

Thanks, looks like maybe a re-install;  nothing else seems to work.

Reading here and on Google, Toshiba laptops seem to be a particular hit & miss issue at the best of times. :(

---

