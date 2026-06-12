---
title: "Installing Yahoo Messenger"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by nonicutie on 2009-11-13
I've been trying several ways to install yahoo messenger using wine and commands.

But:
After i install wine, i dont know how to install yahoo messenger. I have wine ready. 
When i put command 'sudo apt-get install yahoo, it doesnt come up for installation but error.

Is there anyway to install yahoo messenger either from repository or directly from website?

---

### Post by dhavalbbhatt on 2009-11-13
Why do you need to install YM? can't you use Empathy? I believe it has all YM features..or does it not?

---

### Post by viper250 on 2009-11-13
many linux versions have their own  built in messenger like kopete, pidgeon,gaim, ect.
all you need to do is start them and add profile (your account type, username and password. so you dont need to download anything.:D

---

### Post by nonicutie on 2009-11-13
I dont expect my friends on yahoo to see me online, i use for several persons close to me. I have msn as separate friends from yahoo that i always like to chat with.

I normally use msn only. But, empathy combines altogether yahoo and msn, all my friend was buzzing me around for nothing. I'm getting annoyed. 

Hope this helps to clarify that i need separate installation. Is there anyway to install it?

I never know what koppet, pigeon, etc. Most my friends are still using windows, yahoo and msn. I'm the only one using Ubuntu so i still need to catch up with them thru msn and yahoo.

---

### Post by kinjiro on 2009-11-16
Hi, i just found about  this. 

You could try using the web version of yahoo messenger.

Go to to the download page of [yahoo messenger]("http://messenger.yahoo.com/download/") then click "web" under "Other versions:"

Hope that helps. :)

---

### Post by solardisaster on 2010-01-26
> **nonicutie said:**
> I've been trying several ways to install yahoo messenger using wine and commands.

But:
After i install wine, i dont know how to install yahoo messenger. I have wine ready. 
When i put command 'sudo apt-get install yahoo, it doesnt come up for installation but error.

Is there anyway to install yahoo messenger either from repository or directly from website?

What the hell are you talking about? Use Empathy or Trillian... If you do it right then you won't have any questions.

---

### Post by isbiyanto on 2010-04-26
I use Pidgin. excellent for me :P

---

### Post by kishorr on 2010-04-27
im ok wit empathy, using it for gtalk aready, how do i configure it for skype n yahoo....???

---

### Post by Ajile on 2010-06-03
What is WRONG with you people?

Someone says, "I need help with X" and you say, why bother with X? Do X-4, and be done with it.

Hey, if you can't answer the question, don't chime in. I LOVE linux, and I desperately want to get off of Windows for me and my 8 computers in my house, but the prima donna attitude of most Linux users make me want to vomit on my keyboard.

Why can't you just actually answer a question instead drip a bunch of attitude?

Oh, and for the record, I've been using Pigden for a month and have yet been able to transfer a file ACCROSS THE ROOM to my wife, much less across the world to a Filipino friend of mine.

Why? Because it doesn't work! And I apologise for the attitude, but krikey! Everytime someone asks a question, the typical response is "Why are you asking this question??" as opposed to, you know, the actual answer.

---

### Post by luciftian on 2010-06-16
Hi, Ajile I completely agree with you.  

I have found a way to install Yahoo (or allegedly any .exe), however I have tried both v10 and v9 and they both just crash when you try to use them.  

From reading other forum entries it looks like there is only one working version of Yahoo (it's a deb; [http://ubuntuforums.org/showthread.php?t=81895&page=14](http://ubuntuforums.org/showthread.php?t=81895&page=14)) that does actually work in Ubuntu, but apparently it is very old and lacks most features. 

I will have no choice but try the built in Kopete, and others and see if any of them are suitable.

Anyway here are the installation instructions for reference:

1) install wine: to do this, enter the following command in the terminal (You may find the terminal by going to Applications -> Accessories -> Terminal)
   sodu apt-get install wine

2) Before using Wine, it is necessary to create the fake C: drive where your Windows applications will be installed. To do this, enter the following command into the terminal: 
   winecfg

This will create a hidden folder (.wine) in your home directory containing the fake C: drive as well as registry files similar to those used in Windows. 

Once this directory is created, the Wine Configuration Window will appear. This window will allow you to customize a variety of settings for Wine, including which Windows Version that is emulated, drive mappings, DLL overrides, as well as application specific settings. 

3)Click the Ok button to close the Wine Configuration window. 

4) Download the full OFFLINE yahoo installer to your Download folder or a known location (the ones for version 10 can be found at [http://www.mydigitallife.info/2009/08/26/download-yahoo-messenger-10-beta-official-standalone-offline-setup-installer-links/](http://www.mydigitallife.info/2009/08/26/download-yahoo-messenger-10-beta-official-standalone-offline-setup-installer-links/)

5)In the terminal navigate to the directory that contains the EXE file [e.g. enter a command similar to: cd Download   Note: it is case sensitive] 

6) Use the terminal to open the executable using wine (opening the file in the GUI using wine does not work).  To do this enter the command:
   wine {the-name-of-the-file.exe}
This will start the .EXE using Wine. It should then run as it would in Windows. If the application asks for a directory to install the application to, select put it under C:\Program Files.

If anyone finds a version that actually works or a fix, please do post it here.

