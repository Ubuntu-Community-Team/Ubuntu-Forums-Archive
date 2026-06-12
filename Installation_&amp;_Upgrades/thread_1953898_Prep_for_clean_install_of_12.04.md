---
title: "Prep for clean install of 12.04"
date: 2012-04-07
forum: Installation &amp; Upgrades
---

### Post by elyse on 2012-04-07
I'm looking forward to 12.04 -- I've been running KDE backports (with akonadi and nepomuk turned off as much as possible) and in the past day or two rekonq is dramatically more stable  -- I don't think it has crashed since I rolled the kernel back to 3.0.0-17 -- and kmail seems a bit less flakey, though it still tends to drop its connection to GMAIL occasionally.

However I think I would be prudent to do a clean install of 12.04 (I did an upgrade to 11.10, and man was that ugly) and after all the weirdness I went through to get kmail working and have access to my old email archives I want to make sure I don't step on anything.

I have a separate /home partition and my old archival emails are being served by a local dovecot IMAP server instead of imported directly into the new kmail. (Kmail mostly talks to 3 different IMAP servers: Gmail, my work email server (Zimbra), and the localhost dovecot server.) 

I plan to do a dump of the list of installed packages before I do the clean install, and copy the old /etc to space on /home so I have a record of all my old config settings. 

Does anyone know is there is other information I will want available for reference to reconstitute my system after doing a clean install? Do the newer versions of KDE and/or Ubuntu store configuration info anywhere weird? I've been doing upgrades for the past couple of years and may have lost track.

Is any of the data used by the kmail-akonadi-nepomuk conglomeration stored elsewhere than on /home?

---

### Post by Zorael on 2012-04-07
Backing up your **/etc** is a good idea, but naturally you may only want to use it as reference rather than copy it all back.

Not all of Akonadi is stored in **~/.kde/share/*** -- if memory serves, the databases themselves are in **~/.config/akonadi** -- but pretty much everything worthy of saving is safe in your home. If you're a good citizen (;3) you haven't modified anything in /usr or other packager-managed directories, so no need to worry about those. You might want to skim the contents of **/usr/local**, I guess.

I cooked up this a few releases back, though it's arguably of limited use. It requires [**debsums**](apt://debsums). Also note that it doesn't check files created by installation scripts, so I think it sometimes misses stuff in **/etc**. It doesn't format errors perfectly, but it serves.
```
#!/bin/bash

if [ ! "$(which debsums) " ]; then
    echo "You need to install debsums!"
    exit 1
fi

packages="$(dpkg -l | grep ^ii | awk '{ print $2 }')"
i=0

printf "Starting hash of %d packages.\n\n" $(echo "$packages" | wc -l)

while read package; do
    ((i++))
    unset list
    printf "."
    [ $((i%100)) -eq 0 ] && printf "(%d)\n" $i
    list="$(debsums -c $package)"
    [ ! "$list" ] && continue
    printf "\n###### Package %s has been modified!\n" $package
    printf "$list\n"
done <<< "$packages"

printf "\n\nDone hashing %d packages.\n" $i
```

---

### Post by SeijiSensei on 2012-04-07
I actually keep /usr/local on a separate partition as well as /home since I occasionally build software from source.  I replaced my 10.10 Kubuntu version with 12.04b1 some weeks back and had no problems to speak of.  There is the annoying issue with [resolv.conf]("http://ubuntuforums.org/showthread.php?t=1914807") in 12.04, but if you don't manually alter your nameserver list like I do, it shouldn't be a problem for you.

---

