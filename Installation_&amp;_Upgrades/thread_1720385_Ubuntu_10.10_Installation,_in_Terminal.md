---
title: "Ubuntu 10.10 Installation, in Terminal?"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by THGIC on 2011-04-03
Hello everyone, 

     I was installing Ubuntu 10.10 on a Toshiba L655-S5096 laptop (for a friend). I tried it both ways; by either partitioning it myself and by letting it auto-install. 

     Needless to say, both times came up in Terminal, while booting into Ubuntu. It looked like it was booting up just fine, then it goes into a terminal view and asks me to log in. When I type in my credentials, it still continues in this Terminal view, and finally says that I am logged in (still in Terminal). 

     I don't know what I did wrong. I know that with an old acer laptop, if a toggled the volume wheel, it would go between the normal boot screen and a Terminal view; unfortunately, this Toshiba laptop seems to be stuck in a Terminal view. 

     Any thoughts or opinions on this matter? This thing has frustrated me for days now.

---

### Post by Quackers on 2011-04-03
Did you select "try ubuntu" from the live cd to see if Ubuntu can run on that hardware? Did it boot to a desktop?

---

### Post by THGIC on 2011-04-03
I did not 'try ubuntu' from the live CD; although, I have a strange feeling it may not work. Give me a minute and I will have an answer for you...

---

### Post by fela on 2011-04-03
When it boots to the terminal, try pressing Ctrl+Alt+F7. What does that give? If it goes to a black screen, or doesn't do anything, try Ctrl+Alt+F8 or maybe F9 too.

---

### Post by THGIC on 2011-04-03
As a matter of fact, it does boot to a desktop. I ran the 'Try Ubuntu' option and I am now in Ubuntu. 

Now, do you think it would be better to install from this point, versus when I installed it from boot up?

---

### Post by fela on 2011-04-03
> **THGIC said:**
> As a matter of fact, it does boot to a desktop. I ran the 'Try Ubuntu' option and I am now in Ubuntu. 

Now, do you think it would be better to install from this point, versus when I installed it from boot up?

I doubt it would make much difference, but it's worth a try, I guess.

---

### Post by Quackers on 2011-04-03
As has been said, that shouldn't make any difference afaik. As long as you use the same partitions it shouldn't cause any problems.

---

### Post by THGIC on 2011-04-03
I tried Ctrl + Alt + F7 first; it went to a black screen. I also tried + F8 and + F9; neither of those worked. 

     Originally, I thought it was a hardware issue; maybe my HDD was dying, so I ran stress tests on my HDD, and it passed. I am also downloading Ubuntu 11.04, so I will install that instead and see how it goes. I think it may have been just that particular version of Ubuntu that doesn't like the hardware. 

     Actually, now that I think about it, there was a message that stated something about my CPU not working with it.

---

### Post by fela on 2011-04-03
> **THGIC said:**
> I tried Ctrl + Alt + F7 first; it went to a black screen. I also tried + F8 and + F9; neither of those worked. 

     Originally, I thought it was a hardware issue; maybe my HDD was dying, so I ran stress tests on my HDD, and it passed. I am also downloading Ubuntu 11.04, so I will install that instead and see how it goes. I think it may have been just that particular version of Ubuntu that doesn't like the hardware. 

     Actually, now that I think about it, there was a message that stated something about my CPU not working with it.

I don't think the CPU message means anything, I get something on my Ubuntu 10.10 netbook saying the CPU lacks certain security features, doesn't seem to affect anything though.

Have you tried Ubuntu 10.04 LTS? It's the long term support release, so it might have more/better support for your machine. Also, 11.04 is (as you must know) still unstable, so I wouldn't attempt to use that, especially if the stable version isn't working.

---

### Post by Quackers on 2011-04-03
If you're having a problem with 10.10 I would not recommend moving to a beta release! Especially if it's intended to be used as a main system. It is very likely to get borked at some time!

---

