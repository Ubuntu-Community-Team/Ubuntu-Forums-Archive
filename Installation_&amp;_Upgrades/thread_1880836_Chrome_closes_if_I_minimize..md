---
title: "Chrome closes if I minimize."
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by katya_sehgal on 2011-11-14
I have installed google chrome. However, it closes whenever I minimize it and I have to restart it every time.

I prefer it over other browsers. 

Is there an immediate solution for this that I may have missed in the forums?

---

### Post by vasa1 on 2011-11-14
> **katya_sehgal said:**
> I have installed google chrome. However, it closes whenever I minimize it and I have to restart it every time.

I prefer it over other browsers. 

Is there an immediate solution for this that I may have missed in the forums?

How do you minimize it?

---

### Post by katya_sehgal on 2011-11-14
> **vasa1 said:**
> How do you minimize it?

by clicking on the minimize button. Just as I do for firefox and others. They then shift to the 'launcher' on the left side of the screen where I can access them at a later stage. This doesn't work for chrome though.

Important: I believe this problem started immediately after installing google voice and video chat. Can this be possible? I am trying to search where the files are located so I can uninstall them. No luck. Can't locate.

---

### Post by BillyBoa on 2011-11-14
You could try to find the packages of google voice and video chat in Synaptic. Install Synaptic through Ubuntu Software Center.

---

### Post by katya_sehgal on 2011-11-14
> **BillyBoa said:**
> You could try to find the packages of google voice and video chat in Synaptic. Install Synaptic through Ubuntu Software Center.

I had successfully installed the chat program from the website. I am now trying to delete it to see if it is causing the chrome error. Chrome was working fine initially. It would minimize just like firefox and other programs.

Any early solutions?

---

### Post by katya_sehgal on 2011-11-14
> **BillyBoa said:**
> You could try to find the packages of google voice and video chat in Synaptic. Install Synaptic through Ubuntu Software Center.

Have just realised that synaptics is a very essential tool. Getting it now.

However, any way out for the chrome minimizing issue?

---

### Post by BillyBoa on 2011-11-14
There is a trick solution. Export your bookmarks and anything you could and close Chrome. Go to Home directory, then push CTRL+H to see the hidden folders and go to .config, open it and rename the folder .google-chrome to something like google-chrome1. Then open again Chrome to see if the problem insists.

---

### Post by vasa1 on 2011-11-14
Running this code will give you a list of software present on your system (as a text file called "installed-software"):
```
dpkg --get-selections > installed-software
```

This maybe useful because the same thing is addressed differently sometimes:
gedit = Text Editor
Evince = Document Viewer
gnome-tweak-tool = Advanced Settings

You may find the software you installed by its other name.

I'm using plain Chrome 15 on 11.10 without a problem so it's quite likely that it's something you've installed that isn't playing well with something else.

Before you try BillyBoa's suggestion you could try something simpler.
**Wrench, Tools, Extensions** and once there, disable all extensions. Then restart Chrome and see.

---

### Post by katya_sehgal on 2011-11-14
> **BillyBoa said:**
> There is a trick solution. Export your bookmarks and anything you could and close Chrome. Go to Home directory, then push CTRL+H to see the hidden folders and go to .config, open it and rename the folder .google-chrome to something like google-chrome1. Then open again Chrome to see if the problem insists.


No luck. The problem persists. I still cannot minimize it. It shuts every time I do so.
Using synaptics, I have also 'marked for complete removal' google video-chat. That has not solved the issue.

---

### Post by katya_sehgal on 2011-11-14
> **vasa1 said:**
> Running this code will give you a list of software present on your system:
```
dpkg --get-selections > installed-software
```This maybe useful because the same thing is addressed differently sometimes:
gedit = Text Editor
Evince = Document Viewer
gnome-tweak-tool = Advanced Settings

You may find the software you installed by its other name.

I'm using plain Chrome 15 on 11.10 without a problem so it's quite likely that it's something you've installed that isn't playing well with something else.

Before you try BillyBoa's suggestion you could try something simpler.
**Wrench, Tools, Extensions** and once there, disable all extensions. Then restart Chrome and see.


I already used BillyBoa's suggestion. No luck there.
I shall now use your method after syncing my bookmarks again and plugins again. 
Do note that chrome had no problems initially. So it may be an additional software that is causing the issue.
I have removed google video chat from synaptics but that has not done anything for chrome.

---

### Post by BillyBoa on 2011-11-14
Then you should remove Chrome and reinstall it

```
sudo apt-get remove google-chrome-stable
```

if you use Chrome beta change -stable for -beta or -unstable if you went too far.

Then you can reinstall it as you did to install it.

---

### Post by vasa1 on 2011-11-14
Can you minimize by holding down alt and then pressing the spacebar and then letting go both the alt key and the spacebar and typing the letter **n** (for minimize)?

---

### Post by vasa1 on 2011-11-14
> **BillyBoa said:**
> Then you should remove Chrome and reinstall it

```
sudo apt-get remove google-chrome-stable
```

if you use Chrome beta change -stable for -beta or -unstable if you went too far.

Then you can reinstall it as you did to install it.

```
sudo apt-get purge google-chrome-stable
``` maybe be better.

It may also be worth deleting the folder **~/.config/google-chrome** after you've exported your bookmarks safely.

I case of a re-install, my *preference* would be to stay with Chrome stable and not to try other versions or Chromium.

---

### Post by katya_sehgal on 2011-11-14
google-chrome-stable_current_i386.deb

this is the package from where I installed google chrome. I got this package from the website. 
I tried deleting from .config 'google-chrome'. However it reappears as soon as I delete it. 
Do you reckon I should delete the package and reinstall it from the website? Considering that this is the stable version of Chrome you were mentioning.

---

### Post by BillyBoa on 2011-11-14
> **katya_sehgal said:**
> google-chrome-stable_current_i386.deb

this is the package from where I installed google chrome. I got this package from the website. 
I tried deleting from .config 'google-chrome'. However it reappears as soon as I delete it. 
Do you reckon I should delete the package and reinstall it from the website? Considering that this is the stable version of Chrome you were mentioning.

But I told you how to, on my message above. Go to a terminal and write:

```
sudo apt-get remove google-chrome-stable
```

---

### Post by katya_sehgal on 2011-11-14
> **BillyBoa said:**
> But I told you how to, on my message above. Go to a terminal and write:

```
sudo apt-get remove google-chrome-stable
```


I did that. Was talking about the deb file, on clicking it you reach the software centre that lets you install chrome. 
This is what I will be doing. I will reinstall entirely, deleting the current file.
Somehow, the Software Centre is not opening for the last 15 minutes. I have read elsewhere that it is a recurring problem for many.

---

### Post by katya_sehgal on 2011-11-14
ok, now the software centre is not opening. :-)

---

### Post by katya_sehgal on 2011-11-14
restarted ubuntu to get the software centre working.
Chrome now looks fine. The minimize option is fine and it stays in the launcher like every other well-behaved program.

Shall import bookmarks and plugins from google sync.
should this cause any problems then I shall notify for other users.

Edit: Shall mark as solved in some days after observation and report plugin conflict if any.

cheers vasa1 and BillyBoa. Coffee on me.

---

### Post by katya_sehgal on 2011-11-16
No problems thus far. I am marking this thread as solved.

Solution: Re-install Chrome. Problem arose probably after I installed Google Video chat in system. 

Idea: Good practice to sync Chrome with your account. This way you never lose anything if Chrome crashes or you have to re-install it.

---

