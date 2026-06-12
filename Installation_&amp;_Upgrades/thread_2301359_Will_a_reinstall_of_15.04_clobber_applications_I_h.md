---
title: "Will a reinstall of 15.04 clobber applications I have added ?"
date: 2015-11-01
forum: Installation &amp; Upgrades
---

### Post by oygle on 2015-11-01
Since adding some new packages and loosing the task bar, have had a blank screen after login. Have tried all sorts of things to fix it, see [http://ubuntuforums.org/showthread.php?t=2301253](http://ubuntuforums.org/showthread.php?t=2301253)

So, am looking at a reinstall (basically no data to speak of on this Dell laptop) of Kubuntu 15.04  Am able to boot from USB and see the options.

1. Will the reinstall overwrite or remove the current applications I have added ? Like cheese, audacity, etc,etc ?

2. Even though I have all the .debs on the laptop, will the install/reinstall go and download the .debs again. Am on limited bandwidth, so trying to have minimal downloads if possible.

---

### Post by Bucky Ball on 2015-11-01
1. Yes. A reinstall on the same partition as you are currently installed will wipe anything that is on that partition before install.
2. If the apps you have added are not default apps in the vanilla Ubuntu install (and as you've added them I'm guessing they're not), no, they won't download again. 

Before you do any of this, do this and reboot:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Post any and all errors that occur from any of those commands.

If you get a blank screen and can't get a terminal, either boot into the recovery kernel or, at the blank screen, hit control+alt+F1, login, issue the update/upgrade commands. Good luck.

---

### Post by oygle on 2015-11-01
Thanks fro your reply. i did those 4 commands .

> **Bucky Ball said:**
> Post any and all errors that occur from any of those commands.

There were messages. Are they in syslog or similiar ? How would I get that onto a USB please ?

---

### Post by Bucky Ball on 2015-11-01
You could perhaps copy the output to a text file and dump that to a USB. Once you've done that, what happens after a reboot?

---

### Post by oygle on 2015-11-02
Couldn't get the output, as I didn't know what file it was stored in. Rebooted, ..blank screen.

---

### Post by Bucky Ball on 2015-11-02
Run each command in a terminal. If there is an error, copy the output of the code from the terminal to a text editor. Save the text file to USB.

---

### Post by oygle on 2015-11-02
I can't run Konsole, it gives some error message. I can only get to bash/shell by pressing shift on boot. Then go into recovery mode. I didn't realise there was a sticky about these issues ( [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) ). Possibly I should post there.

---

### Post by Bucky Ball on 2015-11-02
If you're looking to fix your graphics, post there or start a new thread as that subject has nothing to do with the topic and title of this thread, which is about whether a reinstall will delete your currently installed apps, and yes, it will. 

If you have finished here, please mark the thread as solved and post a new thread or on the link re. your graphics issue. Good luck.

---

### Post by oygle on 2015-11-02
At this stage I do not know what the source of the problem is.

---

### Post by oygle on 2015-11-02
Did the install/reinstall. Same issue - black screen. yes, the install clobbered the applications, but I have the .debs backed up.

---

