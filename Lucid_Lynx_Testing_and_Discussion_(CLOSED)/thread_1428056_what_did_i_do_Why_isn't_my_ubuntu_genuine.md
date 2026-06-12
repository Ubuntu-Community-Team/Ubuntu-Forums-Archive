---
title: "what did i do?? Why isn't my ubuntu genuine??"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rahilm on 2010-03-12
I decided to try ubuntu software center to check it out. I find that i can't install packages because it doesn't have application data. It says to update it. There is also an "Update now". button below. When i click on it. software center crashes. When i try to repost the issue. I am told my ubuntu isn't genuine. I don't understand. What did i do? Does installing ppa makes ubuntu not genuine??
I have attached screenshots.

(Also on a much unrelated not, the guest session does not work)

---

### Post by philinux on 2010-03-12
It just means gvim is not part of the ubuntu repositories.

---

### Post by rahilm on 2010-03-12
> **philinux said:**
> It just means gvim is not part of the ubuntu repositories.
then what is?..name one application that is part and i'll check updating that one and reply

---

### Post by rahilm on 2010-03-12
That thing also happens with Kate...well that HAS to be in the repositories..
i m telling you, it has to do with the software center crashing because that message does not show up if i don't report the bug.

---

### Post by ranch hand on 2010-03-12
So, have you tried to get the same package by using apt-get install.  Seems like that would be the first thing to try.  If it goes there then you know the problem is USC.  If it doesn't then it would be time to post here with a real question.

---

### Post by VMC on 2010-03-12
> **ranch hand said:**
> So, have you tried to get the same package by using apt-get install.  Seems like that would be the first thing to try.  If it goes there then you know the problem is USC.  If it doesn't then it would be time to post here with a real question.

Either that or synaptic or aptitude.

---

### Post by rahilm on 2010-03-12
> **ranch hand said:**
> So, have you tried to get the same package by using apt-get install.  Seems like that would be the first thing to try.  If it goes there then you know the problem is USC.  If it doesn't then it would be time to post here with a real question.
sudo apt-get and synaptic works fine. Its the ubuntu software centre which doesn't. The real question is why i can't post the bug i am getting and why is it showing that my ubuntu isn't genuine.

The objective here isn't to get kate  or gvim installed on my system. This is not the system I am using. It is just for testing purposes. I tested the USC, it didn't work. I tried to submit the bug through apport, it didn't work. i don't know what else to do so i came here.

---

### Post by NCLI on 2010-03-12
> **rahilm said:**
> sudo apt-get and synaptic works fine. Its the ubuntu software centre which doesn't. The real question is why i can't post the bug i am getting and why is it showing that my ubuntu isn't genuine.

The objective here isn't to get kate  or gvim installed on my system. This is not the system I am using. It is just for testing purposes. I tested the USC, it didn't work. I tried to submit the bug through apport, it didn't work. i don't know what else to do so i came here.

Is your system fully up-to-date?

---

### Post by kernco on 2010-03-12
It is not saying that YOUR Ubuntu isn't genuine.  It's saying that the gvim package is not a genuine Ubuntu package, meaning that bugs with gvim do not belong in the Ubuntu bug tracker because it's not Ubuntu's responsibility to fix it.

---

### Post by BwackNinja on 2010-03-12
Did you add a ppa and not add the corresponding key?

---

### Post by rahilm on 2010-03-12
> **NCLI said:**
> Is your system fully up-to-date?
NO. not at all. i see that's the problem. i'll try to update it then. It will update overnight.
one question: do i update it with:
sudo apt-get upgrade
OR
sudo apt-get dist-upgrade

because the dist-upgrade brings up a lot more packages than upgrade


> **kernco said:**
> It is not saying that YOUR Ubuntu isn't genuine.  It's saying that the gvim package is not a genuine Ubuntu package, meaning that bugs with gvim do not belong in the Ubuntu bug tracker because it's not Ubuntu's responsibility to fix it.

All i know is that I can't install software through the USC. And I even can't submit bugs.  I tried Gvim, Kate, Pidgin, Tracker Search tool, tux paint, and even GIMP.
All these are canonical maintained application as i selected it in the 'View' menu.

Nevertheless, I'll try updating the system overnight.

---

### Post by teh603 on 2010-03-12
I'd suggest against using the Software Center, and sitck to Synaptic or apt-get if you're more comfortable with the command prompt.

At least it actually tries to download software in Lucid. The one in Karmic just sits there like a bump on a pickle.

---

### Post by ranch hand on 2010-03-12
I would just do the apt-get  upgrade.  There are some packages that need held back.

If you, then, still have the problem with USC do;
```

ubuntu-bug software-center

```
and that should do it.

