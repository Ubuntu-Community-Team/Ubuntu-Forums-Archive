---
title: "Synaptics issues?"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by raedbenz on 2008-05-25
HI ,
when i use synaptics to install applications i cant find the icon for running the program. example I installed Acrobat reader and aMSN.
how can i let it add icons to Applications or desktop,??
thanks

---

### Post by luisromangz on 2008-05-25
The problem might be in those packages, but not synaptic, as synaptict just installs what the packages contains. If they don't install a menu icon or place correctly it's a problem of the package, not synaptic's.

---

### Post by raedbenz on 2008-05-25
> **luisromangz said:**
> The problem might be in those packages, but not synaptic, as synaptict just installs what the packages contains. If they don't install a menu icon or place correctly it's a problem of the package, not synaptic's.
thanks
but i tried to install aMSN using the Add/remove and an icon has been generated in Applications-->Internet,, Why???

---

### Post by PmDematagoda on 2008-05-25
> **raedbenz said:**
> thanks
but i tried to install aMSN using the Add/remove and an icon has been generated in Applications-->Internet,, Why???

If you are used to the Windows way of putting all the icons on the Desktop, then GNOME doesn't do that, not even KDE. Personally I find that an uncluttered desktop is more functional than a cluttered one. But if you want the icon to be there on the desktop, then all you have to do is drag the menu entry for that particular application from the menu to the desktop.

---

### Post by raedbenz on 2008-05-25
HI PmDematagoda , well but the issue is not to be on the desktop only..
but the icons are not either on dekstop or Applications some times...

---

### Post by lswest on 2008-05-25
I think he means that when he uses Add/Remove to install applications they do indeed create launchers in the applications menu, but when he uses Synaptic to do the same, it does not.

@ the OP: does it create the launchers if you use the terminal? ```
sudo apt-get install *packagename*
```

---

### Post by raedbenz on 2008-05-25
> **lswest said:**
> I think he means that when he uses Add/Remove to install applications they do indeed create launchers in the applications menu, but when he uses Synaptic to do the same, it does not.

@ the OP: does it create the launchers if you use the terminal? ```
sudo apt-get install *packagename*
```

HI lswest,
yes u r right...
u mean to try install from terminal rather than Add/remove or synaptic by the given code above????
if yes,i tried and i did not get any icons...
thanks

---

### Post by lswest on 2008-05-25
I'd just like to test to see if the problem lies only with synaptic, so yes, if you could try to install it from the terminal using that command where you substitute *packagename* with "amsn" (for example) and then post back if it did create the menu launchers or not.

Ah, saw your update.  Very strange problem, because i can't understand why Add/Remove would make the launchers yet the terminal and synaptic do not.  For me (I test it just now) all 3 programs install aMSN and create the launchers, so it may have something to do with your settings in synaptic.  Maybe have a look at the preferences (or take a screenshot and post it here) and i'll compare it with my own.  That's about the best i can do.

---

### Post by raedbenz on 2008-05-25
> **lswest said:**
> I'd just like to test to see if the problem lies only with synaptic, so yes, if you could try to install it from the terminal using that command where you substitute *packagename* with "amsn" (for example) and then post back if it did create the menu launchers or not.

Ah, saw your update.  Very strange problem, because i can't understand why Add/Remove would make the launchers yet the terminal and synaptic do not.  For me (I test it just now) all 3 programs install aMSN and create the launchers, so it may have something to do with your settings in synaptic.  Maybe have a look at the preferences (or take a screenshot and post it here) and i'll compare it with my own.  That's about the best i can do.

hi 
i tried and no icons appeared.
well, if i go to synaptics and i find the installed applications and look to its "properties" then i can find the installed path.
but what is the extenson of the executable file, in orderto copy it manually?? i mean in Windows we have ".exe" in Linux what??
thanks

---

### Post by lswest on 2008-05-25
you don't need to copy it anywhere, right-click on the menu and choose "edit menus" go to the correct menu you want the icon in, hit "create new launcher" give it a name and type in the command for it (e.g. amsn for aMSN).  I'm just trying to solve the problem so that you don't have to do it.  And i meant the properties of your synaptic program (found under Settings-->Preferences), not the package.

