---
title: "Re: Libre Office Calc - Cell font 'Re-colour' issue"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by paulbuk on 2011-07-10
Hi,
My 2 yr Old ubuntu machine recently went through an automatic upgrade to the latest 11.04.
This week, when I went to go do some 'financial modeling' I loaded up a previously made spreadsheet that I've been using for years. I noticed that the cells which I have 'coloured' text (ie 100% white text on 100% black cell background) won't change at all, to any colour.
Strangely, on my 12 month old laptop which I freshly upgrade the week 11.04 released works fine so me thinks the issues lies with the Libre upgrading the old Open Office which was on my desktop. Don't really want to go back working with M$ Office 2007. Period.

Anyone ideas on how to fix above or completely removed any old O/Office references within my ubuntu if that is the case?
Cheers,

PB
("ex-FE IT [M$] college adult Ed lecturer", 10 years standing)

---

### Post by luvr on 2011-07-10
Does Synaptic list any *"openoffice"* packages? (I would be surprised if it did, since I don't think that Ubuntu 11.04 has them in its repositories. It won't hurt to check, though.)

If your system used to run OpenOffice.org, but now runs LibreOffice instead, then your home directory may still contain an OpenOffice work folder. Open your home location ("Places" -> "Home Folder"), make sure that hidden files and folders are being shown ("View" -> "Show Hidden Files"), and see if you can find an **".openoffice.org"** folder. If you do, then you can simply delete it. I'd be surprised if that solved your issue, though.

In addition to deleting the (obsolete) *".openoffice.org"* folder, you may try and delete the **".libreoffice"** folder as well, to try and get LibreOffice into a brand new, initial state. It could be that your *".libreoffice"* took over some of the OpenOffice.org stuff during the upgrade, and that something went wrong there.

---

### Post by paulbuk on 2011-07-10
Thank you, that is very helpful. (:
I was of course considering first deleting as a whole the update O/O come Libre Suite then just 're-installing' it as I wasn't 'afraid' to do so, just wanted to see if there was a 'quick' fix via these forums.

QUOTE:
"In addition to deleting the (obsolete) ".openoffice.org" folder, you may try and delete the ".libreoffice" folder as well, to try and get LibreOffice into a brand new, initial state. It could be that your ".libreoffice" took over some of the OpenOffice.org stuff during the upgrade, and that something went wrong there."

A new fresh install may be the answer as I said, it works AOK on the laptop which had a 'fresh' install around the same weekend, the laptop being previously a M$ Vista then I made it a 'dual' System but my primary desktop had had Ubuntu on pre- 10.XX.

Anyway thank again, I'll post a follow up in case anyone else should have similar issues in the future.
(:
PB

---

### Post by paulbuk on 2011-07-10
To fix an issues like this I did the following part as suggested by 'luvr':

1) - un-installed all previous Libre Office.
2) - deleted all .openoffice.org and .libreoffice dirs in 'home' folder.
3) - rebooted just in case (not sure if required but did so anyway).
4) - opened 'Synaptic Package Manager' repository from system settings, searched for Libreoffice and installed said 'suite'.
5) - went and made a brew (:
6) - re-booted and tested Calc.
7) - errors fixed and works 100% fine. (you may then also need to add to 'keep in launcher' - load software first then right click over launcher icon if using the new leftbar). 

Voila!

Hope this helps any others who may have a future similar issue.
Regards,
:D

Paul B

---

