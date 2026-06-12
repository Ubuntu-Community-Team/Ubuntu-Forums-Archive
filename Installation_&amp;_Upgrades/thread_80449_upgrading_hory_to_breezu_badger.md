---
title: "upgrading hory to breezu badger"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by much better on 2005-10-22
Hi 
i have a problem installing Breezy Badger :
[http://www.ubuntuforums.org/showthread.php?t=79476](http://www.ubuntuforums.org/showthread.php?t=79476)

So i want to try to upgrade Horay to breezy badger .. Can you explain how to do that ?

---

### Post by some_random_newbie on 2005-10-22
I am wondering this exact same thing.  I would like to upgrade from v5.04 to whatever the latest stable build is.

---

### Post by GoldBuggie on 2005-10-22
To update thye system goto synaptic and in the repositories change every word saying hoary to breezy. Then to a reload and update. Now wait and have a cup of coffee while your system is beeing updated.

---

### Post by much better on 2005-10-22
Sorry but can you explain more where can i find repositories ? :confused:

---

### Post by Xian on 2005-10-22
From the Synaptic main menu:
Settings > Repositories

---

### Post by much better on 2005-10-23
ok .. i am lost here . How can i change the word horay with breezy ??? a little help !!!

---

### Post by Tiede on 2005-10-23
Ok, here is a different way that might be more comprehensible for you. I gathered you neve change your repositories before from your question, but if one of you guys reading this did, you might wanna divert back to the original sources.list before attempting the upgrade (for compatibility issues)...
On an empty portion of the desktop, right-click and select Terminal
Type in the terminal:
```
sudo apt-get install ubuntu-dektop
``` if you use Gnome
**OR** ```
sudo apt-get install kubuntu-desktop
``` if you use KDE.
This will select the meta-package of your distribution, just to make sure that all needed packages will be there for upgrade.
Install any packages the APT asks you to (usually 0 -3) and then continue as follows.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
>This will make a copy of your original sources.list in case you want it again later.

```
sudo gedit /etc/apt/sources.list
```
>This will open your list of repositories in the text editor gedit.
>Once in gedit, on the toolbar, go to Search and select Replace.
>>(Tip) Typing Ctrl+R has the same result.
>In the pop-up window that appears, where it says "Search for:" put **hoary**
> and put **breezy** where it says "Replace with:"
>Now click on the button at the bottom that says "Replace All"
>Close the finder, save the file, and exit.

>Now back at the shell, type:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
>It will calculate how many packages are needed, and then ask you to continue. >Select yes, and go watch TV for about 4-5 hours depending on your DSL >connection's speed. :)

>4-5 hours later, go back on the PC and answer the questions asked by apt. Don't worry, usually answering yes to every question is the right thing to do.

After it finishes poking at you with its questions, logout and restart the PC.
Next, come and tell us if you like the new look!

***WARNING: IF YOU USE WARTY, **DO NOT** USE THIS GUIDE TO MOVE DIRECTLY FROM WARTY TO BREEZY. This situation has _not_ been tested (to the extent of my knowledge) and most likely will break the system over a XFree86 > Xorg conflict. Please upgrade to hoary first then to breezy badger.

---

### Post by some_random_newbie on 2005-10-23
Thank you for the responses all.  I'll do this soon and see where it goes. :-)

I do appreciate the assistance.

---

### Post by much better on 2005-10-23
[QUOTE=some_random_newbie]Thank you for the responses all.  I'll do this soon and see where it goes. :-)

I do appreciate the assistance.[/QUOTE]

Thanks man .. i guess i will still using horay because i am dial up .. anyway thanks alot

---

