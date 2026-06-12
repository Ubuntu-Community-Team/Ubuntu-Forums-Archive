---
title: "backing up installed software for fresh reinstall"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by svesmeralda on 2010-05-21
Hi,

I have been using Ubuntu for three years and haven't had a problem upgrading until Karmic Koala, it broke my system twice, not fataly, though.

I am currently using Jaunty and wish to upgrade to Lynx.  My question is, "Can and how do I backup my current installed software so that I can install it on to Lynx withoug having to install each program again?"  Would Clonezilla do this?  

I am not a technical user but I have learned how to use the command line so I would be willing to go that route as well as a GUI application.

I am sure the answer is posted somewhere but after an hour I could not find it to my satisfaction.

Thanks in advance,

Jim

Fair winds and smooth seas to all.

---

### Post by Rasa1111 on 2010-05-21
You might want to check out "APTonCD"
         [FONT=Verdana][SIZE=2]      [**APTonCD** -]("http://en.wikipedia.org/wiki/APTonCD")

It makes a "repository" of everything you have installed, 
then you burn it to a disc,  and once you have your new install...
just put the ATPonCD disc in that you just made... 
and go from there..
its pretty straightforward. 

Its the easiest thing Ive found. 
all with a nice GUI also. 

 I havent used it in Lucid yet, but i did in Karmic and it went great. 
Hope it helps. 

[/SIZE][/FONT]

---

### Post by svesmeralda on 2010-05-21
Thanks, that was quick.  I installed aptoncd with synaptic pm and burned an iso file.  Do I need to do anything else?  From the instructions I would think not but I do not wish to take anything for granted.  I will read the wiki again to see if there is something else I need to do.  It just seems too easy, even for Ubuntu.

Jim

Fair winds and smooth seas to all.

---

### Post by Rasa1111 on 2010-05-21
No problem. 
I dont think you should have to do anything else. 
I didnt. 
Just make sure your iso image burned properly..
Put the disc back in and see what comes up..
if it's all there...  you *should* be set.  lol

heres to it going without any problems! cheers! lol

---

### Post by oldfred on 2010-05-21
this creates a list of all of your installed packages and then reinstalls all of them (but latest version).

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)


The issue I had with a system updated for 3 years and very little housecleaning was I reinstalled some available but older packages. It does not install obsolete packages as they are not available anymore.

---

### Post by svesmeralda on 2010-05-21
The only apps that were found by the aptoncd program were the ones that were downloaded from Synaptic.  It did not show any of the other apps that are currently installed.  I have Linxmint8 on my Dell mini-9 and the aptoncd program seem to put everything on it.  For some reason it did not work quite right on Ubuntu.  Maybe it is because it is 9.04.

I am going to try an upgrade to 10.04 thru 9.10 and see how that goes.  Fortunatley Ubuntu makes it relatively easy to re-install my apps manually so I am not too disappointed.

Thanks and I will post how aptoncd works on 10.04.

Jim

---

### Post by svesmeralda on 2010-05-24
The upgrade to Lucid Ubuntu from Jaunty was too buggy for me so I did a backup with APTonCD and did a fresh install using the WUBI installer.  The re-install also failed.  It eventually corrupted a file in Windows so that I could not boot to Ubuntu or reinstall with WUBI and it also disabled my cd/dvd drive.  I fixed the last problem by restoring Windows to an earlier time but when I boot to Windows the menu to choose it or Ubuntu is still there even with Ubuntu removed.  I may have to reinstall Windows to fix that problem some day if I cannot google an answer.  I installed Lucid back on the computer around windows using the alternate desktop cd.  Too soon to tell if I have any problems there.

I was not able reinstall my apps.  APTonCD restored the app list but from there I did not know what to do next.  I did research and tried some things to no avail.  I did not document what I did so I cannot give any details on what happened.

What should I do after the software list is restored?  Everything went fine up until then.

