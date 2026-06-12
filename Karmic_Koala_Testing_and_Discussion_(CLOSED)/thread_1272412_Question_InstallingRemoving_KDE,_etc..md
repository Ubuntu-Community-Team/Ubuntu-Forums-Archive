---
title: "Question: Installing/Removing KDE, etc."
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cyberkilla on 2009-09-22
This isn't specifically related to Karmic, but I would be using it to further test it...

I see that I can install KDE by grabbing the kubuntu-desktop package (or whatever it's called).

However, it isn't half as easy to *remove* everything it installs. This effectively means that a mess is made each time I install KDE (or the like), then get rid of it.

Is there a foolproof method to remove everything kubuntu-desktop installs? Thanks in advance.

---

### Post by n3had on 2009-09-22
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

check the above link and try removing most of the packages

---

### Post by cyberkilla on 2009-09-22
> **n3had said:**
> [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

check the above link and try removing most of the packages

Thanks for responding, but I've already seen that. It doesn't quite work as a proper solution.

It would be easy if everything could be auto-removed once kubuntu-desktop is gone. It doesn't seem to work that way though. I'm sure there are valid reasons why it doesn't work.

---

### Post by MacUntu on 2009-09-22
I usually diff the depends lists I get via 'apt-cache depends (k)ubuntu-desktop' and purge every package with a "+" (as long as it's not important like 'hal' :D). After purging the auto-removable packages most of the stuff is gone. For the rest I use Synaptic's search function.

Easy, huh?

---

### Post by dinxter on 2009-09-22
does 
$apt-get purge kubuntu-desktop --auto-remove
not do the trick? its supposed to! its what i use for kde install/remove but i dont use kubuntu-desktop so i dont know for sure, its a big download to try it out :)

---

### Post by cyberkilla on 2009-09-22
> **dinxter said:**
> does 
$apt-get purge kubuntu-desktop --auto-remove
not do the trick? its supposed to! its what i use for kde install/remove but i dont use kubuntu-desktop so i dont know for sure, its a big download to try it out :)

No, it doesn't seem to. The packages it installs do not appear to be flagged as "installed automatically"

> **MacUntu said:**
> I usually diff the depends lists I get via 'apt-cache depends (k)ubuntu-desktop' and purge every package with a "+" (as long as it's not important like 'hal' :D). After purging the auto-removable packages most of the stuff is gone. For the rest I use Synaptic's search function.

Easy, huh?

Simple as that:lol:

---

### Post by knarf on 2009-09-22
Use deb depends/recommends and the shell:

```

for f in ubuntu kubuntu;do apt-cache show $f-desktop|grep ^Depends|sed -e 's/[,:] /\n/g'|sort > /tmp/$f-desktop-packages;done
rm -f /tmp/only-in-kubuntu;for f in $(cat /tmp/kubuntu-desktop-packages);do grep -q $f /tmp/ubuntu-desktop-packages ; [ $? -gt 0 ] && echo $f >> /tmp/only-in-kubuntu;done
sudo apt-get autoremove --purge $(cat /tmp/only-in-kubuntu|egrep -v 'hal')
```

This removes all dependencies for kubuntu-desktop while leaving those for ubuntu-desktop in place.  The check for [FONT="Courier New"]hal[/FONT] in the last line is necessary because kubuntu-desktop has this as a dependency while ubuntu-desktop does not. Removing hal leads to bad things happening to your system as it would remove everything which depends on it as well... like the X server...

A more thorough version checks for the dependencies AND recommended packages. Use this with care as it might remove packages you installed manually which happen to be recommended packages in kubuntu-desktop but not in ubuntu-desktop. Check what is going to be removed first!

[COLOR="Red"]I warned you, didn't I? **Check first**!
[/COLOR]

If it wants to remove more than you care for you can either add those exceptions to the last line (like this: [FONT="Courier New"]egrep -v 'package_I_want_to_keep|another_package_I_want_to_keep'[/FONT]) or remove the last line ([FONT="Courier New"]sudo apt-get autoremove ...[/FONT]) alltogether and hand-tailor the list of packages to be removed ([FONT="Courier New"]/tmp/only-in-kubuntu[/FONT]). After checking that list you can feed it to apt-get (or aptitude) to remove those packages you don't care for.

```

for f in ubuntu kubuntu;do apt-cache show $f-desktop|grep -e '^Depends\|^Recommends'|sed -e 's/[,:] /\n/g'|sort > /tmp/$f-desktop-packages;done
rm -f /tmp/only-in-kubuntu;for f in $(cat /tmp/kubuntu-desktop-packages);do grep -q $f /tmp/ubuntu-desktop-packages ; [ $? -gt 0 ] && echo $f >> /tmp/only-in-kubuntu;done
sudo apt-get autoremove --purge $(cat /tmp/only-in-kubuntu|egrep -v 'hal')
```

[SIZE="1"]And don't forget to check before allowing it to remove anything, mkay?[/SIZE]

Of course you can do the same thing to remove unwanted packages from any other meta-package like xubuntu-desktop, lxde, ubuntu-desktop if you want to keep kubuntu-desktop, etc...

---

