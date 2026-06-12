---
title: "Avant Window Navigator"
date: 2014-06-17
forum: MINT
---

### Post by ramakanta on 2014-06-17
I can not find **Avant Window Navigator**  in software centre  of Linux Mint 17 . how to install  it in Linux mint ???? 

thank you.

---

### Post by ramakanta on 2014-06-18
when i try to this commabd [FONT=system] $ sudo apt-get install avant-window-navigator
[/FONT]following massage displayed..

[FONT=system]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package avant-window-navigator[/FONT]

please help me ???

---

### Post by mauro7 on 2014-06-29
Hi, try with the ubuntu 14.04 procedure:

sudo add-apt-repository ppa:awn-testing/ppa

sudo sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/awn-testing-ppa-trusty.list

sudo apt-get update

sudo apt-get install avant-window-navigator

---

### Post by woo10jw on 2014-10-19
> **mauro7 said:**
> Hi, try with the ubuntu 14.04 procedure:

sudo add-apt-repository ppa:awn-testing/ppa

sudo sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/awn-testing-ppa-trusty.list

sudo apt-get update

sudo apt-get install avant-window-navigator

has anyone got this to work correctly. All I get is Firefox icon (which works), the config icon is greyed out and says "Whoop's applet crashed click to restart" left or right click does nothing, can't get into settings to make any adjustments

---

### Post by joll-nicholas on 2015-03-15
I have the same problems: the tip in this thread allowed me to install a version of the software, but the program cannot then be configured. I too am using Linux Mint 17.

---

### Post by juanjo3 on 2015-07-04
thanks, i can install it!

---

### Post by Rob Sayer on 2015-07-06
You're all going to hate me for this, but:

Why in the world would you want to use a dock app that you have to install from an external ppa ... and possibly break your install ... when there are a bunch of dock apps in the repos?

I won't even install application software from a ppa unless it does something I totally need that I can't get from the repos.  But DE level apps?  Forget it.

The ubuntu/mint forums have many noobs whose linux installs don't work properly after using ppa's or tar files to install.  That's one of the most common beginner mistakes.  You bugger up the updating process and it takes a lot more skill to deal with it than they have.

A rudimentary search would have told you that the program has been in limbo for some time because the guy who was maintaining it left.  Yes, it's often one person.

Please uninstall that crap, remove the ppa from the sources list, and install something that's been tested.

---

### Post by v3.xx on 2015-07-06
There is nothing wrong with PPAs as long as you know how to use them ;)

I started using Mate when it was just a PPA, look at it now.

I think its better said to use caution when installing a ppa.   And not try to discourage the general public because of personal feelings.  Look at how many pps's there are; I think some of us must be liking them :)

---

