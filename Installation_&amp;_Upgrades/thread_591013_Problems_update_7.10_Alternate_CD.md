---
title: "Problems update 7.10 Alternate CD"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by nsL on 2007-10-25
I upgraded my ubuntu to 7.04 and started having problems cause X didnt worked and showed a blue window and reached me to a console terminal. I decided to upgrade to 7.10 in order to solve the problem.

I downloaded Alternate ISO so i could upgrade by console. I mount the iso, and execute "sh ./cdromupgrade"

The first time i executed that, it gave me an error about icons or something like that. Then i executed again and says that "gutsy.tar.gz" its missing.

Here is part of shell code of cdromupgrade:
```

CODENAME=gutsy
UPGRADER_DIR=dists/stable/main/dist-upgrader/binary-all/

cddirname=${0%\/*}
fullpath=$cddirname/$UPGRADER_DIR

# extrace the tar to a TMPDIR and run it from there
if [ ! -f $fullpath/$CODENAME.tar.gz ]; then
    echo "Could not find the upgrade application archive, exiting"
    exit 1
fi

```

UPGRADER_DIR ends on a slash "/" and here they're adding another slash between path and namefile -> $fullpath/$CODENAME.tar.gz 

So it tries to find file: dists/stable/main/dist-upgrader/binary-all/[COLOR="Red"]**/**[/COLOR]gutsy.tar.gz

Maybe its a bug, maybe im noob (i am) and im doing things wrong, however i liked to share it with you.

How can i modify the content of an ISO in order to change that?, cause is protected by readonly.

Sorry for my english. Greetings!!

---

### Post by ianmidd on 2007-10-25
I had the same problem.

Here's the fix:

[http://ubuntuforums.org/showthread.php?t=580338&highlight=alternate+cd+spaces+upgrade]("http://ubuntuforums.org/showthread.php?t=580338&highlight=alternate+cd+spaces+upgrade")

---

