---
title: "Stuff installed in Synaptic"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by peyre on 2011-07-02
I'm getting ready to back up all my data and reinstall Ubuntu from scratch, to clear up some various issues.  It sure would be helpful if I could see a quick list in Synaptic or the Ubuntu Software Center of all the things I've installed myself.  That would help with this whole process.

---

### Post by scu-ba-de-buntu on 2011-07-03
Edit: This doesn't seem to work for me, so try another method. The various options seem to only save what you have marked in that session. :/ ??

I believe there is a file, maybe an XML file somewhere which your saved packages are stored, however I can't seem to remember where that is.

> You should be able to just do FILE->Save Markings As. and then load them back up later. Test this first though

---

### Post by mörgæs on 2011-07-03
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857) (search for 'dpkg').

---

### Post by peyre on 2011-07-03
Hey, that worked.  It looks, though, like it shows *everything* installed on my computer, including what installed with Ubuntu.  That's the next best thing though, and I can use this.  I guess I'll mark it solved, since I got close to what I was hoping for.

For those coming to this discussion, what you do is open a terminal window and enter:
```
dpkg --get-selections > installed-software
```
It may error out, but you can ignore the error.  It will create a text file called "installed-software" with a list of all the software installed on your computer.  It created the file on the root of my home directory, probably because that's what the terminal window defaults to.  So look for the file either on your home directory, or wherever your terminal window is pointed when you run the command.

---

