---
title: "Install pepper flash"
date: 2014-12-04
forum: Installation &amp; Upgrades
---

### Post by michael-piziak on 2014-12-04
I need to install pepper flash to get my flash working for Chromium.

I tried "[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install pepperflashplugin-nonfree"
but it couldn't locate the package.

Flash works with Firefox oddly enough.

There's only one website I need flash for when running Chromium (to upload photos to photo contests - dpreview), or I wouldn't bother.

[/FONT][/COLOR]

---

### Post by carlwsnyder on 2014-12-04
Did you check with Ubuntu's Software Center?  I believe the package pepperflashplugin-nonfree is in the Multiverse repository, which you must have enabled, and is NOT enabled by default for software which is encumbered by licensing which makes the contents non-free.

---

### Post by michael-piziak on 2014-12-04
> **carlwsnyder said:**
> Did you check with Ubuntu's Software Center?  I believe the package pepperflashplugin-nonfree is in the Multiverse repository, which you must have enabled, and is NOT enabled by default for software which is encumbered by licensing which makes the contents non-free.

How do I enable this multiverse repository ?    See my screen shot below of what I think is enabled.

---

### Post by carlwsnyder on 2014-12-04
You have the same repositories that I have enabled, and I have flashplugin-nonfree installed from Synaptic in Xubuntu.

---

### Post by slickymaster on 2014-12-04
> **michael-piziak said:**
> How do I enable this multiverse repository ?    See my screen shot below of what I think is enabled.

Multiverse repository can be enabled by uncommenting the corresponding apt lines (i.e. delete the '#' at the beginning of the line).

Open a terminal window and run the following:```
sudo nano /etc/apt/sources.list
```and remove the # from the front of the respective line.

