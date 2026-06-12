---
title: "Updates are ready for installation"
date: 2016-05-02
forum: Installation &amp; Upgrades
---

### Post by peredur-peredur on 2016-05-02
Since upgrading to 16.04 (from 15.10) I now occasionally get a message appearing at the top right hand corner of the screen saying that I have updates and that they are ready for installation.  The message gives no other instructions and clicking on it doesn't do anything.  Starting the Updater doesn't do anything either: it just says that the system is up-to-date.  The impression I have is that the message is telling me that packages have been downloaded and just need installing.

In the end I tracked the packages down via Synaptic, but I'm sure that's not what I'm expected to do.

So my question is, what should I do when this message appears?

Thanks


Peter

---

### Post by RobGoss on 2016-05-02
Hello Peter, I'm also running Ubuntu 16.04 and I believe that message is just letting you know there're Updates available that needs to be installed.

---

### Post by peredur-peredur on 2016-05-09
> **RobGoss said:**
> Hello Peter, I'm also running Ubuntu 16.04 and I believe that message is just letting you know there're Updates available that needs to be installed.

Except that when I run the updater, it says that the system is up-to-date.  So it can't be that, I'm afraid.

---

### Post by Fende on 2016-05-09
I'm having the same problem as peredur-peredur. Sometimes after booting my computer in Ubuntu 16.04 64-bit, I get the system message "new updates are available", so I check for new updates, and I see that there are really no new updates available. I installed Ubuntu 16.04 64-bit in my parent's computer and they are experiencing the same problem, so I suspect that this is a system-wide bug in this release.

---

### Post by RobGoss on 2016-05-09
**Peruder**, Are you able to run the updater successfully and complete any and all system updates

---

### Post by vasa1 on 2016-05-09
> **peredur-peredur said:**
> ...
So my question is, what should I do when this message appears?
...

> **Fende said:**
> I'm having the same problem as peredur-peredur. ...
Could you please open a terminal and run
*sudo apt-get update*
and follow that with
*sudo apt-get dist-upgrade*
and press "N" when the latter command asks you if you wish to proceed. You can then post the entire screen output here between code tags for people to guide you further.

---

### Post by bapoumba on 2016-05-09
One routine check would be to open a terminal and run :
```
sudo apt-get update
sudo apt-get upgrade
```
You will see the packages to be upgraded after the last command. In doubt, please post the full outputs to both commands here.

---

### Post by vasa1 on 2016-05-09
@bapoumba, I mentioned dist-upgrade because I suspect there also could be the recent kernel upgrade to be dealt with:```
11:14 PM ~ $ uname -r
4.4.0-22-generic
11:14 PM ~ $ 
```

---

### Post by bapoumba on 2016-05-09
> **vasa1 said:**
> @bapoumba, I mentioned dist-upgrade because I suspect there also could be the recent kernel upgrade to be dealt with:```
11:14 PM ~ $ uname -r
4.4.0-22-generic
11:14 PM ~ $ 
```
Yes, good call :)
Did not see your reply, blame multiple tabs open and not reloading before posting :/

---

### Post by peredur-peredur on 2016-05-10
> **RobGoss said:**
> **Peruder**, Are you able to run the updater successfully and complete any and all system updates

No.  If I run the updater it just says that the system is up-to-date.

However, if I open Synaptic and select to view Installed (Updateable) i.e. Instalado (actualizable) on my system, I can see the updateable items from there and can apply the updates.  I haven't found any other way of doing this.

---

### Post by Fende on 2016-05-10
I don't see any error message if I run "apt-get update" in terminal after getting the "Updates are ready for installation" message: 

```


$ sudo apt-get update
Teño:1 http://archive.canonical.com/ubuntu xenial InRelease
Teño:2 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease   
Teño:3 http://archive.ubuntu.com/ubuntu xenial InRelease                       
Teño:4 http://ppa.launchpad.net/libretro/stable/ubuntu xenial InRelease        
Teño:5 http://archive.ubuntu.com/ubuntu xenial-updates InRelease               
Teño:6 http://ppa.launchpad.net/mdeslaur/steamos/ubuntu xenial InRelease       
Teño:7 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial InRelease   
Teño:8 http://archive.ubuntu.com/ubuntu xenial-backports InRelease             
Teño:9 http://ppa.launchpad.net/noobslab/apps/ubuntu xenial InRelease          
Teño:10 http://archive.ubuntu.com/ubuntu xenial-security InRelease             
Teño:11 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease      
Teño:12 https://deb.opera.com/opera-stable stable InRelease
Lendo as listas de paquetes... Feito



$ sudo apt-get upgrade
Lendo as listas de paquetes... Feito
Construindo a árbore de dependencias       
Lendo a información do estado... Feito
Calculando a anovación... Feito
0 anovados, 0 instalados, Vanse retirar 0 e deixar 0 sen anovar.

$ sudo apt-get dist-upgrade
Lendo as listas de paquetes... Feito
Construindo a árbore de dependencias       
Lendo a información do estado... Feito
Calculando a anovación... Feito
0 anovados, 0 instalados, Vanse retirar 0 e deixar 0 sen anovar.

$ uname -r
4.4.0-22-generic





```

