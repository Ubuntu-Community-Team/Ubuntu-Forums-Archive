---
title: "Upgraded, and BlueJ stops working"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by efang95 on 2012-05-08
I did a fresh install to upgrade my computer to 12.04. I tried installing BlueJ again through the website, and it "installed" without errors, but whenever I click on the icon, it doesn't open. There are no Error messages either. Help!?

---

### Post by critin on 2012-05-08
You're certain you have the correct version of java and it's (java) installed properly?

---

### Post by efang95 on 2012-05-08
I'm pretty sure. I downloaded OpendJDK 7 and 6 also got sun-java6

---

### Post by bspymaster on 2012-05-08
I have been having the same problem. Not sure what is wrong with it. I've tried reinstalling it and made sure I had openjdk-6-jdk (which bulej.org recommends) and for some reason it doesn't work.

---

### Post by critin on 2012-05-09
I suggest you go to BlueJ's help forum and see if they can help.  If it turns out to be an ubuntu issue, you'll find out.  It will save you some time.

[http://www.bluej.org/help/help.html](http://www.bluej.org/help/help.html)

---

### Post by critin on 2012-05-09
I found this post, it's old but might help.

[http://ubuntuforums.org/showthread.php?t=1063425&highlight=blueJ](http://ubuntuforums.org/showthread.php?t=1063425&highlight=blueJ)

---

### Post by efang95 on 2012-05-20
Nope, it still doesn't work. I don't know what's going on, instead I downloaded netbeans, but i miss the UML diagrams from bluej

---

### Post by cct on 2012-07-17
> **efang95 said:**
> Nope, it still doesn't work. I don't know what's going on, instead I downloaded netbeans, but i miss the UML diagrams from bluej

I downloaded the .deb file from the BlueJ site, and double-clicked it to install. Since this Debian installation file is expecting version 6, I needed to tweak it a bit after the installation so it can launch nicely from the DashHome. I installed an application called "Main Menu" with the "Ubuntu Software Center." 

Launch "Main Menu" and select Applications->Programming->BlueJ and click the Properties button. In the Command: box type:

java -jar /usr/share/bluej/bluej.jar

If you used the BlueJ unix installation, it might have put bluej.jar someplace else, like your home directory. In Main Menu, just add an Application and make the command to launch refer to the bluej.jar wherever it lives. For example, if it is in your Downloads folder:

java -jar /home/your-login-here/Downloads/bluej.jar

---

