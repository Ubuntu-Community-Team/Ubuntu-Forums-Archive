---
title: "Dual Booting Problems with Ubuntu &amp; Windows XP"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by alligoodw on 2007-05-23
I'm new to Ubuntu or Linux for that matter.  I have been able to install Ubuntu 7.04, install software (watching my  DVD's and listening to my music) with absolute and total success.  Before doing so, I defragmented the Windows partition, getting it ready for a dual booting system.  

Upon rebooting the system, I select Windows XP option from the GRUB menu, and I get the following error:

WINDOWS COULD NOT RESTART BECAUSE THE FOLLOWING FILE IS MISSING OR CORRUPT - 
<WINDOWS ROOT> \SYSTEM32\HAL.DLL
PLEASE REINSTALL A COPY OF THE ABOVE FILE.  

I am able to view this partition from the Ubuntu side.  I can play my music from that partition and etc.  If I actually have to replace the system32\hal.dll file, how would I go about doing it?

---

### Post by cyrusrayne on 2007-05-24
Since you're able to see all your files from Feisty, I would suggest trying to back up your files and reinstall Windows and any apps you are able to.  Usually when something is missing in the system32 folder, it's a very bad thing and generally involves reinstalling Windows which will of course destroy your files.  Since you have music and other files you don't want to lose, the backup is an essential part of the rebuild.  I had a similar dilemma, except I had the misfortune of losing all of my files.

If you can find a way to replace that particular file without reinstalling however, than that will work out more to your benefit because you hopefully won't need to reinstall anything.

Good Luck!

---

### Post by alligoodw on 2007-05-25
Problem Resolved:

I'm including this solution for other's future reference.  This is how I corrected my dual/boot problem.   Windows XP Home Edition was installed first.  I later added Ubuntu 7.04.

1.  Use the Windows XP CD-ROM to start your computer. 

2.  When you receive the message to press R to repair Windows by using the Recovery Console, press the R key. 

3.  Select the Windows installation that you want, and then type the administrator password when prompted.  (If you have one. If not, then just hit the enter key)

4.  Type **bootcfg /rebuild**, and then press ENTER.

5.  When the Windows installation is located, the following instructions are displayed:
[B]
Add installation to boot list?  (Yes/No?All)[/B]
[Type Y in response to this message.]
[B]
Enter Load Identifier:[/B]
[This is the name of the operating system.  Type Windows XP Professional or Windows XP Home Edition.]
[B]
Enter OS Load options:[/B]
[Leave this field blank, and then press ENTER.]

After you perform the preceding steps, restart the computer.

---

### Post by geezerone on 2007-05-25
[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

---

### Post by Upunter on 2008-01-20
Thank you alligoodw for your solution which fixed my problem.  I think I caused my problem when I  removed Ubuntu 6.06 yesterday.  I had the same error message as you.  Then I installed Ubuntu 7.10, and the problem persisted.

Today, I followed your instructions.  My Windows XP Home disk repaired my Windows XP Home operating system.  (The XP Home disk also found my BartPE which I made with PEBuilder.)  My XP Home disk was manufactured before service pack 1.

---

