---
title: "Upgrade issues"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by Ubun00btu on 2007-08-22
Well, first of all, I gotta say thanks to the Ubuntu creators for putting out this OS.  I've fooled with Linux before, but since this has come out my machine has been dual-boot and XP only gets used to game with.  So far, I'm really liking it.

The only real stumper I've had is using the upgrade scritp on the desktop:

 ```
ksudo sh /usr/share/ultimate/gamers.sh
```

It pops up a terminal window, asks for the password, and the disappears as soon as I enter the password.  I'd like to upgrade to the Gamer's Edition.

Is there a know bug?  I searched the forums, couldn't find anything on it or a workaround.

I'm using The most current release of Ubuntu Ultimate (Feisty, I believe), and it's all up-to-date.

---

### Post by mocoloco on 2007-08-22
I'm not too familiar with Ultimate edition, but it looks like it still uses Gnome.  The command you need is "gksudo" or if you're using KDE it's "kdesu"; "ksudo" is not the correct command.

Since it's popping up a terminal for you, I assume you're using a "run" window or something similar, which normally be fine.  In situations like this a good thing to do is open a terminal and run it from there, then you should be given clues as to why it's failing (in this case it would have told you "ksudo: command not found").

---

### Post by Ubun00btu on 2007-08-22
The code is simply what I pulled from the icon after right-clicking, nothing I entered by hand.  I'd previously installed Ubuntu on an old HDD and double-clicked the upgrade icon and it began the upgrade process after I made a few selections.  Out of curiosity, how many GB does the upgrade take?  I've got Ubuntu on a 23GB partition, maybe if that's too small it won't allow it?

Edit:  I went back and looked, it is actually gksudo...  I just clipped a letter when I cut'n pasted it to the forums.

---

### Post by Ubun00btu on 2007-08-24
*bump*


Bueller?

---

### Post by Ubun00btu on 2007-09-10
bump x2, still no help...

---

### Post by kenji-san on 2007-09-10
> **Ubun00btu said:**
> Well, first of all, I gotta say thanks to the Ubuntu creators for putting out this OS.  I've fooled with Linux before, but since this has come out my machine has been dual-boot and XP only gets used to game with.  So far, I'm really liking it.

The only real stumper I've had is using the upgrade scritp on the desktop:

 ```
ksudo sh /usr/share/ultimate/gamers.sh
```

It pops up a terminal window, asks for the password, and the disappears as soon as I enter the password.  I'd like to upgrade to the Gamer's Edition.

Is there a know bug?  I searched the forums, couldn't find anything on it or a workaround.

I'm using The most current release of Ubuntu Ultimate (Feisty, I believe), and it's all up-to-date.

As mocoloco stated, try it in a terminal window.  Open the terminal and enter it this way:
> sudo sh /usr/share/ultimate/gamers.sh
Then it will print out any errors.

Also you should be able to execute the script this way:
> sudo ./usr/share/ultimate/gamers.sh
The leading "sh" should not be required.  A well written script will specify what shell is to be used.

---

### Post by Ubun00btu on 2007-09-10
Thank you for the response, but still no joy...

Iv'e tried entering the command in terminal.  It asks for my password, I type it in, <enter> and then.....

Nothing happens.

---

