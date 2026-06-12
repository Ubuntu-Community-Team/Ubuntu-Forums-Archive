---
title: "Re-install corrupted distro"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by LorraineO on 2011-12-03
My xubuntu is corrupted so I would like to do a re-install. At present my /home directory is on a separate partition. How do I do a re-install without creating another home partition or destroying the one I have. 
Lorraine

---

### Post by MAFoElffen on 2011-12-03
> **LorraineO said:**
> My xubuntu is corrupted so I would like to do a re-install. At present my /home directory is on a separate partition. How do I do a re-install without creating another home partition or destroying the one I have. 
Lorraine
Install > When it gets to the partitioner choose "custom" > When it desplays the drives and partitions:
- select your system partition > Ext4, mount as "/", format
- select your home partition > mount as /home, keep existing data (do not format)
- select swap partition > done
But be aware that most of the time that you have "corruption" from a user's point-of-view... it's usually a configuration file in the home directory.  What would confirm, your suspicion on that is if multiple users (even the Guest account) have the same problems.  So if, after your reinstall while keeping that home directory, if you have the same problems, you might want to back that off (by creating another directory under /Home and copying over) and start with a fresh home.

---

### Post by zvacet on 2011-12-03
When you get to the partitioning stage select something else (or similar to that) and then make new install on partition where your xubuntu is now.Partition on witch you will install Xubuntu you will mark as /root and ext4 and you will format it.You will mark your home as /home and ext4, **but do not format it**.

---

### Post by LorraineO on 2011-12-03
Thanks for the advice I will try it. Regarding the corruption here is a copy of the terminal when I try to upgrade.


Setting up update-manager-core (1:0.152.25.5) ...
Sorry: TypeError: ('compile() expected string without null bytes',)
dpkg: error processing update-manager-core (--configure):
 subprocess installed post-installation script returned error exit status 101
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.152.25.5); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        Errors were encountered while processing:
 update-manager-core
 update-manager
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)

Lorraine

---

### Post by MAFoElffen on 2011-12-04
> **LorraineO said:**
> Thanks for the advice I will try it. Regarding the corruption here is a copy of the terminal when I try to upgrade.


Setting up update-manager-core (1:0.152.25.5) ...
Sorry: TypeError: ('compile() expected string without null bytes',)
dpkg: error processing update-manager-core (--configure):
 subprocess installed post-installation script returned error exit status 101
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.152.25.5); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        Errors were encountered while processing:
 update-manager-core
 update-manager
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)

Lorraine
You know you "could" probably fix that without another install, right? On version 11.10 install aptitude (earlier has aptitude already):
```

sudo apt-get install aptitude  # <-- This line only needed if 11.10 and newer.
sudo aptitude -f install
sudo aptitude build-depends update-manager-core
sudo update
sudo aptitude safe-upgrade

```Build-depends should find the unmet dependencies for upgrade-manager core and the dependencies of those dependencies and resolve all those... (hopefully) Sometimes during the process, it will give you little hints.

---

### Post by LorraineO on 2011-12-05
Thanks for looking at my problem. I am still having  problems and have decided to do a re install, as I am still learning Linux I do not have many programs loaded on that partition. Will make sure I do not format my home partition and will do a back up as well. 
Could you give me a link as to where I can learn more about all these commands people come up with?

---

### Post by MAFoElffen on 2011-12-05
> **LorraineO said:**
> Thanks for looking at my problem. I am still having  problems and have decided to do a re install, as I am still learning Linux I do not have many programs loaded on that partition. Will make sure I do not format my home partition and will do a back up as well. 
Could you give me a link as to where I can learn more about all these commands people come up with?
Personally, I have a lot of experience with different platform installs on various hardware, but I specialize in helping people work out Graphics Issues: 
**[B]Sticky:**[/B]                         [COLOR=#008C00]**[all variants]**[/COLOR] [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")             

If you go to Post #2, I created a Link page to my graphics tutorials for different issues.  On install variations and such, do a search on "Ubuntu __subject__"  When I get stuck on something, Ubuntu has documentation, both Official and by Users for just about anything. Another place to look is in the Forum under:
[Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100")

On commands use "man __particular_command__". If you're trying to find a command to do something, then search on "linux __purpose_or_Use__"... There is also a few good Linux command references at:
[Unix/*Linux Command Reference*]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CC0QFjAB&url=http%3A%2F%2Ffiles.fosswire.com%2F2007%2F08%2Ffwunixref.pdf&ei=MPvcTvjBOtTciQLTo-jICQ&usg=AFQjCNFoqwy575s_1_-03UGCgTaOEApBzw")
[*Linux* Quick *Reference Linux*]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&ved=0CDQQFjAC&url=http%3A%2F%2Fwww.cfa.harvard.edu%2F%7Ejbattat%2Fcomputer%2FlinuxReferenceCard.pdf&ei=MPvcTvjBOtTciQLTo-jICQ&usg=AFQjCNG6nBEgA8IMEWS6akBt5D5veSzcsA")

The only thing you want to look out for is that Ubuntu is a Debian Branch distro, some others are RPM... So commands and Instructions. even though Linux. may vary to the Distro it's geared for.  Luckily for you, Debain, Ubuntu, Xubuntu... is fairly mainline.

---

### Post by zvacet on 2011-12-05
Try with 

```
sudo dpkg --configure -a
```

and see if that help.

---

