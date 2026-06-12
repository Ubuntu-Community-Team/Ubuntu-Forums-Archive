---
title: "Upgrade 22.04 to 24.04.1 - 'update-manager' is marked for removal but..."
date: 2024-08-30
forum: Installation &amp; Upgrades
---

### Post by squishier on 2024-08-30
Hi folks,
I'm trying to upgrade from 22.04 to 24.04.1. Started out the graphical way but then by running `sudo do-release-upgrade`

I'm getting this error


```
Calculating the changes


Could not determine the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


The package 'update-manager' is marked for removal but it is in the 
removal deny list. 


If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If 
you want to investigate this yourself the log files in 
'/var/log/dist-upgrade' will contain details about the upgrade. 
Specifically, look at 'main.log' and 'apt.log'. 




Restoring original system state
```



I _could_ remove `update-manager` but that takes `ubuntu-desktop` and a bunch of others with it, most of them say something along the lines of "used to ensure a smooth upgrade experience, it is recommended not to remove" in their descriptions so removing seems kinda counter intuitive &#128579;

Any suggestions?

---

### Post by squishier on 2024-08-31
For anyone who ends up here, the problem was due to having previously set up a PPA to get a newer version of pipewire. Using ppa-purge to get rid of that PPA and downgrade did the trick

---

### Post by raxod502 on 2024-09-02
Why on earth would having a newer version of pipewire cause an issue with *update-manager* of all things?

---

### Post by goldstein2034 on 2024-09-03
Sorry but I'm facing this exact problem and I'm not sure how to downgrade pipewire.

Would any expert be kind enough to post a step-by-step guide?

Thanks!

---

### Post by serrano-pereira on 2024-09-03
Do this:

```

sudo apt install ppa-purge aptitude
sudo ppa-purge -o pipewire-debian -p pipewire-upstream

```

Unfortunately ppa-purge exited with an error. So I added the PPA again so that I can try ppa-purge again:

```

sudo add-apt-repository ppa:pipewire-debian/pipewire-upstream
sudo ppa-purge -o pipewire-debian -p pipewire-upstream
sudo apt --fix-broken install

```

Surprisingly that ended up in a different ppa-purge error, so I just kept repeating that until it succeeded. In the end it did succeed, and I was able to do the upgrade.

---

