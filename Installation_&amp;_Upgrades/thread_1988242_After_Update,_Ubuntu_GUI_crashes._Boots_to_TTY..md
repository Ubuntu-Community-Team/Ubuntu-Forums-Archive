---
title: "After Update, Ubuntu GUI crashes. Boots to TTY."
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by hutchisonryan on 2012-05-27
Hello all, and thank you in advance for your help.

I have been running 12.04 since it's release, and haven't had any real issues until now. 

I ran an update from the Update Manager today (it had only been a day or two.) And after it completed it said that I needed to restart to complete the changes. For some reason I couldn't get the update manager to come back up, so I couldn't view the patch notes. Thinking nothing of it, I restarted.

However, afterwards GRUB would load up, but it didn't have the option to load with previous kernels like it did before. (I'm guessing there was a kernel update and it removed obsolete kernels.) I booted from the most recent generic, but once I get to the Ubuntu flash screen, the GUI crashes and it boots to TTY. Unfortunately I can't paste any error messages, since currently I'm running off of a live USB, and this is my only machine. I tried booting Unity and it said it didn't exist. I tried booting Ubuntu-desktop, and it said it didn't exist. From the looks of my .xsession-errors file it seems that compiz is the culprit. When I try to run compiz or do any configuration I get the error message "Compiz (core) Fatal: Couldn't Open Display". I don't see how it could be a driver or video card issue, since I've been running fine for quite some time now. 

Dmesg didn't really seem to give me much information. I've removed and reinstalled compiz via TTY to no avail. I'm at a loss. Once again, thanks for the help.

---

### Post by josephmills on 2012-05-27
Hi there there is a cool tool that I would like you to install it is called pastebinit 
when you get to tty sign in and follow these instructions  
```
sudo apt-get install pastebinit
```
then 
```
lspci -nn | pastebinit
```
you will get a link at the end of the output please write that down so you can paste it here late with others 

then 
```
lsmod | pastebinit
```

grab that link and post both of them here. 
thanks

---

### Post by cam3roon on 2012-05-27
I have the same problem after the update

---

### Post by figuratively on 2012-05-27
I had the same problem. Turns out it was a AMD driver issue. I uninstalled and re installed and now everything works proper. Someone recommended this on another forum but after several reboots I don't have the page otherwise I would post it. Hope that helps.

---

### Post by hutchisonryan on 2012-05-28
Thanks for all of the quick responses and help. Josephmills here are my pastebinit links

[http://paste.ubuntu.com/1010866](http://paste.ubuntu.com/1010866) 
[http://paste.ubuntu.com/1010867](http://paste.ubuntu.com/1010867)

@Figuratively - I am running an ATI HD5670. Seeing as you said it was an AMD issue for you, I guess that could be it. Was it the fglrx driver for you? Why would the update cause a driver issue, and cause it to malfunction in this fashion?

---

### Post by hutchisonryan on 2012-05-28
Welp, looks like that was it. I re-installed the fglrx driver and I'm good to go. Not sure why, but the update completely uninstalled it. However, I'm still having issues with compiz being incredibly unstable.

---

