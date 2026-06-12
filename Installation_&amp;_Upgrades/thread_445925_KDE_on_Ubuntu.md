---
title: "KDE on Ubuntu"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by gspaulding on 2007-05-16
My installed Feisty 7.04 Ubuntu works fine, but I wanted to compare gnome to the kde desktop I have used before on other distributions.  I used the code "sudo aptitude install kubuntu-desktop" and it asked for my 7.04 cd, then took several minutes to go through a lot of scrolling messages and finished at 100% and displayed a text file and ended seemingly successfully.  While the installation started, a message box opened in response to the cd "A volume with software packages has been detected.  Would you like to open it with package manager?"  I had seen no instructions relating to this message in the posts about installing kde, so I just closed that window.

Upon shutting down and restarting, there is no option to use the kde desktop.  It simply boots into Ubuntu (gnome).  If I logout, there is still no option to start kde in the new session.  What happened to kde?  Did I need to do something with package manager?  Any suggestions for getting to the kde desktop?

---

### Post by mitch.c on 2007-05-16
You need to select a KDE session at the GDM login screen. Click the Options button at the lower left corner and then Select Sessions. Choose KDE. Login as normal. You will be asked if you want to use KDE for this session, or set as the default.

-- 
Mitch

---

### Post by gspaulding on 2007-05-16
Thanks for the reply.  When I open 'options', 'select session', I get a sessions screen that offers:
Last session
1. Run Xclient script
2. Gnome
Failsafe Gnome
Failsafe Terminal

No kde option is available and if I choose Xclient script, I just boot into Gnome desktop.  Did the install kubuntu-desktop not complete properly (nothing indicated an error during the process)?  What should I try next?  Thanks for the help.

Edit: Just for clarification, to install the kde desktop all I did was to enter the code 'sudo aptitude install kubuntu-desktop' and let it run, then restart.  Is this correct?  Was the prompting for my install cd (live cd, 7.04 i386 alternate) part of the process.  Should I have just closed the message box concerning package manager as I did?

---

### Post by gspaulding on 2007-05-16
AAARRRGH-
I just realized when prompted to insert my install cd I actually put in the regular i386 cd not the i386 alternate cd I installed from.  Probably explains why things are not as they should be.  Can I reverse what I did and try again inserting the proper alternate cd when prompted?  How would I go about reversing my goof up?

---

### Post by mitch.c on 2007-05-16
Your regular CD should have been fine (I prefer to remove CD from sources.list and download packages). What is the output of:
```
$ aptitude search kubuntu-desktop
```
If the first character is 'i' then aptitude thinks it is installed. You could try:
```
$ sudo aptitude reinstall kubuntu-desktop
```
Check /var/log/aptitude for clues as to what happened.

-- 
Mitch

---

### Post by gspaulding on 2007-05-16
Thanks Mitch,

The code returned:
pi  kubuntu-desktop                 - Kubuntu desktop system 

The aptitude log seemed clean, finishing on:
[INSTALL, DEPENDENCIES] zoo
[INSTALL] kubuntu-desktop
=====================================

Log complete.

Should I try the reinstall code anyway?

---

### Post by mitch.c on 2007-05-16
> **gspaulding said:**
> Thanks Mitch,

The code returned:
pi  kubuntu-desktop                 - Kubuntu desktop system 
Interesting...

pi means the package is not installed (current state 'p')  but is set to be installed (action 'i')

You might try:
```
$ sudo aptitude -f install
```
and see what happens. If not try:
```
$ sudo aptitude reinstall kubuntu-desktop
```
Let me know what happens.

-- 
Mitch

---

### Post by gspaulding on 2007-05-16
Mitch,
Thanks so much for your help.  I am an idiot.  But, I am posting from my kde desktop.

Upon using the code 'aptitude -f install' the install process went through, and again I seemed to get hung on the 'Postfix Consideration' screen which I could not get past.  Finally, I realized I had to press 'tab' to activate the 'ok'.  When I got the next screen and selected 'No Configuration', I had to press 'tab' again to get to 'ok'.  So simple, yet so confounding.  I'm kind of liking the kde desktop.

Again, thanks for your help.  I am so impressed with the support given by the Ubuntu community and loving the idea that I could abandon MS after I retire and don't have to support the windows only sqlserver accounting package that I support for a living.
Gary

---

### Post by mitch.c on 2007-05-16
Glad to help.

Cheers
-- 
Mitch

---

