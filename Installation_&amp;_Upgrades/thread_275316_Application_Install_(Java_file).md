---
title: "Application Install (Java file)"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by ricanelite on 2006-10-11
Okay, I have some what of a situation, I will like to know if I can install a file for my job that I use on a everyday bases on Linux. The file name is **main.jnlp**. Bascially it is a Java file. Now my main question is I'm pretty sure I can't just double click it on it and there it will open. So what I have done is I installed and configured Wine. 

Now my main question is does anyone know how will I be about going to install this file **main.jnlp** or will I have to use Wine?

Thank you for reading, Hope you could help me out. Because being I have been using Ubuntu Linux alot right now. I'm really hopeing if I could run this Application which is very important because I need to use it in a ever day basis, and if it could run that will be awesome!!

Thank you again!!!

---

### Post by taurus on 2006-10-11
If it is a java file, then just install either Blackdown or Sun's java and run it directly from Linux.  No need to install wine or any other emulator!

---

### Post by ricanelite on 2006-10-11
How will I go about that and getting it installed and runned.

Also what is Blackdown?

---

### Post by ricanelite on 2006-10-11
Okay, I got it installed, but now when the Application starts it just goes away and does not open up in a window?

What did I do wrong?

---

### Post by taurus on 2006-10-11
Try to run it from a terminal so you can see what the error message is, Applications -> Accessories -> Terminal.

```
java <filename>
```

---

### Post by ricanelite on 2006-10-11
The error message is this

**Exception in thread "main" java.lang.NoClassDefFoundError : main/jnlp**

---

### Post by ThrobbingBrain66 on 2007-04-15
I realize this thread is very old, but I have a solution to the problem, so it may help others who have this same issue.

.jnlp are Web Start Apps, which I believe means you have to run them through a Web Browser.  In Firefox (or any browser) go to File > Open File and navigate to your jnlp file.  Select it and click open.  Then follow the on-screen prompts and your file will run.

---

### Post by enthusaroo on 2007-04-28
> **ThrobbingBrain66 said:**
> I realize this thread is very old, but I have a solution to the problem, so it may help others who have this same issue.

.jnlp are Web Start Apps, which I believe means you have to run them through a Web Browser.  In Firefox (or any browser) go to File > Open File and navigate to your jnlp file.  Select it and click open.  Then follow the on-screen prompts and your file will run.

Unfortunately, I'm having the exact same problem as the original poster. In fact, we are both trying to open the same file (main.jnlp). He must be a ChaCha search guide too. hehe

ThrobbingBrain66: Thank you for posting. I tried your solution opening the file with Firefox, unfortunately when I attempt to open the file it just gives me the option to open it with Document Viewer which doesn't work. :(

---

### Post by thomma on 2007-05-09
You have to use Java Web Start
```
javaws file.jnlp
```

---

### Post by enthusaroo on 2007-05-09
Hey thomma

> **thomma said:**
> You have to use Java Web Start
```
javaws file.jnlp
```

Thank you for your reply. I was really hopeful when I read your reply, because it's been a week since my original post and I really need to get this program to work. I'm still having no luck. 

Unfortunately, when I try ```
javaws main.jnlp
``` it gives the following error message under Java:
```
An error occurred while launching/running the application.

Title:  ChaCha Guide Application 
Vendor: ChaCha Search, Inc.
Category: Launch File Error

Unsupported JNLP version in launch file: 1.5+. Only version 1.0 is supported with this version. Please contact the application vendor to report this problem.
```

Any idea what I need to do to get it to work? Maybe I have the wrong version of Sun Java or something? I don't understand what the error means.

---

### Post by djhbrown on 2007-05-13
> **ThrobbingBrain66 said:**
> I realize this thread is very old, but I have a solution to the problem, so it may help others who have this same issue.

.jnlp are Web Start Apps, which I believe means you have to run them through a Web Browser.  In Firefox (or any browser) go to File > Open File and navigate to your jnlp file.  Select it and click open.  Then follow the on-screen prompts and your file will run.

i dont know ho this worked for you, but when i follow your suggestion i get into a loop where it asks me "do you want open this file in firefox?" and the it opens a new tab and says "do you want open this file in firefox?" and so on and so on.

hopefuly there's an ubuntu master out there who will notice our plight and come to the rescue.  to bad i dont enough enough to type in a url for an ubuntu bug report - its a usability bug but i guess not a functionality one as there would ziilions of people asking in that case.  what do they know that we don't (apart from anything!)

---

### Post by djhbrown on 2007-05-13
> **taurus said:**
> Try to run it from a terminal so you can see what the error message is, Applications -> Accessories -> Terminal.

```
java <filename>
```

i followed all the sun instructionsto install jre, then tried your suggestion.

this is what i get:

root@a-desktop:~# java cgoban.jnlp
Exception in thread "main" java.lang.NoClassDefFoundError: cgoban.jnlp
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: cgoban.jnlp not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)
root@a-desktop:~#

---

### Post by peas on my plate on 2007-09-05
I've run into the same problem, but with uide.jnlp (for family search indexing).  I realize this is an old problem, but I've got it running now so I'll post what I did.

Opened a terminal and typed>  java -version to see what version of java I had installed.  It turns out I only had the 1.4.2 version, so I updated to Java J2SE as per the ubuntu wiki:

> sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts

My uide.jnlp is saved to my desktop, so I changed directory and then ran javaws:

> cd Desktop
javaws uide.jnlp

It ran perfectly from there

Hope that helps!

---

### Post by iffbiff on 2007-09-06
I have the same problem with the FamilySearchIndexing application.  I haven't been able to find the jnlp program that you have mentioned.  Where can I find it?  A search on the web is unhelpful.  It only brings up this very page.  To be clear I am not running Ubuntu (Vista) and I found this page in an attempt to figure out why the app was dying.  Any help is *greatly* appreciated.

---

### Post by peas on my plate on 2007-09-06
Hi, I got your message.  I actually don't use Vista at all, so I'm not sure how much help I can be, but I will try.:)

jnlp is a file that javaws (java Web Start) uses to launch.  So you will need both Java SE Runtime Enviornment 6 Update 1 *and* the .jnlp file that you download from Familysearch.org.  From the error message you got it looks like something is wrong with the family search jnlp file.

I tried to replicate your problem on my windows xp machine, but couldn't get it.  About all I can suggest at this point is going to Add/Remove programs, wait for the list to populate and then first check to see if you have the current Java package installed.  You should, both Internet Explorer and Firefox update automatically.  Then find the Family Search Indexing Program and Remove it.  You may have to restart your computer at this point, windows seems to like that.:)

Then go back to familysearch.org and download an install the program again.  You'll loose any indexing you haven't already submitted online yet, but the program *should *work again.

I hope that works!

---

### Post by Pikestaff on 2007-10-23
> **peas on my plate said:**
> I've run into the same problem, but with uide.jnlp (for family search indexing).  I realize this is an old problem, but I've got it running now so I'll post what I did.

Opened a terminal and typed to see what version of java I had installed.  It turns out I only had the 1.4.2 version, so I updated to Java J2SE as per the ubuntu wiki:



My uide.jnlp is saved to my desktop, so I changed directory and then ran javaws:



It ran perfectly from there

Hope that helps!

Thank you for this!  I've been trying to run the Family Search Indexing as well, mostly unsuccessfully, but this worked!!

Although, for me it was **iude.jnlp**, as opposed to uide.jnlp as you said ;)  Just in case anybody else sits there for a while wondering why the directions don't work exactly, double check your file name! :)

---

