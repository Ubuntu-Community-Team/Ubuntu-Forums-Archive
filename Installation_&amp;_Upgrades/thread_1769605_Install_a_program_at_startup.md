---
title: "Install a program at startup?"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by newbie2210 on 2011-05-28
I want to install the following command as a program and get it on startup.
cd Desktop/
sudo lkl -l -k keymaps/us_km -o log.file

and running it since the computer starts up until it's shut down.
How can I do it?
I have Ubuntu 10.14

---

### Post by sag0th on 2011-05-28
Create executable file with content:

```

#!/bin/sh
cd ~/Desktop
sudo lkl -l -k keymaps/us_km -o log.file & 
```

and place it in some directory included in your PATH (lets say /usr/bin). Then use:
System -> Preferences -> Startup Applications
to run it at start up.

---

### Post by newbie2210 on 2011-05-28
> **sag0th said:**
> Create executable file with content:

```

#!/bin/sh
cd ~/Desktop
sudo lkl -l -k keymaps/us_km -o log.file & 
```and place it in some directory included in your PATH (lets say /usr/bin). Then use:
System -> Preferences -> Startup Applications
to run it at start up.

How do I exactly place it on the directory that I want?

---

### Post by sag0th on 2011-05-28
cut/paste??? :shock: 

if you want to move it in /usr/bin just:
```
sudo mv <your-file> /usr/bin/
```

in console.........

---

### Post by rvchari on 2011-05-28
a small doubt and sorry to jump in...

does he have to give the path cd /home/USERNAME/Desktop instead of ~/Desktop ? i presume you advised to move it to /usr/bin. if the batch file has to be pointed to the particular user desktop then do we have to do what i said or will it take care of that ?

---

### Post by sag0th on 2011-05-28
~/Desktop
/home/[color=red]$[/color]USERNAME/Desktop
/home/`whoami`/Desktop

are equal and the result depends on the user that executes the script. 

If user is sag0th and the file is located only on rvchari's Desktop the path must be hardcoded /home/rvchari/Desktop

---

