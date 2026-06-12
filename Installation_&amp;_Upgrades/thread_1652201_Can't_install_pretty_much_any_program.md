---
title: "Can't install pretty much any program"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by Inanitas on 2010-12-24
I have just installed Ubuntu 9.10 (though now upgrading to 10.04 LTS), and trying to install some audio plugins and some apps (Wine and aMSN), but, everytime I try to install something, a message appears, saying "E: unable to lock the download directory". What is wrong?
What I think is that it is because of the fact my PC doesn't recognize my C: drive anymore, where all the system files are (moreover, the C: drive was made one with another drive which was just for data storing by my PC when I had Windows for some unknown reasons), though I may be wrong, since I don't know anything about these kind of things.
Thanks in advance to anyone willing to help.

And, by the way, I hope I posted this in the right section.

EDIT: I tryied running the console and typing "sudo pkill apt", just to make sure nothing was running anymore while installing the plugins, but now the error message changed and says there IS something running in background. I don't understand...

---

### Post by matt_symes on 2010-12-24
Hi

What kind of install is this (wubi or partition)?

```
E: unable to lock the download directory
```

Don't confuse the E: here with a windows drive number. E: means error not windows drive E:

EDIT:

> EDIT: I tryied running the console and typing "sudo pkill apt", just to make sure nothing was running anymore while installing the plugins, but now the error message changed and says there IS something running in background. I don't understand

What was the new error message?

Kind regards

---

### Post by Inanitas on 2010-12-24
I am no expert in these things, but I pretty much think it's a partition install...

EDIT: the new error message is: "unable to obtain an exclusive lock".

EDIT 2: yet another error message while trying to install Mozilla Thunderbird: "The software index is broken".

---

### Post by matt_symes on 2010-12-24
Hi

From a terminal type (case sensitive)

```
sudo mv /var/lib/dpkg/lock /var/lib/dpgk/lock.bak
```

and enter your password when prompted. You will not see it echoed to the screen. This is normal. then type

```
sudo apt-get update
```

EDIT: Blimy. Your were in the middle of upgrading??????? I didn't get that from your post.

Kind regards

---

### Post by Inanitas on 2010-12-24
> **matt_symes said:**
> Hi

From a terminal type (case sensitive)

```
sudo mv /var/lib/dpkg/lock /var/lib/dpgk/lock.bak
```and enter your password when prompted. You will not see it echoed to the screen. This is normal. then type

```
sudo apt-get update
```Kind regards


When running the first command, I receive this message: "unable to run stat of /var/lib/dpkg/lock": no files or directories".

---

### Post by ImDougy on 2010-12-24
this means a program is already using synapyic or apt i'm not really sure but it's probably update manager or something. a restart should end all those but if not .......*confused*

---

### Post by ImDougy on 2010-12-24
it must be the upgrade to 10.04 u have to wait till that finishes then u can download software

---

### Post by dino99 on 2010-12-24
step by step:

close everything but terminal

sudo rm /var/cache/apt/archives/*
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by matt_symes on 2010-12-24
Hi

Are you trying to install things while in the middle of upgrading? If you are, i did not get that from your first post.

Kind regards

---

