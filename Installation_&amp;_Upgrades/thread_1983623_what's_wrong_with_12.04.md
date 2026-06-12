---
title: "what's wrong with 12.04"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by truico on 2012-05-20
:confused: My life with Ubuntu used to be pleasant, inspiring, relaxed, etc. etc. But since I upgraded from 11.10 to 12.04 on my laptop (brand new Lemur Ultra 64 bt) I get 'system error', however without any noticeable bug. 
On my Dell Inspiron 530 I tried to upgrade as well, but after some hesitation decided to get a clean install. Result: same 'system error' and freezing of pages/mouse while scrolling. 
Rather irritating, since all I can do is cut off the system the hard way. Another thing that bothers me is the terrible slow startup of both machines. Does this problem look familiar?
I spent some time searching the forums, but so far no good.

Hence my question: does anyone of you forum friends experience something similar? Does it make sense to wait for a 'repair'- upgrade? Or shall I go back to 11.10? Which would be a shame, for 12.04 looks very beautiful.

---

### Post by jadtech on 2012-05-20
the system error notice is a bug they are aware of  I seen a post some where as well as notes in documentation how to shut the notice off .. 

the freezing of the mouse while scrolling I  do notice that  now and again  how ever I never noticed  any issue untill I installed compiz and tweak started installing various transparent and 3d themes ..

any freezing is generally video card related I know the dell 5030 I had running 11.10 and 12.04 I could only  boot ubuntu 2d the ati card just wasn't up to the job on 12.04  I could load ubuntu 3d and see the Icons  and effect in launcher I just couldn't scroll or use it   .. 

as for booting  I find booting 12.04 dose take a bit  even with the quad core processor and 7gb of ram how ever unlink window  you really dont need to reboot  that often unless there  is an update requiring  it .. 

found there is an issue with the logitech wireles moiuse  too not alway being detected on restart unless you go to the effort of moving the mouse  on the desk top before  logging in with your password if you do that it is dected and woeks everytime who knows why ..

---

### Post by wilee-nilee on 2012-05-20
> **truico said:**
> :confused: My life with Ubuntu used to be pleasant, inspiring, relaxed, etc. etc. But since I upgraded from 11.10 to 12.04 on my laptop (brand new Lemur Ultra 64 bt) I get 'system error', however without any noticeable bug. 
On my Dell Inspiron 530 I tried to upgrade as well, but after some hesitation decided to get a clean install. Result: same 'system error' and freezing of pages/mouse while scrolling. 
Rather irritating, since all I can do is cut off the system the hard way. Another thing that bothers me is the terrible slow startup of both machines. Does this problem look familiar?
I spent some time searching the forums, but so far no good.

Hence my question: does anyone of you forum friends experience something similar? Does it make sense to wait for a 'repair'- upgrade? Or shall I go back to 11.10? Which would be a shame, for 12.04 looks very beautiful.

Download the cd and run it live to see if you have the same problems. If not you might consider a fresh install along side the problematic one and dragging and dropping what you need, including PPA's and extra repos, make a instaledl list from the first with.

dpkg --get-selections > installed-software

And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,

Code:
dpkg --set-selections < installed-software

followed by
Code:
dselect

And just install the same stuff in the new setup.

Personaly I never upgrade but make this list and save the repos and install.

---

### Post by truico on 2012-05-21
:pThank you for your reactions. 
Jadtech said: *you really dont need to reboot that often unless there is an update requiring it ..* All true, but if nothing moves any more, what else is there to do?
Re. WileeNilee: your instructions I will follow the next time:
[I][I]Download the cd and run it live to see if you have the same problems. If not you might consider a fresh install along side the problematic one and dragging and dropping what you need, including PPA's and extra repos, make a instaledl list from the first with.

 dpkg --get-selections > installed-software

 And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,[/I][/I]

 Code:
 dpkg --set-selections < installed-software

 followed by
 Code:
 dselect

 *And just install the same stuff in the new setup.*

Thanks.

---

### Post by bariamtak on 2012-05-21
> **wilee-nilee said:**
> Download the cd and run it live to see if you have the same problems. If not you might consider a fresh install along side the problematic one and dragging and dropping what you need, including PPA's and extra repos, make a instaledl list from the first with.

