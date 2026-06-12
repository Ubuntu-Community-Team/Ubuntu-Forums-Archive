---
title: "Problems upgrade with latest version Ubuntu 22.04.03"
date: 2024-02-14
forum: Installation &amp; Upgrades
---

### Post by mamp on 2024-02-14
I usually update at the end of the day with these commands


sudo apt clean
sudo apt --fix-broken install
sudo apt autoremove
sudo dpkg –configure -a
sudo apt-get install -f
sudo snap refresh
sudo apt update && sudo apt upgrade -y






sudo apt-get dist-upgrade
sudo apt-get update && sudo apt-get dist-upgrade
sudo update-manager –devel-release
sudo update-manager -d
sudo do-release-upgrade -d


I've already made 4 attempts on the HD and the update is failing, the main reason being the network goes down and the network-manager service stops. I have numerous installation failures.

---

### Post by Rubi1200 on 2024-02-14
You update with all these commands at the end of every day? 

Why?

Just to clarify, is this a Desktop or Server install?

---

### Post by MAFoElffen on 2024-02-14
My curiosity is peaked why you think you have to do all that? Is there a problem that is prompting it?

And why to an interim release, if there are problems that are not resolved? Isn't that just flirting with bigger problems?

Just reading between the lines of that...

---

### Post by mamp on 2024-02-14
I want to keep updated.
My desktop version

---

### Post by mamp on 2024-02-14
I created a script because it makes the commands easier.
becomes automated.


No, I just use one line and everything runs. very simple.


As for the problem, when updating, an error occurs during the update.
I've been running this script with these commands since Ubuntu 18 and it's never given me an error.


But now, yes, the first effect was to paralyze the network service, I saw that the network-manager service stopped.


Then, after removing and reinstalling, doing library by library, I discovered that the X64 update only did not install a library because the corresponding X86 in the update was not done. I did it by hand, but the problem persisted.


Then I redid a new HD again from scratch and the errors increased.

---

### Post by Rubi1200 on 2024-02-14
I must admit in all my years of using Linux I have never seen someone run so many commands to keep updated.

It would help if you post the actual error messages for us to see and analyze.

---

### Post by deadflowr on 2024-02-14
Your commands are weird and mostly unnecessary.
You run commands to fix broken package twice (or 3 times if you include the dpkg --configure -a command) 
and run commands to allow upgrades to the development release version 3 times.

Only command you need is this
```
sudo apt-get update && sudo apt-get dist-upgrade
or
sudo apt update && sudo apt full-upgrade
```
Note that the apt update/apt full-upgrade command automatically clears out the package archive, so running those commands will render apt-get clean moot.

You can periodically run
```
sudo apt autoremove --purge
```
but that's optional.

These commands
```
sudo update-manager –devel-release
sudo update-manager -d
sudo do-release-upgrade -d
```
all attempt to allow or run release upgrade.
A release upgrade will move you to a new release, from 22.04 up to whatever the next available release is.
(I see right now, if you run with the -d option it'll try to upgrade to 24.04 which is barely beta right now.
So I doubt you would want to do that)

Edit: attaching image of what it shows when running update-manage -d or update-manager --devel-release (those are the same command anyway)
[ATTACH=CONFIG]293410[/ATTACH]

---

### Post by mamp on 2024-02-14
Which do you prefer?
journalctl?
Kernel?
boot log?
Ulitmo generated so much blocking that it generated direct Canonical and I couldn't generate anything.


But which report do you want?

---

### Post by mamp on 2024-02-14
Yes..
first block I try to clean the packages
then an update... I realized over time that before doing an update it was always good to update.


I will read your comments and respond below.

---

### Post by mamp on 2024-02-14
"Note that the apt update/apt full-upgrade command automatically clears out the package archive, so running those commands will yield apt-get clean moot."


I didn't know how to clean the package.
It may be generating conflicts


"sudo do-release-upgrade -d'
I wanted to get more updated LTS packages, but as I didn't leave the beta option activated, it doesn't work. Only if it came out, this way if at the end of the day something new LTS came out I wouldn't need to go to the Ubuntu or Canonical website to find out what it would do.
Do you think it's not worth it?

---

### Post by SeijiSensei on 2024-02-14
No. I probably update my installations about once a week at most.

---

