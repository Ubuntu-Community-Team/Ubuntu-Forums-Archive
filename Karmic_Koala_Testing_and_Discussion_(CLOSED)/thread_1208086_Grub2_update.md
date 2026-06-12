---
title: "Grub2 update"
date: 2009-07-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by alphacrucis2 on 2009-07-08
I notice a new version of grub2 just came through. I decided to reboot to test it and it seems that the menu timeout before booting seems to have increased. I had thought the timeout previously was a little short for deciding which kernel you want to boot but i hadn't got around to seeing if I could tweak it.

---

### Post by tad1073 on 2009-07-08
I have tried configuring it with no time-out, but the best I could get was to adjust the time.

---

### Post by alphacrucis2 on 2009-07-08
> **tad1073 said:**
> I have tried configuring it with no time-out, but the best I could get was to adjust the time.

Looking at the grub.cfg file I see it has timeout=5. It says not to edit the file so there must be some other way you are supposed to change this stuff. I guess I have some reading up to do on grub2

---

### Post by alphacrucis2 on 2009-07-08
> **alphacrucis2 said:**
> Looking at the grub.cfg file I see it has timeout=5. It says not to edit the file so there must be some other way you are supposed to change this stuff. I guess I have some reading up to do on grub2

Not sure about this but I gather the timeout should be changed in the file /etc/default/grub which is used by update-grub to generate a new /boot/grub/grub.cfg

---

### Post by ranch hand on 2009-07-09
I have not had any luck changing the time out in /etc/default/grub.  Does not seem to stick.  On reboot you are right where you were.

/boot/grub/grub.cfg does work but is over writen by update, or so I have heard.  

Yesterdays update seems to have advanced grub2 quite a ways.  I need to do some more studying.  an interesting link if you haven't got it;

[http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)

---

### Post by zika on 2009-07-09
> **ranch hand said:**
> I have not had any luck changing the time out in /etc/default/grub.  Does not seem to stick.  On reboot you are right where you were.

/boot/grub/grub.cfg does work but is over writen by update, or so I have heard.  

Yesterdays update seems to have advanced grub2 quite a ways.  I need to do some more studying.  an interesting link if you haven't got it;

[http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)At the very beginning of grub2 in Karmic I've changed time-out to 4 (in /etc/default/grub via GRUB_TIMEOUT=4) and it is there after all (daily) upgrades of either grub2 or kernel (I use 2.6.31-999-generic) ... Did You issue update-grub command after changing /etc/default/grub? Because if You did not, You did not make it go (properly) in /boot/grub/grub.cfg ...

---

### Post by drs305 on 2009-07-09
Added:  Here is a command line method of changing the grub2 timeout value. I believe the default timeout is 5 seconds. Replace "T" with the desired new timout in seconds.
```

cat /etc/default/grub | grep 'GRUB_TIMEOUT='   # Checks current timeout value
sudo sed 's/GRUB_TIMEOUT=**[COLOR="DarkRed"]5[/COLOR]**/GRUB_TIMEOUT=**[COLOR="DarkRed"]T[/COLOR]**/g' -i /etc/default/grub   # Replaces TIMEOUT VALUE, change "**T**"

```

You can also edit /etc/default/grub as root to change the *GRUB_TIMEOUT* value.
```

gksudo gedit /etc/default/grub

```


Corrected:
The easy way to set the *default **menu** entry* is to run the following, substituting a value  for N:
```
sudo grub-set-default N
```



I wrote a guide on Grub 2 basics, linked in my signature line, and there is also the Grub 2 wiki, still a work in progress but with much of the same information:
[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

---

### Post by zika on 2009-07-09
> **drs305 said:**
> The easy way to set the timeout is to run the following, substituting a value (seconds) for N:
```
sudo grub-set-default N
```You can also edit /etc/default/grub as root. Change the *DEFAULT* value.

I wrote a guide on Grub 2 basics, linked in my signature line, and there is also the Grub 2 wiki, still a work in progress but with much of the same information:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)Isn't grub-set-default ment to change default boot entry in grub.cfg file ... ? [http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dset_002ddefault.html](http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dset_002ddefault.html) ... ?

---

### Post by budluva04 on 2009-07-09
> **zika said:**
> Isn't grub-set-default ment to change default boot entry in grub.cfg file ... ? [http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dset_002ddefault.html](http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dset_002ddefault.html) ... ?

yes but as drs305 pointed out you can also edit /etc/default/grub as root, then run update-grub they both do the same thing

anything edited in /etc/default/grub has to be update aftwards with updtae-grub for the changes to be saved to grub.cfg

---

### Post by zika on 2009-07-09
> **budluva04 said:**
> yes but as drs305 pointed out you can also edit /etc/default/grub as root, then run update-grub they both do the same thing

anything edited in /etc/default/grub has to be update aftwards with updtae-grub for the changes to be saved to grub.cfgThat is OK. I know that, look at the message #6, but I just wanted to point out that grub-set-default does not do what was said it does, for the sake of ranch hand (as far as I recall) ... :) Everything is clear, at least for me ... :)

---

### Post by ranch hand on 2009-07-09
> **zika said:**
> At the very beginning of grub2 in Karmic I've changed time-out to 4 (in /etc/default/grub via GRUB_TIMEOUT=4) and it is there after all (daily) upgrades of either grub2 or kernel (I use 2.6.31-999-generic) ... Did You issue update-grub command after changing /etc/default/grub? Because if You did not, You did not make it go (properly) in /boot/grub/grub.cfg ...
I tried it both ways with and without update grub and it did not survive rebooting.  I know that there is a difference in what comes in updates to different systems and that they effect different systems differently.