dpkg --get-selections > installed-software

And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,

Code:
dpkg --set-selections < installed-software

followed by
Code:
dselect

And just install the same stuff in the new setup.

Personaly I never upgrade but make this list and save the repos and install.

I don't mean to hijack this thread but as far as i've noticed , the problems seem to be with upgrading. I also upgrade from 11.10 to 12.04 and now I get system error quite frequently. sometimes the system hangs but its not that frequent. I am using HP laptop. 
I do a fresh install  (ubuntu 12.04 ) in one desktop which is an IBM but no error of the sort happens. So i am concluding that it is related to upgrading.
And for the options of a fresh install over upgrading i don't like it very much because I hate to waste my time again in customising the settings and all that stuff ( if you know what i meant ). I have many applications which are installed manually and i don't want to repeat installing them. I prefer upgrading and tweak around with my problems which seems not very serious , and above all we have the forum if we ever encounter serious problems.
And to the problem of freezing i think someone will come up with a workaround.

---

### Post by collisionystm on 2012-05-21
I get the same system error message as well.

Clean Install. 64 bit.

---

### Post by jadtech on 2012-05-21
this error message  in 12.04 is hard to search about because it is so common and is happening to people upgrade or clean install.. 

I get that error message on  this new HP g6 I started with a clean install at frist I didnt have the error at frist and though it can be closed seems to hang  trying to report the error .. 

i just found a post about this  error on google just want to check if we all have some programs in common first weather indicator second is newest version of  conky  with a script they run  the script works but if you leave the terminal up you can see some part of the script fail but  you  ignore it .. 

weather indicator is first on my list because before I installed this program I didn't get the error at all, after I installed it I noticed once in a while I would get the notice about  some error or internal,  error in testing I discovered I can replicate the error message almost always geting to popup by just logging out not reboot or shut down but logging out and logging back in .. 

first thing noted is that  though weather indicator is  running the menu for it is no longer on the top bar menu it is missing if you dont notice or ignore the fact in a short time the error message will popup if you click the weather indicator icon the menu will reapear and be fine no error messages .. 

conky running the script is showing errors , on this HP g6 I get an error message any time I run a script with a fan speed command  the there is apparently the sensor probed for does not work to indicate fan speed and will over time cause internal errors to  popup the  other suspect I have seen is running a conky scripts for weather that no longer work most use curl to check forcast where it is no longer offering service for free ..

removing any of these solve error messages I have seen your mileage may vary

---

### Post by rewyllys on 2012-05-21
> **bariamtak said:**
> . . . . And for the options of a fresh install over upgrading i don't like it very much because I hate to waste my time again in customising the settings and all that stuff ( if you know what i meant ). I have many applications which are installed manually and i don't want to repeat installing them. . . .
You could avoid having to recustomize "the settings and all that stuff" by putting your "/home" directory on a separate partition from your "/" (root) directory.  

That way, the fresh install goes on the "/" directory's partition without changing anything in the "/home" directory's partition.  The new install will pick up your configuration settings and other stuff from the unmodified "/home" directory.

---

### Post by bariamtak on 2012-05-22
> **rewyllys said:**
> You could avoid having to recustomize "the settings and all that stuff" by putting your "/home" directory on a separate partition from your "/" (root) directory.  

That way, the fresh install goes on the "/" directory's partition without changing anything in the "/home" directory's partition.  The new install will pick up your configuration settings and other stuff from the unmodified "/home" directory.
Oh thank you for the tips. Maybe someday it'll come handy.

And coming to system errors , I 'd like to inform all that I am also using weather indicator and screenlets .But i'm not sure if they're the cause for it because my weather indicator has no problem . But sometimes the screenlets ( i.e, system Monitor) use to change its position. Well i am no expert.

---

### Post by truico on 2012-05-24
Hi,

As far as the 'system error' is concerned: I've decided to ignore 'm since nothing seems to be wrong so far. 

The solution for the 'freezing' I found at the Dutch Ubunteiro-site and is as follows: it seems the Nvidia drivers are conflicting with Ubuntu-12.04. Someone suggested to remove them both (system settings). Which I did, and, lo & behold: no more freezes! Wow. :P :lolflag:

(Keep fingers crossed:) problem solved.

---

