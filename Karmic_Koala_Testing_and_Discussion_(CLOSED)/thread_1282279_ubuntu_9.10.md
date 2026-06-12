---
title: "ubuntu 9.10"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by agarrett5 on 2009-10-04
I have just upgraded from 9.04 to 9.10.  I loved 9.04, it was really good, used it with no problems picked up all drivers , dual booted well.  9.10 seems to not be able to use the graphics drivers with compiz which 9.04 could, and the mouse doesnt work.  The computer is a Toshiba Satellite L30-113, model number psl33e.  I realise that this release is in testing phase so the drivers may not be there yet, is there anyway I can either get hold of them and how do I install them or is there anyway I can create them myself and help out the community?  Not had much chance to explore 9.10 yet, but going to have a look soon :)

Andy

---

### Post by jonabyte on 2009-10-04
I'll have to admit, all my laptops running ubuntu are of an older flavor. Most of them are Toshiba satellite models and for some reason the newest versions of any ubuntu version does not seem to work completely well enough.
I finally got 9.04 on my main one and I am happy to have it, I will save the 9.10 for my desktop.
Sorry, this reply doesn't really help your issue, but maybe shed some light.

---

### Post by ikisham on 2009-10-04
The Karmic Koala discussion section of the forum is [http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359) (maybe you have better luck there).

---

### Post by slakkie on 2009-10-04
You could add jaunty repo's to your sources.list and then downgrade the drivers.

aptitude install package=version, like mentioned here: [http://ubuntuforums.org/showthread.php?p=8048281#post8048281](http://ubuntuforums.org/showthread.php?p=8048281#post8048281)

Your next action would be to use pinning so no upgrade will upgrade that particular package, edit /etc/apt/preferences (file may or may not exist).

```

Explanation: I do not want to upgrade package XYZ to a higher version
Package: <packagename>
Pin: version <versionnumber>
Pin-Priority: 1001

```

You could use these functions for that:

```

pkg2pin () {
        [ -z "$1" ] && return
        local pkg
        local msg
        msg="$(date +'%Y%m%d:%H%M%S')"
        for pkg in $@
        do
                pkg=$(dpkg -l "$pkg" 2>/dev/null)
                [ $? -ne 0 ] && continue
                pkg=$(echo -e "$pkg" | grep "^ii" |awk '{print $2" "$3}')
                echo -e "$pkg" | awk '{print "Explanation: Added on '$msg' by pkg2pin or dpkg2pin\nPackage: "$1"\nPin: version "$2"\nPin-Priority: 1001\n"}'
        done | sudo tee -a /etc/apt/preferences
}

dpkg2pin () {
        [ -z "$1" ] && return
        local pkg
        pkg=$(dpkg -l | grep "^ii" |awk '{print $2}' | grep "$1")
        [ $? -ne 0 ] && return
        for i in $pkg
        do
                pkg2pin $i
        done
}

```

Put this in your .bashrc, source the .bashrc file and run dpkg2pin <packagename>. It will pin the package for you.

---

### Post by agarrett5 on 2009-10-04
Ok ill try all that.  I really appreciate the fast response.  If all else fails is there anyway I can put it back to 9.04?  or does it need a complete reinstall?  I dont want to loose my settings and files.  Im reletively new to linux (if it doesnt already show!), but I have always been someone who likes experimenting and testing things and learning more etc.  I feel being a self employed engineer it helps alot. I really appreciate all the help.  All advice greatfully received.

---

### Post by aamukahvi on 2009-10-04
Your laptop may have the ATI X200 mobile graphics, which I think isn't supported by the ATI fglrx driver anymore. If you had it installed, it may prevent the open source driver from working.

In that case, getting rid of fglrx or doing a fresh install would help.

---

### Post by joey-elijah on 2009-10-04
A fresh install is always better when upgrading to a new version, imo, but your graphics problems probably are due to as mentioned above me. Un-installing the prop. driver and installing the opensource one will sort you out if this is the case. I've heard good things about the opensource driver, so don't fear! :P

---

### Post by agarrett5 on 2009-10-05
Where do I get the open source driver from and how do I uninstall the old one to install the new one?  Would this work for the mouse as well?

---

### Post by agarrett5 on 2009-10-05
> **slakkie said:**
> You could add jaunty repo's to your sources.list and then downgrade the drivers.

aptitude install package=version, like mentioned here: [http://ubuntuforums.org/showthread.php?p=8048281#post8048281](http://ubuntuforums.org/showthread.php?p=8048281#post8048281)

Your next action would be to use pinning so no upgrade will upgrade that particular package, edit /etc/apt/preferences (file may or may not exist).

```

Explanation: I do not want to upgrade package XYZ to a higher version
Package: <packagename>
Pin: version <versionnumber>
Pin-Priority: 1001

```You could use these functions for that:

```

pkg2pin () {
        [ -z "$1" ] && return
        local pkg
        local msg
        msg="$(date +'%Y%m%d:%H%M%S')"
        for pkg in $@
        do
                pkg=$(dpkg -l "$pkg" 2>/dev/null)
                [ $? -ne 0 ] && continue
                pkg=$(echo -e "$pkg" | grep "^ii" |awk '{print $2" "$3}')
                echo -e "$pkg" | awk '{print "Explanation: Added on '$msg' by pkg2pin or dpkg2pin\nPackage: "$1"\nPin: version "$2"\nPin-Priority: 1001\n"}'
        done | sudo tee -a /etc/apt/preferences
}

dpkg2pin () {
        [ -z "$1" ] && return
        local pkg
        pkg=$(dpkg -l | grep "^ii" |awk '{print $2}' | grep "$1")
        [ $? -ne 0 ] && return
        for i in $pkg
        do
                pkg2pin $i
        done
}

```Put this in your .bashrc, source the .bashrc file and run dpkg2pin <packagename>. It will pin the package for you.
  Unfortunately it didnt work, but, I am certainly learning alot from this which is good :)

---

