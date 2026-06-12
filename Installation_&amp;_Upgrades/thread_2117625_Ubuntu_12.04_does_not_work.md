---
title: "Ubuntu 12.04 does not work"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by krishna85 on 2013-02-19
Hello guys,

I am quit new to linux. I have a pc with following specs
Asus p8z68V
i7 2600K
GTX-580 
8 GB Kingston ram
250 GB WD
1TB WD
Win 8 64bit Pro

I have been trying to install linux for a long time now, I first tried Fedora I constantly got Error 15 File missing, so I tried mint, that did not work too. I downloaded Ubuntu 12.10 I burned it on a DVD using an ISO burner, I boot from the DVD and choose install I get many many errors and sometimes it just would not install. So after reading a bit I downloaded the Alt installer(12.04), I burn it to a DVD and boot and start installing, all was good and at the end of the installation the DVD popped out and I restart, but it would directly boot to win 8. I do a bit of reading and I was told that I need to repair the grub, 3 options were give, since I could not boot into linux at all the advanced GUI mode was out of the question. 

The method I tried was to boot the system "Try Ubuntu" and then open the console and excute a command. I tried a 100 times but could not get the live desktop, it goes up to the brown background with Ubuntu in the middle and it would be there for hours. 

So I got fed up and installed ubuntu using the same 12.04 Alt Installer, this time it installs and it asks me to install the grub.

I install in on sdb which is where I installed ubuntu 12.04(I install it on the same partition as win 8, so right now there is just ubuntu on my pc).

I restart the pc and it boots to ubuntu, I hear the sound that says its on the login screen. 

That's it, it is stuck there for ever, none of the icons on the login screen are clickable the keyboard does not work(I have a razer blackwidow mech keyboard, it works perfectly well during the installation)
I tried waiting for couple of hours but still nothing works on that screen. So I try to install it again this time I try to "Detect keyboard" option during installation. I follow the onscreen instructions and finish the installation. 

The problem still won't go away.

Please help me. 


PS: sorry for the long description.

---

### Post by Bucky Ball on 2013-02-19
Welcome to the forums.

Why not use the 12.04 LTS desktop version? Any reason you are using the alt version? It is the text based installer and you don't need to use it. Might not make a difference but worth a try.

12.04 LTS (long term support) is the place to start. It is stable and supported until April 2017 (12.10 for 18 months, until April 2014). Use the desktop version, 64bit if you have a 64bit machine, and report back. ;)

---

### Post by arnav803 on 2013-02-19
yes, bucky ball is right.Use an LTS version it's stable and secure.

---

### Post by ooleyguy on 2013-02-19
Sounds to me like you need to enable nomodeset. I have an nVidia 550 GT and something in the initial system doesn't like it.

Use your Alternate CD or a 12.04 LTS CD to install and when you get to the menu asking you if you want to try it or install it, press F6 and a little menu will pop up. I suggest also pressing the spacebar a few times while the system is getting into graphical mode, as it sometimes just skips the menu and goes to a purple-brown desktop with two little unclickable icons at the bottom.

Anyway, when you get the little menu, mare the area where it says nomodeset, hit ESC and then either try or install Ubuntu. There is a remix DC you can DL from sourceforge that contains boot-repair that will fix GRUB issues.

When you do finally get Ubuntu installed, until you install the nVidia drivers for your 580GTX, you will need to manually edit GRUB each time you boot. If you only have Ubuntu installed, hold SHIFT down until the GRUB menu appears. Use your arrow keys to move up and down through any list you see, but the top one is all you really need. 

Once it is highlighted, hit the E key on your keyboard and look through the lines of text until you see one that ends in quiet splash. Add nomodeset at the end of that and hit F10 to boot. If that works and you actually get into Ubuntu, do the following as the first thing you do.

Open Terminal with CTRL+ALT+T and enter the following, one line at a timeL

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

You can highlight the code above and go to terminal and use CTRL+SHIFT+V to paste or right click and hit paste to eliminate typos.

After you have installed the nvidia drivers, you can probably boot just fine without needing to edit that line in GRUB each time.

In [http://ubuntuforums.org/showthread.php?t=2114764]("http://ubuntuforums.org/showthread.php?t=2114764") I expalined how to enable you to change your video card fan speed.

---

### Post by krishna85 on 2013-02-19
> **Bucky Ball said:**
> Welcome to the forums.

Why not use the 12.04 LTS desktop version? Any reason you are using the alt version? It is the text based installer and you don't need to use it. Might not make a difference but worth a try.

12.04 LTS (long term support) is the place to start. It is stable and supported until April 2017 (12.10 for 18 months, until April 2014). Use the desktop version, 64bit if you have a 64bit machine, and report back. ;)
I should have mentioned that I have installed the 12.04 LTS version. I assumed that 12.04 was LTS. My bad. 

I am pretty sure I downloaded 12.04 LTS 64bit. 

@ooleyguy Here are some photos from the boot to desktop.

At the screen where it asks what to boot I choose the first option which is to boot Ubuntu normally and there I hit 'e' it took me a screen with a code. I saw the quite splash that you were talking about.
' quit splash $vt_handoff ' so I replaced $vt_handoff with nomodeset as you said. Hit F10 and it booted into what looked like a safe mode. It let me login and I could see the desktop for the first time. 

