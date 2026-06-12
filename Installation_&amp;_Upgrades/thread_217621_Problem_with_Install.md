---
title: "Problem with Install"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by burton178 on 2006-07-17
I'm a newbie linux user. I'm very interested in learning about it. While trying to install ubuntu I've had quite a few road blocks along the way. This one is one that I can't get by and I'm sure there is a simple command that will get me back on track... Please excuse my crude knowledge, but I've been only a Windows user for years...

I've done the install from the CD and then rebooted (as instructed)... most of the "how to's" on the internet say a beautiful graphical login screen will appear... This doesn't happen...  I'm asked for my login and password in a command-line type setting (which I complete successfully) but then it stays in that command line setting and says something like...

UserName@ComputerName>   

Is there something I'm missing... how do I get to the graphical login... Any help would be apprecited...
I also searched for this a lot so I hope it's not a repeat question.

---

### Post by Herman on 2006-07-17
It sounds to me like your xserver needs some help to start. The xserver is the part of our software that gives us our nice picture on our monitor and use of our mouse.
This is a common enough occurence following an install, and many people are like you, they don't know what to do next. All you need to do is type a command and then help guide your new Ubuntu operating system to install the right drivers. It's fairly easy, it will probably detect your hardware and pick most of them out automatically. Perhaps there is one or two in your machine it isn't completely sure about and it is afraid to start without your confirmation. You can hold Ubuntu's hand while it walks you through setting up the drivers and asks you to confirm lots of things it guesses you want. It's easy really, but I made a new web-page to help you. 
Since the web page is new it hasn't been tested yet as far as I know, so there might be one or two mistakes in it, so be careful, but I hope they'll only be minor ones. Please let me know if you see something wrong with the web page so I can improve it for the next people who use it.
Here is the new web-page,  sudo dpkg-reconfigure xserver-xorg..................................................[Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html")
I hope that helps you, good luck with it, Regards, Herman :D

---

### Post by burton178 on 2006-07-17
...on my way to trying it now... What an incredible way to help! I'll be sure to post the results...
Whether my brain can wrap around the concepts or not, it is awesome for you to help this way!:mrgreen:

---

