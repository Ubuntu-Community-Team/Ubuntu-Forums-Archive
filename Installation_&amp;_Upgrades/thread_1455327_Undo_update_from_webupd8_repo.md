---
title: "Undo update from webupd8 repo"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by ericmo on 2010-04-15
I'm kind of new to Ubuntu, I have been only using it for a couple of weeks.

Today I've tried to update Audacious 2.1 to a version, 2.3, that isn't yet on Karmic or Hardy repositories, by adding a PPA to my software sources through this line:

```

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update && sudo apt-get install audacious
```I saw those lines [here]("http://www.webupd8.org/2010/04/install-audacious-230-in-ubuntu-via-ppa.html").

But then, my Ubuntu started acting weird. For example, Nautilus was disassociated from my Main Menu > Places, in such manner that when I tried to open my local folders, I'd get something like "Could not open 'file:///home/' ". I fixed that by opening Nautilus through terminal and doing "open with Nautilus" in some folder. Besides that, my Main Menu is now in english. My native language is pt-br, and even though I've tried to configure Language Support to show everything in pt-br, it doesn't work. There might be more things that are not working, I'm not sure yet. My Creative Zen MP3 Player is not mounting in Nautilus, even though Rhythmbox recognizes it.

So, I'd like to undo this update.
For what I've googled, it seems that I cannot do that. But I was trying to "downdate" the packages, by removing that PPA above and doing a sudo apt-get update, but it says I can't update because I've already got the newest packages. Is there a way to force sudo apt-get to install the latest packages in the standard repos, ignoring what is already installed? Or maybe, to do that from the CD - I tried to "update" to Ubuntu 9.10 from the CD, but it doesn't work because I'm already using 9.10. Or to reinstall Ubuntu without losing my data? I did put /home in its own partition, but not /etc, so would I have to install every software again, if I do reinstall Ubuntu? 

I'm using Ubuntu Studio distribution.

---

### Post by ericmo on 2010-04-15
I can open my local folders, but I can't open trash and network folders within Nautilus.

---

### Post by ericmo on 2010-04-15
Ok, so I went ahead and reinstalled Ubuntu. Thought that having /home in its own partition would let me keep my files, but I can't access them, Ubuntu won't even load the Gnome panel, and Nautilus says it can't mount some folders.
 
Well, think I'll have to start from scratch...

---

