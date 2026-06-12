---
title: "How to delete directory after git clone"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by marcjn on 2011-06-25
[SIZE=2]Hello, [/SIZE]
 
 
 

[SIZE=2]I am quite new to Ubuntu. I have a couple of beginner questions;[/SIZE][LIST=1]
[*][SIZE=2]I have checked out some source code in a directory, not inside the home directory, using:[/SIZE] 
[SIZE=2]```
git clone git://git.videolan.org/ffmpeg.git ffmpeg-git
```[/SIZE]
[SIZE=2]I moved the folder around (was not originally in the right directory), and now would like to delete it and start from scratch. How can I do it without creating issues with git? (I don't see ffmpeg-git in Synaptic)[/SIZE]
 

[*][SIZE=2]More generally, what is the best way to delete old folders related to obsolete or malfunctioning software, or even unsuccessful attempts at installing software ? Can I do 'delete' in the file manager? or just sudo rm <folder name> ? Or is there hidden issues?[/SIZE]
 

[*][SIZE=2]Another related question: When manually installing packages not available in Synaptic, for example, from downloaded tar.gz, what is the recommended directory structure. For example, is it better to use, for example: [/SIZE]
[SIZE=2]/home/<program name>/source to unpack the source code[/SIZE]
[SIZE=2]/home/<program name>/build to build the software?[/SIZE]
[SIZE=2]as opposed to using folders in the root directory? Is there a tutorial on the subject of best practice for directory structure?[/SIZE]
[/LIST][SIZE=2]Thanks[/SIZE]

---

### Post by FakeOutdoorsman on 2011-06-25
> **marcjn said:**
> [*][SIZE=2]I have checked out some source code in a directory, not inside the home directory, using:[/SIZE] 
[SIZE=2]```
git clone git://git.videolan.org/ffmpeg.git ffmpeg-git
```[/SIZE]
[SIZE=2]I moved the folder around (was not originally in the right directory), and now would like to delete it and start from scratch. How can I do it without creating issues with git? (I don't see ffmpeg-git in Synaptic)[/SIZE]
Just delete the ffmpeg-git directory. It won't create issues with Git because each cloned directory contains it's own Git information.

> **marcjn said:**
> [*][SIZE=2]More generally, what is the best way to delete old folders related to obsolete or malfunctioning software, or even unsuccessful attempts at installing software ? Can I do 'delete' in the file manager? or just sudo rm <folder name> ? Or is there hidden issues?[/SIZE]
It depends on how you installed or attempted to install the compiled software. If you simply used *sudo make install*, then you should keep the directory until you want to remove the software. Once you are ready to uninstall it run *sudo make uninstall*, and then you can delete the directory either in the file manager or with *rm*.

If you used *checkinstall* or another method to integrate the software into the package management system, then you can delete the source directory whenever you want because Synaptic/apt/aptitude will know where all of the installed files are.

> **marcjn said:**
> [*][SIZE=2]Another related question: When manually installing packages not available in Synaptic, for example, from downloaded tar.gz, what is the recommended directory structure. For example, is it better to use, for example: [/SIZE]
[SIZE=2]/home/<program name>/source to unpack the source code[/SIZE]
[SIZE=2]/home/<program name>/build to build the software?[/SIZE]
[SIZE=2]as opposed to using folders in the root directory? Is there a tutorial on the subject of best practice for directory structure?[/SIZE]
[/LIST][SIZE=2]Thanks[/SIZE]
I don't think there are any rules for this. Just do whatever is comfortable to you. For example, on one distro I place them in a build directory such as:
```
~/builds/<program name>
```
...but on another one (a virtual machine just for testing) I simply use:
```
~/<program name>
```
Note that ~ is the equivalent of the user's home directory, such as */home/marcjn*.

---

### Post by marcjn on 2011-06-27
FakeOutdoorsman, 
 
Many thanks for the very clear and concise guidelines. It has really helped me.

---

