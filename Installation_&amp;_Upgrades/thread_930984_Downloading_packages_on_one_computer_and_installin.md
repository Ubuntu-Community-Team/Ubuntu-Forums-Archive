---
title: "Downloading packages on one computer and installing them on another"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by Annoying Moose on 2008-09-26
Hello.

In my computer engineering class, I will be using a computer running the i386 desktop edition of Xubuntu Hardy, and I will want to be able to install/upgrade software.  The catch is that the computer will not have internet access, so I will need to download the packages on my own computer (amd64 Ubuntu Hardy desktop), transfer them to the CE computer via removable media, and install them manually.  Could someone please explain to me how to accomplish this?

Thanks.

---

### Post by Custom Cowboy on 2008-09-26
The program you need is "Apt on CD" from "Add remove applications".It will create a cd containing all the applications installed as well as updates. It will place the data in the cache and they can be installed when needed.It will also create an ISO instead of a CD. Happy computing.:guitar:

---

### Post by Annoying Moose on 2008-09-26
Alright, but first I need to download the specific packages and their dependencies without installing them and regardless of whether or not they're already installed.  What's the best way to do that?

EDIT: Also, it's worth reiterating that my own computer uses amd64 Ubuntu, while my CE computer will use i386 Xubuntu.  How do I download the x86 packages instead of the x64 ones?

---

### Post by robert shearer on 2008-09-27
Hmm, the left field answer is to install  Xubuntu (32bit) on your machine as a second o/s and dual boot. 
Then you can boot into Xubuntu and download updates (and install to check that all is ok) then make an APToncd cd or iso to take to the other computers.
You would only need a small Xubuntu install(5-10Gb?)

Or dig out an older low-spec machine and do a Xubuntu install on that keeping it only for making APToncd updates.

---

### Post by Annoying Moose on 2008-09-27
Oof.  I'm not willing to put my hard drive back under the knife for this.  I think I have an older desktop machine downstairs that I could use, but it still seems a rather roundabout solution when all I'm essentially trying to do is find a specific group of files and download them.  Hm... I haven't tried using aptitude to download packages onto removable media from the LiveCD, so I'll try that first.  If it doesn't work out, I'll try bringing up the old beast downstairs.  Thank you two, for your help.

EDIT: Okay, here's what I did:

I booted into i386 Xubuntu using the LiveCD.  From there, I used aptitude to simulate installing the packages I wanted.  Then I manually downloaded the packages on the list given by the simulation.  Booting back into amd64 Ubuntu, I used the downloaded packages to make the disk image with APTonCD, which I then burned to a CD.  Come Monday, I'll copy the packages to /var/cache/apt/archives and install the software as I would if there were an internet connection.  If there's something wrong with that process, please let me know now so I can correct it before Monday.

---

### Post by robert shearer on 2008-09-28
> EDIT: Okay, here's what I did:

I booted into i386 Xubuntu using the LiveCD.  From there, I used aptitude to simulate installing the packages I wanted.  Then I manually downloaded the packages on the list given by the simulation.  Booting back into amd64 Ubuntu, I used the downloaded packages to make the disk image with APTonCD, which I then burned to a CD.  Come Monday, I'll copy the packages to /var/cache/apt/archives and install the software as I would if there were an internet connection.  If there's something wrong with that process, please let me know now so I can correct it before Monday.



Good to know that it can be done with the live cd. 
I wonder if there will be a problem doing this in the future as searching for the updates will be based on the static live cd and not an up to date o/s?.Dependencies could be a concern as Hardy moves through it's point releases (currently 8.04.1)
You may have to download and burn a new live cd at each point release then use that to run update searches.
Would be interested to know how it goes.

On my Aptoncd updates I have not experienced any major troubles.
Though after the point release I had to connect the target computer to the net to resolve a couple of dependency issues but the download was minor.

See here for other experiences and ways to use the APToncd cd.
[http://ubuntuforums.org/showthread.php?t=928022](http://ubuntuforums.org/showthread.php?t=928022)

---

