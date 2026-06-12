---
title: "Fan not working upon upgrade 8.10 to 10.04"
date: 2013-09-24
forum: Installation &amp; Upgrades
---

### Post by luiznetto on 2013-09-24
Hi. My roommate just upgraded my Ubuntu 8.04 to 10.04 (Lucid Lynx) on my Acer Aspire 5315. When I arrived home and tried to use the computer, I noticed the fan was not working properly, the laptop was overheating and shutting down. I realize there is already a thread for this (Acer Aspire 5315 Shuts Down, Hardware & Laptops), but it's quite confusing. Some suggest that I flash the BIOS, which I am not willing to do because I know it's a dangerous procedure, and I'm not prepared for total loss of the computer. But according to Isparkes,

[http://ubuntuforums.org/showthread.php?t=604158&page=12&p=4925392#post4925392](http://ubuntuforums.org/showthread.php?t=604158&page=12&p=4925392#post4925392)

this may not be necessary. Some suggest that I install lm-sensors (is that an L or an I as in "Italy"?) and conky; some say I should install computertemp instead of conky. Another poster said I should download and install acer_fancontrol.tar.gz. Some Ubuntu documentation says Gnome sensors-applet should solve the problem:

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Another Ubuntu site suggests yet another way to solve the problem:

[http://askubuntu.com/questions/22108/how-to-control-fan-speed](http://askubuntu.com/questions/22108/how-to-control-fan-speed)

Which one is more likely to work, without having to upgrade the BIOS? The fan itself - the hardware, I mean - seems to be working all right, because I am typing this right now with the Ubuntu 8.04 live CD.

Any imputs and I will be very grateful.

Luiz

---

### Post by mörgæs on 2013-09-25
Both 8.10 and 10.04 are obsolete. A good first try is a fresh install of 13.04.

Have you seen warnings about upgrading BIOS on this particular Acer?

---

### Post by luiznetto on 2013-09-25
I don`t know if it will work on my machine. And, to upgrade anything right now, I first need the fan to work, otherwise if the fan doesn't work during the upgrade, I am lost.

---

### Post by Topsiho on 2013-09-26
mörgæs wrote: "Both 8.10 and 10.04 are obsolete. A good first try is a fresh install of 13.04."

That's quite correct, only I think you should go for Ubuntu 12.04.3, as this is far longer supported.
I am not sure whether this applies for 13.04 already, but the newer Ubuntu non LTS versions are only supported for 9 months, so you would have to replace 13.04 very soon.

The LTS version 12.04 is supported for 3 years on the desktop, so it still lasts much longer than the newer 13.04.

Topsiho

---

### Post by kamranm1200 on 2013-09-26
> **Topsiho said:**
> mörgæs wrote: "Both 8.10 and 10.04 are obsolete. A good first try is a fresh install of 13.04."

That's quite correct, only I think you should go for Ubuntu 12.04.3, as this is far longer supported.
I am not sure whether this applies for 13.04 already, but the newer Ubuntu non LTS versions are only supported for 9 months, so you would have to replace 13.04 very soon.

The LTS version 12.04 is supported for 3 years on the desktop, so it still lasts much longer than the newer 13.04.

Topsiho

I am not sure he should use 12.04. It's a terrible version of Ubuntu. I would recommend 13.04. Yeah, try 13.04 and see if that helps.

---

### Post by Topsiho on 2013-09-26
luiznetto wrote  "I don`t know if it will work on my machine. And, to upgrade anything right now, I first need the fan to work, otherwise if the fan doesn't work during the upgrade, I am lost. "

That's indeed a real problem.

An ==> upgrade <== can last very long, depending on what you already have installed on your computer, which has to be replaced. All the replacements have first to be downloaded, which may be very much more than the download of a complete version of Ubuntu. And have to be installed. The process may take hours, during which your computer may easily get overheated.

A NEW install however, is much "cooler" to do, I hope cool enough:

You first have to download a new version of Ubuntu (12.04.03), and either burn it on a dvd (as image), or create an USB stick from it.
This you can do on another computer, if thia alltakes a too long time.

Then you install the new version on your computer, which takes entering the information it needs, and after that the actual install may be done, which on my slowest (8 years old) computer takes about half an hour, and on my fastest computer 7 minutes (with language support, which you may omit or do later, and which takes a lot of the install time).

Maybe this can help you :)
During the process you might let an exteriour fan blow into the computer case ...., just an idea.

After this you have to reinstall the applications you use. leaving out the unused ones :)

