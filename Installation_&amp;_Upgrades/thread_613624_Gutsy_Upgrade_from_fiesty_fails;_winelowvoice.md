---
title: "Gutsy Upgrade from fiesty fails; winelowvoice"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by Joedude on 2007-11-15
I've searched and haven't found this one. However, I even have the same problem during updates. Whenever I try to do the online upgrade from fiesty to gutsy, I get the following error:

[IMG]http://i220.photobucket.com/albums/dd153/pofnlice/Screenshot-gutsy.png[/IMG]
```

Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg Could not resolve &#8216;wine.lowvoice.nl&#8217;
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2 Could not resolve &#8216;wine.lowvoice.nl&#8217;
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz Could not resolve &#8216;wine.lowvoice.nl&#8217;
```

Are there some quick fixes for this? Should I just remove wine and try again? I'm not sure how that would help as it seems to be a failed connection to the repos for wine...maybe I should just remove the wine repo? Anyone with suggestions would be appreciated.

---

### Post by bulldog on 2007-11-15
Open your sources list```
gksu gedit /etc/apt/sources.list
```
Put a ## in front of the lines you don't want to use.
Save the file and ```
sudo aptitude update && sudo aptitude upgrade
```
See if there are more sources errors,if yes do the same again with these lines.

---

### Post by Joedude on 2007-11-15
Thank you for the quick reply. Trying it out right now. I figured the answer wqould be to comment out the line...don't know why I didn't just try that to start with. Guess I was maybe concerned about losing a part of the upgrade.

---

### Post by Joedude on 2007-11-15
worked like a charm, posting from 7.10 right now. Thank you!

---

### Post by bulldog on 2007-11-15
> **Joedude said:**
> worked like a charm, posting from 7.10 right now. Thank you!

Nice,have fun :)

---

