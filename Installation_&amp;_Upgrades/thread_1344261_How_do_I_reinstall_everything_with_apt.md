---
title: "How do I reinstall everything with apt?"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by dragos240 on 2009-12-02
Would it be:
sudo apt-get reinstall world?

I am switching my system to 64 bit. I only had a 32 ubuntu drive with me. It's actually jaunty. Could I just switch my repos to karmic and:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade?

Forgive me if my apt knowledge is a bit off. I'm using ubuntu for chrooting purposes. Installing gentoo is very tedious. Ever since I quit ubuntu, I've known different package managers than apt, most of the time I'm used to pacman -S package or emerge package. Help?

---

### Post by sisco311 on 2009-12-02
Is Ubuntu the host or the target environment?

EDIT: anyway, 

to get a list of installed packages:
```
dpkg --get-selections | awk '$2=="install"{print $1}'
```

to reinstall a package:
```
sudo apt-get install --reinstall packagename
```

I don't think that switching the repos will work.

If Ubuntu is the chroot environment, than I would simply reinstall it via debootstrap. [uhelp]community/DebootstrapChroot[/uhelp]

---

### Post by phillw on 2009-12-02
> **dragos240 said:**
> Would it be:
sudo apt-get reinstall world?

I am switching my system to 64 bit. I only had a 32 ubuntu drive with me. It's actually jaunty. Could I just switch my repos to karmic and:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade?

Forgive me if my apt knowledge is a bit off. I'm using ubuntu for chrooting purposes. Installing gentoo is very tedious. Ever since I quit ubuntu, I've known different package managers than apt, most of the time I'm used to pacman -S package or emerge package. Help?

If you choose update, I'm pretty sure it will give you 32Bit karmic. I'm pretty sure you could 'get' the 64 bit kernel version. You can get use synaptic to give you a list of all your apps - but they'd also be in 32 bit format. Some of the apps may, or may not be available in 64Bit. 

Me ? I'd backup my data & do a clean install. You'd also have the advantage of switching to ext4 and wouldn't have to run the gauntlet of upgrading to Grub2 (and messing it up - like I did - lol).

If you want to get a list of your apps --> [http://jamsubuntu.blogspot.com/2009/03/save-list-of-installed-applications.html](http://jamsubuntu.blogspot.com/2009/03/save-list-of-installed-applications.html)   has a quick how-to, but be aware of my warning about the availability of 64bit Vs 32 Bit. I'd certainly keep the list if you have added lots of stuff - else, just backup /home & do a clean install.. Less things to go wrong. But, as with all replies like this - that is just IMHO - Others may dis-agree with me.

Regards,

Phill.

---

### Post by dragos240 on 2009-12-02
Something that annoys me about chrooting, is that the chroot host needs to have the same arch as the target host. Meaning, I can't chroot into a 64 bit system while inside a 32 bit system.

---