Back up all your precious data first!!!

it is lm-sensors, wih the l of Lima

Topsiho

---

### Post by Topsiho on 2013-09-26
"I am not sure he should use 12.04. It's a terrible version of Ubuntu. I would recommend 13.04. Yeah, try 13.04 and see if that helps."

I use 12.04 from day zero, and still have to discover how terrible it is. So far no success :)

It is true that Unity develops fast, and in 13.04 has attained new heights. But the time that 13.04 is maintained is anyhow much shorter than that for 12.04(.3).  You can also wait until 14.04 comes out, in april 2014, which will be supported for 5 years I think (and be really obsolete in 2019!).
Then there is 13.10 which is released next October, and will last only 9 months, this time for sure. But will have the newest Unity so far.

Topsiho

---

### Post by mörgæs on 2013-09-26
Time for some experimenting. How does it work in a live boot of Lubuntu 13.04?

---

### Post by luiznetto on 2013-09-26
The problem with upgrades is this: I am never sure an upgrade will work on my machine. There is often hardware incompatibilities. If I am having ***this*** trouble upgrading from 8.04 to 10.04 (the fan isn't working!), imagine how much trouble I will have upgrading to a newer version! I bought this laptop in 2008. I had the same problem - hardware incompatibility - when I installed 8.04 - my wireless card wouldn't work, and I had to find, download and install a tarball to operate it, which consumed a lot of time. Sometimes the live CD/DVD works fine, but when you try to install it, the installation aborts.

By the way, does any of you guys know if there is a command in Linux that turns the fan on/off, as you have the command

$ eject

that does nothing but eject your CD/DVD? That could be very useful to test the hardware.

Another doubt that I have is: I would like very much to install Gnome sensors-applet

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

because it's a very nice idea to have something on my panel that indicates temperature, fan speed, etc., but I don't know if for this to work I have to install the acer_fancontrol tarball first, if it conflicts with the Gnome applet, or if computertemp is a better option.

I don`t care if a version is "obsolete", as long as it works satisfactorily on my machine. 8.04 was working fine until yesterday (well, a little slow when I went to some websites), but other than that it was excellent.

---

### Post by mörgæs on 2013-09-26
By obsolete I mean that no security holes are fixed. You might be an easy target for an attacker. 

Why do you wonder about incompatibility when you can just test it in a live boot?

---

### Post by luiznetto on 2013-09-28
I tried the solution proposed by isparkes:

[http://ubuntuforums.org/showthread.php?t=604158&page=12&p=4925392#post4925392](http://ubuntuforums.org/showthread.php?t=604158&page=12&p=4925392#post4925392)

and it didn`t work. I installed the acer_fancontrol tarball. When I get to the point when I do

sudo ./acer_fancontrol

I see all the expected messages, but I don't hear the fan. It continues to overheat and shut down.

But it's not just the fan that's not working. Several keys changed function during the upgrade - which is an easy problem to fix, I admit, I know how to use xmodmap - but there are also problems with boot. Sometimes boot is aborted, sometimes it boots with a lot of strange messages and gibberish running on the black screen, things that shouldn't be there. The whole system is behaving very weirdly. I guess I'll have to uninstall 10.04 and either go back to 8.04 or install another operating system.

---

### Post by mörgæs on 2013-09-28
An upgrade can make a complete mess of an operative system and it seems like it has happened to you. Much more than the fan control is wrecked.

Using a five years old thread for troubleshooting is not likely to help; my advice is still a live boot of 13.04. 

Signing out.

---

### Post by whitesmith on 2013-09-28
I once had a similar problem with a laptop. I started the installation from a DVD and then placed the laptop in a refrigerator and allowed installation to proceed. Sounds a little extreme, but it worked!

---

