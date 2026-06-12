---
title: "Install IE in Ubuntu"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by Shun on 2005-10-03
Hi, 
   
   I had already download the IE and install into my PC. It cannot work well when i browse some website. For example, when i open a website then in the log in process is progressing, it suddenly close the browser. Beside of this problem, another problem that i face is when i want to browse the yahoo or google website, it loading is damn slow and the wont come out. Do anyone face this same problem after installed the IE in ubuntu? Is it i make any mistake when i install the IE? Pls advise. Thank you!

---

### Post by Mustard on 2005-10-03
What software are you using to run IE on Ubuntu?

---

### Post by Shun on 2005-10-03
I using the wine to operate with my IE.

---

### Post by Juzz on 2005-10-03
What is the reason you have to use IE?

Is it possible to use either Firefox or Opera (now free of ads).

---

### Post by Mustard on 2005-10-03
I believe IE is a pre-requisite install for the wine package, Juzz. It could be for browsing pages that are not Firefox friendly aka configured for IE.

---

### Post by Mustard on 2005-10-03
I would think most of the knowledge about wine and it's intricacies would be in the gaming sections of this forum.  They seem to be pretty fluent in things to do with wine.

---

### Post by Shun on 2005-10-03
Juzz,

   I wanna test something in IE. When i testing in firefox, it wont show me the background color, but in IE it show. So this is the reason that i wanna install IE into my PC.

---

### Post by skoal on 2005-10-03
I installed Wine + IE6 [this way](http://www.ubuntuforums.org/showthread.php?t=58644&highlight=wine), usind the sidenet script and IE6 worked great.  Ran pretty comparable to regular browsing speed with native linux browsers...

\\//_

---

### Post by Shun on 2005-10-03
Skoal,

   When you browse to yahoo, is it going smooth? I try to install the wine-config-sidenet (i think the software i used is same with yours). After all the installation, when i browse to yahoo or google, it cannot load out the page. Is it in my installation got any mistake.

1. I try to upate the apt-get, and install the wine.
2. After that, i extract the wine-config-sidenet and run ./setup at terminal.
3. I choose en as my language and select the silent installation. (Only install the IE6).
4. I run the IE with "wine iexplore" command in terminal.

   After all of this i try to browse to yahoo, but it still cannot load the page out. So is there any solution for these? Pls advise. Thanks!

---

### Post by skoal on 2005-10-04
Hmm, I've actually since deleted my wine + IE stuff.

Check out the following thread: [http://www.ubuntuforums.org/showthread.php?t=65190&highlight=explorer](http://www.ubuntuforums.org/showthread.php?t=65190&highlight=explorer)

* Basically, if you had a prior wine install, you may need to remove the ~/.wine directory first (getting you a clean environment) and re-install per that first link I gave you, using that wine version, dcom98, and the sidenet script.

Do any other websites load for you? I know I ran across an old thread whereby someone said they had to do something like:

wine iexplorer.exe google.com

first, then set it as the homepage.  But that was just for some sort of loading error where _no_ pages would load at all.  I think yours is just a slowness issue, and some web sites still load, right?  Either way, I would try out that suggestion from the link and * above.

\\//_

---

### Post by logicaloperator on 2005-10-04
[FONT="Tahoma"][SIZE="2"]try sudo apt-get install winetools.  Winetools is a collection of tools to automatize WINE installation tasks, such as installing Internet Explorer, MS Web fonts, DCOM98, Visual C++ Runtime, and other Windows libraries, as well M[/SIZE][/FONT]:D

---

### Post by Shun on 2005-10-04
Hi,

   Other link like yahoo mail can able to link but when i wanna browse to yahoo.com then it is unable to do that (sound weird right). Another problem is when i wanna log in to some websites, when i key in all the password and id then in the middle way of the log in process, the IE will automatic close. 

   Regarding with remove the /.wine, how can i do that? I do not know the command for remove the wine. Pls advise. Thanks!

---

### Post by skoal on 2005-10-04
[QUOTE=Shun]Regarding with remove the /.wine, how can i do that? I do not know the command for remove the wine. Pls advise. Thanks![/QUOTE]
Well, I wouldn't advise removing that path if you already have other Win apps installed or want to keep anything in general from your current Wine configuration.

However, if you just want to test the difference (between the current and clean wine install), do this:

cd ~ && mv .wine .wine~

...which will backup your current .wine directory to .wine~.  Then, follow those step from the link I gave before and it will create a new and clean .wine path from the sidenet installation script.  If all goes well, keep the current .wine.  If you see no difference:

cd ~ && rm -rf .wine && mv .wine~ .wine

...which will restore your original wine stuff and get you back to where you are now.  Then, you can at least eliminate the possibility it was something with your initial .wine configuration, reg settings, et cetera.

\\//_

---

### Post by Shun on 2005-10-05
Hi,

   If i installl IE with wine-config-sidenet software, is it already included the DCOM98 or i need to install it separately. By the way, can i know what is DCOM98?

Thanks!

---

