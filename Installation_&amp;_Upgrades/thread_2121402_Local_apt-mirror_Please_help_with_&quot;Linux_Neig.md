---
title: "Local apt-mirror: Please help with &quot;Linux Neighbors&quot; Install Fest"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2013-03-01
We've started a LUG called "Linux Neighbors" to help new users familiarize themselves with Linux, especially Ubuntu.

We're going to be having an Install Fest on the 23rd of March and we want to use our local Ubuntu and Debian Testing mirrors during the installations. However, we are not all that interested in PXE booting at this time; we would prefer to have the installs follow procedures that are very similar to the procedures a person would need to follow if they were installing Ubuntu on their own. This is because part of our purpose is to train people to install Linux on themselves without relying on extra help from anyone. (I know that this is easy with Ubuntu, but people who've never done it before don't know. Also, getting multimedia stuff going is a bit complicated for someone who's never had to deal with it before; we're talking about totally green here.)

So we were hoping to use the Ubuntu install disk but point it to our local server somewhere along the way; so far, we've not found a way to do this. What are we missing? Is there no built-in protocol to direct the Ubuntu installer to our local server to get the packages and updates? (The Debian installer has this feature.) If there isn't a way to manually configure where the installer points to, then I guess what we might do is alter the sources.list file on the Ubuntu .iso before burning it. 'Seems a shame to do it that way though as we've already paid for 10 Ubuntu 12.04 disks that are sitting right in front of me. . .

Any other suggestions? BTW, if we do alter the sources.list, should we comment out references to the default repos? I'm not sure what will happen if we leave them in and I'm just anticipating that if apt's behavior is to just go with the first hit and ignore the rest then we shouldn't comment out. What I mean is that we'd prefer to not have to alter the sources.list after installing; but, if we add our local repos to the sources.list then this could potentially trigger errors from apt. I just don't remember how apt works; does it throw up an error whenever it can't stat a repo? Will it continue on to the next working repo if the previous repos can't be found?

Thank you for any help you can offer. Also, if you're in the DC metropolitan area, please come out to our Install Fest!

You can also join us at [http://www.meetup.com/Linux-Neighbors](http://www.meetup.com/Linux-Neighbors)

Cheers.

---