Would I be able to use APTonCD to restore them back on to Ubuntu from my LinxMint9?  It is based on Lucid.

Jim

Fari winds and calm seas.

---

### Post by Rasa1111 on 2010-05-24
Hi Jim, 

Sorry man, Im really not sure what is going on. 

 As i said, i havent used the APTonCD in Lucid yet.. 
and it's been awhile since Ive used it in karmic..
But when I get home, I will get in there and see whats up with it, 
and see if we can get it worked out. 

 Im not sure on your last question... 
So i guess the only help this post is going to bring is the BUMP to the top of the pile,
.. and hopefully someone wiser comes through.

 Ill post back after i get home and check out whats goin on with APTonCD.
Sorry bro.  :( <3

---

### Post by svesmeralda on 2010-05-25
I did install Lucid around windows on my Toshiba with the alternate cd.  It went well and seemed okay.  I installed the apps I wanted but when the update manager told me there were no updates I knew somehting was seriously wrong with my install.  

I used APTonCD  to create the file.  It seemed to want to copy a lot of files that did not seem necessary to me and did not list all the ones I wanted on it.  I unchecked all the ones I felt/guessed did not need to be backed up.  It made the iso just fine to my home directory.  The only mistake I made was to not burn it right away and, also, not copying it to an external memory device.

This afternoon I did a fresh install of Lucid from a live CD, erasing my restore iso file, thus I have to install my programs with the software center.  Last night I found out how easy that is.

I read on the APTonCD documentation that the programs have to be installed manually.  Do they have to be done one at a time or is there a way to do them all with one command on the command line or even with the GUI?

I will be waiting to hear what you are able to find out.

Jim

Fair winds and calm seas.

---

### Post by svesmeralda on 2010-05-25
I did install Lucid around windows on my Toshiba with the alternate cd. It went well and seemed okay. I installed the apps I wanted but when the update manager told me there were no updates I knew something was seriously wrong with my install of Lucid.

I used APTonCD to create an iso file. It seemed to want to copy a lot of files that did not seem necessary to me and did not list all the ones I wanted on it. I unchecked all the ones I felt/guessed did not need to be backed up. It made the iso just fine to my home directory. The only mistake I made was to not burn it right away and, also, not copying it to an external memory device.

This afternoon I did a fresh install of Lucid from a live CD, erasing my restore iso file, thus I have to install my programs with the software center. Last night I found out how easy that is.

I read on the APTonCD documentation that the programs have to be installed manually. Do they have to be done one at a time or is there a way to do them all with one command on the command line or even with the GUI?  I feel that the article was not clear on that point.

I will be waiting to hear what you are able to find out.

Jim

Fair winds and calm seas.

---

### Post by samigina on 2010-05-25
Theres no news about APToncd since 2007, time to look for new options.

---

### Post by Rasa1111 on 2010-05-25
sadly , you might be right samigina....

I've sat here for the last 2 hours trying to get APTonCD to function properly and it is just not doing what it should.  Its almost a mess. 

Im sorry Jim~ The last time I used it, about 5-6 months ago with Karmic,
it worked fine.   Now I cant even get it to bring up what it's supposed to. 

Youre right Jim, Software center is easy.
glad you found it. :)

 I know there are other methods for this...
 Ive never used them but have read a bit on it.
Im still not sure which route to take....
but i will keep looking for the both of us.

:/

---

### Post by svesmeralda on 2010-05-25
Thanks guys, I am glad it was not just me.  I did find where someone showed how to backup using the command line, actually much easier than APTonCD.  Unfortunately when Lucid crashed and I could not get back into it (it was inside of Windows) I lost the copy of the instructions I had made.  Haven't been able to find it again.  It looks like it should work, though.

I erased the entire hard drive and installed the Lucid desktop version.  It is going beautifully so far, really like it except for the default theme and background.

Thanks again,

Jim

Fair winds and calm seas.

---

