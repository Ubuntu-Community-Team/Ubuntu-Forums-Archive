---
title: "interrupted upgrade from 11.04 to 11.10"
date: 2011-12-24
forum: Installation &amp; Upgrades
---

### Post by roger_reject on 2011-12-24
Hi All,

A laptop was shut off mid-upgrade from 11.04 to 11.10 and now seems pretty broken.  During startup I can get to a command line login, and from there I ran all the usual suspects,

apt-get update
dpkg --configure -a
apt-get -f install
apt-get dist-upgrade

cycling through that several times no longer yields anything left to install, update, or configure.  However, when I boot in, x never loads, and I get some text saying

*starting bluetooth  [ok]
* pulseaudio configured for per-user sessions
saned disabled: edit /etc/default/saned

then nothing.  from here i can still F1 into a command line session but that's about it.

any suggestions short of booting from a flash disk, getting all of the files off the hard disk, and then doing a clean install?

---

### Post by Paddy Landau on 2011-12-24
Try these.
```
sudo apt-get update
sudo apt-get --fix-broken install
```If you get messages saying to install something specific, install it and then repeat.

Then:
```
sudo apt-get update
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get upgrade
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by roger_reject on 2011-12-24
Paddy,

Thanks for the reply, but after trying your suggestions still no joy.  --fix-broken install didn't find anything broken to fix...

---

### Post by Paddy Landau on 2011-12-24
Unfortunately, I have hit the limit of my knowledge.

When you boot the machine, hold down the Shift key until you get the Grub menu. Choose one of the previous versions (before your upgrade) to see whether or not you can boot from that. If you can, then retry your upgrade.

---

### Post by roger_reject on 2011-12-24
Hi Paddy,

I tried booting into recovery mode from grub, and after running a disk check it gives me the option to run dpkg, and when i do that from grub, it lists several packages that it wants to repair, but then doesn't seem to have any network access to download the files.  Any suggestions for this?  I tried dropping to the "root with networking" prompt and running dpkg from there, but then it doesn't find anything worth updating, and running things like 

/etc/init.d/networking start

doesn't seem to help once i exit back to the recovery mode menu.

---

### Post by roger_reject on 2011-12-24
okay I actually got the network up and dpkg to run, but even after that, still no luck in getting ubuntu to load.

---

### Post by Paddy Landau on 2011-12-25
What about booting to a previous kernel instead of booting from recovery mode?

---

### Post by roger_reject on 2011-12-26
Hi Paddy,

I did try, but had the same problem booting from all of the previous kernels.  it would show a purple screen, then show the ubuntu logo with the dots, and then go back to a black screen and spit out some loading text and never get to a login screen.

---

### Post by Paddy Landau on 2011-12-26
Hmm, sorry, I have run out of ideas. In your place I would simply reinstall from scratch (after backing up all data, of course).

---

### Post by Kslawdog on 2011-12-26
Hey roger,
     I guess I'm just not understanding but why don't you just do a fresh install?  Seems to me that would be the easiest thing to do.:)

---