I had a little trouble finding the correct name of the package (don't use it myself), but I did run the above command and it did start collecting data for the bug report before I canceled it.

If you do file the bug post back and some of us will give it a try and see if we can confirm your bug.  Give a link to the bug.

I would  like to know if you are on dialup as you mentioned updating over night.  I am on dsl right now but hope to get another ranch job that has me out of range for that.  Dial up is sometimes tough to get working in Ubuntu so I am wondering about 10.04.

Sorry to get off topic.

---

### Post by phillw on 2010-03-12
> **rahilm said:**
> 
one question: do i update it with:
sudo apt-get upgrade
OR
sudo apt-get dist-upgrade

because the dist-upgrade brings up a lot more packages than upgrade


I was advised to use ```
sudo apt-get update
sudo apt-get dist-upgrade
```

> so anything that needs to be uninstalled is. 

From CLI, if you're not using Update Manager (which I use for 10.04 'main').  
I use it in Lubuntu - so far, so good :D

Regards,

Phill.

---

### Post by VMC on 2010-03-12
The latest upgrade, has USC on the list. Its now V1.1.17

---

### Post by rahilm on 2010-03-13
I updated the USC it is now 1.1.17. Now it doesn't crash when i click on  "Update Now". Rather, it downloads some 11mb worth data and does  nothing afterwards. I've clicked it at least three times, only got 35mb  downloaded..
 
 i'll stick to synaptic and apt-get in the near future. I have acutally  never used USC or even the previous Add/Remove even when I was new to  ubuntu and didn't knew how to install software. The tutorials here and  there said that add/remove was excellent and software installation is  better in ubuntu than in windows..but I disagreed then and so do now..
 
 USC is "tried and failed" in the alpha 3 for me.
 
 NOTE:

> **ranch hand said:**
> I would just do the apt-get  upgrade.  There are some packages that need held back.

If you, then, still have the problem with USC do;
```

ubuntu-bug software-center

```and that should do it.

I had a little trouble finding the correct name of the package (don't use it myself), but I did run the above command and it did start collecting data for the bug report before I canceled it.


If you do file the bug post back and some of us will give it a try and see if we can confirm your bug.  Give a link to the bug.

I think something isn't right. When i executed that, apport sprang up and started collecting information about the said bug but the resut was the Same "The ubuntu package isn't genuine". I have attached screenshot as well.

> **ranch hand said:**
> 
I would  like to know if you are on dialup as you mentioned updating over night.  I am on dsl right now but hope to get another ranch job that has me out of range for that.  Dial up is sometimes tough to get working in Ubuntu so I am wondering about 10.04.

Sorry to get off topic.

ohh..that..i am on dsl. current speed is 55 Kb/s and fluctuating so it takes about 1.5 hours to download 303mb of updates. I am kinda lucky to have an unlimited broadband connection. The time of posting is late in the night. so i decided to start two simultaneous downloads and go to sleep.
The sad part is ubuntu enters into sleep mode by default if nothing is done for 30 minutes. The alpha version of lucid which I had supposedly crashed while in sleep mode. I realised that when i woke up around 6 am . so i disabled it and started again.

On a much unrelated note: I think what i downloaded was Alpha 2 instead of 3. it has become 3 now. I know that because now I can see the new brand art, new themes and the heavily criticised window-buttons-on-the-left look. There are also new menu items here and there.

---

### Post by ranch hand on 2010-03-13
I never liked add/remove either (MS or Ubuntu).  Software center, so far, seems kind of silly.

The search function is nice.

I use apt for most updating and synaptic for research.  Why we need yet another layer on top of dpkg is beyond me.  The more complex you make something the more it has to break.

---

### Post by rahilm on 2010-03-13
> **ranch hand said:**
> I never liked add/remove either (MS or Ubuntu).  Software center, so far, seems kind of silly.

The search function is nice.

I use apt for most updating and synaptic for research.  Why we need yet another layer on top of dpkg is beyond me.  The more complex you make something the more it has to break.
what search funtion??

anyway..to be back on the topic the 'help' program crashed (although i didn't notice, it started and closed normally but apport says it did crash) i tried sending another bug report but i am getting the same response

It seems the problem is really with apport..or my ubuntu box

---

### Post by coffeecat on 2010-03-13
> **rahilm said:**
> what search funtion??


This search function?

---

### Post by VMC on 2010-03-13
Unless some major work is being done on USC, I don't think I will be using it. I'm completely updated and trying to use it took forever. And to top it off it some how got confused. 
I went to game section and it brought claws-mail! WTF! Then I tried to go to the beginning page and it froze solid.

Hopefully by the time it is slated to replace Synaptic it will improve.

---

### Post by rahilm on 2010-03-13
> **coffeecat said:**
> This search function?
oh..there is one in synaptic. and the difference is that it displays the packages and **I** can install them.

Coming back to the topic of this thread, which is not for discussing USC. I find that I cannot submit any bugs via apport because it says the ubuntu package isn't genuine. I have seen some threads in this forum where apport does not connect to server. I think mine is a unique problem. So i'll probably not submit bugs anymore ubtil I re-install everything.

---

