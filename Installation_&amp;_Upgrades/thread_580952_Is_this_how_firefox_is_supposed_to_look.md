---
title: "Is this how firefox is supposed to look?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by ryankask on 2007-10-19
I had some errors upgrading the official way so I ended up changing my apt sources list directly and messing around with apt-get and dpkg. Anyway, everything seems to be upgraded:

ryan@rlk-linux:~$ sudo lsb_release -a
[sudo] password for ryan:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
ryan@rlk-linux:~$

But is this how Firefox is supposed to look? Also notice my cursor at the "more" link to the right of the Google logo. It seems like anything GTK related is ugly (Thunderbird appears the same way).

---

### Post by Vicfred on 2007-10-19
try the [firefox widgets]("http://ubuntuforums.org/showthread.php?t=369596")

=d

---

### Post by ryankask on 2007-10-19
Okay a restart fixed the cursor issue....I must say the new Kubuntu is beautiful aside from the GTK (though it seems much faster and smoother).

---

### Post by ryankask on 2007-10-19
Thanks for that link...it's not the form "widgets" that bother me, it's the overall look of GTK applications.

---

### Post by LanDan on 2007-10-19
can you try to rename the .mozilla folder in your /home to .mozillaOLD?


then start firefox again and see if there's a difference

---

### Post by kerry_s on 2007-10-19
you could grab the firefox kde theme to make it blend in more to the rest of the qt applications in kde.
[https://addons.mozilla.org/en-US/firefox/addon/3652](https://addons.mozilla.org/en-US/firefox/addon/3652)

you also might want to look into opera, as that is qt based.

---

### Post by snickers295 on 2007-10-19
ya that is how firefox looks in kde. you probably could find a kde theme at the firefox add-ons website.

---

### Post by RedfishBluefish on 2007-10-19
Whoa, it looks like KDE and Gnome have totally disowned each other in Gutsy.:lolflag:
I saw that exact same effect, but with gnome when running a Qt application (QSynth).
I fixed that by copying over my old (Fiesty version) .qt/qtrc file in my home dir.

---

### Post by Lord Landis on 2007-10-19
Aside from a better-looking theme (I like AquaTint Black), don't forget to modify your Firefox configuration file.

Open a new tab and type the following for your location:

```
about:config
```

Find the item called *ui.allow_platform_file_picker* and set its value to **false**.

Restart Firefox.

When it comes back up, it will use KDE-native file dialogs, which goes a long way to helping it blend in better.

---

