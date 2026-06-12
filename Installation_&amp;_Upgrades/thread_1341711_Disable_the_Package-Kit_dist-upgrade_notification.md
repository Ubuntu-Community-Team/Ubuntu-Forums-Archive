---
title: "Disable the Package-Kit dist-upgrade notification"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by JNowka on 2009-11-30
I have dealt with this for a while, but now its driving me a bit insane.  I am working on a laptop that I use as my software development system.  I have spent many hours customising everything so that it will just work.  And as of now it is running near flawless.  With what I have heard with karmic, i am willing to hang back and wait for the next iteration of ubuntu to come out.  But I have this notification in my taskbar that keeps coming up notifying me about a dist-upgrade to karmic koala 9.10.  I have gone to System Settings -> Notifications and unchecked all the dist-upgrade options.  Yet it remains.  Does anyone know how to disable it so that it doesn't show for dist-upgrade anymore.  I do want to see it when I have bug fixes and the like.      

Thanks,  
j

---

### Post by gawadelnil2002 on 2009-12-04
I had the same problem, I wanted always to disable this in jaunty and when I googled that I just found your thread that no one replied to it .

And way CONGRATULATION .............   I solved That by my own efforts

just open the terminal and type
```
sudo nano /etc/update-manager/release-upgrades
```Then edit that file
```
# default behavior for the release upgrader
#

[DEFAULT]
# default prompting behavior, valid options:
#  never  - never prompt for a new distribution version
#  normal - prompt if a new version of the distribution is available
#  lts    - prompt only if a LTS version of the distribution is available
Prompt=[COLOR=Red]normal[/COLOR]
```                         You will notice that if you replaced "[COLOR=Red]normal[/COLOR]" by "never", it will stop dist-upgrade notification, that dose not mean that will stop all notifications, it will stop only the release upgrade one :)........... I think u like that :)

Then "ctrl+x" to save the changes
done..

---

### Post by presence1960 on 2009-12-04
Go System > Administration > Software Sources. Select Updates tab and set Release Upgrade to "never". See below pic

---

### Post by gawadelnil2002 on 2009-12-04
> **presence1960 said:**
> Go System > Administration > Software Sources. Select Updates tab and set Release Upgrade to "never". See below pic


That will never happen in kubuntu (**jaunty**)

look at this I just taked from my machine

The terminal way is the only way I can do it in jaunty

---

### Post by presence1960 on 2009-12-04
> **gawadelnil2002 said:**
> That will never happen in jaunty

look at this I just taked from my machine

The terminal way is the only way I can do it in jaunty

**_you did not say you were running Kubuntu._**

**_My bad, did not notice it in your info w/avatar!_**

---

### Post by gawadelnil2002 on 2009-12-04
I need something if anybody can help, firefox 3.5 is not good in jaunty , it's still called shiretoko and it takes time before loadiing page
I did google that but and I followed some threads to tweak firefox like network pippling stoping ipv6 but all didn't help

---

### Post by presence1960 on 2009-12-04
> **gawadelnil2002 said:**
> e

I believe I already corrected myself, but if you have the need to do so again for me that is ok with me.

---

### Post by gawadelnil2002 on 2009-12-04
> **presence1960 said:**
> I believe I already corrected myself, but if you have the need to do so again for me that is ok with me.
  I'm sorry I didn't mean to correct you just, I'm not kind of guys love to correct people and I will erase what I wrote ,I was removing my replay when I realized that u corrected yourself
Sorry again

---

### Post by presence1960 on 2009-12-04
> **gawadelnil2002 said:**
> I'm sorry I didn't mean to correct you just, I'm not kind of guys love to correct people and I will erase what I wrote

It is no big deal really, I like to have some fun in here. That is the problem with the written word- you can't see body language and hear sarcasm & the like. You really didn't have to erase it.

---

### Post by gawadelnil2002 on 2009-12-04
> **presence1960 said:**
> It is no big deal really, I like to have some fun in here. That is the problem with the written word- you can't see body language and hear sarcasm & the like. You really didn't have to erase it.

hahhahahah yeah it is better than no one can hear what I say just see it's enough for reading 
my accent is not good english......... I'm egyption

---

### Post by presence1960 on 2009-12-04
> **gawadelnil2002 said:**
> hahhahahah yeah it is better than no one can hear what I say just see it's enough for reading 
my accent is not good english......... I'm egyption

it is all good. It should not matter in person either, but you know some people have hard to break ways.

---

### Post by JNowka on 2009-12-05
gawadelnil2002:   
   Thank you for your help, this helps a lot.  

presence1960:   
   Thanks for your help, though I am running Kubuntu.

---

