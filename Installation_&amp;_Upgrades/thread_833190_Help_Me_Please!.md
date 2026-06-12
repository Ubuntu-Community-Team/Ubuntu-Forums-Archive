---
title: "Help Me Please?!"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by justjohn924 on 2008-06-18
Ok so i'm attempting to download and use a theme from gnome-look.org 
when i read the instructions they say to................
1. Open a terminal

2. cd to the directory the script is in.

3. type "chmod +x INSTALL" without quotes

4. type "sh INSTALL" without quotes

5. Follow instructions once it is finished.

but i don't know how to "cd to the directory the script is in"

Someone PLEASE help me!

---

### Post by JWL610 on 2008-06-18
What is  the name on  folder ? 

if you unpack it to 
/home/you name/gnoom-lock"if this is name on the folder" 
than you use chmod and than sh install. 

understand ?

---

### Post by justjohn924 on 2008-06-18
it's a vista theme.
here's the link
[http://gnome-look.org/content/show.php/Complete+Vista+Aero+theme+(automated)?content=72318](http://gnome-look.org/content/show.php/Complete+Vista+Aero+theme+(automated)?content=72318)

not sure what to do with it never had a .sh file before

---

### Post by Victormd on 2008-06-18
cd is change directory so if your folder is on your desktop, from the terminal window type:
```
cd ~/Desktop/FOLDERNAME
```

You can use the TAB key to autocomplete the folder name. Also, it is case sensitive so desktop is different from Desktop.
The ~/ indicates that it is located in you home folder (similar to going to places>home folder)

---

### Post by justjohn924 on 2008-06-18
this errore

---

### Post by justjohn924 on 2008-06-18
sorry i mean this one

tannerandjohn@tannerandjohn-desktop:~/Desktop/vista-aero-theme-automated.v2.2$ chmod +x INSTALL
tannerandjohn@tannerandjohn-desktop:~/Desktop/vista-aero-theme-automated.v2.2$ sh INSTALL
: not found 


Make sure this script is being run by root or sudo


: not found: ot or sudo? [y/n] --->
y
: bad variable name
: not found: 
INSTALL: 156: Syntax error: end of file unexpected (expecting "fi")
tannerandjohn@tannerandjohn-desktop:~/Desktop/vista-aero-theme-automated.v2.2$

---

### Post by Victormd on 2008-06-18
well, you'll have to
```
cd ~/Desktop/vista-aero-theme-automated.v2.2
```
then
```
sudo chmod +x INSTALL
```
here it will ask for a password. as you type, nothing will show on the screen, but it's working... hehe
then
```
sudo sh install
```
Note: anytime you need root privilege, use the **sudo** command.

---

### Post by justjohn924 on 2008-06-18
did that stupid thing keeps giving me the same error

whatevs guess it's just not meant to be

---

### Post by Victormd on 2008-06-18
after you go to the directory where you downloaded the theme, if you type
```
ls
```
do you see the file "install"?
again, keep in mind that everything in linux is case sensitive so INSTALL is different from install.

---

### Post by justjohn924 on 2008-06-18
yes i see the file

---

### Post by Victormd on 2008-06-18
is it all CAPS?

---

### Post by justjohn924 on 2008-06-18
and it's "INSTALL" btw

---

### Post by Victormd on 2008-06-18
If you can wait until later tonight, I can check it for you. Right now I'm at my office but when I get home I can try to install and let you know. Based on what you told me, there's no reason why it shouldn't be installing.

---

### Post by Victormd on 2008-06-18
I was just looking at the error message again and it looks like there might be something wrong with the script. it asks you a **y/n** question and when you answer **y**it returned a **bad variable name**... that looks like a script error but I would have to look at the script to be sure.
> : not found: ot or sudo? [y/n] --->
y
: bad variable name
: not found:
INSTALL: 156: Syntax error: end of file unexpected (expecting "fi")

---

### Post by justjohn924 on 2008-06-18
i'm pretty sure it is script error but i'm not sure how to fix that

---

### Post by Victormd on 2008-06-18
Ok, so I've modified the script a little bit but will have to leave now. To run it, you'll need to use:
```
chmod +x INSTALL
```
```
gksu sh INSTALL
```
Simply replace the original with this one and give it a go. Here it worked up to the last step but I don't have time to fix it right now, but you should get the basic vista look.

It will give you some errors towards the end. If you'd like, you can open the INSTALL file and look at the script, I think it's only 1 or 2 steps that are messed up, but you can follow the terminal output and the script to manually finish the install, or wait a bit more so that I can have a closer look at it... :)

---

### Post by Victormd on 2008-06-18
Assuming you have emerald, go to SYSTEM>PREFERENCES>EMERALD THEME MANAGER and click on the IMPORT icon, browse to the folder you extracted the theme and go to vista>emerald-theme. There you'll see 2 files:
1. aero_blue.emerald
2. subvista.emerald
Select one, repeat the import process and select the other. Now you'll have to window decorations to choose from.

For the remainder of the theme, better e-mail the author of the script. I don't want to get in trouble by messing with his script. Plus, the author asks to be notified if the script doesn't work... and it doesn't... :)

Edit: I removed the attached script from the previous post, sorry.

---

### Post by Nero147 on 2008-06-19
have you try going into the directory and then put in.
sudo ./INSTALL or
sudo .\INSTALL

---

### Post by Felix-the-Cat on 2010-04-19
I would suggest that you take another look at this automated script that you are having trouble with. There were some major changes made this year that make installing much much easier and there were a lot of bugs fixed. You can still get to it from gnome-look but it is not being hosted on Google code here [http://code.google.com/p/gnome-vista-aero-theme-automated/](http://code.google.com/p/gnome-vista-aero-theme-automated/)

---

### Post by roynoblin on 2010-04-19
right click the install file and check properties. this is a way to verify the path and how it is named

---