btw I found out the info about using Wine at [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by lechien73 on 2010-06-16
Check this link for details on what does and doesn't work under Wine for Yahoo Messenger: 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=29](http://appdb.winehq.org/objectManager.php?sClass=application&iId=29)

According to the wiki, version 8 seems to work better, which can be downloaded from:

[http://www.oldapps.com/yahoo_messenger.php](http://www.oldapps.com/yahoo_messenger.php)

Everyone seems to have problems getting video and audio to work, but if you're just using it for IM, then it seems to be ok.

My personal preference would be to use Empathy for MSN, and Pidgin for Yahoo. Then you don't have to be logged on to both chat accounts at the same time.

---

### Post by GeoPirate on 2010-06-22
I understand the outrage about someone not answering your question directly, but sometimes the correct question isn't asked.  Instead of asking the question:

"How do I get the windows version of yahoo working on ubuntu?"

it would be better to ask 

"What's the best way to transfer a file over yahoo on ubuntu?"

The first question usually will not get the best response on here, often running something through wine is a hacky, buggy experience, and a program designed to run on linux works much better.  But, if someone were asking the second question then I would suggest they try GyacheI.  It's able to do most of the things you can do on the windows version of yahoo, and it's only for the yahoo protocol it's not an all-in-one like pidgin or empathy.  The ppa can be found here [https://launchpad.net/~baudm/+archive/ppa](https://launchpad.net/~baudm/+archive/ppa) after you install it a simple: 

sudo apt-get install gyachi

in the terminal will get you going.

---

### Post by kennedyvelez on 2010-07-25
> **luciftian said:**
> Hi, Ajile I completely agree with you.  

I have found a way to install Yahoo (or allegedly any .exe), however I have tried both v10 and v9 and they both just crash when you try to use them.  

From reading other forum entries it looks like there is only one working version of Yahoo (it's a deb; [http://ubuntuforums.org/showthread.php?t=81895&page=14](http://ubuntuforums.org/showthread.php?t=81895&page=14)) that does actually work in Ubuntu, but apparently it is very old and lacks most features. 

I will have no choice but try the built in Kopete, and others and see if any of them are suitable.

Anyway here are the installation instructions for reference:

1) install wine: to do this, enter the following command in the terminal (You may find the terminal by going to Applications -> Accessories -> Terminal)
   sodu apt-get install wine

2) Before using Wine, it is necessary to create the fake C: drive where your Windows applications will be installed. To do this, enter the following command into the terminal: 
   winecfg

This will create a hidden folder (.wine) in your home directory containing the fake C: drive as well as registry files similar to those used in Windows. 

Once this directory is created, the Wine Configuration Window will appear. This window will allow you to customize a variety of settings for Wine, including which Windows Version that is emulated, drive mappings, DLL overrides, as well as application specific settings. 

3)Click the Ok button to close the Wine Configuration window. 

4) Download the full OFFLINE yahoo installer to your Download folder or a known location (the ones for version 10 can be found at [http://www.mydigitallife.info/2009/08/26/download-yahoo-messenger-10-beta-official-standalone-offline-setup-installer-links/](http://www.mydigitallife.info/2009/08/26/download-yahoo-messenger-10-beta-official-standalone-offline-setup-installer-links/)

5)In the terminal navigate to the directory that contains the EXE file [e.g. enter a command similar to: cd Download   Note: it is case sensitive] 

6) Use the terminal to open the executable using wine (opening the file in the GUI using wine does not work).  To do this enter the command:
   wine {the-name-of-the-file.exe}
This will start the .EXE using Wine. It should then run as it would in Windows. If the application asks for a directory to install the application to, select put it under C:\Program Files.

If anyone finds a version that actually works or a fix, please do post it here.

btw I found out the info about using Wine at [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)


use skype...

---

### Post by incatrekker on 2010-08-24
Hi all, I'm new here...just installed Ubuntu for the first time and am very happy already.
Why dont you do X-4 is a valid question IMHO....surely one of the objectives of a forum is to suggest better or different alternatives based on collective experiences? I just installed empathy, selected YM and entered my ID and P/W and within a minute I'm chatting....cool stuff...onward and upward without a backward glance.

Thanks for your help here...keep it open
JD

---

### Post by dilantha on 2010-11-05
Can we do video chatting between empathy client in ubuntu and yahoo messenger client in windows ?

---

### Post by ben2talk on 2010-12-09
The way to handle this is to use Pidgin/empathy/amsn etc for ubuntu, and if you REALLY need to use Yahoo Messenger, you need to have a Virtualbox set up - you can launch your virtualbox (run XP in a window, or run it seamlessly) and launch Windows version to run seamlessly on your desktop - but it does use a bit more cpu in a virtualbox, so it's only really a solution when you really need to use it.

For videochat, use Skype in Ubuntu - and keep Pidgin open to stay in contact - so you can get all the functions that way without having to start up your virtualbox.

---

### Post by crummychrome on 2013-02-21
Well I can see this thread is a few years old, but it doesn't hurt to document my learning experience on ubuntu since i'm a new user.

:popcorn:

So before I found this thread to install yahoo messenger - i read this documentation [http://www.ehow.com/how_4778510_install-yahoo-messenger-ubuntu.html](http://www.ehow.com/how_4778510_install-yahoo-messenger-ubuntu.html) and it worked perfect on my 12.04. After installing wine and restarting my laptop - there were no more unsuccessful installs - it finally went thru - so for those still trying to figure this out - maybe it will work for you. good luck.
):P

---

### Post by wildmanne39 on 2013-02-21
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