### Post by THGIC on 2011-04-03
Alright, I will use 11.04 on my main machine: Sony Vaio VPCEB23FM/Bl. 

     I am going to try the 10.04 LTS version. The fact of the matter may be that 10.10 does not support some hardware in that model of Toshiba laptops. Hopefully, 10.04 LTS will have the hardware support. 

     Now, if 10.04 does not work -- is there any hope for my friend's Toshiba laptop? He had Windows 7 and I wanted to bring him to the light (Linux OS). Plus, he does not have recovery discs, so my options from there would be; order from discs from Toshiba ($25 and arrives in ~2 weeks), buy Windows 7 OEM disc and do it from scratch, or use Ubuntu. My personal opinion, use Ubuntu -- overall, Linux is better, period.

---

### Post by Quackers on 2011-04-03
There should be an option to make a set of recovery dvd's. (Alternatively make a backup image with Clonezilla or Macrium Reflect or even Windows backup image itself). To be honest, if you have neither heard of these things, nor made backups before, it may not be the sensible choice to be installing OSes or partitioning anything.
You can also make a repair cd from Within Windows (for repair purposes, not recovery).

---

### Post by THGIC on 2011-04-03
I have Acronis and I have tried to recover the deleted partitions and such, but there is no such luck. I really need Recovery Discs or just an OS disc, so I can recover their unit back to day one. 

     If all else fails with 10.04 LTS, I will just grab an OEM Windows 7 disc and reinstall Windows. 

     Like I said, this is for my friend; I wanted to show him the beauty that is Linux, but it may not be his time to experience it. If so, then so be it.

     Thank you both for your thoughts, ideas, and very helpful support. I am truly grateful. 

Thanks again,

---

### Post by Quackers on 2011-04-03
No problem.
Your friend's computer is likely to have a recovery partition. If it has, there will be a program on the system to create a set of recovery dvd's. It is worth making those discs, if possible. It is also worth making the repair disc, via Control Panel > Backup & Restore centre, as you are likely to need one at some time.

---

### Post by 23dornot23d on 2011-04-03
> 
As a matter of fact, it does boot to a desktop. I ran the 'Try Ubuntu' option and I am now in Ubuntu. 

Now, do you think it would be better to install from this point, versus when I installed it from boot up?
Its probably just a [graphics card problem]("http://www.google.com/search?hl=en&client=ubuntu&channel=fs&q=graphic+problem+2011+toshiba&aq=f&aqi=p-p1&aql=f&oq=") ..... on the install .

In the old days I used to try different distros as some would pick up the graphics and others would not .....

It may be worth giving Linux Mint a try (or another distro ......) or try to work out if its the graphics card - what is it in the Toshiba ?

 That's ...... before giving up and going back to using Windows ........ 

If you got a terminal up from the install ..... and the fact you got a  desktop up from the Live CD ...... do you have a network connection too  ...... can you do 

sudo apt-get update from the terminal ......

might be worth trying this below ... ( just incase a update to one of the x files does any good )

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude safe-upgrade

also what happens when going in the option 2 on the grub boot menu and going into safe-graphics mode ...... does that work .........

or

Even try a different Desktop Manager ...... 
( just another option - as it runs ok from Live-cd it means that the graphics should run .... its working out where it fails from the install .....[COLOR=Red]** when [plymouth]("http://www.google.com/search?hl=en&client=ubuntu&hs=177&channel=fs&q=plymouth+problem+2011+toshiba&aq=f&aqi=&aql=&oq=") was messing me about one time **[/COLOR]- I swapped from gdm to kdm and got better results ..... )

sudo aptitude install kdm

A few more options hope this helps in some way .....

---

### Post by THGIC on 2011-04-03
> **Quackers said:**
> No problem.
Your friend's computer is likely to have a recovery partition. If it has, there will be a program on the system to create a set of recovery dvd's. It is worth making those discs, if possible. It is also worth making the repair disc, via Control Panel > Backup & Restore centre, as you are likely to need one at some time.

