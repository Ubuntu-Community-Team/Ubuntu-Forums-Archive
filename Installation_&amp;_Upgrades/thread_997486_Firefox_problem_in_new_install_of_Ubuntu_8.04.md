---
title: "Firefox problem in new install of Ubuntu 8.04"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by bubbabeernuts on 2008-11-29
I just installed Ubuntu Linux version 8.0.4(Hardy Heron) inside a second partition on my laptop.  I then downloaded and installed all the latest updates. Everything went fine. But I have one problem.  Every time I click to open Firefox, the Clear Private Data window opens, and won't close.  I click Cancel or Clear Private Data Now, but nothing happens.  That's as far as I get when trying to open Firefox.  I can close it by opening a 
terminal and typing killall firefox.

I then opened the Synaptics Package Manager and marked Firefox for removal.  I then removed it, reinstalled it, and tried again.  And again, I got the Clear Private Data window.  But this time I was able to click the Cancel button, which then brought me to the Restore Previous Session window.  That's where I got stuck again.

I then marked Firefox for complete removal in Synaptics Package Manager, downloaded a fresh install package, and tried to start from scratch.  Now it locks up at the Clear Private Data window again.

It's Firefox version 3.0.4.  And all this started happening when I tried installing the Foxmarks plugin.

I've been using Konqueror for browsing in the meantime.

Can anyone offer any suggestions for getting past this roadblock?

---

### Post by sosaudio1 on 2008-11-29
> **bubbabeernuts said:**
> I just installed Ubuntu Linux version 8.0.4(Hardy Heron) inside a second partition on my laptop.  I then downloaded and installed all the latest updates. Everything went fine. But I have one problem.  Every time I click to open Firefox, the Clear Private Data window opens, and won't close.  I click Cancel or Clear Private Data Now, but nothing happens.  That's as far as I get when trying to open Firefox.  I can close it by opening a 
terminal and typing killall firefox.

I then opened the Synaptics Package Manager and marked Firefox for removal.  I then removed it, reinstalled it, and tried again.  And again, I got the Clear Private Data window.  But this time I was able to click the Cancel button, which then brought me to the Restore Previous Session window.  That's where I got stuck again.

I then marked Firefox for complete removal in Synaptics Package Manager, downloaded a fresh install package, and tried to start from scratch.  Now it locks up at the Clear Private Data window again.

It's Firefox version 3.0.4.  And all this started happening when I tried installing the Foxmarks plugin.

Can anyone offer any suggestions for getting past this roadblock?

How familiar are you with tinkering around in FF???

---

### Post by bubbabeernuts on 2008-11-29
> **sosaudio1 said:**
> How familiar are you with tinkering around in FF???

I don't have a problem with it if I get good instructions.

I was kind of thinking that I might need to reconfigure something manually.  

I'm a newb to Ubuntu, by the way.  But I'm a quick study.  I installed Epiphany to use in the meantime.

---

### Post by sosaudio1 on 2008-11-29
> **sosaudio1 said:**
> How familiar are you with tinkering around in FF???

try going into your .mozilla folder and then firefox and see if you see your extension there....then try looking into extensions and see if it is there...if you are unsure go inside the folder and see if you see anything that looks like your extension from there. Make another folder called bad extensions and place that folder in there. Start FF and see if it works.

There was a time when I had crash that was bad enough where FF would start and die. I made a new profile and discovered that FF would work. So I went back removed the extensions in the extension folder and added them back one by one restarting FF in between to see if it made a difference until I got to the one that caused FF to crash and I deleted that extension's folder to get FF working again....deleted the new profile made and then voila back to working again

---

### Post by aysiu on 2008-11-30
Close Firefox completely and then open a [terminal](http://www.psychocats.net/ubuntu/terminal) and type the command ```
firefox -profilemanager &
``` This should allow you to disable your extensions and/or create a fresh profile.

---

### Post by bubbabeernuts on 2008-11-30
> **aysiu said:**
> Close Firefox completely and then open a [terminal](http://www.psychocats.net/ubuntu/terminal) and type the command ```
firefox -profilemanager &
``` This should allow you to disable your extensions and/or create a fresh profile.

The terminal solution seems to have done the trick. I'm able to open Firefox with no issues.  Thanks for the assist!  I hope I'm able to become well-versed enough on Linux so I can give back when someone else has problems.

Let me ask this: does Foxmarks have issues in Linux?  I have no problems when using it in Windows.  Maybe I was using the wrong version.  Is there a Linux-only version of Foxmarks?

---

### Post by aysiu on 2008-11-30
I've never used Foxmarks, but I do know that sometimes a badly constructed extension can ruin a Firefox profile... or sometimes extensions can conflict with one another.

---

### Post by sosaudio1 on 2008-11-30
> **aysiu said:**
> I've never used Foxmarks, but I do know that sometimes a badly constructed extension can ruin a Firefox profile... or sometimes extensions can conflict with one another.

This is very true considering the one I had...I forget the name of the plugin...but geez

---

