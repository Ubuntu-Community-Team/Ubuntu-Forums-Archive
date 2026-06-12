---
title: "Installing Eclipse 3.3"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by framebuffer on 2007-10-02
Hello!

I am new to Linux and I wanted to give eclipse 3.3 + CDT4 a try. I have read most of the posts on this topic but they either didn't work or failed for some reason or another.

For example, on the following thread:

[http://ubuntuforums.org/showthread.php?t=544032&highlight=eclipse+3.3](http://ubuntuforums.org/showthread.php?t=544032&highlight=eclipse+3.3)

After giving the following command:

sudo apt-get install sun-java6-jdk

Java displays a license agreement and I had no clue how to accept it. I tried clicking on OK, I tried hitting enter...It just wouldn't go.

I tried to get it from synaptic but it has 3.2 and not 3.3

I downloaded eclipse-cpp-europa-fall-linux-gtk.tar.gz from eclipse's website, but don't know what to do with it.

I tried to dump in in my home and tried to run the "eclipse" file it contains but it wont do.

Can anyone please guide me in the right direction or point me to a resource that shows how to install eclipse 3.3. Its really frustrating since installing it on windows is a 10 minutes process. :confused:

I tried searching the eclipse website but found none.

Thanks,
fb.

---

### Post by fvbakel on 2007-10-02
Hi,

> I tried to get it from synaptic but it has 3.2 and not 3.3

Eclipse 3.3 is not in the ubuntu repositories yet. The work is in progress see:
[https://bugs.launchpad.net/debian/+source/eclipse/+bug/123064](https://bugs.launchpad.net/debian/+source/eclipse/+bug/123064)

That is why you can not get it with synaptic yet. 

> sudo apt-get install sun-java6-jdk

Java displays a license agreement and I had no clue how to accept it. I tried clicking on OK, I tried hitting enter...It just wouldn't go.

I think you have to type: yes

> I downloaded eclipse-cpp-europa-fall-linux-gtk.tar.gz from eclipse's website, but don't know what to do with it.
You can try the instructions on this page. The instructions are for a previous eclipse version but the remarks at the bottom give hope for the eclipse 3.3 users
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

I will try to install this eclipse 3.3. on my 7.04 installation later this week.

> Its really frustrating since installing it on windows is a 10 minutes process.

Do not give up. You are just going through a learning curve. 

Hope you have some directions now.

---

### Post by framebuffer on 2007-10-02
Hi!

Thanks for the info. Just compiled my "Good Bye Visual Studio!" program :)

Eclipse rocks! :guitar:

CDT 4 has some really neat features built in....

But now there is a new problem...the content assist (ctrl+space) is not working. Looking for a solution.

It works from the right lick menu, but not from the keyboard.

But thanks for your help!

---

### Post by fvbakel on 2007-10-03
Eclipse is indeed great! Would would we have to do without?

I have no idea about this ctrl + space problem. For me this working in eclipse 3.2 but instead the ctrl + F11 is not working.

---

### Post by scawa on 2007-10-13
Ok have you been successful in installing Eclipse 3.3 on Ubuntu.

I've been beating my head against the wall, because I'm having to work with several operating systems for work.... Vista, XP, Ubuntu Linux and the AS/400.....   I need some kind of walk through to successfully install it.

Thanks for the help in advance.


Stephen McConnell

---

### Post by scawa on 2007-10-14
Ok...  Just wanted to post that in a fit of impatience,  I figured out how to do this.

The instructions that **fvbakel** provided worked like a champ so far for Eclipse 3.3.  Since I am the only  person on this workstation, I installed Eclipse 3.3 under my personal directory as described in:

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

I also use the MyEclipse plugin for Web development and AJAX development.  I did a manual install as described in their manual install Linux MyEclipse plugin and I now have my Web development and AJAX development setup going.  The next step is to get Apache/Tomcat and JBoss up and running and then Postgresql...   

Very nice...  

Keep on trucking with Ubuntu/Kbuntyu

---

### Post by Iztok on 2008-02-08
I am still not able to get beyond installing the JDK.  The install shows the lawyer speak but I can't get by this.  My terminal may be the problem since it seems unresponsive to keyboard events although the mouse wheel lets me scroll through the copyrights.

Did anyone else have this problem and get around it?

Thanks,
Iztok

---

### Post by justifiedandancient on 2008-02-21
Well I rather rashly attempted to get Eclipse to update itself having installed the Ubuntu package a while ago. That didn't make it all that well, it never ran again and I even dropped the package and reinstalled it with no change. Anyway, that drove me to find out about version 3.3 which I installed from the previously quoted europa-fall2 tarball. I unpacked it under my home directory and updated the menu entry to point at that. Having checked that it was using the right JVM it all fired up and worked for me. I also re-installed subclipse into it. I didn't have to do anything with the JVM as the required 1.6 sun version was already installed (I have Ubuntu gutsy which has been KDE'd)

---

### Post by razorxpress on 2008-06-12
There are many methods of installing Eclipse 3.3 on ubuntu. The main headache is installing jdk. Which you can do by typing on a terminal
sudo apt-get install sun-java6-jdk

sudo update-java-alternatives -s java-6-sun

Next, edit the JVM configuration file

sudo -b gedit /etc/jvm

and add the following to the top of the file

/usr/lib/jvm/java-6-sun

Now download eclipse 3.3 froe eclipse.org and unzip it and copy to any directory. The locations i prefer are /etc/eclipse or /opt/eclipse. Copy the unzipped directory to /etc/ or /opt.

Now configuration for /opt/eclipse. Same for /etc/eclipse. Just adjust path

sudo -b gedit /opt/eclipse/java_home

and add

/usr/lib/jvm/java-6-sun

to the top of the file.

If you have lot's of memory adjust 
sudo -b gedit /opt/eclipse/eclipse.ini
The argument Xms refers to the minimum heap size and Xmx refers to the maximum heap size.

adjust them as your memory

Cheers

---

### Post by Kalrog on 2008-06-12
What about those of us who installed Eclipse using Adept on the latest version of KUbuntu?  Where is the launcher or how do I get Eclipse to run?

---

