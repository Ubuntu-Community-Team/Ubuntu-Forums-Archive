---
title: "Make A Shortcut to a Program"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by php-zbatev on 2008-06-11
Hi,

I was wondering how to make a shortcut for a program in Linux, I mean there are some installation instruction that includes these procedure but how about those that do not include them should it follow that you could not make a shortcut link to it, like you have to start that program from the terminal always?

A particular example would be what i am working on right now, I have just successfully installed Zend Studio 5.5.0. and I do invoke the program through terminal. I just couldn't find/google a tweak to making a shortcut for ZDE. All of the tutorials/guides that I've found only suggest to start the program through the terminal.


Is there a generic way of doing this or does it have to be specific like most of them

---

### Post by mick222 on 2008-06-11
right click on applications in panel and choose edit menus you acan add a launcher to the program from here .

---

### Post by vanadium on 2008-06-11
> I was wondering how to make a shortcut for a program in Linux

Details will differ whether you use gnome, KDE or something else as a desktop environment. In gnome: right-click desktop, create launcher. To add to your menu: right-click menu (Applications , Places, System), select "edit menus". Even better: drag the application from nautilus (the file manager) to the menu.

---

### Post by avtolle on 2008-06-11
You could try the following: on the desktop, find an empty space, right click, and select create launcher. Then, enter the information requested in the three blanks that appear. The one of paticular importance is the second one, where you MAY need to enter the path to the application. Generally, you would enter the terminal command you use to start the application in that box.

---

### Post by cpetercarter on 2008-06-11
Have you tried making a custom launcher? In Gnome, right click on a panel > Add to Panel > Custom Application Launcher. In the dialogue box which then appears, give your launcher a name and description, and enter the command which runs your programme i.e. the command you use to launch it from the terminal.

You can also add the application to the applications menu. System > Preferences > Main Menu - select the menu you want to edit > add new item.

Hope this helps.

---

### Post by php-zbatev on 2008-06-11
I use Gnome.

Yep! the Launcher did the trick thanks a lot guys. your response is well appreciated.

I also tried the other methods.

---

### Post by virsto on 2010-07-20
> **mick222 said:**
> right click on applications in panel and choose edit menus you acan add a launcher to the program from here .

Yes, I am aware that one can make a launcher for any application program; but, this is not my problem as stated in my first posting. Note, I included a screen shot of the Main window (OpenOffice.org) --- this is what I wish to have a launcher for --- not the individual programs listed in Applications -> Office.

I wish to have a launcher for OpenOffice.org (Main window). I do know that when I examine all the tasks with System Monitor that soffice.bin is the task that corresponds to the Main window --- How can I launch this?;)

---

### Post by virsto on 2010-07-20
> **cpetercarter said:**
> Have you tried making a custom launcher? In Gnome, right click on a panel > Add to Panel > Custom Application Launcher. In the dialogue box which then appears, give your launcher a name and description, and enter the command which runs your programme i.e. the command you use to launch it from the terminal.

You can also add the application to the applications menu. System > Preferences > Main Menu - select the menu you want to edit > add new item.

Hope this helps.

Ok! You put me on the right track! I found that I could launch OpenOffice.org from a terminal window by entering

 ```
soffice
```

Now, I will see if I can manage to create a launcher for it.:D

---

### Post by virsto on 2010-07-20
Ok! Finally. 
I found a suitable OpenOffice icon on the web, downloaded it, now it works and looks the way I would like.

Thanks for all that helped :D
Have a good day.

---

### Post by Malvolio on 2011-01-30
This thread was relevant to my problem so I thought it best to post here instead of creating a whole new thread.  I've done all of the above and can't run my program in a launcher at all, even though running the program directly works just fine.  It spends all of a split second loading the program then disappears if loaded from a launcher.  I'm practically at wits end, what with my lack of knowledge in using Ubuntu and the general lack of indepth guides on the subject online.

---

