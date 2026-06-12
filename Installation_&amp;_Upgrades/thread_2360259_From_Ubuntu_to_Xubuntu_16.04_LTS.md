---
title: "From Ubuntu to Xubuntu 16.04 LTS"
date: 2017-05-02
forum: Installation &amp; Upgrades
---

### Post by ubu112 on 2017-05-02
Please,I'm not an expert and I have an old pc with just 1 Gb of RAM,with Ubuntu 16.04 LTS installed.

Now,I'm tring Xubuntu from a live USB and it seems faster.Have I to update to make a good test?can I install Chromium?

I'd like to know if I install it from the USB,everything will be deleted? I mean it's like to make a fresh install?

Which is the best way to install it?

Thank you

---

### Post by Qew on 2017-05-02
I'd just install packages xfce4 and xfce4-goodies on your current installation using Synaptic or apt-get (I'll post the code below), which will drag in the necessary packages. If your current installation is running OK, then there's no reason why you can't install XFCE on it and use it on what you've got. Once installed, when you log in the next time, select XFCE in the login screen, and you'll be using XFCE and it'll default to that the next time you login (you can change it back to Unity if you want). There is no major issue having two desktops installed on your machine, bar space. 

BTW, the reason why I don't say install xubuntu-desktop is because it'll drag in a lot of stuff that you might not be interested in or have similar packages already installed. You can install it, it won't break anything, but it's not necessary and adds stuff that might be clutter and redundant for you. Still, if you want the default Xubuntu applications, configuration and feel, then maybe you should install that too. However, I've gone without and gone with just XFCE.

If you're not using Synaptic or Software Center, open a virtual terminal or Xterm and type in:

```
sudo apt-get update && sudo apt-get install xfce4 xfce4-goodies
```

Oh, yeah, you can install and use Chromium just fine. I have it installed and occasionally use it.

---

### Post by Bucky Ball on 2017-05-02
I would strongly advise you do a clean install of Xubuntu or install it on a separate partition next to your current install (dual-boot) rather than the method given by Qew (although that will work). Adding more software will slow your machine further, not speed it up, as you are dumping a whole load of xfce4 stuff on top of an already sluggish Ubuntu. Doesn't make sense. You may also find your application menu populated with Ubuntu stuff and xfce4 stuff, as mentioned. Although you won't drag many in, you will drag some apps (and background bits).

While Qew's method may have worked for them, I would almost guarantee they have more than 1Gb of RAM and Ubuntu was not running slow to start with. ;)

With specs like yours, Ubuntu is not going to run great no matter how you look at it. Throwing more software at it is the wrong way to go. Xubuntu, or Lubuntu, are intended for machines like yours. Trying Xubuntu in a live session will be fine (and even better when installed) while throwing more software at a Ubuntu will be slower as you have just loaded a whole load of bloat.

All the Ubuntu flavours use the same repositories so anything available in one will be available in the other (re. Chromium).

As for installing, if you choose 'Something Else' on the Xubuntu install, you can manually partition and leave the existing partitions alone and have Ubuntu and Xubuntu dual-boot. The new install can use the existing /swap partition and the existing /home, if you have one. Post another thread about installing if you get that far. :)

Good luck.

---

### Post by Qew on 2017-05-02
> **Bucky Ball said:**
> 
While Qew's method may have worked for them, I would almost guarantee they have more than 1Gb of RAM and Ubuntu was not running slow to start with. ;)

Very sensible advice. You're right, I neglected to think about the OP's 1GB of RAM and limited specs. Also, your suspicions are correct about my own set-up.

Mind you, when you say installing XFCE on top of Unity Ubuntu will cause bloat, that's more menu clutter and disk space than system resources when running. As a single user, you only run one desktop at a time, not both at the same time. My system runs way easier with my XFCE session than my Unity one. But, yeah, if you do have start-up scripts, autoruns and stuff running that came from the original Unity installation, then that'll add up. However, that also depends on them being called. Still, yeah, I agree that a clean install is probably better for the OP.

OP: good luck with Xubuntu. XFCE is a great desktop. :)

---

### Post by litlesam on 2017-05-03
Running Xubuntu on a low spec system like yours and it has been wonderful. Tried Ubuntu Unity first and moved on to a fresh install of Xubuntu and never looked back. As already posted above, Chromium will work just fine.

---

### Post by Bucky Ball on 2017-05-03
> **Qew said:**
> Mind you, when you say installing XFCE on top of Unity Ubuntu will cause bloat, that's more menu clutter and disk space than system resources when running. As a single user, you only run one desktop at a time, not both at the same time.

Yep, been there, done that many years ago when initially experimenting with Ubuntu. Moved on to using the minimal install with xfce4 for ages then switched to [Xubuntu-core]("https://xubuntu.org/news/introducing-xubuntu-core/") at 16.04 LTS as that saved me some time. It was the basic state I would spend time getting the minimal install to anyway. Just install Synaptic and Firefox into the basic Xubuntu-core and take it away installing only what you want/need.

I use that on every machine in the house, including my desktop box with 16Gb of RAM. Worth noting that Ubuntu Studio, which is resource heavy in other ways, uses xfce4, probably to lighten the load and devote the resources to AV work. ;)

