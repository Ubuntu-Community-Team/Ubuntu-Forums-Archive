---
title: "Installer not detecting existing windows installation for dual boot"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by holastickboy on 2012-10-09
Hi all.

I have a situation in which I am trying to install Ubuntu x64 12.04 on my HP DV3138-TX notebook in a dual boot setup.  The reason for doing so is that I  have to use Visual Studio 2012 and Access 2012 for my university subjects (I know, its a shame they don't encourage the use of alternative software there).

When booting up the CD and beginning the installation, it doesnt give me the option to install alongside.  In fact, it actually says that it cannot detect an installation of another operating system, and when I try to do things manually, it shows a completely blank drive, which is definitely not what is there (currently have Windows 7 x64 as my other operating system).  I know what I am doing with the installation procedure, I just did the same thing the other day on a desktop system and was able to detect the other operating system, as well as manually partition the drive.

What's even weirder, is when I quit the installer and it it sends me to the livecd desktop, I am able to see the existing paritions on the drive, and am even able to browse them (so it definitely sees them in this sense, just not in the installer for some reason).

If all else fails, I will have to reinstall everything and do it all from scratch, but I was wondering if anyone else has come across this issue, and if so, have they fixed it?

---

### Post by Bucky Ball on 2012-10-09
Are you required to submit files in the Access/Visual Studio formats? My university has never encouraged open-source anything, nor are they likely to, but I'm in my sixth year and have used Ubuntu for the lot. If it spews out in the right format for them they wouldn't have the foggiest what it was created on. Nor would they care as long as the works in by due date. ;)

Not sure if the spreasheet in Libre/Openoffice will spit out files suitable for Access and know nothing about Visual Studio. 

Just a thought.

Just tried in the Libreoffice database but not letting me 'Save As' so no joy there.

---

### Post by holastickboy on 2012-10-09
> **Bucky Ball said:**
> Are you required to submit files in the Access/Visual Studio formats? My university has never encouraged open-source anything, nor are they likely to, but I'm in my sixth year and have used Ubuntu for the lot. If it spews out in the right format for them they wouldn't have the foggiest what it was created on. Nor would they care as long as the works in by due date. ;)

Not sure if the spreasheet in Libre/Openoffice will spit out files suitable for Access and know nothing about Visual Studio. 

Just a thought.

Thanks for the reply Bucky Ball!  Alas, I am required to use the software (one of my assignments actually has me screenshotting tasks within Access, it's pathetic).  I already use LibreOffice for everything else, but I am stuck with Visual Studio and Access for the courses I am in this semester.

---

### Post by Bucky Ball on 2012-10-09
> **holastickboy said:**
> Thanks for the reply Bucky Ball!  Alas, I am required to use the software (one of my assignments actually has me screenshotting tasks within Access, it's pathetic).  I already use LibreOffice for everything else, but I am stuck with Visual Studio and Access for the courses I am in this semester.

Message received and understood. ;(

PS: And hello from Adelaide!

---

### Post by Mark Phelps on 2012-10-09
It may not just be the "output" you produce, you may have to utilize parameter and/or config files made available to the class.

MS Access won't work through Wine, and even if Visual Studio does (which I doubt), you would do better using it in "native" mode for classwork.

Sorry, but it looks like you're stuck with MS Windows as long as you have to use these for classwork.

---

### Post by oldfred on 2012-10-09
If you still want to dual boot, you  probably have the 4 primary partition limit issue in MBR partitioning.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

