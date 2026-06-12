---
title: "How do I download packages to install on another PC?"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by kavoura on 2008-01-25
I am running Ubuntu 7.10 and my friend has a laptop on which she wants to install the same, but without having a lot of bandwidth. So I need to get as many upgrades to the Ubuntu software to install onto her laptop which I can download on my generous bandwidth allowance, write to DVD and then use those to update her Ubuntu.
I found the website [http://packages.ubuntu.com/gutsy/]("http://packages.ubuntu.com/gutsy/") but is there some pre-prepared updates DVD or list of required updates for Ubuntu 7.10 so I can grab what I need easily and without wading through the whole listing of all software?
And is there an add-on CD that contains the restricted software not on the normal installation disk?

---

### Post by mikewhatever on 2008-01-25
I've never heard about restricted software distributed on CDs. Try this site [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/).

---

### Post by ugm6hr on 2008-01-25
@OP:
nonetdebs is a good solution, but you will still have to download 180+ links to update Gutsy from a standard installation CD at the moment.  Which still requires clicking on all the links :(  I found Firefox addon snaplinks which can speed things up a bit, but is less than perfect.

My suggestion:

If you have Ubuntu on your HD, it is worth just looking in your /var/cache/apt/archives, and copying those files to your friends same directory.  You *should* then just be able to use Synaptic / Update manager offline to install them all.  Of course, if you clean up your archive directory, that won't be an option.

Synaptic's generate download script is another (potentially better) option.  She could generate the wget script (select mark all upgrades in Edit menu, then Generate package download script in File menu) for you to download onto your computer, copy to hers, and then just install downloaded packages (in File menu).

---

### Post by Ryadt on 2008-01-25
try aptoncd
sudo apt-get aptoncd

you will need it on both pcs..then you can download and install any package on your pc, make a back-up of your installed packages on a disk and finally restore it on your friends laptop...

hope this helped...

---

