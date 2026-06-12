---
title: "Java Help"
date: 2006-05-04
forum: Installation &amp; Upgrades
---

### Post by sonis on 2006-05-04
Still Need Help
Look At Later Posts For Details

I Am Trying To Install Java
I Have Currently "jre-1_5_0_06-linux-i586.bin" From Sun
When I Try To Open, I Get This Error....
[img]http://img52.imageshack.us/img52/5616/screenshot9dp.gif[/img]
Someone Tell Me The Correct Code Please

---

### Post by Sef on 2006-05-04
you misspelled apt-get.  You used a g instead of an a.

sudo apt-get install  (package name)

I have done the same thing, so feel too dumb about it.

---

### Post by Gannin on 2006-05-04
Right-click on the jre icon on your desktop, and select Properties.  Then go to the Permissions tab.  Check the Execute box on the Owner line, then click on Close.

Open your terminal, and then type &#8220;cd Desktop&#8221; and hit enter.  Then type &#8220;sudo ./jre-1_5_0_06-linux-i586.bin&#8221; and then hit enter.

It will ask you for a password.  Type in the same password that you use to login to your computer account with.

---

### Post by yager on 2006-05-04
From the screen shot though, he has the the bin file on his desktop.  You should be able to
```
cd Desktop
sudo chmod +x JRE(complete the file name here)
sudo JRE(complete file name here)
```

---

### Post by sonis on 2006-05-04
I Still Have A Problem :(
[Img]http://img204.imageshack.us/img204/6799/screenshot7qa.gif[/img]
[img]http://img348.imageshack.us/img348/5127/screenshot1av.gif[/img]

Thanks For Getting Me This Far :)
But I Still Need Help

I Have Installed The Java,
How Do I Affect This For The FireFox Program?

---

### Post by Sef on 2006-05-04
To get java installed, read this wiki.  Java is at the bottom.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by Gannin on 2006-05-05
To make sure Java is installed properly, from your terminal type &#8220;java -version&#8221; and see if it gives you the version information.

---

