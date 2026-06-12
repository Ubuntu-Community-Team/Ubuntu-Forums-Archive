---
title: "fonts not installed"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by Sherman_Willden on 2014-09-10
During today's upgrade the fonts appeared to be downloaded but immediately after a message stated that the user did not accept the license and that the fonts are not installed. I am running the following script named update in my home directory and I call as sudo ./update: 

apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get autoremove
apt-get autoclean

How do accept a license when I am not presented with a yes|no prompt?
How important are these font updates?

I do use LibreOffice for most of my work.

Thank you;

Sherman

---

### Post by SeijiSensei on 2014-09-10
The only fonts I know of where you need a license is the set of Microsoft TrueType fonts like Arial and Times New Roman.  They are installed as part of ubuntu-restricted-extras, or separately in the package ttf-mscorefonts-installer.  If you install these fonts, an End-User License Agreement is presented which must be accepted to continue.

---

### Post by ajgreeny on 2014-09-10
A dialog box should have appeared with info about accepting the license. Use "tab" to highlight OK and hit enter.

---

### Post by SeijiSensei on 2014-09-10
I suspect he never saw the dialog box because he was running a script.  It probably timed out after waiting a while for him to click OK.

---

### Post by craig10x on 2014-09-10
The problem is on the ubuntu software center, often the microsoft acceptance agreement doesn't always come up, so if i were him, i would install synaptic package manager (if he doesn't already have it installed) and locate ms-corefonts in there and mark it for re-installation... Upon re-installing, the license agreement WILL pop up and he can check "accept" and then the ms core fonts will be properly installed...

That's been a bug in ubuntu software center for quite a LONG time now...surprised it hasn't been fixed by now...

---

### Post by ajgreeny on 2014-09-10
Well, that's the software centre for you; I never use it myself but always use synaptic which is a great deal better an application for all package management.

---

### Post by grahammechanical on 2014-09-10
I have been caught out by the failure to notice the dialog to accept the Microsoft end user licence. It appears behind the software centre window! I have never known a normal update/upgrade to update Microsoft true type fonts. It does not happen.

It seems to me that a disadvantage of running a script like that is that the user gets no information about what is being upgraded or removed.

---

### Post by Sherman_Willden on 2014-09-15
Thank you all for the good help.

Sherman

---

