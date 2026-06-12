---
title: "Crash while upgrading to 8.04. Lost my home folder"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by mdsingh on 2008-07-14
Hi All,

I was in process of upgrading from Ubuntu 7.10 to 8.04.

Due to power failure, my system rebooted just 10 min before full installation complete. Now, system can't boot because /home/{user} is no longer there. (my bad I didn't do a backup before)

I am able to boot in recovery mode to get a command line. Is it possible to get my home folder back? setup should have copied it somewhere before removing. I can't find it. Please help

---

### Post by pytheas22 on 2008-07-14
You could use photorec to recover your files.  Boot to the live CD and install it with:
```

sudo apt-get install testdisk
```

then run it with:
```

sudo photorec
```

It will recover files in /home.

But there may be a better way to get your things back if the installer did indeed copy /home to a certain location.  I don't know where it would put it, however.  Does the command:
```

locate YOUR-USERNAME
```

return anything?

---

