---
title: "How to install blender 2.46 - New User of linux system"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by Orlenka on 2008-05-25
Hi everyone,

i'm a new user to Ubuntu and linux system. It's the first time i work on ubuntu.
I want to install the 3d Software Blender 2.46. I've downloaded a package with the extension tar.bz2. And i don't know how to install it?!

I've already opened it with the Archive Manager and open the program with the executable file...but it's not what i want...

I would like to have blender in my application - graphics menu and install the 2.46 version. I don't want to keep the file on my desktop. I want like on Microsoft Windows, install blender in "Program files" folder and have my shortcuts on the desktop to launch the application.

With the add/remove application utility, it installs blender 2.45 version... how install the version i've dowloaded?

Thanks for help

Orlenka

---

### Post by sanone on 2008-05-25
Well you need to understand a bit more about the installation process in linux. 

First, there are the official repositories from which you can install applications using the add/remove utility or synaptic. These repositories are build during the development cycle of hardy and then frozen. This basicly means that no new version of applications will make it there only security fixes. In some cases there are additional repositories which keep the latest version of a package availible. I haven't found any for blender. 
You meantioned you want to install it 'like in windows'. Well there is no one 'program files' folder on linux. Applications are placed at a few places (/usr/bin/, /usr/share, etc.). 

Second, there are downloadable tar.bz/zip/bz2 compressed folders which contain a certain application or game. These archives can be extracted to any place you want. I would recommend something like '/home/orlenka/Applications/'. To create a shortcut to an application in that folder you simply right click on the desktop and select 'create launcher'. If you want the application to appear in the Applications menu just right click on the Applications menu and select 'Edit Menus'.

I hope this helps.

Cheers,
San

---

### Post by Orlenka on 2008-05-25
Hey thank you very much, it works!

But i have another question: when by mistake i installed an older version of blender (2.45), Ubuntu installed it automatically in some what folders?! and automatically create "Blender Icons" in the application menu etc.

I create now a Folder where i put my application files and launch it from that folder... Is there a way to install it like Ubuntu would? in a folder that is already create for application?

Thanks

Orlenka

---

### Post by sanone on 2008-05-25
I really would not advice a new user to modify system folders. Just install it somewhere in your home folder and create the shortcuts as you like. 

Like I said linux has files of a single application stored at multiple places and since it is not maintained with apt (synaptic or add/remove programs) you would have to maintain it. So just install this in your own 'program files' folder but stay away from those system folders.. you would not win anything by trying to place those files there.

San

PS. This way you can also have the official supported blender version (2.45) installed next to the latest and greatest 2.46, 2.47, 3.00 whatever ;)

---

### Post by Orlenka on 2008-05-25
Ok thanks for advices :)

---

### Post by ztirffritz on 2008-05-25
I believe that Blender is in the repositories.  Why not just use the Synaptic application to install it.  
1) Select 'System' from the menu bar at the top of the screen
2) Select 'Administration'
3) Select 'Synaptic Package Manager'
4) Search for 'Blender'
5) Click the check box next to the application
6) Click on Apply

---

### Post by sanone on 2008-05-25
> **ztirffritz said:**
> I believe that Blender is in the repositories.  Why not just use the Synaptic application to install it.  
1) Select 'System' from the menu bar at the top of the screen
2) Select 'Administration'
3) Select 'Synaptic Package Manager'
4) Search for 'Blender'
5) Click the check box next to the application
6) Click on Apply

Please read the starting post more careful. Blender is in the repositories it is only not the latest version. Orlenka already installed it.

He just wants to test/use the latest and greatest...

---