---

### Post by RobGoss on 2016-05-10
After viewing your first I see you stated you upgraded from** 15.10 To 16.04**, maybe this has caused a problem with your systems and the updater

I also try to upgrade from **14.04 to 16.04** and had all kinds of problems with my upgrade, I them decided to just do a fresh install of **16.04 **and everything is running as it should including the updater.

[COLOR=#000000][/COLOR][COLOR=#000000]*Bapoumba, mentioned a *[/COLOR][COLOR=#000000]*[I]kernel upgrade this might be something you might want to do to see if something is *missing[/I][/COLOR]

---

### Post by peredur-peredur on 2016-05-10
> **RobGoss said:**
> After viewing your first I see you stated you upgraded from** 15.10 To 16.04**, maybe this has caused a problem with your systems and the updater

I also try to upgrade from **14.04 to 16.04** and had all kinds of problems with my upgrade, I them decided to just do a fresh install of **16.04 **and everything is running as it should including the updater.

[COLOR=#000000]*Bapoumba, mentioned a *[/COLOR][COLOR=#000000]*[I]kernel upgrade this might be something you might want to do to see if something is *missing[/I][/COLOR]

I may do a fresh install if I can't find any other solution, but I'm a bit reluctant to do it as I dual boot with Windows 8.1 and it took me an age to get grub to boot Ubuntu after I'd installed it and I'm not looking forward to going through that again.  I also had driver problems with my mousepad that I'd have to sort out again.

As for the kernel, what should I be looking for?  uname -r gives: 4.4.0-22-generic

---

### Post by RobGoss on 2016-05-10
> **peredur-peredur said:**
> I may do a fresh install if I can't find any other solution, but I'm a bit reluctant to do it as I dual boot with Windows 8.1 and it took me an age to get grub to boot Ubuntu after I'd installed it and I'm not looking forward to going through that again.  I also had driver problems with my mousepad that I'd have to sort out again.

As for the kernel, what should I be looking for?  uname -r gives: 4.4.0-22-generic

Yes I can certainly understand that if your system is running good and the updater is the only thing that is not yet working correctly you may want to wait a bit until you can resolve it
In the mean time I'll keep researching to see if anyone else is having this issue.


> [COLOR=#000000]As for the kernel, what should I be looking for? uname -r gives: 4.4.0-22-generic[/COLOR]

I'm not that familiarized with everything about what to look for that has to do with Kernels but I'm assuming you would want to make sure you have the correct version with you installation which I see you do **[COLOR=#000000]4.4.0-22-generic[/COLOR]**

Maybe someone who has more knowledge of kernel will lend a helping hand and point out what you should be looking for.

---

### Post by peredur-peredur on 2016-05-10
> In the mean time I'll keep researching to see if anyone else is having this issue.

Thanks.  I'm subscribed to the thread, so I should know if you post.  As for others having the same problem, I'm sure you've seen that there are a couple who've posted to this thread.

---

### Post by RobGoss on 2016-05-10
Quick question have you try changing your download source **Software & Updates, **choose a new source from the drop-down menu then choose **Other, **click on**Select the best server, **it will find the best download for your location I'm not sure if this will help but maybe it's the current server you're using now. I'm thinking if you changed it that you might be able to download what's needed to fix this problem worth a try...Just note what your current server is now in case you want to change it back. Good luck

---

### Post by peredur-peredur on 2016-05-10
> **RobGoss said:**
> Quick question have you try changing your download source **Software & Updates, **choose a new source from the drop-down menu then choose **Other, **click on **Select the best server**

OK.  Done that.  Will let you know if it makes any difference.  Was on the Main Server (Servidor Principal) before.  Now on a UK server.

---

### Post by RobGoss on 2016-05-10
> **peredur-peredur said:**
> OK.  Done that.  Will let you know if it makes any difference.  Was on the Main Server (Servidor Principal) before.  Now on a UK server.


Now try running your system updater and let me know what happens

---

### Post by peredur-peredur on 2016-05-11
> **RobGoss said:**
> Now try running your system updater and let me know what happens

It comes back and says the system is up-to-date.  As before, everything seems to run correctly.  I think I need to wait until I get the message again and then run the updater to see if it is still denying that there are, in fact, updates available.

Just to be clear, what was happening was that a message appeared saying there were updates, but when I ran the updater it said that the system was up-to-date.  The updater did not indicate an error, just contradicted the message by denying that there were updates to do.  Using Synaptic I was able to find some available updates and could apply them without error.

---

### Post by bapoumba on 2016-05-11
Have you been installing packages out of apt-get or Software Updater ? Funny apt-get shows none to install and Synaptic does.

---

### Post by peredur-peredur on 2016-05-11
> **bapoumba said:**
> Have you been installing packages out of apt-get or Software Updater ? Funny apt-get shows none to install and Synaptic does.

As far as I'm aware, the updater does updates not installs?  I would guess that most of the software on my system was originally either installed by default, or using apt-get from the command line, or, occasionally, using the Ubuntu software store (or whatever they call it).  It is all from the Ubuntu repositories, though, and ultimately installed using apt-get install either directly or indirectly as far as I know.

All the updates on the system have been done, until now, using the software updater.  It's only when this message started appearing that I looked for them elsewhere (in synaptic).  And I couldn't guarantee that the "updates available" referred to in the message are the same ones as those displayed as "Installed (updateable)" in synaptic.

And I don't know if apt-get (from a terminal) shows none to install.  The software updater says that (i.e. the GNOME apt update manager) - so I suppose it uses apt-get in the background ... 

Anyway, the contradiction remains: that a message appears saying that there are updates to install, whilst the updater (GNOME apt update manager) says the system is up-to-date.  And it seems that it's a, fairly minor, problem that appears on systems other than just mine.  As you say, funny...

---

### Post by VE6EFR on 2016-05-12
I may be a bit late to the party, but go into Ubuntu Software (the old software centre) and then select the updates tab. You will probably see the updates there. Not sure why we now have 2 places to check to be sure our systems are up to date, but it appears at least for now that's the way it is.

---

### Post by peredur-peredur on 2016-05-12
> **VE6EFR said:**
> I may be a bit late to the party, but go into Ubuntu Software (the old software centre) and then select the updates tab. You will probably see the updates there. Not sure why we now have 2 places to check to be sure our systems are up to date, but it appears at least for now that's the way it is.

Now that's a thought!  OK.  Here's the plan.  The next time that the message is displayed I'll do the following:

Ha! the message has just popped up!

And guess what?  This time the updater agrees and says there are updates, and I can install them.

I'll keep an eye on it, guys, but for now it looks as though it was something to do with my (and others') system that has auto-magically sorted itself out, or somebody has quietly fixed it.

Thanks for all the help and suggestions.  If the problem returns, I'll re-post to this thread.

---

### Post by bapoumba on 2016-05-12
Yeah, sorry, using Ubuntu Mate, it's called Software Boutique, I had not checked how it was labeled on Ubuntu and it came out as nonsense. Anyways, the apt-get upgrade (or dist-upgrade) commands you earlier ran show no packages to upgrade. I was surprised synaptic found some. In the old times, they did not share their history files but I think they do now.

Worth watching, we'll send magical brainwaves once again should you need some :)

---

### Post by peredur-peredur on 2016-05-12
> **bapoumba said:**
> Yeah, sorry, using Ubuntu Mate, it's called Software Boutique, I had not checked how it was labeled on Ubuntu and it came out as nonsense. [\QUOTE]

Between that and the fact I'm translating my interface from Spanish to something approximating to English, it's lucky we're communicating at all!  :):)

[QUOTE]Anyways, the apt-get upgrade (or dist-upgrade) commands you earlier ran show no packages to upgrade. I was surprised synaptic found some. In the old times, they did not share their history files but I think they do now.

Worth watching, we'll send magical brainwaves once again should you need some :)

Thanks.  I wish I knew what had put things right (assuming they stay put right), and I hope that the other people who've been reporting the same problem manage to get it sorted too.

Muchas gracias para la ayuda.  Thanks for helping.

---

### Post by RobGoss on 2016-05-12
I'm glad it was all sorted out I'm sure there are more people out there with the same issue, I have that updater popup but when I run the updates it seems to let me know what updates are available.

If you are happy with the out come would you mind marking this post as solved, Thanks so much

---

### Post by peredur-peredur on 2016-05-12
> **RobGoss said:**
> If you are happy with the out come would you mind marking this post as solved, Thanks so much

How do I do that?  Just post again  with "Solved" in the title?

---

### Post by RobGoss on 2016-05-12
> **peredur-peredur said:**
> How do I do that?  Just post again  with "Solved" in the title?


Use the **Thread Tool **tab at the top of this post

---

### Post by vasa1 on 2016-05-12
> **peredur-peredur said:**
> How do I do that?  Just post again  with "Solved" in the title?

See [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by bapoumba on 2016-05-13
We should have a thread prefix for "Automagically Solved" :)

---

