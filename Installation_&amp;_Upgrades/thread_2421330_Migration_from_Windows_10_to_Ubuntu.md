---
title: "Migration from Windows 10 to Ubuntu"
date: 2019-06-19
forum: Installation &amp; Upgrades
---

### Post by jfpolacko on 2019-06-19
Evening Everyone! Hope everyone is having a wonderful day/evening!!! So I have a question that maybe stupid but then again i was always told there was no such thing as stupid question lol Anyway's I'm tired of using Windows since Win 8 they've seemed to of gone down hill. My question would be is there a easy way to migrate from the Win O/S to Ubuntu without losing some important documents? I'm not new to the Linux world and have been messing with Suse to Fendora but personally I've always liked tinkering with Kubuntu. So any help would be awesome!! Thanks

---

### Post by Mark Phelps on 2019-06-19
You failed to mention the file formats of these "important documents" -- and if they are Office 365 files, then the answer is "most likely NOT" -- as there is no Linux equivalent of Office 365.

There ARE quite a number of "office-like" apps, which have various degrees of success in reading MS Office files. and some of these are free -- but most of them only offer equivalents to MS Word, MS Excel, and MS Powerpoint.  If your "documents" have been created with other MS Office components, like Project, or Visio, or others, again, you are likely out of luck.

---

### Post by Frogs Hair on 2019-06-19
I don't use MS OneDrive anymore, but when I did I could download my documents from my browser onto my Ubuntu OS. A removable drive would also do the trick which is my preference but, if you have a lot of data it may not be that simple. Before you switch just be sure there are no Windows programs that you need to use regularly. I happen to dual boot , but Virtual Box is an option if you need Windows for anything.

---

### Post by Impavidus on 2019-06-20
Have you got proper backups? Then you won't loose your important files. If not, you'll lose them some day.

As for still being able to access your files, it depends on the format. I mostly use common graphical file formats (.png, .jpg, .pdf) and plain text (.txt, .tex, .c, .ps, .conf, .dat, .this-one-I-made-up-myself, ... etc.). Plain text always works.

---

### Post by jfpolacko on 2019-06-21
Sorry been busy the last couple days!! Anyway's I use Google Drive for my document/photo back up stuff. I haven't used Microsoft Office since Office 2003 lol. So most of my important stuff is Tax information I don't wanna loose. and they are PDF Format!

---

### Post by TheFu on 2019-06-21
> **jfpolacko said:**
> Sorry been busy the last couple days!! Anyway's I use Google Drive for my document/photo back up stuff. I haven't used Microsoft Office since Office 2003 lol. So most of my important stuff is Tax information I don't wanna loose. and they are PDF Format!

PDF has different data file versions, just like other documents.  I've had trouble viewing PDF v1.7 documents this week on Ubuntu.  PDF v1.6 seems to be the last well-supported version of the PDF standard for Linux.  Of course, Adobe has interest in both improving the file format capabilities AND selling new tools to create and read the new format.  I've had the most problems with IRS publications being newer than v1.6 PDF.

[https://www.prepressure.com/pdf/basics/version](https://www.prepressure.com/pdf/basics/version) has some info on PDF file versions.  v2.0 was released 2 yrs ago, so that sort of .pdf will probably happen more and more to us, making PDF less and less useful for Linux users not paying to use commercial tools.


IMHO.

As for easy ways to migrate - just backup your files, then wipe Windows and install the current Ubuntu LTS with the desktop you think you might like.  Check out some youtube videos of the different GUIs to get a feel BEFORE you wipe.  There are about 50 different GUIs, but most people would start with one of these:
[LIST]
[*]Gnome3
[*]KDE
[*]Mate
[*]LXDE
[*]LXQt
[*]XFCE4
[*]Cinnamon
[/LIST]
Gnome3 is the default when you download "Ubuntu Desktop".  It has lots of "cheese" and demands a nice GPU to work well.  KDE has lots of tweak options along with a few variations of the GUI.  

Mate is nice looking, but really cuts back on the GPU requirements.  It can be grouped into the "lighter desktop" list. All the others also fall into the lighter desktop list.  Mate is what I put on relatively new computers for friends. It is simple, fast, works great with the on-CPU graphics from Intel and has a fairly complete point-n-click set of programs to modify system settings.  I used it for a few months just to be sure.  

I'm a little old-school and prefer my CPU to do computing work rather than spend time showing a pretty desktop. For that reason, I've been running openbox for a long time without any DE. Recently returned to a WM from the mid-1990s, fvwm2, to get more control over the environment. It is much lighter than any modern solution and I haven't found anything it can't do that the new programs provide.

Anyway, go find some youtube videos for each of those and watch 2-3 minutes of each.  Always remember, the desktop is just another program and you can swap them out just like you might swap out notepad++ for notepad or other 50 editors.

There is no magic "migration tool" for Windows to Linux.   Copy the files you want to keep off. It is really that simple.

---

### Post by jfpolacko on 2019-06-21
Thanks for the help!!! I was thinking about using Cinnamon or KDE I like the feel of them and my wife won't know much difference ;) but I didn't know about the different PDF versions. 




> **TheFu said:**
> PDF has different data file versions, just like other documents.  I've had trouble viewing PDF v1.7 documents this week on Ubuntu.  PDF v1.6 seems to be the last well-supported version of the PDF standard for Linux.  Of course, Adobe has interest in both improving the file format capabilities AND selling new tools to create and read the new format.  I've had the most problems with IRS publications being newer than v1.6 PDF.

[https://www.prepressure.com/pdf/basics/version](https://www.prepressure.com/pdf/basics/version) has some info on PDF file versions.  v2.0 was released 2 yrs ago, so that sort of .pdf will probably happen more and more to us, making PDF less and less useful for Linux users not paying to use commercial tools.


IMHO.

As for easy ways to migrate - just backup your files, then wipe Windows and install the current Ubuntu LTS with the desktop you think you might like.  Check out some youtube videos of the different GUIs to get a feel BEFORE you wipe.  There are about 50 different GUIs, but most people would start with one of these:
[LIST]
[*]Gnome3 
[*]KDE 
[*]Mate 
[*]LXDE 
[*]LXQt 
[*]XFCE4 
[*]Cinnamon 
[/LIST]
Gnome3 is the default when you download "Ubuntu Desktop".  It has lots of "cheese" and demands a nice GPU to work well.  KDE has lots of tweak options along with a few variations of the GUI.  

Mate is nice looking, but really cuts back on the GPU requirements.  It can be grouped into the "lighter desktop" list. All the others also fall into the lighter desktop list.

Anyway, go find time youtube videos for each of those and watch 2-3 minutes of each.  Always remember, the desktop is just another program and you can swap them out just like you might swap out notepad++ for notepad or other 50 editors.

There is no magic "migration tool" for Windows to Linux.   Copy the files you want to keep off. It is really that simple.

---

### Post by CatKiller on 2019-06-21
> **jfpolacko said:**
> I was thinking about using Cinnamon or KDE I like the feel of them and my wife won't know much difference ;)
I use Cinnamon on my laptop and KDE on my desktop. They're both good to use. I switched to KDE, after using Gnome for years, because of Gnome's twin habits of removing options and making really odd choices for the (now unchangeable) behaviors.

Try a bunch of them out in VMs or live USBs to see which feel comfortable, and to see if you can still access the things you need to. Then make sure everything you want to keep is somewhere other than your computer and dive in.

---

