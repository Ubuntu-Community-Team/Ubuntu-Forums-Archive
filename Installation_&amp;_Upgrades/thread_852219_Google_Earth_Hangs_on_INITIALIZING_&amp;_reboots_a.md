---
title: "Google Earth Hangs on INITIALIZING &amp; reboots after 20 secs"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by John Kemp on 2008-07-07
I installed Google Earth into Hardy Heron 8.04 via the Terminal using the recipe at: [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)
and it hangs on the initializing phase and after about 20 seconds reboots to the user login page. HELP - please! I'm moderately computer-literate with Windows XP (i.e. can solve most problems by extensive googling) but am a newbie to LINUX. AMD Processor.

---

### Post by Partyboi2 on 2008-07-07
What graphics card are you using? When you start it from the terminal are you getting any error messages?

---

### Post by John Kemp on 2008-07-08
> **Partyboi2 said:**
> What graphics card are you using? When you start it from the terminal are you getting any error messages?

I have the NVIDIA GeForce 7300 GS graphics card. I get no error messages with Google Earth, but the same behaviour whether I launch it from the Applications menu, the desktop shortcut I created, or from Terminal: the splash screen comes up plus a minimised "Initialising..." message, and then the system spontaeously reboots. I get no error messages. 

I should add that Google Earth installed an runs perfectly on my XP bootup. On further reading I had it in mind to unistall GE from Ubuntu, and reinstall from the Medibuntu repository, but there is no hurry for this as I can access the program on XP. Therefore, if it helps the community to investigate the problem as I have reported it, and Partyboi2 or someone else can tell me what to try - bearing in mind I'm a newbie - I'm happy to stay with it and try a few fixes, but cannot spend hours on it.

---

### Post by cdoebbler on 2008-07-10
Just adding my voice to the hapless Google Earth users. Running Hardy (Ubuntu 8.4.1 // Linux 2.6.24-19-generic (i686) on a Sony Vaio (PCG-TR3A). Display is at 1664X768 pixels and Mesa GLX indirect Open GL rendering. No error message. just hangs (apparently) then reboots. 

This happened with both GE 4.2 and 4.3.

:confused:

---

### Post by John Kemp on 2008-07-14
As no-one has taken up my offer to assist an investigation of this, I plan to go ahead and uninstall Google Earth and reinstall via the Medibuntu repository when I have time.

---

### Post by stchman on 2008-07-14
> **John Kemp said:**
> I installed Google Earth into Hardy Heron 8.04 via the Terminal using the recipe at: [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)
and it hangs on the initializing phase and after about 20 seconds reboots to the user login page. HELP - please! I'm moderately computer-literate with Windows XP (i.e. can solve most problems by extensive googling) but am a newbie to LINUX. AMD Processor.

That is because you do not have any openGL or Mesa drivers installed.

Since you are using an Nvidia 7300GS then simply enable the restricted driver.

I recommend you install Google Earth via Synaptic using Medibuntu.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

Follow the Medibuntu repository install and type:

```
sudo apt-get install googleearth
```

This way it can be completely uninstalled.

---

