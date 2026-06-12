---
title: "Installing over Fedora/other linux"
date: 2005-05-24
forum: Installation &amp; Upgrades
---

### Post by David Kirkland on 2005-05-24
Hi, I'm thinking of installing Ubuntu over an existing Linux installation (specifically FC2). My system currently dual boots between WinXP and FC2. I'd like to keep my existing partitions, but I don't mind overwriting the existing linux installation. I would like to keep my existing /home (no formating) partition.

Is the installation SW smart enough to know/do this? What options should I select in the installation process?

I'm going to backup my existing /etc and /boot directories so I can still access my the configuration files.

I'm worried about residual FC2 files being left around and messing up my Ubuntu configuration.

Any guidance is appreciated.

Thanks,
David

---

### Post by JonahRowley on 2005-05-24
You won't have any problems with this.  The installer is pretty good when it comes to this, it doesn't try to do everything for you.  I can't remember the exact menu options you'll have to choose, but I did a similar thing, and it was very straightforward.

---

### Post by alastair on 2005-05-24
When you come to "partitioning", you can choose to :

"keep existing data" for a partition e.g. mount on /home
"format with <filesystem>" e.g. /, /boot, /usr etc.

No need to change partition layout (start/end etc.) - just a question of where to mount and whether to format. Shouldn't be a problem.

---

### Post by David Kirkland on 2005-05-25
Great. That's good to here. Thanks for the help.

Cheers,
David

---

### Post by dave9191 on 2005-05-25
I would do a backup of your data first just to be sure :) 

I had a slight prob when i tired to keep my data from a previous /home dir. Ubuntu couldnt access it and wouldnt let me log in. Since I didnt have anything there that I could loose I just installed and wiped the /home, but thats not an option for everyone. 

Dave

---

