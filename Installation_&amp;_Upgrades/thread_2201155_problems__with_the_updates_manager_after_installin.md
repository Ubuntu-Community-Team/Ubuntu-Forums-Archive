---
title: "problems  with the updates manager after installing Adobe Reader"
date: 2014-01-22
forum: Installation &amp; Upgrades
---

### Post by mrayo on 2014-01-22
Hi everyone,
I am very concerned because I can not get the updates since I installed Adobe Reader, my laptop shows me this message

--------------------------------------------------------------------------------------------
The package system is broken 

Check if you are using third party repositories. If so disable them, since they are a common source of problems. 
Furthermore run the following command in a Terminal: apt-get install -f



It said: An error occurred, please run Package Manager from the right click of the menu or apt-get in a terminal to see what is wrong. The error message was: 'Error brokenCount >0' This usually means that your installed packages have unmet dependencies.
_________________________________________________________________________

So when I go to the terminal and write apt-get the info that I get is :
 E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied) 
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? 

What can I do?

Thanks for any help

---

### Post by Dreamer Fithp Apprentice on 2014-01-23
That was a misleading error message. For any kind of 'buntu it should have said type in ```
sudo apt-get install -f
```, then press the [enter] key. It will ask for your password. Type that in and press the [enter] key again. 

Anytime the system responds to a command by asking if you are root it means you need to prefix the command with sudo.

Anytime it refuses or fails to respond properly, even without some give-away like talking about root, it is worth trying. Generally anything that starts "apt-get" should probably start "sudo apt-get" on all 'buntus.

---

### Post by mrayo on 2014-01-29
Hi there,
I did the sudo apt-get command and after I run the update manager it pops a window saying that the program is broken. I really do not know what to  do!!!
Any suggestions, please!!!

---

### Post by Bucky Ball on 2014-01-30
Post that error message back here or we can't do much.

Bit off topic, but just wondering if there's a specific reason you are using Adobe Reader? There's a perfectly good PDF reader already installed by default; Evince document viewer.

---

### Post by mrayo on 2014-02-02
Hi, 
here is the message.
I like to use adobe reader because I can do snapshots from papers or books if I have to give a class, I have checked Evince but up to now I can not do the same.

Thanks

[IMG]/home/mrayo/Pictures/Screenshot from 2014-01-22 22:28:43.png[/IMG]

[ATTACH=CONFIG]250040[/ATTACH]

---

### Post by Bucky Ball on 2014-02-02
The crash report (bottom window) has 'Show Details' in the bottom left corner. Open that, wait for it to think, then post whatever the report says here.

---

### Post by mrayo on 2014-02-02
Ok,
here it is
[ATTACH=CONFIG]250043[/ATTACH]

---

### Post by mrayo on 2014-02-02
Hi,
do you think that if I uninstalled acrobat reader should be enough to solve the problem?
Thanks

---

### Post by Bucky Ball on 2014-02-02
It might. If you installed using a PPA simply untick the PPA in software sources, uninstall acro, then run an update.

---

### Post by mrayo on 2014-06-17
Hi,
I am here again, I still have the same problem I can not upgrade ubuntu because the errors that I have posted previously.
I tried to uninstall adobe reader but I can not do it. Here are the messages that I get from the terminal. I am very concerned because I starting to have errors in ubuntu performance which I suspect is because the missing upgrades.

--------------------------------------------------------------------------------------------
Terminal:
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 acroread : Depends: acroread-bin
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mrayo@mrayo-Lenovo-IdeaPad-S400-Touch:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 acroread : Depends: acroread-bin
E: Unmet dependencies. Try using -f.
mrayo@mrayo-Lenovo-IdeaPad-S400-Touch:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mrayo@mrayo-Lenovo-IdeaPad-S400-Touch:~$ locate adoreader
mrayo@mrayo-Lenovo-IdeaPad-S400-Touch:~$ locate adobereader
/home/mrayo/.cache/software-center/piston-helper/rec.ubuntu.com,api,1.0,recommend_app,adobereader-enu,,e9925bf1b7f267f4512f9636f297a26d
/home/mrayo/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,reviews,filter,en,any,any,any,adobereader-enu,page,1,helpful,,0abda0a111fde8942cbc52970446758f
/var/lib/dpkg/info/adobereader-enu.copyright
/var/lib/dpkg/info/adobereader-enu.list
/var/lib/dpkg/info/adobereader-enu.postinst
/var/lib/dpkg/info/adobereader-enu.prerm
mrayo@mrayo-Lenovo-IdeaPad-S400-Touch:~$ adobereader
adobereader: command not found
mrayo@mrayo-Lenovo-IdeaPad-S400-Touch:~$ sudo apt-get purge adobereader-enu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 acroread : Depends: acroread-bin
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mrayo@mrayo-Lenovo-IdeaPad-S400-Touch:~$ locate adoreader

--------------------------------------------------------------------------------------------------------

If anybody can help me I will appreciate it!!

Thanks

---

