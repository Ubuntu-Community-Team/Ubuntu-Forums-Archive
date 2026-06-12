---
title: "jEdit install problems"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by ax4413 on 2007-04-09
I have installed jEdit on my edgy Ubuntu box and unfortunately for me it does not work. On reading their documentation found at: [[COLOR="Blue"]http://www.jedit.org/index.php?page=compatibility#unix[/COLOR]]("http://www.jedit.org/index.php?page=compatibility#unix") 
It appears that I need to set my JAVA_HOME PATH. I am a Linux newbie and  I have no idea how to do that. I have searched far and  wide but cant find a definitive way to achieve this or much in the way of help. 

All help will be welcomed :confused:  

Cheers in advance

Steve

---

### Post by ax4413 on 2007-04-11
Hi just thought that id post again and try to generate a bit more interest for helping me...

steve

---

### Post by ax4413 on 2007-04-12
Problem solved... :D :D :D 
Cheers for all the views and if any one else  is stuck with the same problem, here is the solution that worked for my system. Type into a console the following code, that is the bold black text the colored text is the response from the console.

**which java**
[COLOR="DarkOrange"]/usr/bin/java[/COLOR]
**java -version**
[COLOR="DarkOrange"]java version "1.4.2-02"[/COLOR]
[B]export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08
export PATH=$JAVA_HOME/bin:$PATH
which java[/B]
[COLOR="DarkOrange"]/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/bin/java[/COLOR]
**java -version**
[COLOR="DarkOrange"]java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)[/COLOR]
**jedit &**

In order to get this to work for you you may need to change the export JAVA_HOME path to some thing that suits your system

#####################################################

Actually this only works the once when you run the code. So what i have had to do is create an executable text file to launch jEdit. Not the tidiest of solutions but it works. I know that there must be a script file some where that i could just edit but i cant find the right one.

Cheers anyway thats me signing out

---

