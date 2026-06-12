---
title: "Cannot load from CD (black screen)"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by savingedmund on 2008-10-10
[COLOR="Red"]**_NOTE: this is my second attempt at posting this. Can someone help me? Please?!_**[/COLOR]

**CONFIRMED: This is most likely related to the known ATI card issue**

Hey guys,

I'm a noob in every sense (new to the forum, Kubuntu, Linux, everything), so bear with me. I am not an expert on the OS side of things. :)

I also apologize if this is a known bug. If so, feel free to direct me to the right place. :)

Anyway, I wanted to try Kubuntu because I wanted something more stable that would run better on my old Pentium 4 machine.

To be clear, I'm using the **Kubuntu KDE 4 Remix (8.04)**.

[LIST]
[*]I downloaded the ISO and checked the hash, then burned the image onto a CD.
[*]I booted to the CD, and the load screen opens fine.
[*]I get to the screen where I can choose an option, and I choose Check CD, and it checks it and there are no errors. 
[*]I reboot and get back to that screen load from CD (because I want to try before I buy, so to speak. this is my first time, after all). 
[*]The machine does the load bars (black screen and little blue bar going across the screen), but when the load bar is complete, my screen goes blank, and I do mean blank. There isn't a cursor. My monitor light goes amber (no signal).
[/LIST]

Now, I waited a while (it is booting off of a CD, so I know it will be very slow), and watched my hard drive light. There was a bunch of activity for a while, but eventually the activity stopped. The CD light was on, but nothing else was doing anything. still no signal. I waited a good 5 minutes and nothing happened.

Am I simply not waiting long enough, or is there something else wrong here?  :confused:

---

### Post by Paul41 on 2008-10-10
What graphics card do you have? I have had this problem before with a ATI card.

---

### Post by savingedmund on 2008-10-10
I will have to go home to check, but I am about 90% sure it's ATI. If it is, is there a workaround?

---

### Post by Paul41 on 2008-10-10
OK, I was just given a computer with a ATI card that had Ubuntu installed and I was having problems because of the video drivers it was using. I was trying to reinstall just to have a fresh install to start from and was having the same problem you are. I have seen someone say they got around it by using the alternate install and selecting a different video driver, so I have downloaded the alternate install and just haven't had time to try it yet. I hope to be able to try it this weekend and will let you know how it goes. I am using Ubuntu instead of Kubuntu but I would think it is the same problem.

---

### Post by savingedmund on 2008-10-10
I appreciate that. Let me know. :)

---

### Post by savingedmund on 2008-10-10
Ok, I've confirmed that I do have an ATI card, and after doing some research, I found that this is a known issue (or, at least, there are many issues people have with ATI cards).

Does anyone have any suggestions about how to get the ATI driver to work with the standard CD, etc.?

---

### Post by Paul41 on 2008-10-11
I just tried the alternate install and no luck. It doesn't give me a black screen but instead I get a screen I can't read (just a bunch of fuzzy jumping lines). I haven't given up yet though so I will post back if I get anything to work.

---

### Post by linux_tech on 2008-12-02
What video card are you using?
```
sudo lshw -C video
```
Have you tried a few different drivers?
Have you tried to install the driver manually?
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

