---
title: "flash"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2011-05-29
What is the cmd i can type into terminal to install flash (so i can play youtube videos)?

when I go to download it from the site, it wants to open with the archive manager in a YUM format. I DONT KNOW what directory to extract it to.

---

### Post by BlouBlou on 2011-05-29
The command is: ```
sudo apt-get install flashplugin-installer
```

---

### Post by kakashi_12 on 2011-05-29
failed.

[sudo] password for 'username'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-installer

---

### Post by sammiev on 2011-05-29
If you are using Firefox, just go into the add-ons and add Flash-Aid then run it. GL :)

---

### Post by kakashi_12 on 2011-05-29
does not show up as an option

---

### Post by Markmental on 2011-05-29
**[B]_ sudo apt-get install flashplugin-nonfree_**
is the command
[/B]

---

### Post by kakashi_12 on 2011-05-29
same error. grrr.

---

### Post by Markmental on 2011-05-29
> **kakashi_12 said:**
> same error. grrr.
what version of ubuntu are you using?

---

### Post by kakashi_12 on 2011-05-29
9

---

### Post by Markmental on 2011-05-29
> **kakashi_12 said:**
> 9
you should upgrade to 10.04  i bet most of these commands are for 1.04 +

---

### Post by kakashi_12 on 2011-05-29
the only 10 version i see is 64 bit. this is a 32 bit cpu. i'll try upgrading to 9.10

---

### Post by Markmental on 2011-05-29
> **kakashi_12 said:**
> the only 10 version i see is 64 bit. this is a 32 bit cpu. i'll try upgrading to 9.10
32 bit is the x86 download  [URL="http://releases.ubuntu.com/lucid/"]http://releases.ubuntu.com/lucid/ download the x86
[/URL]

---

### Post by kakashi_12 on 2011-05-29
well updating was fine. i was able to have access to it through the Ubuntu Software Center. Although, i don't know if i should mark as solved or not. I still don't know the cmd or what irectory to extract to if it's a yum or deb package.

Here's the thing that still stumps me with this system... [http://ubuntuforums.org/showthread.php?t=1770533](http://ubuntuforums.org/showthread.php?t=1770533)

---

### Post by BlouBlou on 2011-05-29
You'll may need to enable "universe", "multiverse" and "restricted" repos. They can be enabled from "software sources" or something like it.

---

### Post by Markmental on 2011-05-29
> **BlouBlou said:**
> You'll may need to enable "universe", "multiverse" and "restricted" repos. They can be enabled from "software sources" or something like it.
yes he should type in this command 
sudo apt-get install ubuntu-restricted-extras

---

### Post by lovinglinux on 2011-05-29
Install [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") and run the Wizard Mode. It will take care of installing flash, removing conflicting plugins and applying performance tweaks.

---

### Post by sammiev on 2011-05-29
> **lovinglinux said:**
> Install [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") and run the Wizard Mode. It will take care of installing flash, removing conflicting plugins and applying performance tweaks.

Suggested that on post 4. :(

---

### Post by lovinglinux on 2011-05-29
> **sammiev said:**
> Suggested that on post 4. :(

I know, but the user wasn't able to find it, so I posted the link :-)

---

