---
title: "Upgrade Ubuntu from 14 to 15 help"
date: 2015-05-19
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2015-05-19
I want to upgrade from Ubuntu 14 to 15. I saw in the beginning and declined it. Now can't find it.

I have tried
kim@brain:~$ apt-get dist-upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
kim@brain:~$ 

update manager

sudo do-release-upgrade -d

Where else could the option to upgrade be?

---

### Post by sammiev on 2015-05-19
Hi,

There is a few ways of doing it but this is what I usually use.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

The above command will download and install the available latest packages.

Reboot your system to finish installing updates.

Now, enter the following command to upgrade to new available version.

```
sudo update-manager -d
```

---

### Post by grahammechanical on 2015-05-19
I think a little explanation is needed. May I?

When we use apt-get dist-upgrade we upgrade the version we already have. We get packages that have been held back for some reason or another. The dist-upgrade process differs from the usual apt-get update/upgrade in that it is supposed to use what is called "smart" conflict resolution. It will remove packages that are causing conflicts. It does not always but it has the potential to break something. I have had it happen to me once. I rarely use dist-upgrade for that reason.

The -d switch in do-release-upgrade -d stands for "development." If you were on 15.04 and you ran that command you would now be on Wily Werewolf (15.10 development version).

Try going to System Settings>Software & Updates>Updates tab and make sure that Notify me of a new Ubuntu version is set for Any New Version. And then do a recheck and Update Manager should offer you an button to click.

Do not take my word for it.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)
> 

**Upgrading to development releases**

 Please  be aware that development releases are unstable, and not suited for  people who do not want to fix/report/triage bugs. If you want a stable  Ubuntu version, stick to the official released versions.  For added  stability, choose a Ubuntu LTS release. 

 
**Desktop / GUI Upgrade**



```
sudo update-manager -d
```

> **Server / Command line Upgrade**

 
```
sudo apt-get install update-manager-core
sudo do-release-upgrade -d
```
Regards.

---

### Post by sammiev on 2015-05-19
> **grahammechanical said:**
> I think a little explanation is needed. May I?

When we use apt-get dist-upgrade we upgrade the version we already have. We get packages that have been held back for some reason or another. The dist-upgrade process differs from the usual apt-get update/upgrade in that it is supposed to use what is called "smart" conflict resolution. It will remove packages that are causing conflicts. It does not always but it has the potential to break something. I have had it happen to me once. I rarely use dist-upgrade for that reason.

The -d switch in do-release-upgrade -d stands for "development." If you were on 15.04 and you ran that command you would now be on Wily Werewolf (15.10 development version).

Try going to System Settings>Software & Updates>Updates tab and make sure that Notify me of a new Ubuntu version is set for Any New Version. And then do a recheck and Update Manager should offer you an button to click.

Regards.

Thanks for the added info. :)

---

### Post by Camilia on 2015-05-19
> **sammiev said:**
> Hi,

There is a few ways of doing it but this is what I usually use.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

The above command will download and install the available latest packages.

Reboot your system to finish installing updates.

Now, enter the following command to upgrade to new available version.

```
sudo update-manager -d
```
That didn't work. Got message that pc up to date.

---

### Post by Camilia on 2015-05-19
> **grahammechanical said:**
> 
Try going to System Settings>Software & Updates>Updates tab and make sure that Notify me of a new Ubuntu version is set for Any New Version. And then do a recheck and Update Manager should offer you an button to click.

```
sudo update-manager -d
```
 
```
sudo apt-get install update-manager-core
sudo do-release-upgrade -d
```
Regards.
Already had new versions set

That didn't work. Got message no new versions

---

### Post by oldos2er on 2015-05-19
14 what to 15 what? I ask because 14.04 is an LTS; another LTS release won't be made until next year. Unless you've changed the defaults, an LTS release will only upgrade to a more recent LTS if available. If one is not available, you will see the "no new versions" message. You can change the settings to allow updating to any release though.

14.10 *should* allow updating to 15.04. Leave off the -d switch and just run ```
do-release-upgrade
``` if you're running 14.10.

---

### Post by Camilia on 2015-05-19
> **oldos2er said:**
> 14 what to 15 what? 
14.10 *should* allow updating to 15.04. Leave off the -d switch and just run ```
do-release-upgrade
``` if you're running 14.10.
Have 14.10. After installing 14.10 had the option to upgrade to 15.04. 

That didn't work. Got message no new release found

---

### Post by oldos2er on 2015-05-19
Can you post output from the following commands? ```
cat /etc/lsb-release

do-release-upgrade -c
```

---

### Post by Camilia on 2015-05-19
kim@brain:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu 14.10"

