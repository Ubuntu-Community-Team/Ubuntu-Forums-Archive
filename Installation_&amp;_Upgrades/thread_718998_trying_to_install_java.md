---
title: "trying to install java"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by christabel3000 on 2008-03-08
I'm trying to install java and I get this...

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

I'm really REALLY new at this..
could someone explain to me step by step what I need to do

Please and Thanks

Chris

---

### Post by taurus on 2008-03-08
Are you trying to use a GUI text editor, gedit, to open a java file that you've downloaded?

If you need to install java, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by christabel3000 on 2008-03-08
This is the file I downloaded from Java...

jre-6u5-linux-i586-rpm.bin

Do I have to change anything?
I tried opening a terminal and typing what you said
but then I got this response

E: Couldn't find package java-version

So then I changed your formula a bit and instead of typing "java" I typed "6u5" and got this response

E: Couldn't find package sun-6u5-version

More help please...

---

### Post by Alnird on 2008-03-09
I had the exact same problem, and I brought up the terminal and wrote what taurus said, and it works perfectly, I think :P Now I'm just gonna see if I can install Azuerus from the file I have :lolflag:

Ok, I could install it, but it wont start properly.. Maybe I should make my own thread :P

---

