---
title: "Jaunty/intrepid language packs conflict"
date: 2009-02-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by braikar on 2009-02-16
Hi,

I have a problem that leaves me only with the gnome UI working, but not correctly.
I am on Intrepid x64.

In fact I wanted to have photorec/testdisk 6.10, so I added the jaunty repository to the sources list to be able to get it (as the intrepid ones only have 6.9, which is kind of stupid, as 6.10 was released in july?). I wanted to remove it from the sources list afterward. Because I saw it added 800 updates to the autoupdate system... 

ANyway I was doing my hdd recovery with photorec, which works really great! But some hours later I forgot I had these repositories activated... ANd I installed new language packs, I guess for jaunty release. And on the next restart everything was corrupted.

The UI starts, but there is no login screen, my background colors are unset, the menubar doesn't show up, awn doesn't show up, kibadock doesn't show up, thankfully I have cairo-dock working else I wouldn't have access to firefox!!

Nautilus doesn't work either, the alt-f2 command doesn't work.

That's the problem, now I'm nearly sure it's imcompatibilities between the language packs that have caused this problem, Because I saw nautilus/gnome/awn language packs being updates. Compiz is not affected, I have the desktop effects working.
Anyway, I have no idea how to correct the problem. I removed jaunty from the sources list, and did apt-get update upgrade, but it doesn't update the language packs back to the intrepid version? it says everything is good.

I assume the language packs are different for intrepid and jaunty??
But I have no idea how to force the upgrade of the language packs to the correct version? I don't even know how to check their versions. Thankfully I have cairo dock and can create launchers to launch applications, so I can run synaptic, the terminal etc. and anything else needed.

Does anyone know what I need to do to get this conflict sorted without reinstalling everything?

Thanks

---

### Post by braikar on 2009-02-19
I solved my problem, I found what I was looking on
[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)
using the second method, forcing a downgrade with
```

        Package: *
        Pin: release a=intrepid
        Pin-Priority: 1001

        Package: *
        Pin: release a=faunty
        Pin-Priority: 60

```
in /etc/apt/preferences

setting the two version sources repositories
and the apt-get command I was especially looking for:
sudo apt-get dist-upgrade
I was still quite suprised! updating the language packs, changed nearly 600 packages at the same time!!

Kudos to the Ubuntu community :), there's always a solution online for any problem... just need to search for the right thing

Just one stupid question, I cannot find the option? How do I set this topic as SOLVED? Should I just change the name or there is a specific option?

---