I have a partition with a fully updated A1 and it only gets grub common files and is still on grub-legacy.

The A2 installation on 2 partitions each on a different drive would not boot at all when installed.  The A2 installed on 1 partition worked fine until another OS was installed after it.

The one partition A2 is the one that I have been trying to get to supply grub to that external but never could get it to after the installation of an other OS.

After this yesterdays update this has ceased to be a problem.

---

### Post by ranch hand on 2009-07-09
[QUOTE=drs305;7587074]Added:  Here is a command line method of changing the grub2 timeout value. I believe the default timeout is 5 seconds. Replace "T" with the desired new timout in seconds.
```

cat /etc/default/grub | grep 'GRUB_TIMEOUT='   # Checks current timeout value
sudo sed 's/GRUB_TIMEOUT=**[COLOR="DarkRed"]5[/COLOR]**/GRUB_TIMEOUT=**[COLOR="DarkRed"]T[/COLOR]**/g' -i /etc/default/grub   # Replaces TIMEOUT VALUE, change "**T**"

```

You can also edit /etc/default/grub as root to change the *GRUB_TIMEOUT* value.
```

gksudo gedit /etc/default/grub

```


Corrected:
The easy way to set the *default **menu** entry* is to run the following, substituting a value  for N:
```
sudo grub-set-default N
```
I believe that
```

sudo grub-set-default N

```
is what I am looking for.  I assume that this is run from a LiveCD.  Is this assumtion correct?

---

### Post by drs305 on 2009-07-09
> **ranch hand said:**
> 
I believe that
```

sudo grub-set-default N

```
is what I am looking for.  I assume that this is run from a LiveCD.  Is this assumtion correct?

The command sets the menu item that is the default for booting. It counts the number of *menuentry* items, starting with 0. So the third menu item, set as default, would be "2".

You can run this from the command line while Ubuntu is running. You have to use the *sudo* command since it is altering a system file.

Trying to figure out your boot setup made my head hurt ;-) . In situations like that I alter the first menu entry in each menu to include a note about which menu.lst or grub.cfg file it's reading from.

Note: You last post didn't format quite correctly - you are probably missing the [noparse] [/quote] [/noparse] entry after the end of the quoted entry.

---

### Post by ranch hand on 2009-07-09
> **drs305 said:**
> The command sets the menu item that is the default for booting. It counts the number of *menuentry* items, starting with 0. So the third menu item, set as default, would be "2".

You can run this from the command line while Ubuntu is running. You have to use the *sudo* command since it is altering a system file.

Trying to figure out your boot setup made my head hurt ;-) . In situations like that I alter the first menu entry in each menu to include a note about which menu.lst or grub.cfg file it's reading from.

Note: You last post didn't format quite correctly - you are probably missing the [noparse]  [/noparse] entry after the end of the quoted entry.[/QUOTE]
Wow, I am pumped.  I am used to grub-legacy and this must be done from the live CD.

My boot is not as tough as it sounds as each HDD system (internal sda and sdb, external dual and single) is separate.  When I change sda the externals are off and sdb is off in bios.  Sdb is handled that way too.  The externals are run separately with the on/off switch with both internals off in bios.

My main OS' are on sda so when using those I can have all the buggers on so I can get to all of them with Nautilus (I know that this is considered risky, it's my system and I like the big hammer).  The externals are set as the first boot option so as long as I only have one on I boot to it.

The dual with no RAID has to have installation of / on its sda and /home on its sdb as it only boots from its sda.

All five Hdds are 320Gb so all but internal sda have plenty of room.  That one has 3 OS' and it is partitioned fully (8.04, 9.04 and Stoner Edition1.0 another 9.04).  Hardy is still my main and used for business, I like LTS.  This will change with Lazy LLama (10.04).

I keep trying other OS' (Linux only) but have to stick with Ubuntu.  I like Mandriva2009-1-Gnome but do not like RPMs.  I do not really like KDE, it just does not blow my skirt up at all.  Xubuntu is nice but I really like Nautilus.

Everyone is supposed to like Fedora, I don't.  It may play nice with Winwhatever (I don't) but it does not play nice with linux OS'.  Same with Foresight.  Gentoo does not like my box for some reason and I have never had much luck with it.  I just put on the new Sabayon to see if it would run and it won't boot and the boot files are trashed when I look at them.

It is on the dual and 9.10 and grub2 pick it up fine as did grub-legacy.  The corrected boot menu looks fine, all the numbers look fine, fstab looks fine (2 partitions 2 HDDs) - just doesn't work and I don't care.

Those partitions will be refilled later this month, about the 23rd.

But, this is why I need to get up to speed with the new Grub.  I like to PLAY and have FUN with my box for a change.  I Started with MS-Dos and quit on 98 (98 from 1998 to 2008 - machine died).  Bought this, much faster box with Vista and both my wife and I were surprised that it ran slower than our old one.

Three weeks later we were switched to Hardy.  Ran like a striped ape.  Ubuntu loves this box.

---

### Post by darco on 2009-07-10
Anyway to adjust the fonts on the grub menu? Pretty nasty....

darco

---

