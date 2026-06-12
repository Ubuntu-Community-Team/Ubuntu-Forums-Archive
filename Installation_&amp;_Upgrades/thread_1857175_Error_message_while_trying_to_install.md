---
title: "Error message while trying to install"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by ijerda on 2011-10-09
I'm very new to Ubuntu Linux and am having trouble installing a writing aid called Scrivener. It's a beta version, but I've spent hours researching how to install .tgz files and have tried everything and have had no success. I've used terminal and this is the error message I've gotten:

jayda@jayda-ubuntu:~/Downloads$ sudo unzip -d /tmp Scrivener-035.tgz
Archive:  Scrivener-035.tgz
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of Scrivener-035.tgz or
        Scrivener-035.tgz.zip, and cannot find Scrivener-035.tgz.ZIP, period.


It isn't a zipfile, nor does it constitute one disk of a multi-part archive. It's a .tgz file. I just need to know if there's something I can do, or if I just shouldn't waste my time trying to install it anymore.

Thanks for the help!

---

### Post by Pynalysis on 2011-10-09
> **ijerda said:**
> I'm very new to Ubuntu Linux and am having trouble installing a writing aid called Scrivener. It's a beta version, but I've spent hours researching how to install .tgz files and have tried everything and have had no success. I've used terminal and this is the error message I've gotten:

jayda@jayda-ubuntu:~/Downloads$ sudo unzip -d /tmp Scrivener-035.tgz
Archive:  Scrivener-035.tgz
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of Scrivener-035.tgz or
        Scrivener-035.tgz.zip, and cannot find Scrivener-035.tgz.ZIP, period.


It isn't a zipfile, nor does it constitute one disk of a multi-part archive. It's a .tgz file. I just need to know if there's something I can do, or if I just shouldn't waste my time trying to install it anymore.

Thanks for the help!


Uncompress the archive using this command:

tar zxvf Scrivener-035.tgz

---

### Post by ijerda on 2011-10-09
Alright, that worked. Now what do I do to install the actual program? Sorry that I'm a complete newb when it comes to this

---

### Post by Hakunka-Matata on 2011-10-09
There may be an install.sh or <somethingelse>.sh file.  They would be install scripts.

---

### Post by ijerda on 2011-10-09
> **Hakunka-Matata said:**
> There may be an install.sh or <somethingelse>.sh file.  They would be install scripts.

Sorry... I don't understand what I'm supposed to do with either of those. Is there a way you could explain that in more detail so I can know what to do?

I know pretty much nothing about Linux, because I just switched from Windows.

---

### Post by ijerda on 2011-10-12
Bump

---

### Post by Hakunka-Matata on 2011-10-12
OK, it's a strange breed, but here's what I found.
[http://www.literatureandlatte.com/wiki/doku.php?id=running_scrivener_in_linux#manual_installation](http://www.literatureandlatte.com/wiki/doku.php?id=running_scrivener_in_linux#manual_installation)

Go to the "**Ubuntu-centric Instructions**" section of the above WebSite.  

I did all that and then when I tried to launch the program from a Terminal window, by entering "Scrivener" I got a "**command not found**" error message.  Discouraged, I then used nautilus to browse to the directory and look around, by right-clicking on the Scivener.bin file, (.bin files in linux are the equivalent of .exe files in Windows"), then selecting **open,** it worked.  
**Edit: **Creating the symbolic link as suggested fixed the launch from Terminal problem.  That is the last step listed in the "**Ubuntu-centric Instructions**" section, I hadn't done that earlier.  You might also want to create the desktop launcher that is discussed in the instructions.

---

### Post by PrimordialAstronaut on 2011-10-19
I'm trying to install the same software and I am so confused... I've been at this for several hours too, and I just don't get it. I have tried installing with both a .tgz file and .deb and neither works.

I have a .deb file, but when I try to run it through Software Center, the Software Center just crashes. And I can't figure out how to install through the terminal either. I just keep getting this "No such file or directory" error or "command not found."

---

### Post by PrimordialAstronaut on 2011-10-19
So I just found a newer version (?) in .deb form and this time Software Center at least tried to install it... didn't crash... but it says, "Package file cannot be opened: Please copy the file to your local computer and check file permissions." ...what does that mean? Something's wrong with the file or ...what?

---

### Post by ijerda on 2011-10-19
I've been having the exact same problems as you, with both the .tgz and .deb files. Neither work and neither will install, whether with terminal or any other installation client. I even tried Wine to use the Windows version and it installed but wouldn't open due to an error.

I think I've basically given up on getting it working on my Ubuntu laptop unless I can get it to work via options given by users on here.

---

### Post by PrimordialAstronaut on 2011-10-20
Well at least now I know I'm not alone! Lol. Hopefully someone here can offer some advice to get us going.

---

### Post by Hakunka-Matata on 2011-10-20
I've just downloaded and installed scrivener.deb from [this]("http://robhamm.com/main/2011/10/04/blog/scrivener-for-linux-035-beta-deb-package") link.  It worked straight out of the box.  When starting the installation of **Scrivener for Linux 0.3.5 beta .deb** package by doubling clicking on it and letting software center install it, an error is generated (see thumbnail), but was not a problem, I just said ignore and continue, it works fine, no problems at all.  

Ubuntu Desktop 32 bit, 11.10 (Oneiric).

If you can explain in more detail exactly where your installation goes wrong, I might be able to help.

> So I just found a newer version (?) in .deb form and this time Software  Center at least tried to install it... didn't crash... but it says,  "Package file cannot be opened: Please copy the file to your local  computer and check file permissions." ...**what does that mean?**  Something's wrong with the file or ...what?
Check file permissions probably means you don't have the privileges necessary to execute the file.  Right click on the file, click the permissions tab, tick the box that says ,"allow executing file as program", or follow the instructions I've linked to in post # 7.

---

### Post by PrimordialAstronaut on 2011-10-22
Thanks for the help, Hankunka-Matata! I finally got it going. That little check box was apparently all that was between me and success. Also, I went ahead and updated to 11.10 so that may have been causing issues too (I was trying to install on 11.04 previous to last night's ultimately successful attempt). 

Anyway, thanks a ton! 

Ijerda, did you have any success with your install?

---

### Post by ijerda on 2011-10-22
Still no success. Wine doesn't work, Ubuntu Software Center failed (multiple times) with both .deb AND .tgz files (no reason given, it just fails to install), terminal isn't working either. Basically, I think I'm just giving up on Scrivener. I want it, but it isn't worth this kind of effort.

I've done the permission thing you mentioned, I've downloaded and redownloaded it to try and install, and neither work. I wonder if it's just my laptop or something.

---

### Post by Hakunka-Matata on 2011-10-22
> **ijerda said:**
> Still no success. Wine doesn't work, Ubuntu  Software Center failed (multiple times) with both .deb AND .tgz files  (no reason given, it just fails to install), terminal isn't working  either. Basically, I think I'm just giving up on Scrivener. I want it,  but it isn't worth this kind of effort.

I've done the permission thing you mentioned, I've downloaded and redownloaded it to try and install, and **neither work**. I wonder if it's just my laptop or something.

More detailed information might be helpful, maybe you could take some screenshots of the Terminal window so we can see exactly what does or does not happen as it should.
Also, what Release and version Ubuntu are you running?, is it a Wine install inside Windows, or a straight partition install?

---

