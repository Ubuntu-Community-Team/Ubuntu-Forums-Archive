---
title: "Stock in Terminal after installing Python 3.12.0"
date: 2023-11-14
forum: Installation &amp; Upgrades
---

### Post by chime-kings on 2023-11-14
Greetings,
An hour ago, I decided to upgrade my Python from 3.10 to 3.12.0. My PC runs Ubuntu Jammy - 22.04, I downloaded the new version from official Python website and installed it. I immediately discovered that my terminal stopped working (not loading when clicked or searched from activities). I spent a little time making my Python 3.12 the default (using VsCode terminal) and afterwards, decided to reboot my PC to know if my terminal could get back.

Since then, I have been stuck at the terminal.
I have set the run level to graphical.target in /etc/systemd/system/default.target, I have updated my graphic driver (Intel i915). I have also checked the display-manager and it's seems to be ok. 

I want is to get back to GUI but every attempt boots into the terminal.

Every assistance to resolve this disturbing issue is highly appreciated.

#Kingsley

---

### Post by ubfan1 on 2023-11-14
You can install another Python but should not try to make it the system default -- things break as you have noticed. Take a look at /bin/python3 link and put it back to the install version of Python.

---

### Post by chime-kings on 2023-11-14
Thank you. But what exactly should I do to /bin/python3? Should I uninstall python altogether?

---

### Post by chime-kings on 2023-11-14
I have been able to resolve it. It was related to my display manager (gdm3). I moved to lightdm with the guidance of ChatGPT

---

### Post by ubfan1 on 2023-11-14
On my Ubuntu 22.04 system, 3.10 is the default python3:
$ ls -l /bin/python3
lrwxrwxrwx 1 root root 10 Aug 18  2022 /bin/python3 -> python3.10

Installing a later python changes(?) that /bin/python3 link to whatever, and system scripts needing python3.10 will break. 
There are virtual (?) environments that you can set up for python, (no experience with that), but that will totally remove the new python from any system interference. 

You've found (and removed) one such program -- there are (many) others.  You should be able to purge the later python you installed, but never purge the python version originally supplied with the system.

---

### Post by MAFoElffen on 2023-11-14
In console, log in. Then do 
```

ls -l /usr/bin/python3

```
As said about...

As said the output should say
```

lrwxrwxrwx 1 root root 10 Aug 18  2022 /usr/bin/python3 -> python3.10

```
When you install another version of Python3.X, it usually updates this symlnk to point to the newly installed version, which means it needs to be rest back the original version. It is probably going to say : 3.12 instead of 3.10

If it doesn't say that, then do this
```

sudo ln -sf /usr/bin/python3.1 /usr/bin/python3

```
Then do this to test
```

python3 --version

```
If you want to play with other versions of Python3, you should run those in a sandboxed environment, such as venv or the Python Virtual Environment. The safest way to do that is via python3-pip.

Here is a good tutorial for that: [https://linuxopsys.com/topics/create-python-virtual-environment-on-ubuntu](https://linuxopsys.com/topics/create-python-virtual-environment-on-ubuntu)

I sort of do the same, with Eclipse PyDev...

---

### Post by rushabh92 on 2024-01-03
[COLOR=#202124][FONT=Roboto]Here's a step-by-step approach to troubleshoot and potentially resolve the issue:[/FONT][/COLOR]

[COLOR=#202124][FONT=Roboto]1. Reset Default Python Version[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Your first step should be to reset the default Python version to the one originally provided with Ubuntu 22.04. You can do this from the terminal:[/FONT][/COLOR]

[COLOR=#202124][FONT=Roboto]Find the Original Python Version:[/FONT][/COLOR]

[COLOR=#202124][FONT=Roboto]Run ls -l /usr/bin/python* to see all the Python versions installed.[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Ubuntu 22.04 typically comes with Python 3.10, so look for something like python3.10.[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Revert the Default Python Symbolic Link:[/FONT][/COLOR]

[COLOR=#202124][FONT=Roboto]Run sudo update-alternatives --config python3 to configure the default python3.[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Select the Python version that came with your distribution (likely Python 3.10).[/FONT][/COLOR]

[COLOR=#202124][FONT=Roboto]2. Repair Damaged Packages[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Sometimes, upgrading Python manually can lead to broken packages. You can attempt to repair them:[/FONT][/COLOR]

[COLOR=#202124][FONT=Roboto]Run sudo apt update to update your package lists.[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Run sudo apt upgrade to upgrade all your packages to the latest versions.[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Run sudo apt -f install to fix broken dependencies.[/FONT][/COLOR]

---