@OP: Xubuntu-core is definitely another option on a machine like yours. Lighter than a regular Xubuntu and you only install what you need. This means everything you need. You need to install a web browser, package manager, word processor, email client; whatever you're going to use. Nothing comes default. Worth the effort, at least in my case. Speed machine!

You could also dump another Gb or three of RAM in the machine. Pretty cheap now.

---

### Post by LastDino on 2017-05-03
For RAM of 1Gb I actually prefer to install LXDE, it is lighter than XFCE, XFCE is my preferred choice when I've around 2Gb.

 > You could also dump another Gb or three of RAM in the machine. Pretty cheap now.

Best advice, you will be shocked to know how much difference it would make. And if you throw in SSD, you might able to extend life of that machine quite a bit.

---

### Post by Bucky Ball on 2017-05-03
> **LastDino said:**
> And if you throw in SSD, you might able to extend life of that machine quite a bit.

+1. Yes indeed. More RAM and an SSD and you've got a new machine! When it eventually dies, the RAM might be a lost cause, depending what it is, but the SSD is easily transferable to your next computer, whatever it is. Compatibility not an issue.

---

### Post by ubu112 on 2017-05-03
First of all,I'd like to say thank you very much for your kindness and good advices.

I thought many times to add more RAM on my Acer Aspire One AOA 150/ZG5,but one day I fund a guide about how to change parts on it and honestly I'm scared just to think 

about making one of them.As I said I'm not an expert at all.

From your advices I think the right solution would be only Xubuntu,that now has XFCE,with LXDE.

Immediately after "SOLVED",I'll make a new thread because,please, I'd need your help for how to make a clean install and how to change from XFCE to LXDE.

Thank you

---

### Post by Bucky Ball on 2017-05-03
All good. Post a link to that thread here if you like. ;)

---

### Post by ubu112 on 2017-05-03
I made a new one "How to make a clean install of Xubuntu from Ubuntu".

Can you,please,be so kind to take a look.

Thank you

---

### Post by ubu112 on 2017-05-04
A strange thing happend.

To try Xubuntu,I downloaded the .iso from - [https://xubuntu.org/](https://xubuntu.org/) - I created a live USB and it seems to be fast.

Then I realized that the .iso name was vers.16.04.

I fund on - [http://cdimage.ubuntu.com/xubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/16.04/release/) - an .iso vers.16.04.2 and I thought that this is the updated version.

So,I formatted the same USB and I made a new live USB.

The strange is that the first (16.04) seems to be faster.The second (16.04.2) from my point of view,it's slower.I mean the system seems to be slower,I tried few speedtest slower.

I checked both .iso with SHA256SUMS and are OK.

Can,please,someone explain to me if this is normal and I downloaded a wrong .iso.Have I to download an other one?

Thank you

---

### Post by Bucky Ball on 2017-05-05
16.04.2 is the latest and supported version. You want that. Install that.

---

### Post by Impavidus on 2017-05-05
Mostly, 16.04.2 is just an updated version of 16.04. There is however one important difference: 16.04.2 has kernel 4.8.0, but a fully updated 16.04 had kernel 4.4.0, which may work better with your hardware.

---

### Post by ubu112 on 2017-05-05
Thank you for your answer.

I'm not an expert at all,so what do you suggest to me to do?

Because,now I'm using Ubuntu 16.04.2 LTS,that has 4.4.0 kernel and I'm tring Xubuntu because Ubuntu is too slow with my hardware.

Isn't it strange that from xubuntu.org I can have just 16.04?but,if I download again the 16.04,won't it be updated?

Thank you

---

### Post by mörgæs on 2017-05-05
If some of the Xubuntus feel slow you could try Lubuntu for comparison. 

The [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") is about as light as you can get within the Buntu family.

---

### Post by ubu112 on 2017-05-13
I tried to download an alternative/minimal version of Lubuntu 16.04.2 LTS(I just fund the 16.04.1) and I made a live USB.

But,when I tried to launch the OS I just fund "Install Lubuntu"and not "Try it before to install",like I want.Is this normal?and can't I  try it before?

Like I'm doing with Xubuntu and Lubuntu,desktop version, I'd like to see how it works and more important,I have to understand what I'll need to install,if I'll be able,because I'm not an expert.

I read somewhere,something about PAE support,I don't think that my Intel Atom N270 has this support.Will it be a problem?

Thank you

---

### Post by mörgæs on 2017-05-14
The ISO is, as the name says, minimal. There will be no GUI to begin with (we'll add that later) and hence nothing to show in a live boot. One can only install from it, and I suggest that you do.

Your Atom does have PAE so just go ahead. Always install using a wired internet connection.

---

### Post by ubu112 on 2017-05-18
Please,as I read in your beautiful thread "Old hardware brought back to life",can you explain to me 

> [COLOR=#000000]applying the first batch of bug fixes[/COLOR]

Where can I find and how can I apply "the first batch of bug fixes?or it comes with the update?

Thank you

---

### Post by mörgæs on 2017-05-19
Good that you liked it.
Just run the commands mentioned in **6) maintenance** and it will all install automagically.

---

