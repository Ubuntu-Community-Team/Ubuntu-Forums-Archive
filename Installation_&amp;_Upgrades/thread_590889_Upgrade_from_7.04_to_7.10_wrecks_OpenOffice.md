---
title: "Upgrade from 7.04 to 7.10 wrecks OpenOffice"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by The Grum on 2007-10-25
Hi. Ive seen a strange problem with openoffice when upgrading from 7.04 to 7.10. This has happened on 2 of my family's PCs so far.

After the upgrade, Draw and Impress perpetually attempt to recover a document (untitled.??? - cant remember the extension, think it was a Draw file). Cancelling the recovery causes it to open a Writer window. Attempting the recovery causes it to bring up the recovery dialog repeatedly.

I tried uninstalling open office (complete removal) and this did not work. I tried deleting ~/.openoffice2 and it also didnt work. The only solution I've found so far is to delete the user (and wipe their home dir) and re-add them.

Has anyone seen a similar problem? Is there a better solution than to delete the user?

Thanks in advance.

---

### Post by kennedyjch on 2007-10-25
I've had a different, but also troubling experience with OpenOffice after the upgrade. 

The Presentation application does not launch properly. The splash screen is displayed and the application hangs. 

Word processing and spreadsheet applications seem unaffected.

Any suggestions how to correct short of clean install would be helpful.

---

### Post by sav2005 on 2007-10-26
Office is hanging when I try to print any document from Writer and I can't use my wireless certificates any more (WPA enterprise/TLS PEM certificate based authentication)! I'm not a newbie and have tried the obvious (rename ~/openoffice2 and reload OOo, editing /etc/networks/interface)

Gutsy (Gusty?) had an upgrade problem and choked on my old emacs21 + modes setup (? :confused: now that was odd) and I had to finish the upgrade with dpkg --configure -a.

---

### Post by theopulus on 2007-10-26
Removin gtk open office package seems to solve the problem, but if use compiz/emerald title bar becomes invisible....

¿Is a fix coming soon?

---

### Post by lars.andersen@ipinion.dk on 2007-10-26
True, removing the GTK solves some of the issues, most important the issue with OpenOffice hanging..., but some features in fx. Presentation does not work, plus I experience errors when closing the presentation.

The funny thing is that this problem with Open Office only accured with one of the profiles on my computer - The other profiles did not have the problem !

Anybody have a solution or information regarding a bugfix ???

---

### Post by sav2005 on 2007-10-27
Check which desktop theme you are using. CRUX breaks OOffice, Human and ClearLook do not. This why different profiles/users are having varying success/frustration. Revert to a standard desktop theme until the issue is resolved.

I've dug a little deeper and find this problem has been reported as a critical bug. I would go further. If you can't use the major Office suite, why would most businesses bother? And no, nice as it is, Abiword is not a solution for enterprise level information processing.

---

### Post by The Grum on 2007-10-29
A bit more info on the issue.

It looks like a file is corrupting OO. Did a clean install on one of the affected machines and everything worked until we put back all the documents. A couple opened fine, then about 30 mins later, the problem reappeared.

Could tracker be responsible? If its opening the file to read the contents for searching, could it be leaving something open that makes openoffice think it needs to do a recovery?

---

### Post by sav2005 on 2007-10-29
The issue with Desktop themes has been posted in OpenOffice bugs by several people. Crux is mentioned more than once. The problem (print dialog, styles, navigator not opening and OOo freezing/crashing) is independent of the file and can be reproduced with an empty file. I use the human theme now and the problem has disappeared. 

I'm not happy with Gutsy - 
[LIST]
[*]I can't play encrypted DVDs anymore despite having installed all the restricted format bits and pieces.
[*]OpenOffice should not be effected by themes.
[*]My WEP enterprise wireless connection is unusable (this has worked flawlessly since Dapper)
[/LIST]
Feisty worked fine!

---

### Post by jmcqueen on 2007-11-04
I"m having a similar problem. OpenOffice spreadsheet is no longer available after the upgrade to 7.10. When I try to install I get the following error.

E: /var/cache/apt/archives/openoffice.org-calc_1%3a2.3.0-1ubuntu5_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libsc680li.so')

---

### Post by pasokon on 2007-11-06
Open Office Impress under Gutsy perpetually crashes. It successfully recovers the crashed presentation and then soon crashes again especially if you are changing the type of the current slide. 

What's going on with it?

---

### Post by sav2005 on 2007-11-06
I know this sounds dumb - but which Desktop theme are you using? Ooo crashes under some of the standard Gnome themes like Crux. It does not crash under Human or  Clearlook. Try disabling Compiz.

I'm hoping that someone who understands such things will be able to fix it. It would be nice to be sure our school's desktop theme works before I export it to other users' workstations.

Laurie

---

### Post by rajman on 2007-11-06
seems to me at least that ooo-gtk is the culprit. After i removed that i had a functional (though ugly) openoffice. at this point i dont care because i have work to do. but it would be nice this weekend to have a pretty openoffice :)

---

### Post by sav2005 on 2007-11-06
> **rajman said:**
> seems to me at least that ooo-gtk is the culprit. After i removed that i had a functional (though ugly) openoffice. at this point i dont care because i have work to do. but it would be nice this weekend to have a pretty openoffice :)
You don't need to remove ooo-gtk even though it is probably the culprit. It is useful in integrating OOo with your desktop -  "Places > Recent Documents" seems to depend on it.

If you use a basic desktop theme OOo will play nicely with Gnome and look OK.

---

### Post by sav2005 on 2007-11-06
> **pasokon said:**
> Open Office Impress under Gutsy perpetually crashes. It successfully recovers the crashed presentation and then soon crashes again especially if you are changing the type of the current slide. 

What's going on with it?
As I have said in the earlier post - disable Compiz and use the Human or ClearLook Theme and OOo will play niicely with Gnome. It seems to be an issue with OOo-gtk, but because this gives some nice low level integration don't get rid of it. It has been reported as a bug but don't hold your breath!

Better to get some work done on a boring desktop than to get no work done on an uber-kool desktop.

---

### Post by mnia on 2007-11-07
Openoffice writer opened and almost ran fine post-upgrade to gutsy. Only prob was the icons had disappeared and there were just words instead (i.e. save, open, bold etc). Not a big deal, but strange. So i followed the advice to change my System>Preferences>Appearance>Theme from Clearlooks to Human and re-opened Oo... all good now!

Thanks to whoever suggested that :)

---

