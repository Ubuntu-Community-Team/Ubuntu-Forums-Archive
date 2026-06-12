---
title: "Running .sh File - Ultra Noob question"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by kyral210 on 2010-12-17
Afternoon all
 
I am relly sorry this is such a basic question, but I am ultra new to Linux and have been using Windows all my life.
 
I need to execute and run a .sh file for work, and I have NO IDEA how to do it. All I have been told is:
 
[FONT=Calibri]./convert_blom_to_telefot.sh <test_dir>[/FONT]

[FONT=Calibri]What does that mean? I am guessing it is in the Ubuntu termninal, but I have no idea what to do with it.[/FONT]

[FONT=Calibri]Please please help me as I am completely lost and over my head in this one.[/FONT]


[FONT=Calibri]Chris[/FONT]

---

### Post by cchhrriiss121212 on 2010-12-17
Place the .sh file in you home folder, then open up a terminal from the accessories menu.
First make sure you have permission to run the file:
```
sudo chmod 755 yourfilename
```
The terminal has an auto complete function with the tab button, so just type the first letter of your file and press tab to save time.
Then this:
```
./yourfilename
```
Again you should be able to use tab to autocomplete.

---

### Post by kyral210 on 2010-12-17
Sorry to be ULTRA stupid here, but what is the Home folder?

---

### Post by cchhrriiss121212 on 2010-12-17
The home folder is where all your personal documents and settings are stored it has folders like documents, music, video etc.. To access it go to: Places>Home folder.

---

### Post by kyral210 on 2010-12-23
Ok, I did that, but im still stuck

I got 
> [sudo] password for lds: 
and when I tried putting my admin password in, nothing happened, no writing in the terminal or anything

So I press enter and I get this:
> lds@lds-TECRA-M10:~$ 

So what so I do now? What am I meant to see or what is meant to happen? I am very very lost here...

---

### Post by kyral210 on 2011-07-23
Thanks for the help here guys. I have since started using Ubuntu a lot and even built a server!

---

