---
title: "what application will open my download?"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by kero20 on 2010-10-28
Please can somebody help me with this, im sure its simple but im pulling my hair out!

Im trying to download a free virus checker software as im pretty sure i just opened an email with a virus in it. Anyway when i try to open the file in the downloads box it keeps asking what application i want to open it with? What do i use, i cant see anything that would open it! 

The file is in the download box i just cant open it arrrgggghhh.

Please help me!

---

### Post by suchislife on 2010-10-28
Viruses are extremely rare on Linux.

Rather then trying to download a free virus... sorry I mean a AV scanner.

Use these to guide you to installing clamav or something that works with Ubuntu.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by cchhrriiss121212 on 2010-10-28
What type of file is it? If it has an .exe on the end of it then it is a Windows file. In any case Ubuntu is designed to install programs from trusted sources, which you access with Software Center.

I would recommend opening software center and installing ClamAV.

---

### Post by cainram on 2010-10-28
Ok, slow down. There are some things you should know about Ubuntu.
[LIST]
[*]Ubuntu is _not_ windows. When you download applications from the Internet you need to start paying attention to what platform or operating system they are for. If you download a program for Windows (like an .EXE for example) do not expect it to run in Ubuntu (which is based on GNU/Linux - NOT Windows). You can install an emulation layer like Wine but I wouldn't recommend something like that until you are more comfortable with Ubuntu.
[*]Virus checkers are not necessary under Ubuntu. Just make sure you get EVERY update as soon as it is available. Software updates provide all the security the average user needs. I'm sure there will be posts aruging with me (just for the sake of arguing) but I think, in general, this is good advice. Either way, virus scanners built for Windows will not run natively in Ubuntu.
[*]Ubuntu installs software differently than Windows. Try looking for the software you need in the Ubuntu Software Center. Think of it like an App-Store or Marketplace. You *can *download applications from the Internet and install them (.DEB, usually) but I wouldn't recommend this method for a new user. Applications in the Software Center (often called 'the Repository' by those in the know) have been vetted and tested by countless developers and bug-testing volunteers. 
[/LIST]

---

### Post by endotherm on 2010-10-28
welcome.

it is very unlikely that you got a virus/worm or a trojan that actually funtions on ubuntu, but in the case that you did, downloading an antivirus program from the web is not a good solution. in ubuntu you will almost never download a program from the web like that. 

I would install clam-tk from the Ubuntu repositories through software center (Applications -> Ubuntu Software Center) and give your home directory a scan if you like. 

as a general rule, in ubuntu, downloading programs from wherever and installing them is a way to Get a malware, not a way to get rid of a malware. almost all the software you will need is in the repositories, and if you stick with them, your malware risk is rather low.

---

### Post by cainram on 2010-10-28
Good luck and enjoy Ubuntu! Don't be a stranger to the forums, they are your greatest resource!

---

