---
title: "Lubuntu- How do I get updates?"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by uRock on 2010-03-11
I can't find update manager or any other program that looks like it can run updates. I was able to get most of the updates after installing by using the terminal, but this doesn't do kernel upgrades. What do i need to run?

Thanx,
Ronnie

---

### Post by uRock on 2010-03-11
Also, is there a lubuntu-restricted-extras in the works?

Thanx,
Ronnie

---

### Post by slakkie on 2010-03-11
sudo aptitude update
sudo aptitude safe-upgrade

Done.

---

### Post by derrick81787 on 2010-03-11
> **slakkie said:**
> sudo aptitude update
sudo aptitude safe-upgrade

Done.

No, I think he knows how to do this, but it doesn't do kernel upgrades, does it?

If you're using apt-get, do:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

If you're using aptitude, do:
```
sudo aptitude update
sudo aptitude full-upgrade
```

It doesn't really matter which one you use.  I usually use apt-get.

- Derrick

---

### Post by Uncle Spellbinder on 2010-03-11
The OP said *"I was able to get most of the updates after installing by using the terminal"*. Seems to be asking about update manager (GUI) as the OP said *"I can't find update manager or any other program that looks like it can run updates"*

---

### Post by derrick81787 on 2010-03-11
> **Uncle Spellbinder said:**
> The OP said *"I was able to get most of the updates after installing by using the terminal"*. Seems to be asking about update manager (GUI) as the OP said *"I can't find update manager or any other program that looks like it can run updates"*

I understood it as he used **apt-get upgrade** from the terminal, and it worked for most of the upgrades.

> **iRock said:**
> ...but this doesn't do kernel upgrades. What do i need to run?

However, now there are kernel upgrades available, and **apt-get upgrade** doesn't handle them, so he's looking for a way to install them.

It might be useful for the OP to come and clarify.  If he is looking for a GUI, he could install update-manager, but since he is using Lubuntu with LXDE, I'm guessing that it was omitted intentionally from the release.

- Derrick

---

### Post by xebian on 2010-03-11
> **derrick81787 said:**
> I understood it as he used **apt-get upgrade** from the terminal, and it worked for most of the upgrades.



However, now there are kernel upgrades available, and **apt-get upgrade** doesn't handle them, so he's looking for a way to install them.

It might be useful for the OP to come and clarify.  If he is looking for a GUI, he could install update-manager, but since he is using Lubuntu with LXDE, I'm guessing that it was omitted intentionally from the release.

- Derrick

If there is a candidate it will be upgraded - kernel or otherwise.

---

### Post by slakkie on 2010-03-11
> **derrick81787 said:**
> No, I think he knows how to do this, but it doesn't do kernel upgrades, does it?


Yes, aptitude actually handles kernel updates via safe-upgrade. 

> 
If you're using apt-get, do:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

If you're using aptitude, do:
```
sudo aptitude update
sudo aptitude full-upgrade
```


full-upgrade is really not needed for kernel-upgrades (I've seen some exception in the past, but in general, not needed).

---

### Post by Vanishing on 2010-03-11
im guess OP is refering to when there is dependency issues(greyed out)....
if this is the case, just wait.

---

### Post by derrick81787 on 2010-03-11
Oh, okay.  Like I said, I don't usually use aptitude.  I know that when just doing a regular apt-get upgrade, you get a message saying that the kernel packages "have been kept back."  I thought it was the same for aptitude safe-upgrade.

Sorry about that.

- Derrick

---

### Post by uRock on 2010-03-11
I am getting ready to read a book to my little one, but just to clarify, I have gotten all updates except for 6, which I am thinking are the grub and kernel updates. I will try the dist-upgrades in a few to see if they do what I need. A gui would be nice, but I have no problem using terminal.

Thanx for all of the help,
Ronnie

---

### Post by mcduck on 2010-03-11
> **derrick81787 said:**
> Oh, okay.  Like I said, I don't usually use aptitude.  I know that when just doing a regular apt-get upgrade, you get a message saying that the kernel packages "have been kept back."  I thought it was the same for aptitude safe-upgrade.

Sorry about that.

- Derrick

Regular "apt-get upgrade" will definitely work just fine for kernel updates. If you get a message that some update is kept back then try with dist-upgrade, although it's most likely just a dependency issue which is quite normal since this is a development release, and simply doing the update a day later will usually work just fine..

The only difference between "apt-get upgrade" and "apt-get dist-upgrade" is that "upgrade" only replaces packages with new versions and adds new packages if required, while "dist-upgrade" can also remove installed packages if that's required for the upgrade (for example when contents of two existing packages are merged into one new package, you'll need to uninstall the two old packages and install the new package in their place so you'll need a dist-upgrade.)

Since a kernel upgrade doesn't require uninstalling anything simple "apt-get upgrade" will be able to do it (as long as all the required packages are available in the repositories, which I suppose wasn't the case at the moment when you tried to upgrade..

What comes to a GUI, feel free to install one if you want one. Synaptic should work just fine with Lubuntu, and so does the Update Manager Gnome uses although it will probably require a bit tinkering to get the update notifications to work. (by the way, the Update Manager does the same as "apt-get upgrade" does, while Synaptic works like "apt-get dist-upgrade" does...)

---

### Post by uRock on 2010-03-11
I ran apt-get dist-upgrade and it did some installing to include the kernel upgrade, then I ran apt-get upgrade, it ran a few more, then I ran apt-get dist-upgrade again and this is what it shows.```
:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  lxlauncher lxpanel parted udisks
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```
P.S. Every install I have done and used the terminal to do the initial updates, the terminal didn't upgrade the kernel.

---

### Post by uRock on 2010-03-11
Thanx for all the help. I am guessing the last four updates will be done in a later update.

Does anyone know if there will be a Lubuntu-restricted-extras?

---

### Post by uRock on 2010-03-11
I installed update-manager via terminal for future updates and xubuntu-restricted-extras works for Lubuntu.

---

