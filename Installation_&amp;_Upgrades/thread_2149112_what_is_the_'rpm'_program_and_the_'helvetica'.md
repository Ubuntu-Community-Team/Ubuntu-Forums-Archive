---
title: "what is the 'rpm' program and the 'helvetica'?"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by iScience on 2013-05-27
I'm running a program called root. i'm getting to it via command line. it's actually FOR operating in CLI. I exported the proper files but it says one is missing. whenever i try to run the program, this is the message that pops up.

```

Couldn't find  font "-adobe-helvetica-medium-r-*-*-10-*-*-*-*-*-iso8859-1",
trying "fixed". Please fix your system so helvetica can be found,
this font typically is in the rpm (or pkg equivalent) package
XFree86-[75,100]dpi-fonts or fonts-xorg-[75,100]dpt.
/home/Max/root/bin/root.exe: error while loading shared libraries: libRint.so:
 cannot open shared object file: No such file or directory

```

So i did the following...

```

$sudo apt-get install rpm

```

and it said "rpm is already the newest version". i don't know what that means... is it telling me that i already have the newest version?... and "0 packages were upgraded, 0 packages newly installed, 0 to remove and 0 not upgraded."


how do i get this program working? any ideas based on the error it's outputing?

---

### Post by oldos2er on 2013-05-27
"rpm" is Red Hat package manager, or the extension for a Red Hat package (similar to *.deb being a Debian package). Helvetica is a sans-serif typeface. It looks like "root.exe" is looking for one of the xfonts-* packages.

What does "root.exe" do, and where might one obtain it?

---

### Post by grahammechanical on 2013-05-27
Are you actually running Ubuntu? Perhaps it is Fedora that you are using. Oh, there is actually in the Ubuntu Software Centre the RPM Package Manager. Well, I never!

Did you notice this warning? On Debian and derived systems (that's Ubuntu) it is recommended to use "alien" to convert RPM packages into .deb format instead of bypassing the Debian package management system by installing them directly with rpm.

Regards

---

### Post by iScience on 2013-05-27
@ oldos2er ,    well, you can get it here [http://root.cern.ch/drupal/content/production-version-534](http://root.cern.ch/drupal/content/production-version-534)  . i ran this on my linux virutal machine and got the SLC 6 version 4.6. i gunzipped and untarred with terminal.

you can go here [http://root.cern.ch/download/doc/ROOTUsersGuide.pdf](http://root.cern.ch/download/doc/ROOTUsersGuide.pdf) and goto chapter 2 to the instructions it gives to install it (i think). And this is where i'm having problems.

@grahammechanical, no i'm quite certain it's ubuntu; it has the ubunutu layout, and it says ubuntu everywhere on it.

---

### Post by grahammechanical on 2013-05-27
Ah, it becomes clearer. Not much clearer. But a little. I do not think that installing rpm is the answer. And any program called root.exe is going to cause concern to Ubuntu users. So, to be clear this is a Linux program (? stil not seen anything confirming that) and you have downloaded the tar.gz file and unpacked it and follwed the instructions. And ROOT is text based program that runs from the command line by simply typing root but when you do that you get those two errors.

The best I can come up with is, 

1) you need an adobe true type font called helvetica and you need it in the place where ROOT expects to find fonts when it loads.
2) you need a library called libRint.so

But I have no idea where that library is supposed to be placed. I suggest that you sue file manage to search through the ROOT programs directories/folders and become familiar with the directory structure.

I am sorry that this is the best that I can manage.

---

