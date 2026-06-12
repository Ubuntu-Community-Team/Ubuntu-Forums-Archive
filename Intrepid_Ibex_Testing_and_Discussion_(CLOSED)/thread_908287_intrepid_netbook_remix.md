---
title: "intrepid netbook remix"
date: 2008-09-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by foerdi on 2008-09-02
Hi guys,

i'm thinking of buying this new convertible netbook from gigabyte M912something...

will there be a stable and worth using netbook remix released with intrepid?

is there development on netbook remix at this moment? and where can i see the blueprints for it.

if netbook remix is ready i will buy this device

---

### Post by plun on 2008-09-02
Dell will be first with Ubuntus netbook-remix preinstalled

[http://arstechnica.com/news.ars/post/20080818-dells-eee-killer-to-ship-with-ubuntu-preinstalled.html](http://arstechnica.com/news.ars/post/20080818-dells-eee-killer-to-ship-with-ubuntu-preinstalled.html)

The code is within Launchpad and works just fine... I have it installed
for testing purposes on my desktop...

Project
[https://launchpad.net/netbook-remix](https://launchpad.net/netbook-remix)


Packages
[https://launchpad.net/~netbook-remix-team/+archive](https://launchpad.net/~netbook-remix-team/+archive)

Some minor work with the code
[https://code.launchpad.net/~netbook-remix-team](https://code.launchpad.net/~netbook-remix-team)

:)

---

### Post by brnetonboy on 2008-10-03
I am also wondering if it's possible to get an Ibex version of Netbook Remix. Does anyone know how this would work?

---

### Post by zorkerz on 2008-10-26
I went to the launchpad netbook remix page and am not quite sure what I need to do to recreate the netbook remix experience. 

Specifically what packages will I need to install?
What else will I need to customize?
Can I do this on my normal desktop without loosing my current settings or should I do it with another user or through a virtual machine?

---

### Post by zekopeko on 2008-10-26
install everything. that's what the page says. before they had a special package for netbooks based on atom but i'm guessing that they put that in the kernel now so you can simply install everything and simply create a test user so that you don't mess your user account.

---

### Post by zorkerz on 2008-10-27
Yep I read that and I don't understand it. Here is what I have done. 

Update: I have edited the below steps they now serve as a HowTo for getting netbook remix on an ubuntu intrepid system. 

1) add the intrepid PPA to sources.list ('sudo nano /etc/apt/sources.lst' and add the lines 'deb [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) intrepid main' and 
'deb-src [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) intrepid main')

2) install the packages ('sudo apt-get human-netbook-theme maximus netbook-launcher go-home-applet window-picker-applet')

3)After installing these packages add a new user. ('system->administration->users and groups' '+ Add User' button)

4)After logging into the new user add maximus and netbook-launcher to startup ('system->preferences->sessions' '+ Add' button)

5) Then logg out and back in to start maximus and netbook-launcher

6) set the theme to 'Human-Netbook' ('system->preferences->appearance')

7) finally as the launchpad page says delete the bottom panel and set the top panel to 'GoHomeApplet|WindowPickerApplet|NotificationArea|Clock' 

Note: there is no mixer applet in intrepid
This is as close to the demo as I have been able to get my setup. 

***The main problem is that when I select gohome all I see is the default intrepid desktop instead of the home screen in the demos where you can select any application you want.*** -> was because I had not run the netbook-launcher

side problems: 
-> im unsure whether the two missing packages are only for hardy or actually needed 
answer: only for hardy
-> I don't have and don't know the purpose of the MixerApplet
answer: not in hardy not my problem :~)

---

### Post by surfed on 2008-10-27
put netbook-launcher into start-up programs in sessions (it is the ume replcement) and not sure if needed but I did install desktop-switcher, just added the hardy repo, installed it and removed hardy repo. Works like a charm for me.

---

### Post by GuitarRocker2562 on 2008-10-27
[http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html)

That's how to do it. It is quite cool IMO.

---

### Post by zorkerz on 2008-10-27
Ok thanks for the responses my problem was that I had not started netbook-launcher I have now added it to my startup list. 

The netbook-launcher is very very slow for me. It also has some graphical glitches, icons have an out of place line on the left side and some other icons are fuzzy (graphics). Again its all very slow to the point of almost being unusable. Ive attached a screenshot so you get the idea.

Do other people have these problems or are they unique to me?

---

### Post by surfed on 2008-10-27
For me on an eee1000h everything is very smooth and quick. No artifacts at all, not using compiz.

---

### Post by zorkerz on 2008-10-28
thanks for the response surfed. I guess I will file a bug on this to let the developers know what im experiencing. If anyone knows anything that may help me figure out whats causing this behavior please let me know.

Im using an x61 thinkpad. Its graphics card is an intel x3100. I know ubuntu has had some problems with graphics on those before. Im also not using compiz.

I will post a link to the bug.

---

### Post by zorkerz on 2008-10-28
I tried to log into my netbook remix account alone without being logged into my main account and the speed issues went away along with the graphical glitches (excepting fuzzy icons), however, I ran into a whole new problem set that appear to be related to the netbook-launcher.

Clicking the go home applet button sends me to the netbook-launcher window as it should but then my toolbar disappears. If I scroll my mouse over parts of it they come back as long as the mouse is over them. I had a firefox and a terminal open. I could click on their icons using the window picker and they would come to the front but almost immediately be replaced by the netbook-launcher.

---

### Post by surfed on 2008-10-28
> **zorkerz said:**
> I tried to log into my netbook remix account alone without being logged into my main account and the speed issues went away along with the graphical glitches (excepting fuzzy icons), however, I ran into a whole new problem set that appear to be related to the netbook-launcher.

Clicking the go home applet button sends me to the netbook-launcher window as it should but then my toolbar disappears. If I scroll my mouse over parts of it they come back as long as the mouse is over them. I had a firefox and a terminal open. I could click on their icons using the window picker and they would come to the front but almost immediately be replaced by the netbook-launcher.

that only happens to me if compiz is running.

---

### Post by zorkerz on 2008-10-28
its not running here unfortunately

---

