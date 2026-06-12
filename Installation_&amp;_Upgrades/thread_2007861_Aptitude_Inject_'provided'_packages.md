---
title: "Aptitude: Inject 'provided' packages"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by Rexilion on 2012-06-21
Look [here]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=3&chap=5") at section 5c.

What it basically would mean in Ubuntu:

- You tell Aptitude/dpkg/apt that network-manager is installed since you installed it yourself from source.

Aptitude will then:
- Not install the package itself, yet 'take it into account'
- Allow packages that depend on network-manager to be installed as if nothing 'else' happened.

Is this possible with aptitude/dpkg/apt?

I looked at apt-mark and 'dpkg --update-avail', but it doesn't seem to provide the functionality I seek.

             TIA

---

### Post by Rexilion on 2012-06-25
I figured it out, it was quite easy actually.

Simply:

1. Create an empty directory/DEBIAN
```
mkdir -p custom_package/DEBIAN
```

2. Create a control file with (for example) the following contents...
```
gnome-text-editor custom_package/DEBIAN/control
```
```
Package: custom_package
Version: 1
Architecture: all
Maintainer: Rexilion <1@2.3>
Provides: phonon-backend-gstreamer
Description: Modified package to make package management easier when combined with source packages or modifications that are in violation with the dependencie's inside the package system.
 .
 phonon-backend-gstreamer: This is a hard dependency of the minitube Youtube player. Purging this package makes the player force to use another backend (phonon-backend-vlc) if it's installed of course. Using this package will stop aptitude from complaining of missing dependencies.
```

In the above fields, everything is mandatory except for the 'Provides' field. I used 'Provides' to fullfil the (in my opinion), incorrect hard dep on phonon-backend-gstreamer. This is the sole purpose of this package as of right now.

Furthermore, in the 'Description' field, lines starting with a space are seen as new paragraphs. And lines containing a space and a dot are interperted as empty lines.

3. Create your custom package
```
dpkg-deb --build custom_package
```

4. Install it
```
sudo bash dpkg -i custom_package.pkg
```

That's it! I was able to purge the real phonon-backend-gstreamer, install this package and do a full system upgrade without the system complaining about this missing dependencie!

You can find the official guide with more information about the dpkg syntax [here]("http://www.debian.org/doc/debian-policy/ch-controlfields.html")!

---

