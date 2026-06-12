---
title: "Opening files from USB"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by RKhadder on 2010-05-08
[FONT=Arial][SIZE=2]I'm trying to open an executable via usb. An error message comes up when I double click it.[/SIZE][/FONT]

[FONT=Courier New][FONT=Arial][SIZE=2]Archive: /media/0000-0199/Ramsey/Network+/Engine.exe[/SIZE][/FONT]
[SIZE=2][FONT=Courier New][/media/0000-0199/Ramsey/Network+/Engine.exe][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]End-of-central-directory signature not found. Either this file is not[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]a zipfile, or it constitutes one disk of a multi-part archive. In the[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]latter case the central directory and zipfile comment will be found on[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]the last disk(s) of this archive.[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]note: /media/0000-0199/Ramsey/Network+/Engine.exe may be a plain executable, not an archive[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]zipinfo: cannot find zipfile directory in one of /media/0000-0199/Ramsey/Network+/Engine.exe or[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/media/0000-0199/Ramsey/Network+/Engine.exe.zip, and cannot find /media/0000-0199/Ramsey/Network+/Engine.exe.ZIP, period.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]I'm fairly new to Ubuntu. I am using ubuntu 9.1 and eventrually be switching to 10.04. Is there anything I can do to open it?[/FONT][/SIZE][/FONT]

[FONT=Courier New][FONT=Arial][SIZE=2]Thanks [/SIZE][/FONT][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=2]Ramsey[/SIZE][/FONT][/FONT]

---

### Post by John Bean on 2010-05-08
The errors are from the archive manager which can open some self-extracting .exe archives. You can't run a .exe file directly in Ubuntu - it's a Windows (or DOS) executable not a Linux one.

What are you trying to do?

---

### Post by RKhadder on 2010-05-08
Well I'm studying for an exam and I have a pratice test on my usb. I can open it on my windows computer and I wanted to use it on my ubuntu computer. When I tried to open it the error came up. I just want to be able to usse the function.

---

### Post by John Bean on 2010-05-08
It may work with WINE (do a search) but it may not be straightforward, depending on exactly what it is and which Windows technologies it requires.

---

### Post by RKhadder on 2010-05-08
Do you mean convert it to wines?

---

### Post by John Bean on 2010-05-08
Wine is a program that allows you to run some Windows .exe files in Linux. There are a lot of references about installing and using Wine in Ubuntu, do a search to find them.

---

