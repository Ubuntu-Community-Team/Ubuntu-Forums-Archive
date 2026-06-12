---
title: "OEM seal having problems"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by DemiAlbedo on 2008-05-17
I installed Kubuntu 8.04 hardy heron with much success but I ran into one problem. I installed hardy heron under the OEM manufacturer setting when I installed it because my intension was to create a whole desktop them and distribute it among several computers. 

The problem I'm having is I have finished my desktop and I wanted to test it on my girlfriends computer. I transfered the partition over to a new hard drive and installed it into her computer. Everything booted fine and I clicked the button for OEM seal. It sealed it so that she can enter in her username and password, however after she booted into kubuntu everything was defaulted back to the way it comes if you did a normal install. My background was not there, colours are gone, panels changed, folders I created are now gone. . .

Any software I had installed is still there. . .

Anyone have any solutions to what went wrong? I thought OEM seal was suppose to keep all my setting, folders, colours, etc and "reset" kubuntu so that a new user could enter in their own username and password?

---

### Post by DemiAlbedo on 2008-05-22
I have semi fixed the problem. The problem is that everything is done under the /home/oem directory,but when you seal your distro the home directory changes to /home/(whatever user name they enter). So because the home directory is changed everything is lost. . .unless the username the person enters is oem 

To fix this problem you have to copy everything from the /home/oem/.kde/share to /etc/skel. Anything that is put into the skel directory tells kubuntu to make that the default. This way when you seal your distro everything you have done is now considered the "default" This makes your wallpaper default wallpaper, icons default icons, etc. 

I still have one problem that i'm working on with the oem seal. I use kdesktop menu instead of the default kmenu. I added some new tabs for videos,music,documents, and pictures. I keep losing these tabs after I seal because the configuration file for kdesktop is not located under /home/oem/.kde/share/ Only a matter of time before I can fix that.

Some serious changes need to be made to the oem seal function because all this work kind of defeats the whole purpose of the oem seal :P

---

