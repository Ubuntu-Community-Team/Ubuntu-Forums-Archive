---
title: "Version of Nvu to download for Feisty Fawn"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by ynottony on 2007-05-29
New to Linux ... as in about as new as it gets.  :)

Just downloaded Ubuntu Feisty Fawn with the help of my son and did updates.  Was amazed that everything loaded without a hitch.  Love what I see so far.  Thank you.

Which version of Nvu do I download?  Is it Debian Linux? (Wild guess on my part.)

Also, downloaded Avast anti-virus and it says it downloaded successfully, but am unable to view in applications.  Tried the same with AVG and received the same message.  Would appreciate any help on this.  Thank you.

Is there a recommendation for either one of these two anti-virus programs over the other?  Also, once I decide on one, how do I remove the other, since I am unable to locate it?  Please advise.  Thanks.

I suspect there are specific prompts I am to type in the Terminal window to view these two programs, but do not know which prompts to use  Again, thanks in advance.  

Am new to dos prompts, but can follow directions reasonably well - despite wife's opinion to the contrary. :)

Again, thanks.

Tony Brigmon

---

### Post by blacksadness on 2007-05-29
hey, welcome to linux!
first let's start with the antivirus.. you dont' really need one :D just don't bother with it.. but if you must have one i guess clamav would be my choice though i never used any on my linux.. 
for nvu it's a bit outdated a bug fix of nvu was made and called kompozer, you would probably find a lot of information about it just by searching the forum
as for installing programs youi don't really need to go in terminal for any installation, and you rarely need to download the programs your self, just go in system -> Adminsitration -> Synaptic and choose what you need to install.
Also i would recommend you follow [www.ubuntuguide.org](www.ubuntuguide.org) 's instructions to get arround the common issues..
Good luck, and i hope you enjoy linux as much as i do :)

---

### Post by Rui Pais on 2007-05-29
[QUOTE=ynottony;2742054]...
Which version of Nvu do I download?  Is it Debian Linux? (Wild guess on my part.)
.../QUOTE]

you can try this pre-build debs:
[http://www.getdeb.net/search.php?keywords=kompozer](http://www.getdeb.net/search.php?keywords=kompozer)

just download the version you want and install by clicking on the deb package (or use dpkg -i from a command line)

hth

---

### Post by ynottony on 2007-05-29
hth ... 

Talking about quick responses!  Thank you.  I will follow your counsel as to not installing anti-virus.  

Is there a way to make the copies of Avast and AVG visible in Add/Remove so I can remove both downloads from my system?  Please advise.  Thanks.

Tony Brigmon

---

### Post by blacksadness on 2007-05-29
i'm not sure about either anti-viruses, but if you could download the .deb packages of the programs you could just double click the downloaded file and it would install..

---

### Post by Rui Pais on 2007-05-29
> **ynottony said:**
> hth ... 

Talking about quick responses!  Thank you.  I will follow your counsel as to not installing anti-virus.  

Is there a way to make the copies of Avast and AVG visible in Add/Remove so I can remove both downloads from my system?  Please advise.  Thanks.

Tony Brigmon

:)

What exactly have you downloaded and how do you install it? (it was scripts? debs?)

---

### Post by ynottony on 2007-05-29
Oops, BlackSadness, meant to thank YOU, rather than "hth" for the anti-virus input.  

And a big thanks to both you and "hth" on the komposer recommendation.  Will definitely check it out.

Sometimes I jump on things without first doing my homework.  Thus, my need now to find and remove both Avast and AVG on my system.  Hopefully I will be more careful in the future.  Thanks.

Tony Brigmon

---

### Post by blacksadness on 2007-05-29
You're welcome :)
how did you download the avast and avg? where they .sh scripts, did they have any graphical installer, try to do a sudo updatedb in terminal (takes time) then locate avg , locate AVG and locate avast to see if they actually installed.. and where..

---

### Post by Rui Pais on 2007-05-29
> **ynottony said:**
> Oops, BlackSadness, meant to thank YOU, rather than "hth" for the anti-virus input.  

And a big thanks to both you and "hth" on the komposer recommendation.  Will definitely check it out.

:lol: your welcome. 
Just a clarification... hth is an acronym for "hope that helps", my name is Rui Pais :)   
> 
Sometimes I jump on things without first doing my homework.  Thus, my need now to find and remove both Avast and AVG on my system.  Hopefully I will be more careful in the future.  Thanks.