---

### Post by PmDematagoda on 2008-05-25
lswest, there is no difference if you use either Add/Remove or Synaptic since they install the package in the same way.

About the application in question, what application in particular did you install?

---

### Post by raedbenz on 2008-05-25
well i meant by "Properties" is a way to find the path  of the file...

---

### Post by raedbenz on 2008-05-25
> **PmDematagoda said:**
> lswest, there is no difference if you use either Add/Remove or Synaptic since they install the package in the same way.

About the application in question, what application in particular did you install?

i installed Acrobat reader and aMSn
and i had the same issue for both

---

### Post by PmDematagoda on 2008-05-25
Ahh, Acrobat Reader, now that is something I don't think automatically creates an entry, in any case it's easy to create entries for both, the command for Acrobat is:-
```
acroread
```
and the one for aMSN should be:-
```
amsn
```

Just go to Main Menu in System>Preferences>Main Menu and make the entries in the relevant sections.

---

### Post by lswest on 2008-05-25
> **PmDematagoda said:**
> lswest, there is no difference if you use either Add/Remove or Synaptic since they install the package in the same way.

About the application in question, what application in particular did you install?

I realize that, but if installing something in Add/Remove and then the same package in Synaptic, and where the Add/Remove creates launchers for it while synaptic does not, it just doesn't make sense.  I thought maybe there was an option in synaptic (i never use it - terminal installs for me) to specify whether launchers or such were created.

(The OP said that it was created when he used Add/Remove) and Adobe Acrobat Reader 8 made a launcher automatically for me after I installed it with apt-get.

---

### Post by PmDematagoda on 2008-05-25
> **lswest said:**
> I realize that, but if installing something in Add/Remove and then the same package in Synaptic, and where the Add/Remove creates launchers for it while synaptic does not, it just doesn't make sense.  I thought maybe there was an option in synaptic (i never use it - terminal installs for me) to specify whether launchers or such were created.

Synaptic does create launchers lswest, but if the package does not have any data pertaining to a launcher, or if the launcher is hidden(yes, they can be), then you may either not see the launcher or have to create it for yourself.

---

### Post by raedbenz on 2008-05-25
> **PmDematagoda said:**
> Ahh, Acrobat Reader, now that is something I don't think automatically creates an entry, in any case it's easy to create entries for both, the command for Acrobat is:-
```
acroread
```
and the one for aMSN should be:-
```
amsn
```

Just go to Main Menu in System>Preferences>Main Menu and make the entries in the relevant sections.
ok i ll try..
but for Acrobat where i can find the launcher of the applications, i mean in which path opt/ , usr/bin etc...???? what is its extension??

---

### Post by lswest on 2008-05-25
> **raedbenz said:**
> ok i ll try..
but for Acrobat where i can find the launcher of the applications, i mean in which path opt/ , usr/bin etc...???? what is its extension??

you do not need to know where the launcher is, typing the command "acroread" in the Command: section of the create a new launcher window is sufficient.  (you can test this by typing "acroread" into a terminal or the run command prompt).

And @ Dematagoda, i understand what you're saying, and i know that I've hidden all the KDE apps from my menu in GNOME when i had it installed.  I'm just curious as to why one program creates the said launchers and the others don't.  Maybe I misunderstood the OP?

---

### Post by raedbenz on 2008-05-25
> **lswest said:**
> you do not need to know where the launcher is, typing the command "acroread" in the Command: section of the create a new launcher window is sufficient.  (you can test this by typing "acroread" into a terminal or the run command prompt).

And @ Dematagoda, i understand what you're saying, and i know that I've hidden all the KDE apps from my menu in GNOME when i had it installed.  I'm just curious as to why one program creates the said launchers and the others don't.  Maybe I misunderstood the OP?

well i typed acroread in the terminal but i get the message "permission denied",,???

---