kim@brain:~$ do-release-upgrade -c
Checking for a new Ubuntu release
No new release found

---

### Post by neb8 on 2015-05-28
> **Camilia said:**
> kim@brain:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu 14.10"

kim@brain:~$ do-release-upgrade -c
Checking for a new Ubuntu release
No new release found

You may need to edit a config file if you have a LTS installation.  

```
cat /etc/update-manager/release-upgrades
```

if Prompt=LTS change to Prompt=normal

This worked for me when upgrading a 14.10 LTS installation to 15.04.

Note:  upgrades are usually performed in a sequential order. e.g. If you're at version 14.04 you will be brought to 14.10 before being able to upgrade to 15.04.

---

### Post by Camilia on 2015-05-28
> **neb8 said:**
> You may need to edit a config file if you have a LTS installation.  

```
cat /etc/update-manager/release-upgrades
```

if Prompt=LTS change to Prompt=normal

This is what I got with the code-
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=lts

Ok so you told me what to do but not how. How do I change it to normal? I don't know how to edit a config file or what it is.

---

### Post by oldos2er on 2015-05-28
Run ```
sudo cp /etc/update-manager/release-upgrades /etc/update-manager/release-upgrades.backup

sudo nano /etc/update-manager/release-upgrades
``` Change the line ```
Prompt=lts
``` to ```
Prompt=normal
``` Press Ctrl-x, you'll be prompted to save your changes, hit "y" to do so. You might need to reboot for the change to take effect.

---