Tony Brigmon

How do you install such programs (i checked avast ant it has a deb version, do you used that?)
We need to know how you install it to help you uninstall.

---

### Post by ynottony on 2007-05-29
Rui Pais ... 

Here's the download information I followed to download Avast and AVG.  When I couldn't locate Avast I assumed there was a problem and downloaded AVG as a second choice.  Now I would just like to know how locate these files and remove them.  Thank you.

**Avastt**
I downloaded the Free avast! Linux Home Edition at [http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)  

I believe it was the debs package  Am so new to this, I'm really not sure.  Just clicked on the Quick-links download icon and it installed from there.

**AVG**
Downloaded avg75fld-r47-a1022.i386.deb at [http://free.grisoft.com/doc/5390/lng/us/tpl/v5](http://free.grisoft.com/doc/5390/lng/us/tpl/v5)

Any help here would be greatly appreciated.  Thanks.

Tony Brigmon

---

### Post by blacksadness on 2007-05-29
for avast, when promted to download, there are rpm deb and tar.gz version, if you downloaded and installed the deb it's just in synaptic, do a search for avast in synaptic, if it was the rpm it didn't install don't worry.. anyway if it's the setup you can't find i think firefox downloads to the home directory by default. same for AVG if you downloaded the deb and installed it it's in synaptic already..

---

### Post by ynottony on 2007-05-29
Rui Pais ...

My not knowing the meaning of "hth" just proves how green I am.  Sorry abou that.  :)

I am so grateful for the help I'm getting.  Never had quick responses like this in my limited experience with support in the Windows world.  Thank you.

Tony Brigmon

---

### Post by Rui Pais on 2007-05-29
> **blacksadness said:**
> for avast, when promted to download, there are rpm deb and tar.gz version, if you downloaded and installed the deb it's just in synaptic, do a search for avast in synaptic, if it was the rpm it didn't install don't worry.. anyway if it's the setup you can't find i think firefox downloads to the home directory by default. same for AVG if you downloaded the deb and installed it it's in synaptic already..

yep.

And, by the way, synaptic is in your main menu on System -> Administration.

Those packages must be listed under: 'Installed (local or obsolete)?

post on any doubts ;)



edit:
> My not knowing the meaning of "hth" just proves how green I am. Sorry abou that.
oops you was faster. No problem at all :)

> I am so grateful for the help I'm getting. Never had quick responses like this in my limited experience with support in the Windows world. Thank you.

Thats because we want your money (:^o)

---

### Post by ynottony on 2007-05-29
blacksadness ... 

Success!!!  Was able to locate both anti-virus programs using  the search in synpatic ... and was able to remove both following the "remove packages" instructions in help.  

First time to use this search feahure  Can hardly wait to let my wife know I was indeed successful in following directions. :)

Many to thanks for all the help.  

Tony Brigmon

---

### Post by ynottony on 2007-05-29
Rui Pais ... 

If I were to think of the money spent  and headaches incurred at the hands of Microsoft over the past many years, I would get depressed ... again. :)  

But, I'm not going to do that anymore ... just count my blessings instead for discorvering the "stable", helpful world of Linux.

Keep shining ...
Tony Brigmon

---

### Post by stchman on 2007-06-13
> **ynottony said:**
> New to Linux ... as in about as new as it gets.  :)

Just downloaded Ubuntu Feisty Fawn with the help of my son and did updates.  Was amazed that everything loaded without a hitch.  Love what I see so far.  Thank you.

Which version of Nvu do I download?  Is it Debian Linux? (Wild guess on my part.)

Also, downloaded Avast anti-virus and it says it downloaded successfully, but am unable to view in applications.  Tried the same with AVG and received the same message.  Would appreciate any help on this.  Thank you.

Is there a recommendation for either one of these two anti-virus programs over the other?  Also, once I decide on one, how do I remove the other, since I am unable to locate it?  Please advise.  Thanks.

I suspect there are specific prompts I am to type in the Terminal window to view these two programs, but do not know which prompts to use  Again, thanks in advance.  

Am new to dos prompts, but can follow directions reasonably well - despite wife's opinion to the contrary. :)

Again, thanks.

Tony Brigmon

I have both Nvu and Kompozer on my site.

Nvu is a .deb and Kompozer is a pre compiled package that works with Feisty.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

I have a script to install and uninstall Kompozer.

---

