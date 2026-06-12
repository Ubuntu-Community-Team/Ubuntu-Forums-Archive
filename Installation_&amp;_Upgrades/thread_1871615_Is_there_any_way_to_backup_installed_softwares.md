---
title: "Is there any way to backup installed softwares ?"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by fawadlzd on 2011-10-29
I have installed many soft wares from ubuntu software center.
I would like to ask you whether there is a system to backup my software. so that if i reinstall complete system i can reuse them. or even if i want to reuse the soft wares in some other Ubuntu Linuxes.
i will be happy for your precious responses.
thanks

---

### Post by Bao2 on 2011-10-29
In var/cache/apt/archives you have all the software you have installed. They are .deb files and you only need to copy them to an USB and then install them again from the USB (double click on the .deb files to install)

---

### Post by Lars Noodén on 2011-10-29
You can see a list of the packages you have installed using dpkg:

```

dpkg -l | less

```

You can get just the names of just the packages that were installed with the help of awk.

```

dpkg -l | awk '/^ii/ {print $2}' > installed-packages.txt

```

That also gets the dependencies that were added to be able to install the packages you added, not just the packages that you added.

To restore the packages, I don't know of a way to read the file directly with APT.  There is a work-around (ab)using [cat](http://manpages.ubuntu.com/manpages/oneiric/en/man1/cat.1posix.html).

```

for pkg in $(cat installed-packages.txt);
 do sudo apt-get install $pkg;
done

```

---

### Post by RaganN on 2011-10-29
There is a program called APTonCD that will put all your downloaded packages into a CD, DVD, or ISO file that can be used on other computers, but restoring with it is somewhat glitchy.  It is essentially an automation of the var/cache/apt/archives method mentioned earlier.

---

