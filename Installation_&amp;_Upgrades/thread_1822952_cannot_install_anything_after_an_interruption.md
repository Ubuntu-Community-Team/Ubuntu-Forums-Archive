---
title: "cannot install anything after an interruption"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by joytree on 2011-08-11
Hi, everyone 

I'm quite new to unbuntu and I'm getting puzzled for whenever I type 

'sudo aptitude install ' for any software, I got the same error:

'E: I wasn't able to locate a file for the skype package. This might mean you need to manually fix this package. (due to missing arch)'

I guess it's due to I manually stopped the installation of skype for 'skype-ubuntu_2.2.0.35-1_i386.deb', and restarted my computer. 

ps. I cannot install anything from Unbuntu software center either.

Could you tell me how to check what's wrong and how to fix?

Thanks!

---

### Post by dino99 on 2011-08-11
close all the opened/running software and try into a terminal:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by joytree on 2011-08-11
> **dino99 said:**
> close all the opened/running software and try into a terminal:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

Thanks!

But in 'sudo apt-get autoremove' and 'sudo apt-get install -f', I get

'E: The package skype needs to be reinstalled, but I can't find an archive for it.'

and it seems I still cannot install anything..

---

### Post by dino99 on 2011-08-11
> **joytree said:**
> Thanks!

But in 'sudo apt-get autoremove' and 'sudo apt-get install -f', I get

'E: The package skype needs to be reinstalled, but I can't find an archive for it.'

and it seems I still cannot install anything..

open nautilus and search for "skype" on top quicksearch field, then delete all the "skype" folders/files found: check each for their proprties (righ click) to know their path.

---

### Post by joytree on 2011-08-11
> **dino99 said:**
> open nautilus and search for "skype" on top quicksearch field, then delete all the "skype" folders/files found: check each for their proprties (righ click) to know their path.


sorry, I don't whether I have nautilus or not..  when I type nautilus in a terminal, it pops out File Browser..

---

### Post by dino99 on 2011-08-11
> **joytree said:**
> sorry, I don't whether I have nautilus or not..  when I type nautilus in a terminal, it pops out File Browser..

Nautilus is the official file manager for the GNOME desktop. It allows
to browse directories, preview files and launch applications associated
with them. It is also responsible for handling the icons on the GNOME
desktop. It works on local and remote filesystems.

---

### Post by TheGuvernor on 2011-08-11
Nautilus is your file browser. When you go to Places>Home it's the window that pops up. Search in there and you should find them.

---

### Post by joytree on 2011-08-11
> **TheGuvernor said:**
> Nautilus is your file browser. When you go to Places>Home it's the window that pops up. Search in there and you should find them.

Thanks. But even after I deleted all the 'skype' file I found in the file system, it still has the problem above...
and when I open Synaptic Package Manager, it pops out the same error : 
E: The package skype needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

... help needed ...

---

### Post by TheGuvernor on 2011-08-11
Try this command in Terminal:

find / -name skype*

See if it comes up with anything

---

### Post by yaddoshi on 2011-08-11
I find 'locate' works a bit better in terminal, but you have to update the database periodically.

```
sudo apt-get install locate
sudo updatedb
locate skype
```

---

### Post by TheGuvernor on 2011-08-11
> **yaddoshi said:**
> I find 'locate' works a bit better in terminal, but you have to update the database periodically.

```
sudo apt-get install locate
sudo updatedb
locate skype
```

The database should update every night at midnight. But you can force it at any time by:

sudo updatedb

---

### Post by joytree on 2011-08-12
> **TheGuvernor said:**
> The database should update every night at midnight. But you can force it at any time by:

sudo updatedb


It's solved, in an unexpected way: 

it seems no use to delete every 'skype' file. One senior guy in my lab tried

sudo dpkg -i skype-debian_2.2.0.35-1_i386.deb

to reinstall it again. and it solved!

Thanks.

---

