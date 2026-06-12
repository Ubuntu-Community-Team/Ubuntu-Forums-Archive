---
title: "App intallation fails in Wine: Check your pif file"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by Arjunanda on 2006-12-06
I have got wine working perfectly. I can run many apps without any problem.  However, when I am trying to install one Win app through wine, I am getting the following error:

16 bit DOS subsystem:
C:\windows\temp\dosshell.pif
Invalid program file name. Check your pif file.

The pif seems to be in some weird format. Cat produces following output:
cat "/[path to wine dir]/C-Fake Windows /windows/temp/dosshell.pif"
&#65533;C-Install DOS shell          &#65533;&#65533;COMMAND.COM                                                                                                                  &#65533;P&#65533;MICROSOFT PIFEX&#65533;qWINDOWS 386 3.0&#65533;h&#65533;&#65533;d(#                                                              WINDOWS 286 3.0!INDOWS VMM 4.0&#65533;&#65533;7&#65533;PIFMGR.DLL2&#65533;&#65533;

TerminalCourier NewP0,<g&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;BB~&#65533;

Any ideas?

---

### Post by ingo on 2006-12-08
you got wine working perfectly??? wow! i don't think it ever did anything i wanted it to...

but sorry, can't help :(

---

### Post by diepruis on 2006-12-08
Are you trying to run a DOS program? In that case, try using DosBox instead.

---

### Post by Arjunanda on 2006-12-08
> **diepruis said:**
> Are you trying to run a DOS program? In that case, try using DosBox instead.

No, that is pure win app, I think for win95. It has the standard win installer and the installation completed succesfully, but after clicking "Finish" I get the error I posted above. Perhaps the intaller wants to open the command line fo finish something - and maybe that is the part which is not working. Is there such thing in wine? Any ideas for a workaround?

---

### Post by Arjunanda on 2006-12-08
And thanks for the tip about DosBox. I did not know about it. Just installed it and wow! Finally I can play my favorite DOS game: BlockOut!

---

### Post by diepruis on 2006-12-08
> **Arjunanda said:**
> And thanks for the tip about DosBox. I did not know about it. Just installed it and wow! Finally I can play my favorite DOS game: BlockOut!

Sweet.

What is the name of the Win95 program?

---

### Post by Arjunanda on 2006-12-08
> **diepruis said:**
> What is the name of the Win95 program?
Parashara's Light

---

### Post by diepruis on 2006-12-12
> **Arjunanda said:**
> Parashara's Light

Couldn't find this in the wine app db.

Maybe you can try installing this on a windows PC and then copying over the relevant files. If that doesn't work, you might want to find out which registry keys / autoexecs / etc. it modifies and carry over those changes to wine.

---

### Post by Arjunanda on 2006-12-14
Hey, got it working! Just started it from the commandline. That never came to my mind. I was just trying to start it by dobule-cicking the icon of exe file. So thank you guys. Though still this mysterious error message keeps me in wonders..

---

### Post by diepruis on 2006-12-14
> **Arjunanda said:**
> Hey, got it working! Just started it from the commandline. That never came to my mind. I was just trying to start it by dobule-cicking the icon of exe file. So thank you guys. Though still this mysterious error message keeps me in wonders..

What probably happened is that the program (or wine) didn't know which working directory to look in for it's files. This has happened to me before using shortcuts and clicking .exe's from Konqueror. Well done, BTW.

---

