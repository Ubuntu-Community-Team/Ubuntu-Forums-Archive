---
title: "Installing in Windows"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by Kauliukzmogis on 2008-05-04
Hey,

I decided to install Ubuntu into Windows in order to try it out. But all my trial started and finished with black command line window. So, how should I start that bloody graphical enviroment?

P.S.
[SIZE="1"]And now I will allow myself to grumble about all this. First of all, I hate command line and I have no idea what to do with it. I am not some kind of geek sitting in front of PC 24/7. I am a user hopping to have user friendly OS. Sorry, but until now, Ubuntu looked more like geek friendly. No offence. Simply I like things to be as simply as possible, because all complicated things takes additional time which is not the thing I have a lot. And here comes rhetorical question: why should I use Ubuntu, if it makes me feel stupid newbie, while Windows lets me feel comfortably?

Sorry for my English[/SIZE]

---

### Post by tvtech on 2008-05-04
if it dumped you to a command line it sounds as though you've installed server edition, and not the desktop edition.  The server is based on command line modules because servers don't need to eat up precious processing power running gui environments something which windows has yet to figure out.  and a significant reason why they are still trying their best to make inroads into the server market, with little success.   However, your wubi, ubuntu install should have installed a graphical user interface if not.  try and run at the command prompt that your given gdm   ```
username@localhost~$gdm
``` if this doesn't work then try the following you will be prompted for your password. not sure if it works the same way in windows I've got a native install an no windows.  
```
username@localhost~$sudo gdm
```
if that fails try ```
username@localhost~$sudo apt-get install gdm
``` or ```
username@localhost~$sudo apt-get install ubuntu-desktop
```




as to your grumble:  linux/bsd can be very user friendly just look at mac osx.  it's stupid simple and it just runs.  you have to pay through the nose for it and get inferior hardware for an inflated price.  but you'll be hip and cool and I"ll make fun of you. Most free graphical linux distro's today are very user friendly and intuitive for 99% of users needs.  even the for pay ones are pretty easy such as Xandros and linspire. I'm sorry your having trouble don't let it get you down.  I dont' have a lot of time in my life either and ubuntu and many of the free programs available within it have helped me out a great deal with that problem.

> Sorry for my English

I'm a native speaker of english and mines fairly aweful, so don't worry about it, YAY US public schools!

---

### Post by Kauliukzmogis on 2008-05-04
ok, thanks. I done something and all is working. at least I hope it works...

---

