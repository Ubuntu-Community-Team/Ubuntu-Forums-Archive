---
title: "What the use of Unity, if it won't start up?!"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by Ariya243 on 2010-12-04
When the live CD is booted up, there is a notice saying Ubuntu is sorry, as there is no 3D support in the laptop. If the Live CD doesn't see the video card etc, then there is a problem.

The laptop has NVidia Geforce 310M, meaning it has the 3D support, only Ubuntu doesn't see it on live boot, so what the use of the Unity desktop?

The Gnome starts up. I have seen Gnome, but I'd like to see Unity.
How can I do it? I can of course download the NVidia driver. But to activate the driver, I have to restart the laptop, then the Live session would go away.

By the way, if Linux to be everybody's OS, I think the "restricted" drivers should be included, as they are allowed by the owners to be downloaded!

---

### Post by princemanjee on 2010-12-12
Agreed.. Distro FAIL. The purpose of a LIVECD is to test without install.. but in this case you can not test unity without installing. LAME.

---

### Post by Quackers on 2010-12-12
The purpose of the live cd is to allow you to see if your hardware will work in ubuntu and to get a general feel for the Ubuntu setup and usability. If all the drivers available were included in the cd it wouldn't be a cd any more - it would be a dvd.

---

### Post by princemanjee on 2010-12-12
That makes sense but then why make two distros called desktop and netbook when they are basically the same thing (gnome). Besides I find it curious thee 'netbook' edition has increased requirements compared to the desktop edition when most netbooks come with lower speed chips and less onboard ram than most desktops...

---

### Post by Quackers on 2010-12-12
I understand your point. I have not used the most recent live cd for the purposes of trying out Ubuntu, so I don't know the ins and outs of trying to use Unity on it. As far as I'm aware Unity requires 3D graphics drivers and as has already been said these can't be used in the live cd environment, which does seem a bit strange.
Maybe somebody who knows more about this will be able to give more insight into this problem.

---

### Post by coffeecat on 2010-12-12
> **princemanjee said:**
> Agreed.. Distro FAIL. The purpose of a LIVECD is to test without install.. but in this case you can not test unity without installing. LAME.

I presume you are using a Natty CD in which case the use of words such as 'fail' and 'lame' are inappropriate and offensive. Natty is still in the early Alpha stage. Much will emerge over the next few months. You can test Unity if you are using a video card that supports 3d with an open source driver. That means many Intel and ATI cards, but it does not include nvidia at the moment because the open source nouveau driver does not yet support 3d. Licensing issues mean that the proprietary video drivers cannot be included in the live CD. People can ***** and moan about that as much as they want, but that does not change a legal issue.

However, my understanding is that it is planned for the nouveau driver to support 3d by the time of final release of Natty, which means that a large majority of users will be able to test Unity from the Natty live CD when it does go final. You can enable 3d with the nouveau driver now using   an experimental package but it is obvious that this will need a lot of testing before it can lose its experimental status. Hence the need for alpha and beta testing.

---

### Post by Quackers on 2010-12-12
Thanks for the clarification coffeecat :-)

---

### Post by coffeecat on 2010-12-12
> **Quackers said:**
> Thanks for the clarification coffeecat :-)

Hi there, Quackers. Unity in the Natty Alpha live CD works just dandy on my Intel graphics laptop and my main desktop with an ATI card. Sometime I'll dust off my no2 desktop (made from a superseded m'board and some bits and pieces) which has a nvidia card, so that I can follow the progress, or otherwise, of 3d in Unity with nouveau. I've taken a solemn oath never to use a proprietary video driver again. :) I presume you're having to use the nvidia driver on your Vaio.

---

### Post by Quackers on 2010-12-12
That would be a correct assumption sir :-)

---

### Post by princemanjee on 2010-12-12
> **coffeecat said:**
> I presume you are using a Natty CD in which case the use of words such as 'fail' and 'lame' are inappropriate and offensive. Natty is still in the early Alpha stage. Much will emerge over the next few months. You can test Unity if you are using a video card that supports 3d with an open source driver. That means many Intel and ATI cards, but it does not include nvidia at the moment because the open source nouveau driver does not yet support 3d. Licensing issues mean that the proprietary video drivers cannot be included in the live CD. People can bitch and moan about that as much as they want, but that does not change a legal issue.

However, my understanding is that it is planned for the nouveau driver to support 3d by the time of final release of Natty, which means that a large majority of users will be able to test Unity from the Natty live CD when it does go final. You can enable 3d with the nouveau driver now using   an experimental package but it is obvious that this will need a lot of testing before it can lose its experimental status. Hence the need for alpha and beta testing.


