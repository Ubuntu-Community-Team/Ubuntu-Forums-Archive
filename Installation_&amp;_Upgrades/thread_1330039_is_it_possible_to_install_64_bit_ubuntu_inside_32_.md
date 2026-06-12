---
title: "is it possible to install 64 bit ubuntu inside 32 bit xp?"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by sajid.bd on 2009-11-18
HI,
i have 64 bit processor.Now can i install 64 bit version of ubuntu inside my 32 bit windows.
i have used 32 bit ubuntu 9.04 . now wants to download 9.10. help me decide 32 bit or 64 bit. bandwidth in our country is not very fast avg users get 16-20kbps.

---

### Post by plusnplus on 2009-11-18
Hi sajid.bd,
What do you mean by "install 64 bit version of ubuntu inside my 32 bit windows"?
You can install ubuntu side by side with windows, but not inside the windows OS.
As i know, not really much application support in 64 bit OS (either ubuntu or windows)

---

### Post by Anarci on 2009-11-18
I assume your talking about virtualization - If so virtualbox can install a 64 bit guest operating system inside a 32 bit host os but will have a higher overhead.

---

### Post by garvinrick4 on 2009-11-18
If you are using WUBI yes you can install 64 bit inside of a 32 bit Windows O.S.

I did it for a quite a while no problems at all. 

Other virtual packages I would Google to make sure.

---

### Post by sajid.bd on 2009-11-18
i meant i  want to install ubuntu 64 bit as a windows application using wubi.exe in the cd.

---

### Post by sajid.bd on 2009-11-18
> **garvinrick4 said:**
> If you are using WUBI yes you can install 64 bit inside of a 32 bit Windows O.S.

I did it for a quite a while no problems at all. 

Other virtual packages I would Google to make sure.


yes i am talking just about that. i want to download 64 bit version and run wubi from the cd.what do you mean by  'Other virtual packages'.?

---

### Post by garvinrick4 on 2009-11-18
Okay I know WUBI.   There are other Virtual companys that have software to answer your question.

.Now in WUBI the installation is a default question on installation. Just put your
CD in the tray, answer yes to WUBI give them the desired disc size for WUBI folder 
and your password click install and 12 minutes later you are installed.

Older versions or WUBI was a different install now just plug and play really.

Your UBuntu folder will be right next to Users in C: drive.

In Ubuntu the /host is where your windows files will be just go host/users/login name.
and drag and drop what you want to Ubuntu.

You have a whole file system in desktop called Nautilus. All in Icons. host is icon users is in icon and so on. It is in Computer to filesystem.

To get Linux files to Windows have to copy to external drive then put in Windows.

Have a uninstall in ubuntu folder in Windows or use Add-remove programs to uninstall
if you get goofed up. Will not harm Windows installation it is like an App in Windows.

WUBI will take care of grub it attaches to Windows dos4grub and puts windows first and select ubuntu with up and down arrows and enter default 10 seconds to make up your mind or boots to Windows.

Best way to learn how to use Linux. is WUBI.  Google a lot for problems and answers
read these Forums and ask questions.
 
Here is a link to read about Wubi. And one to download a .iso file then BURN it to
a CD.     Then just put CD in tray and off you go.


[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide")

[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

