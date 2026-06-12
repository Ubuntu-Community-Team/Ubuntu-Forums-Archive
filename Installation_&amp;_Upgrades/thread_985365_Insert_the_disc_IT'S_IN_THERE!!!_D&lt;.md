---
title: "Insert the disc? IT'S IN THERE!!! D:&lt;"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by TheBlueBeastie on 2008-11-17
So, I decided to try Ubuntu.
Everything's great, except, it does NOT want me on the internet.
For you see, I've been trying to install a wireless card with a windows driver.

So, I go to the help section in Ubuntu and I follow the steps for installing ndisgtk from the Ubuntu disc.

Then, I go to the Synaptic whatchamacallit and mark it and the two other things (ndiswrapper-common and ndiswrapper-utils) and click "Apply".

And then it tells me to insert the disc.  Which is already in the cdrom drive.

I clicked okay a couple of times, but it did no good, so I clicked "Cancel" and it tells me that it couldn't fetch the files from the place it was at on the cdrom.

I know that it knows it's in there.  After all, the cdrom icon shows up on the desktop when I put it in, and I can browse through it and everything.

Is there something I'm doing wrong? D:
I would very much like to have this working please. >:

---

### Post by Mark Phelps on 2008-11-17
NDISWrapper only allows you to USE windows drivers in Linux; it doesn't provide the actual drivers.  What it's asking for is the disk with the Windows drivers -- which are NOT included in Synaptic.  You have to obtain those yourself.

---

### Post by TheBlueBeastie on 2008-11-17
Really? o.o
It's just that, it keeps telling me that it couldn't fetch the ndiswrapper.deb thing.

It kept saying that it wanted the "Ubuntu 8.10 i386 .. so on and so forth" disc, and that it couldn't fetch the .deb file from the /cdrom/ drive.

But I guess I'll try popping in the disc with the driver on it now, just to see what happens...

EDIT: Didn't work.  It might be that the driver isn't actually on the wireless cards installation disc...

BUT, I did write down the messages.
This is the disc it tells me to insert: Ubuntu 8.10 _Intrepid Ibex_- Release i386 (20081029.5)

When I click "Cancel" I get:
W: Failed to fetch cdrom: [Ubuntu 8.10 _Intrepid Ibex_- Release i386 (20081029.5)]/pool/main/n/ndiswrapper-common_ 1.52-lubuntu_all.deb

Does that help? D:

---

### Post by djm-uk on 2008-11-17
It SHOULD download the packages from the internet... On Hardy (prev release) I go into system / software sources and there is a list of ticks to download from the internet, & the CD source at the bottom is NOT ticked - is yours set to only use the CD for some reason?

David

---

### Post by TheBlueBeastie on 2008-11-17
> **djm-uk said:**
> It SHOULD download the packages from the internet... On Hardy (prev release) I go into system / software sources and there is a list of ticks to download from the internet, & the CD source at the bottom is NOT ticked - is yours set to only use the CD for some reason?

David

Doesn't matter, I don't have internet on Ubuntu.
I'm posting here on Windows XP.

Besides, I'm apparently using Intrepid. Or something. 8.10
Also, I have the CD source ticked.

---

### Post by djm-uk on 2008-11-17
"no internet"... Ah of course that's where we started! that's why it's trying to get them from the CD...

Most of the packages will need an active internet connection to download as there are far too many to put on a CD....  I am sure there are ways to get the install package onto a USB flash drive (try the wiki) but the easiest way would be to use a cabled connection or a cheap/old wifi card that is recognised directly (EG the old Lucent / orinoco cards are picked up directly)... TBH it's far less hassle to just find a card with native support (try searching on Ebay for wireless card and linux or ubuntu)..

David

---

### Post by TheBlueBeastie on 2008-11-17
> **djm-uk said:**
> "no internet"... Ah of course that's where we started! that's why it's trying to get them from the CD...

Most of the packages will need an active internet connection to download as there are far too many to put on a CD....  I am sure there are ways to get the install package onto a USB flash drive (try the wiki) but the easiest way would be to use a cabled connection or a cheap/old wifi card that is recognised directly (EG the old Lucent / orinoco cards are picked up directly)... TBH it's far less hassle to just find a card with native support (try searching on Ebay for wireless card and linux or ubuntu)..

David

D:

I'm just trying to install ndisgtk.
I thought everything I needed for that was already on the disc. ):

---

### Post by djm-uk on 2008-11-17
"I thought everything I needed for that was already on the disc. ):"

Unfortunately not! 

The bulk of the packages in the package manager require downloading from the central repositories & so require internet access...

David

---

### Post by Mark Phelps on 2008-11-18
Sorry, didn't realize that you didn't have an internet connection ... so, I assumed that you had already downloaded the packages and you were being prompted to insert a disk with the Windows drivers.

The Ubuntu CD only contains a small subset of the packages -- the ones most frequently used during installation and setup. My guess would be, and your messages bear this out, that the NDISWrapper stuff is not part of that subset.

And, yes, if you have the Windows driver "disk", that will contain the ".inf" and other files needed to load the driver.

---

