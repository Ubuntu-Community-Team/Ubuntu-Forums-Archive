---
title: "Flash for Chromium not working"
date: 2016-04-08
forum: MINT
---

### Post by Alex D on 2016-04-08
Hi,

I am using Chromium with my latest version of Mint 17.3 Xfce, Firefox is very slow with this installation and cannot be used.

However, I am happy with Chromium, it is a good browser and on my machine is fast for internet browsing, the only problem I have is flash.

Many sites are still using it and although I have installed pepperflashplugin-nonfree, I still receive a message saying: your flash plugin is out of date...

To give you an example, try the video from this newspaper:

[http://video.repubblica.it/edizione/bologna/in-1000-a-cantare-i-foo-fighters-esibizione-record/208393/207491?video=&ref=HRESS-31](http://video.repubblica.it/edizione/bologna/in-1000-a-cantare-i-foo-fighters-esibizione-record/208393/207491?video=&ref=HRESS-31)

The same video plays fine in FF, Chrome is not an option because I am on a 32bit machine.

Any solution for this?

Thank you
Alex

---

### Post by Dennis N on 2016-04-08
I use Chromium too in my Linux Mint 17.3, but I installed the package **adobe-flashplugin**. It provides the correct plugin regardless of whether you use Firefox or Chromium (or even both). Currently, it gives me the latest version of flash for Chromium, 21.0.0.213

I suggest you install that package.

---

### Post by Alex D on 2016-04-08
> **Dennis N said:**
> I use Chromium too in my Linux Mint 17.3, but I installed the package **adobe-flashplugin**. It provides the correct plugin regardless of whether you use Firefox or Chromium (or even both). Currently, it gives me the latest version of flash for Chromium, 21.0.0.213

I suggest you install that package.

Hi Dennis,

I have the same package and flash version, but those videos give me the message: Adobe Flash is out of date

Are you able to play the video in the link I posted?

Alex

---

### Post by Dennis N on 2016-04-08
No, the video at the link does not play, and  there is no newer flash version:

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

At the moment, no ideas on why this fails. I have had no problem with other web sites I visit that use the flash player.

---

### Post by sammiev on 2016-04-09
I'm watching the video in FF without flash with no issues.

---

### Post by howefield on 2016-04-09
Thread moved to the "*MINT*" sub forum.

---

### Post by Dennis N on 2016-04-09
Well, this is interesting. 

I tried the linked video again from Chromium Browser installed in Manjaro Linux, and it plays fine. It uses the same version of flash plugin, 21.0.0.213.

I then tried the linked video from Chromium Browser installed in Xubuntu 14.04 and it does _not_ play. Using flash plugin 21.0.0.213, it gives the same warning message about outdated plugin as seen in Linux Mint. This is not surprising, as the source of the package (Canonical Partners) is the same as in Mint.

---

### Post by Alex D on 2016-04-09
> **Dennis N said:**
> Well, this is interesting. 

I tried the linked video again from Chromium Browser installed in Manjaro Linux, and it plays fine. It uses the same version of flash plugin, 21.0.0.213.

I then tried the linked video from Chromium Browser installed in Xubuntu 14.04 and it does _not_ play. Using flash plugin 21.0.0.213, it gives the same warning message about outdated plugin as seen in Linux Mint. This is not surprising, as the source of the package (Canonical Partners) is the same as in Mint.

This is really a good finding Dennis.
I wonder whether there is any way to install flash on Mint from the same package of Manjaro :confused:

Alex

---

### Post by Dennis N on 2016-04-09
> **Alex D said:**
> This is really a good finding Dennis.
I wonder whether there is any way to install flash on Mint from the same package of Manjaro :confused:

Alex

Yes, it's possible to copy the plugin, and in fact I did exactly that a few days ago - from Manjaro to Xubuntu 15.04 on another computer I have here. I will check the site in question and let you know.

EDIT: Using Chromium with the copied plugin, the video still didn't play in Xubuntu 15.04 - same warning about the plugin being outdated. So there's nothing special about Manjaro's flash player package.

---

### Post by Alex D on 2016-04-12
This is a mystery to me, however thank you for your effort to help :D

Alex

---

### Post by bcschmerker on 2016-04-13
**I recognize this issue.**  There's already an open bug at Launchpad.net for the Package pepperflashplugin-nonfree:  [Bug #1398145](https://launchpad.net/ubuntu/+source/pepperflashplugin-nonfree/+bug/1398145), originally filed 1 January 2014 for Mint Cinnamon 17.1; I have a duplicate situation in Ubuntu® 16.03b2, which I spell out in "[ERROR: Failed to retrieve status from Google attempting to set up pepperflashplugin-nonfree](http://ubuntuforums.org/showthread.php?t=2319398)."  Basically, pepperflashplugin-nonfree is failing to download the google-chrome-stable package from Google® Download where the skunk PPA Package pepflashplugin-installer succeeds in versions of Ubuntu® prior to 14.04.3-LTS.

---

### Post by roland_burley on 2016-07-09
I am having what I understand to be a common issue but given the lack of discussion here I am wondering if you geniuses have already solved it.
I am running Ubuntu 14.04.3 LTS 64 bit with Chromium and recently Shockwave Flash player keeps on crashing on multiple sites including Facebook. I go to the Adobe site Home/Products/Flash Player/Adobe Flash Player and they auto detect that I have FP ver 16,0,0,235 installed. On the table there it states that FP ver 22.0.0.192 is the latest version for Chromium. I follow the link to their download page where it again auto-detects but this time it says I have FP ver 11.2.202.626 installed and analyses my system as 32 bit. When I try to get a download of FP ver 22.0.0.192 their system slings me over to Ubuntu software centre which informs me I already have FP ver 11 installed. FP still crashes all the time and any residual positive opinion I had of Adobe vanishes like spring mist on a hot summer day. I have tried various of the solutions posted online but still crashville. Any cunning suggestions either as to how I get FP ver 22.0.0.192 OR how to stop the crashing OR both?

---

### Post by Dennis N on 2016-07-09
@roland_burley,

You can get the correct flash player for Chromium by installing the package **adobe-flashplugin** in Ubuntu. You need to enable the Canonical Partners repository in your Software Sources first, and then reload (refresh). Then you can install the package. Doing this would install the latest 22.x version for you.

---