### Post by raedbenz on 2008-05-25
> **PmDematagoda said:**
> 

Just go to Main Menu in System>Preferences>Main Menu and make the entries in the relevant sections.
well i did these steps. 
and the thing is that Acro read doesnt have any icon (no colors), hence i created a ".svg" from ".png " to add it as an icon. but whenever i browse it it doesn t appear in the path , the ".svg" image i created...

help??
tanks

---

### Post by PmDematagoda on 2008-05-25
From what I have, Acrobat Reader does have an icon, and just entering acroread should be enough.

About the permission problem, can you post the full output f the error.

---

### Post by PmDematagoda on 2008-05-25
> **lswest said:**
> And @ Dematagoda, i understand what you're saying, and i know that I've hidden all the KDE apps from my menu in GNOME when i had it installed.  I'm just curious as to why one program creates the said launchers and the others don't.  Maybe I misunderstood the OP?

It all depends on the deb file in question, if it has the necessary data included then it will create a launcher as well, if not then it doesn't.

---

### Post by raedbenz on 2008-05-25
> **PmDematagoda said:**
> From what I have, Acrobat Reader does have an icon, and just entering acroread should be enough.

About the permission problem, can you post the full output f the error.

the permission error is only that i mentioned above

---

### Post by raedbenz on 2008-05-25
> **lswest said:**
> I think he means that when he uses Add/Remove to install applications they do indeed create launchers in the applications menu, but when he uses Synaptic to do the same, it does not.

@ the OP: does it create the launchers if you use the terminal? ```
sudo apt-get install *packagename*
```

Hi,,,
i uninstalled the adboe...
and the package name is "adobe.deb". 
i am trying the terminal to install it.using the above command in this way:

sudo apt-get install adobe

and i get this error msg: Couldn't find package adobe

the paths is correct i am sure..
Y?? help....

---

### Post by PmDematagoda on 2008-05-25
Are you using the deb file given by the Adobe website or using Medibuntu?

---

### Post by raedbenz on 2008-05-25
> **PmDematagoda said:**
> Are you using the deb file given by the Adobe website or using Medibuntu?

well the file originaly was ".rpm" and using alien i converted it to ".deb"
i downloaded the installation package from Adobe website. do u know other packages just to try..??
tahnks

---

### Post by PmDematagoda on 2008-05-25
Get the deb file from here:-
[http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i386.deb](http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i386.deb)

Converting the rpm to deb using Alien is not really recommended and may have caused the problem.

But first remove the old install of Acrobat with:-
```
sudo apt-get remove --purge acroread
```

---

### Post by raedbenz on 2008-05-25
> **PmDematagoda said:**
> Get the deb file from here:-
[http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i386.deb](http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i386.deb)

Converting the rpm to deb using Alien is not really recommended and may have caused the problem.

But first remove the old install of Acrobat with:-
```
sudo apt-get remove --purge acroread
```

thanks i ll do...
i also found ".tar" format for adobe7.
one more thing, the add/remove gets the applications from repositories? isnt it?
the adobe i cant find it in the add/remove i only find the aMSN.
how can i find it in add/remove the adobe???

---

### Post by PmDematagoda on 2008-05-25
You can't, in any case it is better if you just get used to using Synaptic or even the terminal via apt-get since they are more easy to use(in the end) and are more flexible.

---

### Post by raedbenz on 2008-05-25
> **PmDematagoda said:**
> Get the deb file from here:-
[http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i386.deb](http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i386.deb)

Converting the rpm to deb using Alien is not really recommended and may have caused the problem.

But first remove the old install of Acrobat with:-
```
sudo apt-get remove --purge acroread
```

here is what i get in terminal:

raed@raed-laptop:~/Documents$ sudo apt-get install AdobeReader_enu-8.1.2-1.i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package AdobeReader_enu-8.1.2-1.i386.deb


help...

---

### Post by PmDematagoda on 2008-05-25
You don't install it that way, you must use dpkg with:-
```
sudo dpkg -i AdobeReader_enu-8.1.2-1.i386.deb
```

---

