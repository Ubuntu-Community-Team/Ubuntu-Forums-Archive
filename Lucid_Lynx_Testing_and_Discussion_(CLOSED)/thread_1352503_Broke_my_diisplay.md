---
title: "Broke my diisplay"
date: 2009-12-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-12-11
I stupidly uninstalled ubuntu-desktop, which is only a metapackage I know but then I removed I think usplash.  Now I cannot see my display.  Is there a way via the live cd & terminal to reconfigure it so I do not need to reinstall karmic & lucid?

---

### Post by Gina on 2009-12-11
Isn't a re-install the easiest way? :)

---

### Post by sports fan Matt on 2009-12-11
Its more of a pain in the rear...gonna probably take several hours since even though I have everything backed up, Gotta reinstall twice...lol

---

### Post by sports fan Matt on 2009-12-11
probably will take 2-3 hrs, to try and get everything the way it was before (have to refind everything, etc)

---

### Post by sports fan Matt on 2009-12-11
oh well, ive got nothing to do anyway tonight :)

---

### Post by Gina on 2009-12-11
Good luck :):)

---

### Post by ranch hand on 2009-12-11
You could chroot in from the live cd and run apt to reinstall your stuff.

---

### Post by sports fan Matt on 2009-12-11
how could I accomplish this?

---

### Post by sports fan Matt on 2009-12-11
Nevermind, I cant.  I already started the reinstall process..lol

---

### Post by sports fan Matt on 2009-12-11
About to reinstall lucid :)

---

### Post by VMC on 2009-12-11
> **sox fan Matt said:**
> About to reinstall lucid :)

Do yourself a favor. This time clone your partition. That way you can play around all you want and in 3 minutes have Lucid back the way you installed it. That's what I do. There's several tools for doing this. I now prefer partclone.ext4.

---

### Post by sports fan Matt on 2009-12-11
Trying to upgrade to lucid from karmic I get: Errors were encountered while processing:
 /var/cache/apt/archives/metacity_1%3a2.28.0-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ranch hand on 2009-12-11
Heck, I'd go with the A1 LiveCD.  You have to do your formating with gparted before the install and do not let the installer partitioner format any partition.  Works slick if you do that.

---

### Post by sports fan Matt on 2009-12-11
I managed to fix this and im on lucid.

---

### Post by Gina on 2009-12-12
> **VMC said:**
> Do yourself a favor. This time clone your partition. That way you can play around all you want and in 3 minutes have Lucid back the way you installed it. That's what I do. There's several tools for doing this. I now prefer partclone.ext4.Good suggestion :)  I'd forgotten that - quicker than a re-install.  I use partimage and haven't tried partclone.ext4.

---

### Post by meborc on 2009-12-12
so... just installing the "ubuntu-desktop" package again did not fix the problem??? i think it should have pulled in the usplash things again etc...

---

### Post by Gina on 2009-12-12
> **VMC said:**
> Do yourself a favor. This time clone your partition. That way you can play around all you want and in 3 minutes have Lucid back the way you installed it. That's what I do. There's several tools for doing this. I now prefer partclone.ext4.Good suggestion :)  I'd forgotten that - quicker than a re-install.  I use partimage and haven't tried partclone.ext4.

---

### Post by sports fan Matt on 2009-12-12
Meborc, nope.  Problem was I couldnt see my display to pull anything..I waited for my display for a good 10 minutes and it never came back.

---

### Post by VMC on 2009-12-12
> **Gina said:**
> Good suggestion :)  I'd forgotten that - quicker than a re-install.  I use partimage and haven't tried partclone.ext4.

Here's what I use:

```
CLONE (Example)
# partclone.ext4 -c -s /dev/sda10 | pigz -c --fast>image.gz
RESTORE (Example)
# zcat *image.gz* | partclone.ext4 -r -o /dev/sda10
```

---

### Post by Gina on 2009-12-12
> **VMC said:**
> Here's what I use:

```
CLONE (Example)
# partclone.ext4 -c -s /dev/sda10 | pigz -c --fast>image.gz
RESTORE (Example)
# zcat *image.gz* | partclone.ext4 -r -o /dev/sda10
```Thank you :)  I'll take a look at that.

---

### Post by darco on 2009-12-12
> **VMC said:**
> Here's what I use:

```
CLONE (Example)
# partclone.ext4 -c -s /dev/sda10 | pigz -c --fast>image.gz
RESTORE (Example)
# zcat *image.gz* | partclone.ext4 -r -o /dev/sda10
```

I get an error when I use partclone.ext4:

open /var/log/partclone.log error

when I check the log its shows:

UID is root.
clone: open /dev/hdb2 error

Tried unmounting drive but same error.  Any idea what I am doing wrong?
thxs

darco

---

### Post by VMC on 2009-12-12
> **darco said:**
> I get an error when I use partclone.ext4:

open /var/log/partclone.log error

when I check the log its shows:

UID is root.
clone: open /dev/hdb2 error

Tried unmounting drive but same error.  Any idea what I am doing wrong?
thxs

darco
Oh I forgot, uner Ubuntu you need to be sudo or root. Since that has a pipe do a "su -" then issue the command again. I usually use Parted Magic mini distro to do this, and it is always under root.

---

### Post by meborc on 2009-12-12
> **sox fan Matt said:**
> Meborc, nope.  Problem was I couldnt see my display to pull anything..I waited for my display for a good 10 minutes and it never came back.

couldn't you ctrl+alt+F1 into a terminal and do it from there?

---

### Post by ranch hand on 2009-12-12
Or boot to xterm.

---

### Post by darco on 2009-12-12
> **VMC said:**
> Oh I forgot, uner Ubuntu you need to be sudo or root. Since that has a pipe do a "su -" then issue the command again. I usually use Parted Magic mini distro to do this, and it is always under root.

Well I guess running the command 'while' in the partition isnt the way to go. I had tried using  "sudo" at first but still got the error. Now that I booted into my other OS, running the command worked. 


Also is that a typo "pigz" ?

thxs

darco

---

### Post by sports fan Matt on 2009-12-12
possibly, but the thing was..my display (screen) was not visible.  it kept saying "not supported"

---

### Post by ranch hand on 2009-12-12
If you got to the login screen you should have the options for "failsafe gnome" and "xterm" sessions after you hit enter to pull up the line where you put your password.

The options should then be in the center of the bottom panel.

---

### Post by meborc on 2009-12-12
> **sox fan Matt said:**
> possibly, but the thing was..my display (screen) was not visible.  it kept saying "not supported"

if you get X errors, then usually the system has loaded far enough for you to be able to use tty's via ctrl+alt+F1(-6)

---

### Post by VMC on 2009-12-12
> **darco said:**
> Well I guess running the command 'while' in the partition isnt the way to go. I had tried using  "sudo" at first but still got the error. Now that I booted into my other OS, running the command worked. 


Also is that a typo "pigz" ?

thxs

darco

No, but gzip will replace it. It you have multiple cores then pigz parallels the compression and its much faster.

Not meaning to hijack, just answering some questions.

---

### Post by sports fan Matt on 2009-12-12
I could never "physically" see the login screen.  I also did not see any x errors--just had a blank screen

---

### Post by meborc on 2009-12-13
> **sox fan Matt said:**
> I could never "physically" see the login screen.  I also did not see any x errors--just had a blank screen

ok... i just assumed it from this: > **sox fan Matt said:**
> ...it kept saying "not supported"

---

### Post by sports fan Matt on 2009-12-13
Not a problem :)

---

