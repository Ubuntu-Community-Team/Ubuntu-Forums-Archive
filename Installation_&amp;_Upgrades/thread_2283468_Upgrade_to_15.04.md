---
title: "Upgrade to 15.04?"
date: 2015-06-22
forum: Installation &amp; Upgrades
---

### Post by mlvmhn on 2015-06-22
I have recently upgraded my laptop with Linux Ubuntu. All works fine. 

But how do i get the latest version 15.04 of Ubuntu?

---

### Post by Bucky Ball on 2015-06-22
What release are you running now? When you say 'upgraded', do you mean you installed Ubuntu on your laptop or actually did a net upgrade from one release to the next? I'm presuming the former.

Be aware that if you are running 14.04 LTS it is supported for five years until 2019. 15.04 is supported until January 2016. If you're running 14.04 LTS, my only question would be why you would want to upgrade to 15.04. Best to have a specific reason to go from a rock solid LTS release to a two month old interim that has seven months support left. With Linux, as with Windows, if it ain't broke, don't fix it, and the latest is not necessarily the greatest, nor the most stable.

Without knowing what version you're running, to get 15.04 you do a clean install. If you are running 14.10 you can do a net upgrade via the update manager or terminal.

---

### Post by mlvmhn on 2015-06-22
ah, i did not know that. i run 14.04 LTS on my laptop now. i dl:ed it from the ubuntu website. 

so this means i do not need to upgrade for several years? 

but the thing is also, that on my stationery computer running Ubuntu 15.04 atm, when i had Ubuntu 14.04 LTS on it i got a question from the Software Center that 15.04 was available for dl. 

i could then choose if i wanted to install 15.04 or keep 14.04 LTS. This was made with a Terminal command although. 

so, in order to install 15.04, i must manually start the installation process right?

---

### Post by grahammechanical on 2015-06-22
If you installed 14.04 then Software and Updates is set to notify you of the next LTS release (16.04). It is the default setting for an LTS release. You can change the setting to be informed of the next available release which will be 15.04.

Go to System Settings>Software & Updates>Updates tab and look for the panel labelled Notify me of a new Ubuntu version and make sure the setting is For any new version. Then run Update Manager/Software Updater.

The default setting for an interim release is to be notified of the next available release.

Regards.

---

### Post by mlvmhn on 2015-06-22
K, will this only be for ready LTS versions, or for any other versions also like beta versions?

---

### Post by LastDino on 2015-06-22
> **mikael.hansson.967 said:**
> K, will this only be for ready LTS versions, or for any other versions also like beta versions?

15.04 is interim version. Not the LTS, so yeah, if you enable it, it'll notify you about it. 

Though, I don't suggest upgrading LTS to interim versions. It's not very informed choice to upgrade 5 year supported version for only one worth 9 months, and you'll be lucky if you didn't brake anything in between.

Also, just to be clear, you don't need to do version upgrade unless it's a LTS, but you do need to update whenever your software manager notifies you.

OR My favorite,  run this in terminal one by one almost every other day

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

```
 sudo apt-get autoremove
```

These will do your daily updating of available packages etc.. 
No need to get involved with GUI update manager

---

### Post by Bucky Ball on 2015-06-22
In any release, interim or LTS: Software and Updates> Update tab> Notify me of ... set it to notify of all versions or just LTS, whatever you want.

---

### Post by mlvmhn on 2015-06-22
Ok, so i think there is best to let it be LTS then. 

Will the next stable LTS be available to the software center?

---

### Post by LastDino on 2015-06-22
> **mikael.hansson.967 said:**
> Ok, so i think there is best to let it be LTS then. 

Will the next stable LTS be available to the software center?

Yes, if you've enabled it (take reference from Bucky Ball's post), it will notify you automatically.

---

### Post by Bucky Ball on 2015-06-22
Yes, LTS upgrades directly to LTS, leapfrogging the interims in between. Cool.

14.04 LTS will upgrade directly to 16.04 LTS. The five year release cycle is at this stage for the first time (it came in with 14.04 from memory as it used to be three years) so not sure if you can go directly 14.04 LTS> 18.04 LTS when that arrives, but doubt it. Too many changes. 

So, from the point release generally, which is about six months after the release, you can upgrade LTS to LTS. When 16.04 LTS reaches 16.04.1 LTS, about October 2016, you should be good to go with the upgrade from 14.04 LTS. You can, of course, upgrade to 16.04 anytime after the point release until the end of life for 14.04. :)

---

### Post by mlvmhn on 2015-06-22
Cool, so on my stationary computer i run Ubuntu 15.04. What and how will i do with that when the next stable release arrives?

My laptop runs 14.04 LTS, and it feels slower with Ubuntu 14.04 LTS. It has only 2 GB RAM and a 2 GHz Celeron processor. 

Is it any point of upgrading this to the next LTS?

---

### Post by v3.xx on 2015-06-22
> My laptop runs 14.04 LTS, and it feels slower with Ubuntu 14.04 LTS. It has only 2 GB RAM and a 2 GHz Celeron processor.
Have you tried any other desktops/WMs?  'Flashback' desktop could be installed to your current install, its a bit lighter.

---

### Post by LastDino on 2015-06-22
> **mikael.hansson.967 said:**
> Cool, so on my stationary computer i run Ubuntu 15.04. What and how will i do with that when the next stable release arrives?

My laptop runs 14.04 LTS, and it feels slower with Ubuntu 14.04 LTS. It has only 2 GB RAM and a 2 GHz Celeron processor. 

Is it any point of upgrading this to the next LTS?

I generally install Xubuntu on such a machines. It's worth taking a look at. There is also Ubuntu Mate, but I haven't tried it yet on low config.

---

### Post by mlvmhn on 2015-06-22
Ok, what about Lubuntu?

---

### Post by LastDino on 2015-06-22
> **mikael.hansson.967 said:**
> Ok, what about Lubuntu?

It's lighter than Xubuntu so sure. I've never used Lubuntu and if my memory serve me right, you'll be better served with googling your hardware compatibility with Lubuntu. Like Wifi and blutooth etc. There might be more threads here than what you'll need.

---

### Post by mlvmhn on 2015-06-22
Ok, i try :guitar:

---

