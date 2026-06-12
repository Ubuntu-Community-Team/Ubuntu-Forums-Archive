---
title: "Buggies during bootup - OS still works though"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by linuxinstalledfromhdd on 2010-05-19
Hi there everyone.. I have been using ubuntu and kubuntu now for about 2-3 years non-stop, and I was originally a windoze user, so please bare with me.. I'm not a god at this stuff....

The previous couple of versions of ubuntu I have been using, have had a few glitches after their immediate initial releases, so I have come to the conclusion now whenever a new release is made there will be issues for a while until someone figures them out..  

As I am sure most of your are aware, during bootup of either ubuntu 10.04 or kubuntu 10.04,we will catch little bugs ..  they will interupt the new plymouth splash theme for a moment, and then the system will boot as a normally. Kubuntu was a little worse, after using remastersys to create a bootable live disc.. It seems that during the bootup of the live disc which I have created with remastersys using originally a fresh install of Kubuntu I see "Bios xxxx-xxxx errors" (I'm not 100% sure what they say, because they go by pretty fast) and I just don't know how to freeze the screen long enough to report exactly what is telling to repeat them here..  The bug that I get normally during bootup of Ubuntu is "Glib error" something to do with "non valid user"..  Every-time I have installed it on my system or Virtualbox from a fresh install - after doing the updates and putting everything on it that I normally like to have for applications and codecs etc, I will start to see errors eventually creep into the Plymouth boot splash process. And I guess if there is no solution at this point, I would like to keep the 10.04 and revert back to 9.10's splash screen and back to when there were no errors.. Is this because of the new graphical drivers in 10.04? Any idea why is it is bad?

I doubt for some reason that I am the only user with these issues on a fresh install of either Ubuntu of Kubuntu, and I just want to know to know if there is anything I can do to help? I don't seem to find maybe people out there reporting this.. Maybe for the fact that we can't stop the screen from progressing to the next stage of bootup long enough to copy the errors to post them here. I don't know, but AFAIK the last version of ubuntu and kubuntu didn't have these problems with bootup.. Maybe with flash.. or maybe with something else...  And many of those previous problem with solved with work-around, and just using different software or drivers or whatever.. 

Again is there anything I can do to help? And how to stop the screen long enough to copy down my hand the errors I am catching during bootup?  Or is there already a solution at this point to switch back to a older splash from 9.10 available, because in my opinion, the system is running flawlessly for my purposes, except the splash screen is coping errors I have never seen before since I first began using Ubuntu or Kubuntu.

Thanks for any suggestions or help with this.. 

:guitar:

---

### Post by oldfred on 2010-05-19
Did you check in system, administration, log file viewer.

Typically all the messages are in log files. Check dmesg, message and possibly several of the other log files for errors and long times between entries (as if it is having trouble with an entry), or repeating entries where it trys to load something and then retries several times.

---

