---
title: "Upgrading Edgy to Feisty = No computer. (Help needed)"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by Scruffynerf on 2007-07-04
Well, I went to upgrade last night from Edgy to Feisty.

I used this method:
```
$ gksu update-manager -c
```

When installing... it glitched on the system log updating. Badly. at 20+ minutes of total hard drive inactivity, it rebooted itself. Came up (very fast) with a bunch of weirdly coded errors (something like swatch errors ???) then xorg dies.

So, I'm downloading the DVD for Feisty, and I'm guessing that I can re-install Feisty over the top of my dead "Feidgy" install.

What I am worried about is that if I re-install a base Feisty image over the top of the dead Edgy, will it nuke my customizations and or some of the programs/applications.

Eg:
I had several custom Nautilus scripts. Will they die or not?
I was running a self-installed Thunderbird 2. Will I be able to keep my address books and emails?
Will I be able to keep my custom metacity theme? Icon themes? Cursor themes?
Will I still have my Firefox extensions / bookmarks etc?

Note: my home folder is on a completely separate hard drive, so I'm confident that I won't lose data. Or will re-installing Feisty recognise that i have a valid home directory elsewhere?

many thanks for any and all help.

---

### Post by scragar on 2007-07-04
I'm almost certain that attempting to install it again will nuke your system, can you not just mash esc to load the options menu that lets you load an old configuration?

if you can't fall back on the last working model try to back up your files onto an external hard drive or online(only works with small files unless you have really fast internet) while running a Live CD.

if all else fails buy a cheap hard-drive from scan.co.uk or radio-shack and use it to re-install 'buntu on then back-up your files onto it, re-install the first hard-drive, copy them back then claim a re-fund on the new hard-drive(scan will give it you if it's returned with packaging and a receipt withing 7 days even if it's not broken)

---

### Post by Scruffynerf on 2007-07-05
> **scragar said:**
> I'm almost certain that attempting to install it again will nuke your system, can you not just mash esc to load the options menu that lets you load an old configuration?

if you can't fall back on the last working model try to back up your files onto an external hard drive or online(only works with small files unless you have really fast internet) while running a Live CD.

if all else fails buy a cheap hard-drive from scan.co.uk or radio-shack and use it to re-install 'buntu on then back-up your files onto it, re-install the first hard-drive, copy them back then claim a re-fund on the new hard-drive(scan will give it you if it's returned with packaging and a receipt withing 7 days even if it's not broken)

1) Nope mashing anything on the computer doesn't work. I do have xorg backups from before, but don't know of the command to restore them.

2) I'm in Australia, and do not have the cash to just go out and buy another hard drive. 

Also, from what I remember, installing the nvidia drivers was an absolutely PITA. (Envy also broke Xorg as well)

---

### Post by scragar on 2007-07-05
what about starting the installer and having it resize the existing partition?

it's a little risky since a powercut or such would make your files almost completely unreadable, but it sounds like your only option.

ifyou resize your main partition to install ubuntu again you can copy your files onto the new partition made from the unused parts of your current one, then delete the old partition afterwards with something like partition magic(allocating the space for your new partion).

a powercut during resizing of the partion would wipe out your current instilation completely though so be warned

---

### Post by Scruffynerf on 2007-07-05
Ext3 filesystems do not have a defragger (afaik) - just about any partition resizing will nuke the installation - as in total data loss. It doesn't need a powercut to destroy the data - the re-sizing will do that all by itself.

Remember, my home partition is on another physical hard drive (an IDE slave FWIW). I'm hopeful that the re-installation of either Edgy or Feisty will have somewhere an option to NOT reformat my home partition. As I understand it, the home partition contains both my data files and the configuration files for most of my applications.

This does not need to be messed with.

I'm hoping that the re-installation (as I'm pretty confident that the "Feidgy" installation is pretty hosed) will overwrite the corrupted files with new ones, and I'm assuming that for a lot of applications I'll need to re-install from Feisty or Edgy repo's, depending on what I go with. I'm pretty resigned to the fact that I'll need to re-install most software I had, and possibly over-writing with the ones in my home directory.

I'm mainly worried about the following (copied from the OP):

Self-installed Thunderbird 2. Will I be able to keep my address books and emails?
Will I be able to keep my custom metacity theme? Icon themes? Cursor themes?
Will I still have my Firefox extensions / bookmarks etc?
I had several custom Nautilus scripts. Will they die or not?

I did have quite a lot of customisations that I had to do in order for stuff to work (eg: not a single guide out there helped me for nvidia drivers, apart from half-following one. I appear to have a computer that nobody's ever seen the like before.)

EDIT: I guess that I'm pretty pissed that the recommended way to update my OS results in me not having an OS. Frankly it's almost a deal-breaker, and I'm tempted just to go back to windows. 

cheers

Scruffy.

---

### Post by scragar on 2007-07-05
dapper repartioned my hard drive letting me keep windows XP when I first installed it, so why would the installer not let you keep your old instillation?

and if you overwrite the partition all your files will be lost, you could back them up from the terminal or graphic safe mode using the mv command.

---

### Post by Scruffynerf on 2007-07-05
Because I don't have the room. As it is, the primary drive already has XP Home partition, 1 Ubuntu Partition and the swap partition. It's full.

I believe that with edgy and feisty installs, if you partition manually, you can select a 'do not format option'. Other posters on the board have already indicated this is the case with the home partition. I'm hoping that the options are also there for the normal partitions.

Hence, I won't need to overwrite the partition, just the files. That's why I'm hoping that a lot of what's on there will be preserved.

Also, as the update worked up until the system log issue, most of my applications should have been updated to Feisty versions - Ergo, there should be no loss of (most) application data, just borked system data. Hence, the re-install should overwrite corrupted files, whilst leaving everything else intact.

Scruffy.

---

### Post by Scruffynerf on 2007-07-05
Update - resolved.

Tunnelled in from another computer, and backed up thunderbird and other profiles. Installed 7.04, unfortunately re-formatting the '/' partition, however not formatting the home partition.

Been madly updating stuff and adding repositories.

cheers

Scruffy

---