Edit: For more information, please refer to [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by michael-piziak on 2014-12-04
> **carlwsnyder said:**
> You have the same repositories that I have enabled, and I have flashplugin-nonfree installed from Synaptic in Xubuntu.

I found "flashplugin-nonfree" and installed it.  It did not allow my Chromium Browser to do flash at dpreview.com when entering a photo in a challenge contest.

I can not find pepperflash in the software center, nor can I get pepperflash to install with the sudo command in terminal.

---

### Post by michael-piziak on 2014-12-04
> **slickymaster said:**
> Multiverse repository can be enabled by uncommenting the corresponding apt lines (i.e. delete the '#' at the beginning of the line).

Open a terminal window and run the following:```
sudo nano /etc/apt/sources.list
```and remove the # from the front of the respective line.

Edit: For more information, please refer to [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)


I'm afraid that performing this is beyond my computer skill level.

Surely there is an easy way to get pepperflash.  Previously when I was running 12.04 32 bit I got pepperflash with ease.  Now that I've updated my system to 64 bit (12.04 lts), I just can't seem to get it.

Why can't "[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install pepperflashplugin-nonfree"  [/FONT][/COLOR]install it?   Why can't I locate it in the software center ?

---

### Post by Dennis N on 2014-12-04
> Why can't "sudo apt-get install pepperflashplugin-nonfree" install it? Why can't I locate it in the software center ? 

I find it in the Ubuntu Software Center (14.04). Put "pepperflash" in the search box, and the result shows "Pepper Flash Player  - browser plugin" which is what you want.

---

### Post by Dennis N on 2014-12-04
Well, I just noticed that you are using 12.04 - in that case, I think you need to use a PPA to install it.

---

### Post by michael-piziak on 2014-12-04
> **Dennis N said:**
> I find it in the Ubuntu Software Center (14.04). Put "pepperflash" in the search box, and the result shows "Pepper Flash Player  - browser plugin" which is what you want.

I am running Ubuntu 12.04 lts (64 bit).  When I type pepperflash in the software center, it can not find it.  See screenshot below.

---

### Post by michael-piziak on 2014-12-04
> **Dennis N said:**
> Well, I just noticed that you are using 12.04 - in that case, I think you need to use a PPA to install it.

ok, please tell me how to use a ppa to install it.  I'm not sure what ppa means, but I have tried to install pepperflash from terminal - with no luck.

---

### Post by carlwsnyder on 2014-12-04
You may want to bite the bullet and install the proprietary Google Chrome to get pepperflash to work on 12.04 64-bit.  If I recall correctly, Google Chrome, and thus pepperflash, was 32-bit only on many platforms during the 2012-2013 era.

---

### Post by michael-piziak on 2014-12-04
> **carlwsnyder said:**
> You may want to bite the bullet and install the proprietary Google Chrome to get pepperflash to work on 12.04 64-bit.  If I recall correctly, Google Chrome, and thus pepperflash, was 32-bit only on many platforms during the 2012-2013 era.

That is fine.  I have no problem using Chrome.   HOWEVER, I can't get it to install.  I downloaded the Chrome deb file and got stuck when it told me to type "google-chrome-stable" in terminal.  See this post if you can help with that.

[http://ubuntuforums.org/showthread.php?t=2255401](http://ubuntuforums.org/showthread.php?t=2255401)

---

### Post by Dennis N on 2014-12-04
See Post #9 first. You won't find it in the Ubuntu repositories.

Try this PPA - I remember using it for Chromium when I had it on 12.04 on my system. Note the install instructions on this page under "Making Chromium Use Pepperflash"

[https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash](https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash)

---

### Post by Dennis N on 2014-12-04
> **michael-piziak said:**
> ok, please tell me how to use a ppa to install it.  I'm not sure what ppa means, but I have tried to install pepperflash from terminal - with no luck.

First you add the PPA to your sources:

```
sudo apt-add-repository ppa:skunk/pepper-flash
```

then update your sources:

```
sudo apt-get update
```

then you can install it.

```
sudo apt-get install  peperflashplugin-nonfree
```

Again note the instructions on the PPA's page under "Making Chromium Use Pepperflash".

---

### Post by michael-piziak on 2014-12-04
> **Dennis N said:**
> First you add the PPA to your sources:

```
sudo apt-add-repository ppa:skunk/pepper-flash
```

then update your sources:

```
sudo apt-get update
```

then you can install it.

```
sudo apt-get install  peperflashplugin-nonfree
```

Again note the instructions on the PPA's page under "Making Chromium Use Pepperflash".

Everything worked until the final sudo command, then I got this again:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo apt-get install peperflashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package peperflashplugin-nonfree
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$


If you could tell me how to undo what I did in the first 2 sudo commands I would appreciate it.   Then I will try to install Chrome.

---

### Post by Dennis N on 2014-12-04
Here is an article on installing pepperflash-plugin from back in 2013 which applies to your 12.04 system. He also mentions in an update that 14.04 uses the repository, which is the reason for all the confusion in the responses (you didn't mention you were using 12.04 until post #7).

[http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)

---

### Post by craig10x on 2014-12-04
For google chrome...open up firefox, go to the google chrome site and click on the download for it (you can select 32 bit or 64 bit versions) when it downloads, a window will come up in firefox asking if you want to save the file or open it in "ubuntu software center"  select that...(open in...) and after about a minute, your ubuntu software center should open and ask you to click it on if you want to install it...
Once installed, bring it up in the dash search, open chrome and lock it to the unity launch (by right clicking)...

Just saw your other post...looks like it installed...just do as deadflwr said and open the dash and type google chrome and you should see the icon for it...click on it and it should open and then lock it to the unity launcher...

---

### Post by Dennis N on 2014-12-04
> **michael-piziak said:**
> Everything worked until the final sudo command, then I got this again:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo apt-get install peperflashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package peperflashplugin-nonfree
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$


If you could tell me how to undo what I did in the first 2 sudo commands I would appreciate it.   Then I will try to install Chrome.

Well, something went wrong here. Seems like the source was not added or the source lists not updated. Could do some troubleshooting, but, you can install Chrome if you wish.

You can remove the repository (if it got added at all) by using Synaptic Package Manager and going to  **Settings > Repositories > Other Software**. Look in the list for the new PPA, highlight it, and click on the **Remove** button on the bottom.

The other command just updated your software list, so nothing to undo.

---

### Post by michael-piziak on 2014-12-04
> **Dennis N said:**
> Well, something went wrong here. Seems like the source was not added or the source lists not updated. Could do some troubleshooting, but, you can install Chrome if you wish.

You can remove the repository (if it got added at all) by using Synaptic Package Manager and going to  **Settings > Repositories > Other Software**. Look in the list for the new PPA, highlight it, and click on the **Remove** button on the bottom.

The other command didn't work so nothing to undo.

I don't have Synaptic Package Manger, all I have is Software Center and terminal.   Perhaps you could tell me how to remove it with one or the other of those.


BTW  Thanks so much for your attempts to help me.  I have installed Chrome, and it works fine with flash.  But I would like to remove anything that was done with the first two commands please.

---

### Post by Dennis N on 2014-12-04
```
sudo apt-add-repository -r ppa:skunk/pepper-flash
```

should do it.

---

### Post by michael-piziak on 2014-12-04
> **Dennis N said:**
> ```
sudo apt-add-repository -r ppa:skunk/pepper-flash
```

should do it.

did you mean sudo apt-remove-repository -r ppa:skunk/pepper:flash

I installed synaptic and removed the 2 skunk ones at the bottom.  Now it looks like the image below.

---

### Post by michael-piziak on 2014-12-04
One last question.  In the Synaptic screen shot I posted, what are the 2 packages that have the word "bearoso" in them.   I wondered if I put them on the system or if they should be there.

---

### Post by Dennis N on 2014-12-04
> **michael-piziak said:**
> did you mean sudo apt-remove-repository -r ppa:skunk/pepper:flash

I installed synaptic and removed the 2 skunk ones at the bottom.  Now it looks like the image below.

The command is correct the way it is. You don't need it now since you did what I suggested with Synaptic Package Manager. The PPA is now gone.

---

### Post by Dennis N on 2014-12-04
> **michael-piziak said:**
> One last question.  In the Synaptic screen shot I posted, what are the 2 packages that have the word "bearoso" in them.   I wondered if I put them on the system or if they should be there.

It's Another PPA -- for Super Nintendo Emulator (snes9x). Someone or something added them at some time.

---

### Post by michael-piziak on 2014-12-05
Thanks to everyone that tried to help me install pepperflash on my 12.04 lts (64 bit) system.

Personally, I believe that pepperflash should be added back to the software center for my distro - as Ubuntu 12.04 is suppose to be supported for a couple more years.

I did upgrade to 14.04 lts once, but I had a few things not work (like Snes9x, etc ...).    I went back to 12.04 lts intentionally.

I've installed Google Chrome, so that's satisfactory to me.  I like to have 2 browsers to use (on any computer), in case a web page doesn't work right in one browser.

Is there anywhere I can report that I would like Ubuntu Software Center to keep offering pepper flash for 12.04 so people can use Chromium better ?

---

### Post by nerdtron on 2014-12-05
The pepperflash plugin is not FREE software (not open source, I believe) and thus it is will never be available on the default or official repositories of Ubuntu

---

### Post by michael-piziak on 2014-12-05
> **nerdtron said:**
> The pepperflash plugin is not FREE software (not open source, I believe) and thus it is will never be available on the default or official repositories of Ubuntu

Thanks for the reply.

My response would be, atleast it should be made available where 12.04 lts  users can get it in terminal.

---

### Post by deadflowr on 2014-12-05
> **nerdtron said:**
> The pepperflash plugin is not FREE software (not open source, I believe) and thus it is will never be available on the default or official repositories of Ubuntu

Pepperflash is Adobe Flash but built to be used with the pepper plugin api (PPAPI) and not the standard NPAPI(netscape plugin api).
So it could, in theory, be made available *if* Adobe wanted it to be, right along side the adobe flashplugin, which is currently installable through the Ubuntu repo system.

But yes, it will never come with the install disk, and never be in the main or universe repos.
(I think flash is in either multiverse or partner)

---

### Post by michael-piziak on 2014-12-08
> **nerdtron said:**
> The pepperflash plugin is not FREE software (not open source, I believe) and thus it is will never be available on the default or official repositories of Ubuntu

Thanks for your reply.  

My response would be:  Well shouldn't pepperflash at least be available to 12.04 lts users with a Terminal command line - ?

---

### Post by pqwoerituytrueiwoq on 2014-12-08
> **michael-piziak said:**
> Thanks for your reply.  

My response would be:  Well shouldn't pepperflash at least be available to 12.04 lts users with a Terminal command line - ?
in recent releases there is a packange that downloads chrome and takes pepper flash and makes it useable via chromium
pepperflashplugin-nonfree - [http://packages.ubuntu.com/trusty/pepperflashplugin-nonfree](http://packages.ubuntu.com/trusty/pepperflashplugin-nonfree)

you can always install google chrome

---

### Post by michael-piziak on 2014-12-08
> **pqwoerituytrueiwoq said:**
> in recent releases there is a packange that downloads chrome and takes pepper flash and makes it useable via chromium
pepperflashplugin-nonfree - [http://packages.ubuntu.com/trusty/pepperflashplugin-nonfree](http://packages.ubuntu.com/trusty/pepperflashplugin-nonfree)

you can always install google chrome

Thanks so much for your reply.

I did install Google Chrome (64 bit version).  It works great.

My response would be:  Google Chromium is Open Source; whereas, Google Chrome is not.  Google Chromium is also in the Software Center.

---

### Post by pqwoerituytrueiwoq on 2014-12-08
Chromium is google chrome without google and there proprietary modifications (PDF and Flash)

---

