---
title: "trying to install j2se runtime environment"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by lmellen on 2005-04-15
:-?In the install j2se section of the 5.04 starter guide, I get to step 4:
   "sudo mv jre1.5.0_02/ /usr/java/ -- it tells me it can't overwrite the file
Thje next line:
   "sudo chown -R root:root  /usr/java/jre1.5.0_02/"
I'm told the file does not exist, and I'm sitting here looking at it!!!
2 questions: 
#1) What is going on????
#2) Do I even need to do this, firefox seems to work fine?
                 Thanks -- Larry :)

---

### Post by Bob D. on 2005-04-15
Not sure if I understand correctly, but when you downloaded the Java .bin file, where did you put it? I just ran it from Home, made the /usr/java directory, moved the jre1.5.0_02 directory created by the script to /user/java with the mv command. Followed the rest of the steps and everything was fine and Java is installed and working.

I'd almost think you got ahead of yourself somewhere in the steps, but I'm not sure. And I'm curious when you say "Firefox seems to work fine." You mean items that require Java on certain web pages are working OK?

Bob

---

### Post by lmellen on 2005-04-15
:smile: Thanks for the reply! I think the problem is I'm using Kubuntu, and I think the jre was installed as part of the KDE package. In the "Unofficial Ubunto5.04 Starter Guide this section is for Gnome. I thought it was for Ubuntu & Kubuntu. I probably don't need this guide. Sorry for being pain. ](*,) 
                                                                                        Larry

---

### Post by Bob D. on 2005-04-15
No problem, glad you got it figured out!   :grin: 

Bob

---

