---
title: "Lubuntu 14.04DT reinstall problems."
date: 2016-08-19
forum: Installation &amp; Upgrades
---

### Post by nu2this2 on 2016-08-19
Hello,

Was recently having problems with lubuntu glitches and decided to reinstall. The old install was completely erased and the new was reinstalled. Now I am having problems. The digital clock has switched from the 12 hour to the 24 hour version, I cannot access links from a web site, I cannot install a plugin that may be required to display media such as Flash. When I attempt to install Flash The Plugin finder service window appears and "No suitable plugins were found" is displayed. There is an option showing on the bottom of the window reading "Find out more about plugins or manually find missing plugins" that can be clicked. when that option is clicked another box appears "Server not found"

I am connected to the internet but like in the previous installation there is no available networks icon present.

All suggestions are appreciated.

---

### Post by Rex Bouwense on 2016-08-20
This should point you in the right direction to fix your clock issue.  [https://help.ubuntu.com/community/Lubuntu/Documentation/CustomizingTheClock](https://help.ubuntu.com/community/Lubuntu/Documentation/CustomizingTheClock)
If you don't want to read all about customizing your clock, just right right on the time in your LXPanel and choose Digital Clock settings.  Replace %R with %r

---

### Post by nu2this2 on 2016-08-20
Thank you, that worked fine for the clock. Have any ideas why I can't load the plugin for flash?

---

### Post by howefield on 2016-08-20
> **nu2this2 said:**
> ... Have any ideas why I can't load the plugin for flash?

You could enable the Canonical Partners repository via Software & Updates application, then..

```
sudo apt-get install adobe-flashplugin
```

---

### Post by nu2this2 on 2016-08-21
> **howefield said:**
> You could enable the Canonical Partners repository via Software & Updates application, then..

```
sudo apt-get install adobe-flashplugin
```

Is this the same as the Synaptic package manager?

---

### Post by Rex Bouwense on 2016-08-21
No. Go to Menu->Preferences->Software and Updates->Other Software.  Make sure that "Canonical Partners Software packaged by Canonical for their partners" is checked.  That is what howefield was talking about.

---

### Post by howefield on 2016-08-21
> **nu2this2 said:**
> Is this the same as the Synaptic package manager?

No it isn't, it is as Rex explained, however if you have synaptic installed you can get to the same place by using it if that is more familiar/convenient to you.

Load Synaptic and choose Repositories from the Settings menu. Then "Other Software" tab > Canonical Partners and enable, then reload and search for adobe-flashplugin and install.

---

### Post by nu2this2 on 2016-08-21
Was able to follow the instructions the best I could but don't know if it was done properly. The screen indicated a down load was installed, a white cursor appeared so I exited by clicking the X at the top of the window. You tube did load but was very slooooow. I was not able to go to the vids by clicking the links. Is there a way to verify that I have installed the latest version of flash?

Thank you

---

### Post by howefield on 2016-08-22
What is the output of

```
apt-cache policy adobe-flashplugin
```

You should also see the plugin as installed in the browsers preferences.. which browser are you using ?

---

### Post by nu2this2 on 2016-08-22
Hi, don't know how to post a screen shot so will have to type it.

Installed: 1:20160712.1-0ubuntu.14.04.1 
Candidate: 1:20160712.1-0ubuntu.14.04.1 
Version table:
***1:20160712.1-0ubuntu.14.04.1 0 
         500 [http://archive-canonical.com/Ubuntu/](http://archive-canonical.com/Ubuntu/) trusty/partner i386 Packages
          100 /var/[ib/dpkg/status

I am using Firefox browser

---

### Post by howefield on 2016-08-22
Yep, that is the latest version of the adobe-flashplugin package and is shown as installed.

You should also see the flash plugin in Firefox > Tools > Addons > Plugins

or visit the [flash about website]("http://www.adobe.com/uk/software/flash/about/") which will confirm and tell you which version is installed.

---

### Post by nu2this2 on 2016-08-22
Thanks for all the help. Unfortunately Firefox is really slow in loading up any internet sites. It takes anywhere from 30 seconds upwards. At times a site wont even load I don't know what the problem is.

 The specs of my laptop are:
 Memory 1.4G
 Processor Mobile AMD Sempron(tm) Processor 3300+
 Graphics Gallium 0.4 on ATI RS480
 OS type 32-bit
 Disc 77.1 GB 

Shouldn't this be sufficient?

---

### Post by howefield on 2016-08-22
Well, the specifications are pretty light but I'd have thought sufficient to browse the internet, did you an issue with browsing speed prior to reinstalling and if not, have you reinstalled with the same version of Lubuntu ?

---

### Post by nu2this2 on 2016-08-22
I did have slow performance before but not as slow as it is now. I used the same disc to reinstall. The version I used was Lubuntu because I thought this would be more compatible with my laptop specs. Should I try a lighter version perhaps? If so which would you recommend.
.

---

