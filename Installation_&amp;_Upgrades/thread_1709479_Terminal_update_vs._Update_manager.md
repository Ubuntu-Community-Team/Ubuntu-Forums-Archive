---
title: "Terminal update vs. Update manager"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by runeh76 on 2011-03-18
Hi

When i do update from Terminal, i dont get all updates which are in Update manager. Why?

```
sudo apt-get update
      sudo apt-get upgrade
```

---

### Post by runeh76 on 2011-03-19
Nobody cant explain this??

In terminal i do updates, and after that i check update manager, there is still updates. Isnt terminal should be powerful?

---

### Post by Dutch70 on 2011-03-19
Not sure really, I've noticed something similar. I believe if you run it in terminal again it will get them all.

---

### Post by misterbiskits on 2011-03-19
I've noticed this as well...

---

### Post by runeh76 on 2011-03-19
Okey thx guys! Im glad to hear that im not alone.
If someone know why this happens, pls let us know!

---

### Post by Old_Grey_Wolf on 2011-03-19
From typing "man apt-get" in terminal:

upgrade

    upgrade is used to install the newest versions of all packages
    currently installed on the system from the sources enumerated in
    /etc/apt/sources.list. Packages currently installed with new
    versions available are retrieved and upgraded; under no
    circumstances are currently installed packages removed, or packages
    not already installed retrieved and installed. New versions of
    currently installed packages that cannot be upgraded without
    changing the install status of another package will be left at
    their current version. An update must be performed first so that
    apt-get knows that new versions of packages are available.


dist-upgrade

    dist-upgrade in addition to performing the function of upgrade,
    also intelligently handles changing dependencies with new versions
    of packages; apt-get has a "smart" conflict resolution system, and
    it will attempt to upgrade the most important packages at the
    expense of less important ones if necessary. So, dist-upgrade
    command may remove some packages. The /etc/apt/sources.list file
    contains a list of locations from which to retrieve desired package
    files.

---

### Post by runeh76 on 2011-03-19
And point was..?

---

### Post by Old_Grey_Wolf on 2011-03-19
> **runeh76 said:**
> And point was..?

"sudo apt-get upgrade" doesn't install new packages. It only upgrades the ones you currently have. It also will not upgrade a package that depends on another package that needs to be installed.

"sudo apt-get dist-upgrade" and the Update Manager will install new packages.

---

### Post by uRock on 2011-03-19
> **runeh76 said:**
> And point was..?
To read and learn how these commands work differently. If you are running these commands, then it is good to know what they are doing.:D

---

### Post by runeh76 on 2011-03-19
Thank you Old_gray_wolf!

And urock... Not all understand english like u do!

---

### Post by Old_Grey_Wolf on 2011-03-19
> **runeh76 said:**
> Nobody cant explain this??

In terminal i do updates, and after that i check update manager, there is still updates. **Isnt terminal should be powerful?**

> **runeh76 said:**
> Thank you Old_gray_wolf!

And urock... Not all understand english like u do!

uRock has a good point. If you read about the apt-get command you will discover that **it is a powerful** command. Most people don't know 80% of what apt-get can do.

---

### Post by runeh76 on 2011-03-19
Yes u are right! But i didnt mean it that way! I know that everything can be done from terminal. Sry i cant say this how i would like it to say, becouse my english isnt so good. Thats my biggest problem to learn Linux. First u have to learn english :)
But my question..u solved it! Thx again i really appreciate this!

---

### Post by uRock on 2011-03-19
> **runeh76 said:**
> Yes u are right! But i didnt mean it that way! I know that everything can be done from terminal. Sry i cant say this how i would like it to say, becouse my english isnt so good. Thats my biggest problem to learn Linux. First u have to learn english :)
But my question..u solved it! Thx again i really appreciate this!
The terminal doesn't work in your native language? If not, then I apologize. Google translate may be helpful with this.

Cheers,
uRock

---

### Post by runeh76 on 2011-03-19
Google translate--> apology received :)

Cheers urock!

---

### Post by Old_Grey_Wolf on 2011-03-19
> **runeh76 said:**
> Google translate--> apology received :)

Cheers urock!

You can change the language your computer uses. This is the Ubuntu documentation for changing it [https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale).

Edit: I just checked what languages are installed on my computer and Finnish is one of them.

---

### Post by runeh76 on 2011-03-19
Thx again, but my computer language is Finnish..hmm.. can i change terminal help/man outputs to Finnish? That would be really awesome!

---

### Post by Old_Grey_Wolf on 2011-03-19
> **runeh76 said:**
> Thx again, but my computer language is Finnish..hmm.. can i change terminal help/man outputs to Finnish? That would be really awesome!

hmm. I looked in the Ubuntu repositories for man pages and found them for French, Turkish, Polish, Japanese, Italian, Czech, Spanish, Chinese, Hungarian, Portuguese, Russian, German, and of course English.

I didn't see one for Finnish. :(

---

### Post by runeh76 on 2011-03-20
Okey then its English for me. Thx anyway  :)

---