Here there were series of windows opening with errors. I was able to capture few of them

---

### Post by ooleyguy on 2013-02-20
Well, we got you part way. Do not delete anything in the GRUB lines. Just add nomodeset after the vthandoff.

Assuming it installed well enough for you to have internet access, follow the enstructions I gave about installing your nvidia drivers. Ignore all the other errors. Most of them are probably because of the nvidia drivers anyway. I know the jockey-gtk one is.

Just open terminal with ctrl-alt-T and after putting those commands in and installing those drivers, you will probably experience a fairly smooth environment and star having fun tweaking Ubuntu all up.

---

### Post by krishna85 on 2013-02-20
> **ooleyguy said:**
> Well, we got you part way. Do not delete anything in the GRUB lines. Just add nomodeset after the vthandoff.

Assuming it installed well enough for you to have internet access, follow the enstructions I gave about installing your nvidia drivers. Ignore all the other errors. Most of them are probably because of the nvidia drivers anyway. I know the jockey-gtk one is.

Just open terminal with ctrl-alt-T and after putting those commands in and installing those drivers, you will probably experience a fairly smooth environment and star having fun tweaking Ubuntu all up.

Hi, I followed the instructions and finally got ubuntu working. Now it boots without me having to edit grub any more and everything seems to be working fine for now. I updated what ever the software center showed and I installed the nvidia drivers like you suggested. 

There are just 2 small things left now.
1. When playing any media the video is fine but the audio is   cracked.
2. when I searched something on chrome and directly type what I am looking for in the address bar it takes me to a google captha page. Any Idea why this is happening? 

The same thing was happening on my Win 8 so I thought it must be some kind of torjan or something. But here on Ubuntu too?

---

### Post by krishna85 on 2013-02-20
I have googled and all I found was a video on youtube when I followed the instruction and opened the file I could not find the line that was to be commented. 
Further googling I could only find this problem was with laptops and many were able to solve it when they fixed a power related issue. Since mine is a desktop I didn't think it would work

---

### Post by ooleyguy on 2013-02-20
> **krishna85 said:**
> I have googled and all I found was a video on youtube when I followed the instruction and opened the file I could not find the line that was to be commented. 
Further googling I could only find this problem was with laptops and many were able to solve it when they fixed a power related issue. Since mine is a desktop I didn't think it would work

Don't comment any lines just add nomodeset to the back of the line we've been discussing. Do not change anything else. All we are trying to do is get you into the Ubuntu desktop and we succeeded. Install the drivers and you should be good. I'll repeat the process here.

Open the terminal with Ctrl+Alt+T. Terminal looks like DOS if you are a former Microsoft user and you enter text commands into it.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

Again, in the GRUB menu, after you hit e to edit the entry, do not comment anything out or delete anything. Just add nomodeset to the line we've been discussing and press F10. If it goes into what might look like safemode, GOOD! That is what we want. Ubuntu won't look real pretty until you get those drivers installed.

---

### Post by krishna85 on 2013-02-20
I did, my ubuntu boots normally and works well. All video drivers are installed. I have updated them as well. The problem now however is with audio. The audio is cracked, there is a constant popping sound. This is new because this was NOT there when I had Win 8.

---

### Post by krishna85 on 2013-02-20
What I just noticed is that the popping sound from the speaker is only when it is connected to the ports on the back side. when I connected speakers to the front jack there was no popping sounds, BUT the volume level kept going up and down on its own. 

I really think this is a driver problem, I do not know how to update the drivers though.

---

### Post by ooleyguy on 2013-02-20
Well sir, You got me. I'm only knowledgeable about the nVidia card thing because I spent 5 days fighting with it on my system. The only thing I can suggest is that maybe the volume in the audio settings is turned up really loud and you are getting feedback.

Hit the little speaker up at the top on the panel next to your name and other stuff and click Sound Settings. Choose your device and make sure output volume at the bottom isn't above 100%. Other than that, I'm afraid I have no further knowledge of the subject. I don't hear really well, so sound problems usually don't affect me since I don't hear them unless it is something wicked bad.

Good luck.

---

### Post by Bucky Ball on 2013-02-21
> **krishna85 said:**
> What I just noticed is that the popping sound from the speaker is only when it is connected to the ports on the back side. when I connected speakers to the front jack there was no popping sounds, BUT the volume level kept going up and down on its own. 

I really think this is a driver problem, I do not know how to update the drivers though.

I suggest you post a new thread in Multimedia & Video about the audio problem rather than trying to get help on this thread which has a thread title which doesn't relate to your audio issue in any way. 
 
You will have more luck. 

PS: Use descriptive thread titles that give us some info about your problem. '12.04 doesn't work' is generic and tells us nothing. Many will just walk on by.

Good luck. ;)

---

### Post by krishna85 on 2013-02-21
> **Bucky Ball said:**
> I suggest you post a new thread in Multimedia & Video about the audio problem rather than trying to get help on this thread which has a thread title which doesn't relate to your audio issue in any way. 
 
You will have more luck. 

PS: Use descriptive thread titles that give us some info about your problem. '12.04 doesn't work' is generic and tells us nothing. Many will just walk on by.

Good luck. ;)

Yes I should have made it clear, my bad. Yes you are right again. I will post this issue in Multimedia section. Thank you.

Also thanks to everyone who helped.

---

