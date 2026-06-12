---
title: "Update Manager Problem"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by the_vaga on 2010-03-31
Hi,
I'm fairly new to ubuntu, but all of a sudden my update manager is no longer working. I'm running ubuntu 9.04 and was happy because I finally got the screen resolution to be a good size, but now I can't update anything or even upgrade ubuntu.
The message I get is
> **Could Not Initialize Package Information**

An unresolvable problem occured while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Unable to parse package file /var/lib/dpkg/status (1), E:The package lists or status file could not be parsed or opened.'I've also had issues with installing new programs (specifically tried Boxee (64bit ver) and Last.fm Scrobbler), but was thinking these issues might be related to the updage-manager error.

Thanks for any help.

---

### Post by bl77122 on 2010-03-31
Hi,

I am totally new to Linux and sorry to post my question in this thread accidentally.

I can't log in Ubuntu (gnome session) whenever the resolution was changed to a lower one (e.g., 1280x1024), even though I can log in Ubuntu by logging into a command line mode (recovery mode) and typing 'startx'.

Any suggestion?

Thank you,

Bruce
p.s., I am using old PC and small screen.

---

### Post by the_vaga on 2010-04-01
Bump  :?

---

### Post by somethingkindawierd on 2010-05-04
Not sure if you still need help, but I just ran into this and here is how I fixed it:

```
# Move into the directory
cd /var/lib/dpkg/
# Rename the old version to a backup copy
sudo mv status status.bak
# Create a new empty file (otherwise apt-get will complain)
sudo touch status
# Update...
sudo apt-get update
```

---

### Post by somethingkindawierd on 2010-05-05
I take it back...that fix only got me part way there...

The real problem was that my /var/lib/dpkg/status file had 1 bad character in it.

Running ```
gksu gedit /var/lib/dpkg/status
``` revealed this line had a bad character in it. In front of the word "Conflicts" is a bad character...it should be a new line. 

```
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libjpeg62, libstdc++6 (>= 4.1.1), libdjvulibre-text (>= 3.5.22-1ubuntu2)Conflicts: libdjvulibre1
```

It should be:

```
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libjpeg62, libstdc++6 (>= 4.1.1), libdjvulibre-text (>= 3.5.22-1ubuntu2)
Conflicts: libdjvulibre1
```

Editing that line in Gedit fixed everything and I can run apt-get fine now.

---

