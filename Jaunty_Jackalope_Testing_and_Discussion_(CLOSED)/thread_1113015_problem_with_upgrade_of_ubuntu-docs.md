---
title: "problem with upgrade of ubuntu-docs"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zika on 2009-04-01
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages have been kept back:
  ekiga 
The following partially installed packages will be configured:
  ubuntu-docs 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up ubuntu-docs (9.04.6) ...
/var/lib/dpkg/info/ubuntu-docs.postinst: 21: Syntax error: newline unexpected
dpkg: error processing ubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-docs
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ubuntu-docs (9.04.6) ...
/var/lib/dpkg/info/ubuntu-docs.postinst: 21: Syntax error: newline unexpected
dpkg: error processing ubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-docs
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
```should I do something or just leave it as it is ... ?
this is the file that is mentioned:```
#! /bin/sh
set -e

# Automatically added by dh_scrollkeeper
if [ "$1" = "configure" ] && which scrollkeeper-update >/dev/null 2>&1; then
    scrollkeeper-update -q
fi
# End automatically added section


case "$1" in
  configure)
    update-alternatives \
      --install /usr/share/ubuntu-artwork/home/index.html \
      firefox-homepage /usr/share/ubuntu-artwork/home/firefox-index.html 40 \
      --slave /usr/share/ubuntu-artwork/home/locales \
      firefox-homepage-locales /usr/share/ubuntu-artwork/home/locales-ubuntu

        link=/usr/share/gnome/help/libs
        if [ -d "$link" ] && ! [ -L "$link" ] \
           && dpkg --compare-versions "$2" lt-nl <9.04.6>
        then
                rmdir "$link"
                ln -s ../../ubuntu-docs/libs "$link"
        fi
  ;;
esac

exit 0
```

---

### Post by Steve1961 on 2009-04-01
Yeh I've just had the same problem.  I've removed the package for now.

---

### Post by kansasnoob on 2009-04-01
Same thing here!

---

### Post by macstevejb on 2009-04-01
can confirm this too

---

### Post by eeclark on 2009-04-01
The error indicates that it is seeing a new line which it is not expecting.
Is there a missing "(" in the case statement?

---

### Post by philinux on 2009-04-01
Yep Same here.

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/353117](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/353117)

---

### Post by zika on 2009-04-01
> **eeclark said:**
> The error indicates that it is seeing a new line which it is not expecting.
Is there a missing "(" in the case statement?
I had several guesses but I am not an expert in bash and I do not want to mess anything on a package that is not important to me (I guess) . did You mean it should look like:```

#! /bin/sh
set -e

# Automatically added by dh_scrollkeeper
if [ "$1" = "configure" ] && which scrollkeeper-update >/dev/null 2>&1; then
    scrollkeeper-update -q
fi
# End automatically added section


case ("$1" in configure)
    update-alternatives \
      --install /usr/share/ubuntu-artwork/home/index.html \
      firefox-homepage /usr/share/ubuntu-artwork/home/firefox-index.html 40 \
      --slave /usr/share/ubuntu-artwork/home/locales \
      firefox-homepage-locales /usr/share/ubuntu-artwork/home/locales-ubuntu

        link=/usr/share/gnome/help/libs
        if [ -d "$link" ] && ! [ -L "$link" ] \
           && dpkg --compare-versions "$2" lt-nl <9.04.6>
        then
                rmdir "$link"
                ln -s ../../ubuntu-docs/libs "$link"
        fi
  ;;
esac

exit 
```

---

### Post by eeclark on 2009-04-01
> **zika said:**
> I thought the same but I am not an expert. did You mean it should look like:```

#! /bin/sh
set -e

# Automatically added by dh_scrollkeeper
if [ "$1" = "configure" ] && which scrollkeeper-update >/dev/null 2>&1; then
    scrollkeeper-update -q
fi
# End automatically added section


case ("$1" in configure)
    update-alternatives \
      --install /usr/share/ubuntu-artwork/home/index.html \
      firefox-homepage /usr/share/ubuntu-artwork/home/firefox-index.html 40 \
      --slave /usr/share/ubuntu-artwork/home/locales \
      firefox-homepage-locales /usr/share/ubuntu-artwork/home/locales-ubuntu

        link=/usr/share/gnome/help/libs
        if [ -d "$link" ] && ! [ -L "$link" ] \
           && dpkg --compare-versions "$2" lt-nl <9.04.6>
        then
                rmdir "$link"
                ln -s ../../ubuntu-docs/libs "$link"
        fi
  ;;
esac

exit 
```

Yes that is what I was thinking.

---

### Post by eeclark on 2009-04-01
```

Setting up ubuntu-docs (9.04.6) ...
/var/lib/dpkg/info/ubuntu-docs.postinst: 11: Syntax error: "(" unexpected (expecting word)
dpkg: error processing ubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:

```

did not work

---

### Post by mbentley on 2009-04-01
here is the solution with a .deb attached that fixes the problem now:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/ubuntu-docs/+bug/303578/comments/19](https://bugs.launchpad.net/ubuntu/jaunty/+source/ubuntu-docs/+bug/303578/comments/19)

it fixed it for my jaunty install

---

### Post by Steve1961 on 2009-04-01
Worked for me as well

---

### Post by ivaarsen on 2009-04-01
I will third this workaround.  Good find!  o/

---

### Post by novafluxx on 2009-04-01
Same here, and since I've upgraded...ubuntu forums is now PINK...yes pink...every page I visit here is PINK and if I hit F5 to refresh, it'll return to normal...strange...

Let me post a Screen...

---

### Post by mbentley on 2009-04-01
well today is april 1st...

---

### Post by stone1343 on 2009-04-01
I just had the pink forums too, on Windows so it has nothing to do with Ubuntu...

Anyway, about the ubuntu-docs problem, I have it too, I've tried re-installing it in Synaptic, problem still there. I guess it's not a problem since 1) it's documentation, 2) it'll be fixed eventually?

---

### Post by novafluxx on 2009-04-01
Yes I'm not to worried about it either. I'm going to wait for it to be fixed in the repos

---

### Post by zika on 2009-04-01
> **philinux said:**
> Yep Same here.
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/353117](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/353117)
no, the .deb did not help ...

---

### Post by ghindo on 2009-04-01
Should be fixed with an additional update:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/353117/comments/3](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/353117/comments/3)

---

### Post by rburkartjo on 2009-04-01
yes i get the same error will just have to wait for a fix

---

### Post by philinux on 2009-04-01
Upgrade just arrived.

---

### Post by zika on 2009-04-01
thank You for a quick remedy.

---

### Post by eeclark on 2009-04-01
For those that are curious (like me), the resolution appears to have been to remove the greater-than less-than signs around the version number:

```

   && dpkg --compare-versions "$2" lt-nl 9.04.7

```

---

