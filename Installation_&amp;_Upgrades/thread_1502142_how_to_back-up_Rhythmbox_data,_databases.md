---
title: "how to back-up Rhythmbox data, databases?"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by Mikko8 on 2010-06-05
I am planning to re-install Ubuntu since my current version breaks down time after time. As I am afraid to loose data, I would rather re-install the whole OS. And for this I would like to backup some system data. I found what to do with firefox but did not succeed in finding **how to backup Rhythmbox data and databases**. In detail - I want to **backup data containing information about the music locations, tags, ratings**.

---

### Post by dv3500ea on 2010-06-05
You need to back up the rhythmbox configuration files in your home folder.
They are found:
[LIST]
[*]~/.local/share/rhythmbox
[*]~/.gnome2/rhythmbox
[*]~/.gnome2/accels/rhythmbox
[*]~/.cache/rhythmbox
[*]~/.gconf/apps/rhythmbox
[/LIST]
You could do this with the following commands:
```

cd ~
tar cvf rythmbox-backup.tar .local/share/rhythmbox .gnome2/rhythmbox .gnome2/accels/rhythmbox .cache/rhythmbox .gconf/apps/rhythmbox

```
and restore by copying the file 'rythmbox-backup.tar' to the home folder of your new installation and running:
```

cd ~
tar xvf rythmbox-backup.tar

```

Alternatively, you could just back up your whole home folder.

---

### Post by Mikko8 on 2010-06-05
thanks

---

### Post by kpoole on 2010-12-01
One can backup the whole of the old home directory but knowing where to look for particular pieces like this is a great help.  Thanks from me as well.

In my case I've been working on my machine but am going to set up a family musicbox to handle all our ripped CDs and iPods.  Finding where all the Rhythmbox stuff was to move it was going to be important to saving a lot of time and effort.  Dang albums with various artists.  They take more work  ;)

---

### Post by Ufogos on 2010-12-03
Thanks a lot.

---