### Post by Camilia on 2015-05-28
> **oldos2er said:**
> Run ```
sudo cp /etc/update-manager/release-upgrades /etc/update-manager/release-upgrades.backup

sudo nano /etc/update-manager/release-upgrades
``` Change the line ```
Prompt=lts
``` to ```
Prompt=normal
``` Press Ctrl-x, you'll be prompted to save your changes, hit "y" to do so. You might need to reboot for the change to take effect.
I pasted the codes. Still don't understand how I am suppose to change the code to normal. Tried highlighting to type over. Tried control O. There is got to be another step. **What is it?**
This is the result: 
[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=lts


                               [ Read 17 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by neb8 on 2015-05-28
From the terminal do this command if you haven't already.

```
sudo cp /etc/update-manager/release-upgrades /etc/update-manager/release-upgrades.backup
```

for an editor you can use gedit instead of nano

(if gedit isn't installed, install using this command) ```
sudo apt-get install gedit 

```

To edit the file "release-upgrades"

 ```
gedit /etc/update-manager/release-upgrades
```

from the editor gedit 

change ```
Prompt=Lts 

``` to ```
Prompt=normal
```

then select "Save" from inside the editor gedit and exit (the editor)

Now you should be good to go with the upgrade using the "Software Update" application from "System Tools"

---

### Post by Camilia on 2015-05-28
> **neb8 said:**
> From the terminal do this command if you haven't already.

```
sudo cp /etc/update-manager/release-upgrades /etc/update-manager/release-upgrades.backup
```

for an editor you can use gedit instead of nano

 ```
gedit /etc/update-manager/release-upgrades
```

from the editor gedit 

change ```
Prompt=Lts 

``` to ```
Prompt=normal
```

then select "Save: from inside the editor gedit and exit (the editor)

Now you should be good to go with the upgrade using the "Software Update" application from "System Tools"

**Where is editor gedit?** All I can find is text editor. That won't work. I keep being told what to do but not how.

---

### Post by BlinkinCat on 2015-05-28
> **Camilia said:**
> **Where is editor gedit?**

Search for gedit in Software Centre where it is known as Text Editor...

[https://help.ubuntu.com/community/gedit](https://help.ubuntu.com/community/gedit)

---

### Post by neb8 on 2015-05-28
> **Camilia said:**
> **Where is editor gedit?** All I can find is text editor. That won't work. I keep being told what to do but not how.

if gedit isn't installed use this command 

```
sudo apt-get install gedit
```

The what is how to complete an update for a LTS installation.

---

### Post by Camilia on 2015-05-28
bump

---

### Post by Camilia on 2015-05-28
bump

---

### Post by Camilia on 2015-05-28
sudo apt-get install gedit downloaded a program. Still don't understand how to from working in the terminal to text editer to change Prompt=LTS to Prompt=normal

---

### Post by neb8 on 2015-05-28
> **Camilia said:**
> I still understand how to go from working in the terminal to using editor. I am more confused now.

The ***wha*t** is the ***how*** to perform a short term upgrade for a LTS (long term) installation  LTS installations are designed to be updated using long term upgrades.

However the ***how*** can potentially create problems. I've been using computers for decades and still learning, teaching myself **how**. PC's original goals of development was to create a computer that is capable of being personal , meaning the user would be able to configure and utilize a computer for personal and other reasons. Before the PC there were mostly only computer terminals connected to mainframes. Each mainframe would have a sysop (system operator) who was mostly in control of the computer. Computer terminals were often refereed to as a dumb terminal. Modern computers (PCs) allow more ***user control ***over ***how*** a computer is used.

We're using the terminal as it's usually faster and easier than using a GUI, allowing a user access to additional programming not available from a GUI. 

It's sort of confusing at first for people unfamiliar with terminals. 

Most computers today use a GUI (Graphical User Interface) where a computer user learns from a GUI vs a terminal.

---

### Post by Camilia on 2015-05-28
In the text editor got it changed. So what do I do now????? Unable to save it. It is only a read only file. Just back to step 1. Probably faster to just reinstall ubuntu. This forum is proving useless to beginners.

---

### Post by neb8 on 2015-05-28
> **Camilia said:**
> In the text editor got it changed. So what do I do now?????

Find and execute "Software Updater" from the GUI which should be located under "System Tools".

You can also perform a distribution upgrade using a command line from the terminal. 

I prefer to do a distribution and other updates/upgrades from the GUI using the "Software Updater" application. It will look for and perform any updates required before a distribution upgrade.

e.g. if you're at a 14.04 revision you will be  updated to a 14.10 revision. After the update and reboot, running the "System Updater" again will first prompt you and ask if you want to update to a 15.04 revision.

---

### Post by Camilia on 2015-05-28
> **neb8 said:**
> Find and execute "Software Updater" from the GUI which should be located under "System Tools".

I have already done that. Didn't get me to 15.05 for get message pc up to date.

---

### Post by neb8 on 2015-05-28
> **Camilia said:**
> In the text editor got it changed. So what do I do now????? Unable to save it. It is only a read only file. Just back to step 1. Probably faster to just reinstall ubuntu. This forum is proving useless to beginners.


try the command ```
 sudo -i  gedit /etc/update-manager/release-upgrades

```
or ```
gksudo gedit /etc/update-manager/release-upgrades
```

if gksudo is not installed, install using ```
sudo apt-get install gksu
```

Yes, a new install is sometimes better. I usually first backup any personal and data files I want to keep.

For some new installations you may need to select other options  from the installer, then choose to edit or create a partition while making it installable.

e.g. if you have multiple hard drive partitions, some installers will wipe out the entire drive including any existing partitions when choosing to " erase and install "  an operating system.

---

### Post by neb8 on 2015-05-29
Gedit can be installed by typing
```

sudo apt-get install gedit
```


To display help for a terminal cmd or program just type --help for after the term. cmd or program name.

e.g. to display apt-get help type " apt-get --help "  ... for gedit type " gedit --help ", etc.

for a list of built-in terminal commands type "help". and "{terminal command} --help" to display help for individual terminal commands.

You can also try an editor such as vim. type vim from the command line, if not installed will show a list of options for installation.

Vim is another popular editor that doesn't use a gui. Initially may be more difficult to use but is fast and easy to use once it's commands are learned.

vim --help for start options

```
vim filename (or)

vim /file path/filename  
```

will load a file.

Once a file is loaded, using the <insert> and <ESC> keys puts vim into three modes of insert, replace and command.

After editing a file you first need to press <ESC> and then type in a colon ":" to enter command mode. Then use a command such as "wq"  (write then quit) to save a file and exit.

---

### Post by oldos2er on 2015-05-29
> **Camilia said:**
> I pasted the codes. Still don't understand how I am suppose to change the code to normal. Tried highlighting to type over. Tried control O. There is got to be another step. **What is it?**
This is the result: 
[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=lts


                               [ Read 17 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

When you have the file opened in nano use the arrow keys to move the cursor down to the "Prompt" line (you use the up down left right arrow keys to control where the cursor is in whatever you're editing). You can either use the Delete key to delete the entire line, or move the cursor to the end of the line and Backspace over "lts." Either way you want to end result to look like "Prompt=normal" without the quotes.

> chmod +rw /etc/update-manager/release-upgrades It's not a good idea to teach someone new to change permissions on system files; if they do this to the wrong file they can break their system.

---

### Post by Camilia on 2015-05-29
Still confused. Why can't you just tell me how to make a change in text editor. Why do you have to make it so complicated. I am thinking of putting windows back on desktop. Everytime I have a problem I have reinstall ubuntu.

---

### Post by oldos2er on 2015-05-30
I'm not sure what you need to know that I'm not telling you.

---

