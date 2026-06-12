---
title: "Decision ubuntu or windows?? pls help."
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by junooni10 on 2010-03-13
alright guys its my 2nd day a ubuntu user and im facing these problems.

1. I loose the wifi connection after 15 mins and i checked it my wifi is working perfectly fine on other devices. and its working fine on my windows, so i don't know what's the deal with losing the connection in ubuntu.

2. I tried installing skype and picasa & in both installations i got error saying its not for teh architecture for i386 some stuff like that.

Well this will be a decision making time for me if i don't get skype to work on ubuntu then ill just stick to windows. So please help. Thanks.

---

### Post by howefield on 2010-03-13
> **junooni10 said:**
> I tried installing skype and picasa & in both installations i got error saying its not for teh architecture for i386 some stuff like that.

You appear to be trying to install 64 bit debs in a 32 bit Ubuntu.  (Or vice versa)

> Well this will be a decision making time for me if i don't get skype to work on ubuntu then ill just stick to windows. So please help. Thanks.

Your choice, although dual booting might give you the comfort of windows, whilst giving you time to play around and get to know Ubuntu. 2 days doesn't quite cut it in terms of getting to know your way around.

---

### Post by Sef on 2010-03-13
> Quote:
 	 	 		 			 				 					Originally Posted by **junooni10** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8962652#post8962652") 				
 				*I tried installing skype and picasa  & in both installations i got error saying its not for teh  architecture for i386 some stuff like that.*
 			 		 	 	 
You appear to be trying to install 64 bit debs in a 32 bit Ubuntu.   (Or vice versa)


Check out this [thread]("http://ubuntuforums.org/showthread.php?t=474790") if you are installing 32-bit apps on a 64-bit system.

---

### Post by Mark Phelps on 2010-03-14
Success in the Linux world is more readily achieved using native Linux apps, but from what I could find, both Skype and Picasa only have beta versions for Linux.

If the apps you want to use are not readily available in native Linux form (i.e. .debs of final versions), you're going to find Linux a very difficult journey.

---

### Post by junooni10 on 2010-03-14
> **Sef said:**
> Check out this [thread]("http://ubuntuforums.org/showthread.php?t=474790") if you are installing 32-bit apps on a 64-bit system.

what about me losing the wifi signal after every 15 mins and its fine when i restart it and then same thin happens.

& can anyone of guide me to where to download skype & picasa....what works for you guys?? thanks

---

### Post by dream_coder on 2010-03-14
Had similar problems with certain wifi cards, is there any restricted drivers available for your card?

also had much success with setting the ip manually in network manager instead of relying on my routers dchp server which doesnt generally work that good depending on how good your router is.

another possibility is adding the network manangers trunk ppa to your sources file then running system update,

[https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)

I found this fixed 99% of all problems I have had with wireless connections.

if you need anymore help with any of the above please just let me know and I will do what I can to help you out.

ps there are other skype clients like ekiga that works fine for me :)
Regards

---