I wiped out the drive when I installed Ubuntu 10.10, because my friend did not have Recovery Discs. I mean, the partitions are unrecoverable. I have a good feeling about Ubuntu 10.04 LTS though. I haven't tried anything since my last post -- I work at the Geek Squad (I am busy all day). 

Do you have any other suggestions as far as versions of Linux go (Kubuntu, Linux Mint, YellowDog...)?

---

### Post by THGIC on 2011-04-03
> **23dornot23d said:**
> Its probably just a [graphics card problem]("http://www.google.com/search?hl=en&client=ubuntu&channel=fs&q=graphic+problem+2011+toshiba&aq=f&aqi=p-p1&aql=f&oq=") ..... on the install .

In the old days I used to try different distros as some would pick up the graphics and others would not .....

It may be worth giving Linux Mint a try (or another distro ......) or try to work out if its the graphics card - what is it in the Toshiba ?

 That's ...... before giving up and going back to using Windows ........ 

If you got a terminal up from the install ..... and the fact you got a  desktop up from the Live CD ...... do you have a network connection too  ...... can you do 

sudo apt-get update from the terminal ......

might be worth trying this below ... ( just incase a update to one of the x files does any good )

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude safe-upgrade

also what happens when going in the option 2 on the grub boot menu and going into safe-graphics mode ...... does that work .........

or

Even try a different Desktop Manager ...... 
( just another option - as it runs ok from Live-cd it means that the graphics should run .... its working out where it fails from the install .....[COLOR=Red]** when [plymouth]("http://www.google.com/search?hl=en&client=ubuntu&hs=177&channel=fs&q=plymouth+problem+2011+toshiba&aq=f&aqi=&aql=&oq=") was messing me about one time **[/COLOR]- I swapped from gdm to kdm and got better results ..... )

sudo aptitude install kdm

A few more options hope this helps in some way .....

In all honesty, I had a hard time comprehending a good bit of what you were trying to explain. As you can tell by my profile info, I am new to Linux in general; although, that doesn't mean that I am ignorant to any hardware/software issues (I am a geek; hence my profile picture). 

I did have an internet connection (1Gbps LAN) and chose to do third party software updates, while installing other updates. 

My only problem(s) with seeing it as a graphics card issue is; there would have been no display or it would have given me some sort of error code, stating that my graphics drivers weren't properly installed/configured. 

I think it was purely the fact that this Toshiba laptop was fairly new (~6 months old) and that 10.10 did not have the hardware support for either the Motherboard or the Hard Drive. 

Again, I am new to Linux (in general); so most likely, I could be miss informed.

---

### Post by THGIC on 2011-04-03
I just looked at that link you posted.

[http://www.google.com/search?hl=en&client=ubuntu&hs=177&channel=fs&q=plymouth+problem+2011+toshiba&aq=f&aqi=&aql=&oq=](http://www.google.com/search?hl=en&client=ubuntu&hs=177&channel=fs&q=plymouth+problem+2011+toshiba&aq=f&aqi=&aql=&oq=)

Those screen shots are basically what appears on my screen when trying to boot into Ubuntu. I can't figure out why it does it though.

---

### Post by THGIC on 2011-04-03
[http://ubuntuforums.org/showthread.php?p=10331367](http://ubuntuforums.org/showthread.php?p=10331367)

That thread solved the issue.

'sudo nano /etc/modprobe.d/blacklist' opened a file and
'blacklist intel_ips' added the intel_ips module to the blacklist. 

It took out the driver for it and it said it was running on a low graphics setting -- I would need to manually change that. 

Thanks all for the help.

---

### Post by 23dornot23d on 2011-04-03
> 
My only problem(s) with seeing it as a graphics card issue is; there  would have been no display or it would have given me some sort of error  code, stating that my graphics drivers weren't properly  installed/configured. 
Sometimes you will find the errors in the logs ...... for issues at boot-up - including kernel and graphics card issues as well as a whole lot of other stuff - that may otherwise go by un noticed.

System - Administration - Logfile viewer

Glad you got it working ......

---

