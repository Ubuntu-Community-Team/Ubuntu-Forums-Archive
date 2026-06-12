---
title: "Aborted prior do-release-upgrade, now no updates found"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by xyverz on 2012-05-14
I had aborted a previous do-release-upgrade from natty to oneiric due to a lack of internet access (proxy issues) on my work machine. Now, when I try to run do-release-upgrade, I get "No new release found":

```
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-15-server x86_64)

 * Documentation:  http://www.ubuntu.com/server/doc

New release 'oneiric' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Mon May 14 14:16:21 2012 from another.computer
[ user @ host]
[ ~ ] 1 >> do-release-upgrade
Checking for a new ubuntu release
No new release found
```

Any suggestions on resetting this?

---

### Post by kc1di on 2012-05-14
try this in a terminal one line at a time and try the upgrade again.

```
sudo apt-get autoclean 
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

---

### Post by xyverz on 2012-05-15
Dave,

Thanks for your assistance. I ran the commands you've listed, but I'm still getting the same error.  This time, however, it took a while to return the error message (instead of returning it immediately).

Does it make a difference that I'm using an internal mirror, even though it's rsync'd nightly?

Thanks.

--X...

---

### Post by jadtech on 2012-05-15
> **xyverz said:**
> I had aborted a previous do-release-upgrade from natty to oneiric due to a lack of internet access (proxy issues) on my work machine. Now, when I try to run do-release-upgrade, I get "No new release found":

```
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-15-server x86_64)

 * Documentation:  http://www.ubuntu.com/server/doc

New release 'oneiric' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Mon May 14 14:16:21 2012 from another.computer
[ user @ host]
[ ~ ] 1 >> do-release-upgrade
Checking for a new ubuntu release
No new release found
```

Any suggestions on resetting this?

do-release-upgrade should get you 12.04 at this point not 11.10  :)

---

### Post by xyverz on 2012-05-15
> **jadtech said:**
> do-release-upgrade should get you 12.04 at this point not 11.10  :)

That's ultimately what I'm aiming for. However, it's telling me that there's no upgrade available.

I'm about ready to just edit my sources.list file by hand and do a dist-upgrade, just like I used to do back in my old Debian days...

---

### Post by jadtech on 2012-05-15
> **xyverz said:**
> That's ultimately what I'm aiming for. However, it's telling me that there's no upgrade available.

I'm about ready to just edit my sources.list file by hand and do a dist-upgrade, just like I used to do back in my old Debian days...

have you  tired changing the server in the software updater run check for updates at that point if any updates show  run them all and reboot then if no upgrade button shows up  go to the terminal ..

```


sudo apt-get update

do-release-upgrade


```

changing the server should rebulid  the whole list to fit  what is on that server ..

---

### Post by xyverz on 2012-05-16
> **jadtech said:**
> have you  tired changing the server in the software updater run check for updates at that point if any updates show  run them all and reboot then if no upgrade button shows up  go to the terminal ..

changing the server should rebulid  the whole list to fit  what is on that server ..

I've tried that - switching from our internal mirror to ANL's mirror (which is what we're rsync'ing every night). Still no dice. I even tried reverting to the default ubuntu repos with no luck. *shrug*

Thanks for the help tho. =)

---

### Post by xyverz on 2012-05-16
I've resolved this problem the same way a vet treats a sick horse: I edited my sources.list file to pick from the precise repos and then did a dist-upgrade from the console.

Along the way I had some problems - most resolved with an 'apt-get upgrade -f install' or one pesky problem with nux-tools that required me to remove the legacy software (libnux-0.9-0 and libnux-0.9-common) in order to get stuff to work, but I've got Precise running now.

Thanks to the both of you for your assistance. I do appreciate it. =)  I shall mark this thread solved now.

---

