---
title: "Can you please help?...I want to kill adobe flash player.!"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by red33m on 2009-12-01
Hello everyone in this forum,

I am facing a first seen problem with adobe flash player...I can't pause,rewind or do anything with the videos from any page(e.g.Youtube).I can only watch.I opened the Update manager and it told me that when I upgraded,something went wrong...so I clicked the partial update button which was supposed to reinstall all the packages in bad or even crucial state.But it didn't ...It told me to reininstall the package adobe-flashplugin manually...And so I went to the Synaptic but it won't open for the same reason....

...So all I can do is open the Terminal and do the job with my "terminal writing skills" which are not good.

So please forum help me murder adobe flash plugin...!!!

(if you have a better solution tell me)

Thank you very much,

Red33m

---

### Post by gradinaruvasile on 2009-12-01
In a terminal:

sudo apt-get install -f

This should correct dependencies etc.
Then:

sudo apt-get install --reinstall flashplugin-installer

Make sure your browser is not running when doing these steps.
Then start the browser and test if it works.

---

### Post by red33m on 2009-12-01
Nope...It told me thatin both terminal codes:

red33m@red33m-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.


What is wrong?

---

### Post by gradinaruvasile on 2009-12-01
Then uninstall the damn thing:

sudo apt-get purge adobe-flashplugin

Its really annoying having a bunch of packages doing the same thing....

---

### Post by darkod on 2009-12-01
If you're running 64bit go here [http://ubuntuforums.org/showthread.php?t=1306113](http://ubuntuforums.org/showthread.php?t=1306113) in post #3 and download the library for 64bit flash.
Close firefox, extract the downloaded file and put it in home/.mozilla/plugins

Launch firefox and it should work. It took me ages to figure out that 64bit has problems even though everything seems installed correctly.

PS. When you open your home folder you need to press Ctrl+H to show the hidden folder .mozilla. If the folder plugins doesn't exist in .mozilla, just create it.

---

### Post by red33m on 2009-12-01
Same here:

red33m@red33m-laptop:~$ sudo apt-get purge adobe-flashplugin
[sudo] password for red33m: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.


Is there any spell that  can kill it?

---

### Post by red33m on 2009-12-01
could you please tell me where this home mozilla plugins is?

guide me through....!

---

### Post by red33m on 2009-12-01
is there any solution for 32 bit system...I don't think I am 64 bit..

---

### Post by darkod on 2009-12-01
Click on the link in that post #3 to download the file. It will either be on the desktop or in Places-Downloads. Right-click on the file and select Open with Archive Manager.
In Archive Manager there will be button Extract on the toolbar, click it and it will ask you where to extract. Select Home for example.
Then open Places-Home and it will be there, the extracted library file. Press Ctrl+H on the keyboard to show the hidden folders. Right-click on the library file and select Copy. Then open the folder .mozilla then plugins. Right-click in that folder, select Paste and the library file will be copied there.
Start firefox and see if it's working better.

---

### Post by red33m on 2009-12-01
a plugins file didn't exist so I created one...I did what you said...then because somehow it removed the flash player I went to reinstall it but nothing(look at the picture)

---

### Post by darkod on 2009-12-01
You created plugins file or folder? It makes big difference so you have to be careful about the working used. You need to create FOLDER named plugins in the folder .mozilla, if it doesn't exist.
Not sure if you need to install flash player again.

---

### Post by red33m on 2009-12-01
no my bad I created a FOLDER...but when I try to play a video it says that the flash player is not installed...

---

### Post by darkod on 2009-12-01
In case you still have the 32bit version do:
sudo apt-get autoremove flashplugin-nonfree

---

### Post by red33m on 2009-12-01
red33m@red33m-laptop:~$ sudo apt-get autoremove flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

My ubuntu is so stubborn....

any other recommendations?

---

### Post by darkod on 2009-12-01
Well then reinstall it once if it complains that much. I never removed adobe-flashplugin anyway.
Maybe it has some core files that are needed, and then the library you downloaded just enables to work properly on 64bit.
sudo apt-get install adobe-flashplugin

---

### Post by red33m on 2009-12-01
I already did that and it gives me the same mistake....if you don't know what to do from now on just tell me quickly ... because I am going to install the whole system again...

---

### Post by darkod on 2009-12-01
Sorry, no idea.

---

### Post by red33m on 2009-12-01
Don't be sorry mate...I am glad you helped..I have done this over 18 times...my favorite show is on TV...so a long way is infront of me....!

P.S. I will install Kubuntu and Ubuntu...just to see the KDE...!!

See you!

---

### Post by red33m on 2009-12-01
You should try Kubuntu...is a totally different and better experience..!!!

I like both Ubuntu and Kubuntu...but KDE is a totally different level...!!

---

### Post by schnelle on 2009-12-01
> **red33m said:**
> You should try Kubuntu...is a totally different and better experience..!!!

I like both Ubuntu and Kubuntu...but KDE is a totally different level...!!

Thumbs up for Kubuntu and KDE 4.3 :p

---

### Post by red33m on 2009-12-02
Yeah I think that too!!

I had some trouble with the sound in flash video files but I managed it..!!

My laptop is a single celled Celeron..with 1Gb of Ram...so it should be slow but it isn't !

KDE is very beautiful...!!

---

### Post by red33m on 2009-12-02
S to sum up things and help every one who is reading this thread seeking for and answer...there is not a solution for this first seen error and just reinstall your system.. :(

---

### Post by SteveDee on 2009-12-04
I think I have the same problem that red33m describes.

Basically I tried installing Adobe-Flash from a web link. Installation failed, and now whatever I do (e.g. try to re-install, try to uninstall) I get a message like:-
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

I also have a red "no entry" sign in my panel which loads Update Manager, tells me a package is not completely installed, and recommends a Partial Upgrade to fix the problem (which does not solve problem).

I'm not prepared to re-install at this stage, so any other ideas would be welcome.

++++++++++++++++++++++++++++++++++++
SOLVED: Fixed my problem with ref to: [http://ubuntuforums.org/showthread.php?t=1346381&highlight=adobe+flash](http://ubuntuforums.org/showthread.php?t=1346381&highlight=adobe+flash)

---

