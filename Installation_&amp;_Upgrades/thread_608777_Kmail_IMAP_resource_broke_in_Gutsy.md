---
title: "Kmail IMAP resource broke in Gutsy"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by dscherry on 2007-11-10
I use kmail's IMAP resources to store my contacts and calendar.  After upgrading Feisty to Gutsy, they no longer displayed in Kontact, or in Kaddressbook/Korganizer.  Though this is likely a KDE problem, it surfaces as a result of the Gutsy upgrade.

After a lot of googling, I found a thread that suggested adding the following line to 
~/.kde/share/config/kmailrc
in the section called [IMAP Resource]

TheIMAPResourceAccount=xxxxxxxxx

where xxxxxxxxx is the account number for the resource - which can be found a few lines above [IMAP Resource] in the section called [GroupwareFolderInfo]

After logging out and back in, my IMAP resources worked as expected.

Though I don't think many people use IMAP resources, hopefully this will save those who do, some time and frustration.

Dan

---