The problem I have is that no where does it say "beta" or Unity only available on install. And I don't know about this Natty you speak of cause it says nothing about that on the download or feature page. So I am sorry if you feel offended or insulted because of my "*****ing and moaning" but the fact is it IS lame and it DOES fail for the purposes of testing.

I ALWAYS test a live version before wiping my root partition and installing. 

And you cant install the driver and test on a live because the nozap feature has been removed from the distro. 

As of the time of this post I installed it on a laptop with an nvidia chip and the netbook desktop doesnt even come up. 

And please explain how the netbook edition has higher requirements than the desktop edition... any one that has used a netbook knows they are EXTREMELY limited on resources and one of the main reasons I put wintendo back on my laptop is because Ubuntu kills the battery and heats up the GPU so badly I could cook and egg on my laptop (this happens without 3D desktop, with 3D desktop it takes about 10 min before the laptop starts lagging because the processor is overheated). Hence why I assumed the netbook edition would have a smaller footprint and be lighter. I think thats a reasonable assumption. This netbook edition was my last ditch effort before having to switch to something like puppy or DSL. THe screenshots make it look very appealing...

---

### Post by Quackers on 2010-12-12
It's perfectly clear what coffeecat is referring to in his use of the words "final release". Of course there is a "final release" of any version of Ubuntu.
To call somebody stupid who is taking the time to help you understand something is just ridiculous in my view, and it certainly won't result in people queuing up to help you in the future. We are all volunteers here.

The time for checking on what you are downloading is before you download it.

I would imagine that the "higher requirements" that you speak of are regarding 3d graphics which are needed to run Unity, but as I have never used a netbook or been interested in using one I can only guess in this respect.

---

### Post by uRock on 2010-12-12
The 10.10 Netbook image does work in LiveUSB mode with Unity. I know this for a fact as I use the LiveUSB to show off Unity to people who may be interested in it.

Your hardware may support 3D, but if the drivers aren't installed to the OS, shich it isn't when using the LiveCD, then you will not be able to see any of the 3D attributes.

If you are talking about Natty, then don't. The devs have too far to go to even think about judging the release for its quality.

---

### Post by princemanjee on 2010-12-12
> **Quackers said:**
> It's perfectly clear what coffeecat is referring to in his use of the words "final release". Of course there is a "final release" of any version of Ubuntu.
To call somebody stupid who is taking the time to help you understand something is just ridiculous in my view, and it certainly won't result in people queuing up to help you in the future. We are all volunteers here.

The time for checking on what you are downloading is before you download it.

I would imagine that the "higher requirements" that you speak of are regarding 3d graphics which are needed to run Unity, but as I have never used a netbook or been interested in using one I can only guess in this respect.

Well its clear that the release on their page is the "final" version on ubuntu.com. So I know what I downloaded... also if they are going to use the netbook edition to debut unity on ubuntu you would think they would make it availible on the live version.

---

### Post by Quackers on 2010-12-12
It is. Look one post up.

---

### Post by princemanjee on 2010-12-12
> **Quackers said:**
> It is. Look one post up.


It doesn't work without installing it... he had to "install it" to the usb to make it work...

---

### Post by Quackers on 2010-12-12
That's not what uRock wrote.

---

### Post by uRock on 2010-12-12
> **princemanjee said:**
> It doesn't work without installing it... he had to "install it" to the usb to make it work...

I use the LiveCD image on the USB, not an actual install on the USB. I use the method listed [here]("http://www.ubuntu.com/netbook/get-ubuntu/download") to place the Ubuntu ISO on a thumb drive. Which is the method I use to install ISOs. I don't use CD/DVDs anymore.

---

### Post by princemanjee on 2010-12-12
> **urock said:**
> i use the livecd image on the usb, not an actual install on the usb. I use the method listed [here]("http://www.ubuntu.com/netbook/get-ubuntu/download") to place the ubuntu iso on a thumb drive. Which is the method i use to install isos. I don't use cd/dvds anymore.



thank you !

---

### Post by uRock on 2010-12-12
Here is a screen shot of Unity running in Ubuntu 10.10 Netbook Edition running from a LiveCD.

Edit: I tested the same LiveCD on my desktop machine and no it doesn't work. I am guessing that the fact that this is a Netbook edition, that it only comes with known Netbook 3D drivers. I see nothing wrong with that. If it were the desktop edition, then yes, I would expect it to work on a desktop machine. I suspect it will work fine on most machines when Ubuntu 11.04 hits the shelves.

---

### Post by mixmastamyk on 2011-03-05
I got it to work like this ...

1)  Boot livecd
2)  Install drivers from the restricted drivers control panel
3)  Log out.  *Don't reboot.*  Just log out.
4)  X will restart and gdm will come up.
5)  Hit enter, there is no password on the live cd
6)  Wait for unity to come up.  It took a long time so I ran unity in a terminal, not sure if it made any difference.

---

