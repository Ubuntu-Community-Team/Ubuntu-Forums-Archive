---
title: "Uninstalling Ubuntu"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by jisjames007 on 2010-09-07
I recently installed Ubuntu 9.04 in my computer. I used the second option which says to install Ubuntu inside windows.
Now I want to uninstall Ubuntu because my parents do not want to use it and I am sharing my computer with them. I did not know how to uninstall it so I did some research and found some very complicated method saying that I need to insert my Windows xp disk and reinstall it etc. So I asked this same question in yahoo answers and got an answer which said that: all i had to do was to go to control panel > add/remove programs> select Ubuntu> uninstall it. I did that and Ubuntu has gone from my add/remove programs list. But when I restarted my computer i still am asked to choose my OS from the boot screen. Now I want know why this happened? and how can I get rid of this problem so that when I turn on my computer I won't be asked to chose my OS. When I used Ubuntu it asked me install some updates and i installed some of them. is this why i am still being asked to chose my OS? please help me solve this I really need to stop this problem. Pls give me detailed step by step instructions.
[IMG]http://3.bp.blogspot.com/_MTYaEhS937o/TIaCEsEzQwI/AAAAAAAAAQ8/8-Bq6vJH1JA/s1600/4654646.JPG[/IMG]

---

### Post by B_rebel on 2010-09-07
Very easy. First you have to enable all hide file to show include system utilities. After that you'll found a boot.ini in your system drive (ex: C:\)
open it. there will be secondary os as your linux-ubuntu just remove from it.

---

### Post by Rasa1111 on 2010-09-07
If you are sharing *your* computer with them,
and they dont want to use Ubuntu, 
why can't they just choose "windows" at startup? 
It's your computer but you can't have on it what you'd like? 

dang. :(

---

### Post by jisjames007 on 2010-09-07
Ok so I went to my computer> C> and found the boot.ini 
[IMG]http://4.bp.blogspot.com/_MTYaEhS937o/TIaLICM-7PI/AAAAAAAAARA/YrvLrBIbPFI/s1600/sdffsdfsdfsfsd.bmp[/IMG]
I clicked on it and it opens up a text editor and do just erase the text highlighted in this image?
[IMG]http://3.bp.blogspot.com/_MTYaEhS937o/TIaLgC57wNI/AAAAAAAAARE/ZccYZ5QBMbQ/s1600/16549876452.bmp[/IMG]

---

### Post by garvinrick4 on 2010-09-07
It was a WUBI install. There will be a folder right next to USERS in C: drive click on Wubi folder and click uninstall. Will remove wubildr from the windows bootmanager if you uninstall this way. Can use ADD and Remove programs in Windows also but very seldom
does not remove wubildr from Windows boot manager, very seldom. So use either way.
First way is cleaner.

Sorry just reread your problem and you have wubildr left in windows boot manager to remove. Will have an extra entry that has wubildr in it.
Remove it and problem solved.  I just googled remove wubildr form xp boot manager and lots of links.

---

### Post by jisjames007 on 2010-09-07
I do not see a USERS folder in C. Went into Docs and Settings and saw All Users but could not find the WUBI folder. Also did a desktop search for WUBI folder and did not give any results. So can I delete that text in the text editor? or is there any other way? pls help...

---

### Post by garvinrick4 on 2010-09-07
> **jisjames007 said:**
> I do not see a USERS folder in C. Went into Docs and Settings and saw All Users but could not find the WUBI folder. Also did a desktop search for WUBI folder and did not give any results. So can I delete that text in the text editor? or is there any other way? pls help... Looks like WUBI is gone but left behind its wubildr in the XP boot manager. If you Google: "remove wubildr from XP boot manager"
it will give you a lot of links on how to do it. I know how to do it in Vista and 7 off the top
of my head but not XP. But there are plenty of articles in googling it that will tell you.
There are ones there that tell you how to just bypass it and go straight to Windows install.

---

### Post by jisjames007 on 2010-09-07
Ok i will try that, but i do not want to re install xp and loose all my data...i will try it if it does not tell me to reinstall xp...

---

### Post by Elfy on 2010-09-07
From the wubi wiki page it seems fairly easy to do 
> 
_In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line._ For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via Control Panel > System > Advanced > Startup and Recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys and remove the Wubi block.

---

### Post by jisjames007 on 2010-09-07
ok found it in [here]("http://webcache.googleusercontent.com/search?q=cache:1L4_Nb852vUJ:https://wiki.ubuntu.com/WubiGuide+remove+wubildr+from+XP+boot+manager&cd=2&hl=en&ct=clnk&gl=us"), now i see that it says in the partition value 1 how do i make that 0 do i just change it and save it? Pls help.
I have highlighted the partition text in green:
[IMG]http://1.bp.blogspot.com/_MTYaEhS937o/TIaUjFjx1zI/AAAAAAAAARI/LfQpEo_qBPk/s1600/16549876452.bmp[/IMG]

---

### Post by Elfy on 2010-09-07
I'd not start messing with partitions unless you are completely sure.

---

### Post by jisjames007 on 2010-09-07
I tried to erase that line f text and does not allow me to save it. what do i do?[IMG]http://2.bp.blogspot.com/_MTYaEhS937o/TIaWJOpSVXI/AAAAAAAAARM/HLn8bv-ZXF0/s1600/untitled.bmp[/IMG]

---

### Post by jisjames007 on 2010-09-07
ok i shall not do any thing with the partitions. but if ubuntu is uninstalled what will happen with the 5GB i partitioned for it?

---

### Post by Elfy on 2010-09-07
Try opening the file in msconfig - if that is what it's called ...

---

### Post by jisjames007 on 2010-09-07
ok I can see the file in msconfig what do i do next 
[IMG]http://1.bp.blogspot.com/_MTYaEhS937o/TIabCBTS5EI/AAAAAAAAARQ/Y5clW6Bdid8/s1600/untitled.bmp[/IMG]

---

### Post by Elfy on 2010-09-07
Sorry - thought you could delete it in there - my windows support is all from memory.

If you can't do it from there then you'll have to do it with notepad - I assume that you have an admin account.

Maybe check all boot paths might help ... [http://windowsxp.mvps.org/bootopt.htm](http://windowsxp.mvps.org/bootopt.htm) would suggest so.

---

### Post by jisjames007 on 2010-09-07
Thank You soooooooooooooooo much!!!!!!! it was a life saver..... this what I did: went to my computer>right click>Properties>Advanced>Start up and Recovery click settings>Under system start up> edit> and then I was able to delete the text line and save it. 
I restarted it and it went directly into Wndows XP.
Now i have doubt about the 5Gb i partitioned for Ubuntu...will that 5GB automatically merge with windows xp? thank you all for the support...

---

