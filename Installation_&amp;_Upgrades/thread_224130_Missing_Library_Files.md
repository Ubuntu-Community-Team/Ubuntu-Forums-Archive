---
title: "Missing Library Files"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by fredbro on 2006-07-27
I am trying to get and install Audacity for sound recording and editing.  Synaptic tells me that 3 library file dependencies are missing.  I have the Universe and Multiverse enabled but don't see these files.  Could someone tell me how to obtain and install these library files so that I can then install Audacity:

libidtag0, libmad0, and libwxgtk2A-1. 

Is there another recommended application for sound recording and editing?  I want to take analog audio from vinyl records and convert it to digital audio files.

Thanks for any help, fredbro

---

### Post by linear on 2006-07-27
Is it possible that something is wrong with sources.list? There shouldn't be any trick to installing Audacity. Those libraries _are_ in the repositories.

---

### Post by fredbro on 2006-07-28
Thanks for your reply Linear, do you know if all the sources.list should show up in Synaptic and how I can check that Universe and Multiverse are really enabled?  I followed the wiki and edited the settings for Multiverse and Universe and did not get any error messages.  I have scanned through all the packages listed by Synaptic and do not seee these library files.  Should I be able to see them?  Or, would they be part of a package with a different name?

Sorry for all the followup questions.  Just trying to learn about this.

Thanks again for your time, fredbro

---

### Post by fredbro on 2006-07-29
I found what appears to be some really good unofficial wiki info at:

```
http://ubuntuguide.org/wiki/Ubuntu
``` 

I followed this information to replace and update my /etc/apt/sources.list files and then was able to find all of the library dependency files and get and install Audacity.

First I made a copy of my /etc/apt/sources.list that was not working very well for me by the following:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bkup
```

Then I replaced the sources.list lines with suggested lines from the ubuntu guide noted above.  

Then I updated and upgrade my sources.list by the following commands:

```
sudo apt-get update

sudo apt-get upgrade
```

Then I used Synaptic to get Audacity and the required library files noted by Synaptic.  

Audacity was then installed.  I have not used and tested it yet.

I really like the Ubuntu guide info noted above because it clearly describes and shows command line examples unlike a lot of the Ubuntu Forum posts.

In case you are thinking about using info in this post, please note that I am a really inexperienced person not too far beyond newbie status so proceed with caution and at your own risk.  That said, I believe referring to the unofficial Ubuntu guide may be very fruitful for people like me.  I actually found it easier to use and more useful then my hours of searching Ubuntu Forum posts and making numerous Ubuntu Forum posts for assistance and advice.

Good luck and help us all slay the MS dragon!:p 

fredbro

---

