---
title: "Photoshop CS2 on Ubuntu Guide"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by Koba on 2007-02-28
This guide is courtesy of PublicidadPixelada Blog.
Original guide located at [http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

This HOW-TO covers up the whole process of installing Adobe Photoshop CS2 on a Ubuntu box in a few simple steps. This method has been tested only on Ubuntu, but it should work on any other linux flavor.

- What you need?

    [LIST] A fresh install of Ubuntu Dapper + all the updates[/LIST]
    [LIST] A Windows box with a fully installed and activated version of Adobe Photoshop CS2[/LIST]

- Fire up a terminal session and type the next commands;

TIP: Instead of using apt-get, you can install them with the Synaptic Package Manager located in the System/Administration menu

    [LIST] $ sudo apt-get update[/LIST]
    [LIST] $ sudo apt-get install wine and then type “yes”[/LIST]
    [LIST] $ sudo wine /*To create the wine file structure*/[/LIST]
    [LIST] $ sudo apt-get install recode and then type “yes”[/LIST]

- Then you need to copy all the necessary files from the Windows box;

    [LIST] Copy the whole Adobe folder from “c:\Program Files\” to “/home/YOURNAME/.wine/drive_c/Program Files/”[/LIST]

- Now you need to export the registry keys of the Adobe Photoshop CS2;

    [LIST] In your Windows box, type “regedit” in the command-line and export the whole “HKEY_LOCAL_MACHINE/Software/Adobe/” to “adobe.reg”.[/LIST]
    [LIST] The next step is to copy that file to your Ubuntu box and convert it to the encoding of YOUR system. For example, if your Ubuntu box has as default charset ascii and your Windows box has ucs-2 then “$ recode ucs-2..ascii adobe.reg” would do the trick. After you converted your adobe.reg file, type “$ sudo wine regedit adobe.reg” to import it to wine.[/LIST]
    [LIST] That’s it! Type “$ sudo wine –winver winxp “[path to Photoshop]/photoshop.exe” or create a launcher and enjoy Adobe Photoshop CS2 on Ubuntu ;)[/LIST]

---

### Post by boast on 2007-03-02
copying those registry keys, I still get "Your Adobe Photoshop user name, organization, or serial number is missing or invalid."

(works fine in windows...)

---

### Post by J-Red on 2007-03-04
I get errors when I try to recode the adobe.reg file. I posted about it somewhere but I'm too lazy to wait until a mod allows that post. Anyone know how to fix that?

---

### Post by J-Red on 2007-03-04
bump? Guys I really need help with this. It gives me an error about it being untranslatable then gives a but number and letter combination thing.

---

### Post by LegoAddict on 2007-04-26
I also have problems.

I have a full legal install of Photoshop CS2 ver.9 on my Windows partition,and I've followed all the steps above.


I get a "System or hardware error, sorry, but this is un recoverable" (not word perfect).  How do I get rid of this?  Photoshop is one of the tools keeping me going back to XP.

To my knowledge, both Ubuntu and XP use ASCII, but how do I find out?



I'm running Feisty and the latest version of WINE.

---

### Post by LegoAddict on 2007-05-03
Update:

After exploring many venues, including Cedega, CrossOver, and WINE, I think it's safe to say that it is impossible to run Photoshop CS2 on Feisty Fawn.  I'm still trying to find a link so that I can complain to Adobe.

---

### Post by proxess on 2007-07-28
[http://ubuntuforums.org/showthread.php?p=3097396#post3097396]("http://ubuntuforums.org/showthread.php?p=3097396#post3097396")

---

