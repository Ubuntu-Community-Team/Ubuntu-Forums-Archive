---
title: "Error trying to get graphics interface!"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by Hoss212 on 2008-01-12
Okay so I have the "Command" interface on here, but I am want the full graphics interface. I try to do..

```
sudo apt-get install xubuntu-desktop gdm
```

Then tells me to enter labeled CD, so I do so...

And then that works but I get a whole bunch of these during th installation...

```
Buffer I/O error on device sr0 or some 'similar' stuff...
```

And then, at the end of the installation it says a few error things and that it could not be found or some crap... And I believe it's because of the Buffer problem, now would my CD be causing this Buffer I/O error on device0? If so, I might have to wait until xubuntu gets a ShipIt! service. All help if greatly appreciated! :)

---

### Post by livestockPimp on 2008-01-12
The only time I have received these errors have been from dud cds or CD roms. why dont you download these packages from an online repository?

---

### Post by Hoss212 on 2008-01-12
> **livestockPimp said:**
> The only time I have received these errors have been from dud cds or CD roms. why dont you download these packages from an online repository?

What do you mean m8?

---

### Post by EXCiD3 on 2008-01-12
Remove the official ubuntu cd from the sources list: System->Administration->Software Sources. Then remove the Ubuntu Cd from the list. This forces Ubuntu to download the packages instead of installing them from local media.

---

### Post by Hoss212 on 2008-01-12
> **EXCiD3 said:**
> Remove the official ubuntu cd from the sources list: System->Administration->Software Sources. Then remove the Ubuntu Cd from the list. This forces Ubuntu to download the packages instead of installing them from local media.

Okay but when i try to do that I type in /system/administration/software sources and it says 'no such file or directory' ...?

---

### Post by EXCiD3 on 2008-01-12
On the gnome-panel there is the System Menu, then go to the Administration Section, then click Software Sources.

---

### Post by Hoss212 on 2008-01-12
I told you I said I only have Command Interface, NOT graphics with desktop and all that. So that's off...

---

### Post by PmDematagoda on 2008-01-12
Open the sources.list file for editing using nano:-
```
sudo nano /etc/apt/sources.list
```

Then uncomment the repository for the CD-ROM by typing # in front of it, after that is done, save the file, execute:-
```
sudo apt-get update
```
After that is completed you should be able to install the necessary packages.

---

### Post by Hoss212 on 2008-01-12
When I type the directory to get in...

```
sudo nano /ect/apt/cources.list
```

it says "sudo: nano: command not found...

I also tried just typing the directory in and it says "No such file or directory" ...?

---

### Post by PmDematagoda on 2008-01-12
Then try VIM:-
```
sudo vim /etc/apt/sources.list
```

You can learn how to use VIM from [here]("http://www.vinacis.net/content/view/23/32/").

---

### Post by Hoss212 on 2008-01-13
Okay that works now but now I'm bloody stuck on what to do after that to uncomment the CD repository or w/e.

---

### Post by PmDematagoda on 2008-01-13
Did you read the guide that I linked to? That has the keys to be used on VIM.

---

### Post by EXCiD3 on 2008-01-13
Since you are running XFCE ```
sudo nano/etc/apt/sources.list
``` should do the trick. VIM is hard to get used to for a lot of people. When you are done editing the file, hit Ctrl-X to save and quit.

---

