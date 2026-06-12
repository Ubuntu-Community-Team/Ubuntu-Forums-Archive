---
title: "Ubuntu installation in Windows not working"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by Dcmac on 2012-01-27
I tried installing Ubuntu though Windows and I get this error message, "There is no disk in the drive. Please insert a disk into drive \Device\Harddisk1\DR1"

Is this a known problem, and how can I fix it?

---

### Post by Karlchen on 2012-01-27
Hello, Dcmac.

As you seem to be trying to perform a Wubi installation, you might like to follow the instruction on how to install Wubi carefully: [B][WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

[/B]In case you go on experiencing problems do not hesitate to report back and ask for help. Yet, please, provide the following details:

[LIST]
[*]The exact Windows version you are using
[*]Which Ubuntu version are you trying to install via Wubi?
[*]Are you using the Wubi.exe that matches this Ubuntu version?
[*]Did you launch Wubi in elevated mode?
[*]During which step of the Wubi installation did you encounter the problem?
[*]Attach the Wubi installation logfile to your post. It will be located inside your %TEMP% folder.
[/LIST]

Kind regards,
Karl

---

### Post by Rubi1200 on 2012-01-28
> **Dcmac said:**
> I tried installing Ubuntu though Windows and I get this error message, "There is no disk in the drive. Please insert a disk into drive \Device\Harddisk1\DR1"

Is this a known problem, and how can I fix it?
Hi and welcome to the forums :-)

Firstly, that was great advice posted by Karlchen and the steps mentioned are for sure important.

In your situation, the error is likely due to a card reader or other external device. Just click through the error messages and you should be able to continue normal installation.

Let us know if this helps.

---

### Post by Dcmac on 2012-01-28
Unfortunately I couldn't get it to work.


[LIST]
[*]Running Windows 7 64-bit
[*]Trying to install Ubuntu 11.10
[*]The installer is for 11.10
[/LIST]
[LEFT]I don't quite know what elevated mode is, and when I try to attach my logfile the uploader says invalid file. The error pops up immediately after I try to run the install. When I try to click through the error (The options are cancel, try again, and continue) it cycles through DR1 to DR4.


[/LEFT]

---

### Post by Karlchen on 2012-01-28
Hello, Dcmac.

Elevated Mode:
Full administraotr privileges activated. You do this in your case by righ-clicking on wubi.exe and selecting **Run as administrator** in the context menu. Most installers on Windows Vista, Windows 7 and newer will required to be run in elevated mode.

As Rubi1200 told you: click through the error message_s_. So Rubi seems to have expected that Windows might cycle through more than one card reader drive.
As a rule card readers can handle more than one card format and will *see* one empty drive for each of the known card formats.
E.g. my card reader offers 3 different drives and 3 different drive letters. So my Windows here might cycle through \Device\Harddisk1\DR1, \Device\Harddisk1\DR2 and \Device\Harddisk1\DR3.

The Wubi logfile should be located inside them %TEMP% folder. %TEMP% is a variable pointing to your personal folder for temporary files. The expanded variable will hold a path looking like C:\User\YourName\Appdata\Local\Temp.
The Wubi logfile name will be something similar to ***wubi-11.10-rev245.log**.* (wubi plus Ubuntu version plus Wubi version number plus .log)

By the way, as you report that Windows cycles through the 4 drives, does this mean that this is an endless loop? It starts by complaining about DR1, then DR2, DR3 and DR4, and then starts all over again with DR1, so that you have no chance of escaping from this cycle and continuing the installation process?!

Kind regards,
Karl

---

### Post by Dcmac on 2012-01-28
> **Karlchen said:**
> By the way, as you report that Windows cycles through the 4 drives, does this mean that this is an endless loop? It starts by complaining about DR1, then DR2, DR3 and DR4, and then starts all over again with DR1, so that you have no chance of escaping from this cycle and continuing the installation process?!

Yeah that's what it's doing.

Also, my logfile is too big to be uploaded.

---

### Post by psychonaut91 on 2012-01-28
maybe you should delete you cookies.:P

---

