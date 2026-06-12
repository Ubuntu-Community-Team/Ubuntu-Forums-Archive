---
title: "Dapper on old laptop stalls on update"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by Gina on 2008-01-08
I have scoured the threads on here and done a search but so far not found the answer to this problem :-

I have an old laptop that I'm trying to install Ubuntu on.  Processor is Celeron 400MHz and 160MB RAM (though some of this is used for graphics).  Later versions of Ubuntu won't install but I managed to install Dapper using the Alternate CD ISO.  Mostly it's working (using a wired connection to the router) and will download from the web - both web pages using Firefox and applications using Synaptic.  However, when I try to download updates the system freezes at the point of starting the download.  The same thing happens using Synaptic and marking all Upgrades for download.

Using terminal** sudo apt-get update** runs but** sudo apt-get upgrade** stalls when answering **Y** to "After unpacking 18.9MB of additional disk space will be used/  Do you want to continue [Y/n]?"  ie. at the start of downloading the update files just like the GUI Synaptic.

Does anyone have any ides please?  Why should most downloads work but not the updates, I wonder.  There is plenty of free HD space and plenty of swap space set up.

---

### Post by zach12 on 2008-01-08
I wouldn't update until 8.04 come's out in may
and any way all that does is update most of the programs

---

### Post by Shazaam on 2008-01-08
Does this only happen while updating one at a time or when you try to do ALL of the updates at once? Or are you trying to go from Dapper 6.06 to Gutsy 7.10?
How old is the laptop? It could be a bad network card or cables.

---

### Post by Gina on 2008-01-10
I haven't tried downloading just one update but I have unticked quite a number from the list of a couple of hundred and the same thing happens - freezes at the beginning of the first file download.  I am not trying to upgrade the distro - just normal updates for Dapper.

The laptop is about 8 or 9 years old I think.  The manual is dated 1998 and the BIOS is Y2K ready.  I made a slight mistake in my original post - it has separate graphics, not shared.  The whole 160MB is available.  Graphics is 800x600 using 4MB separate RAM.

Network card is newer- a 3Com Megatertz LAN+Modem - 10/100 LAN + 56K Modem CardBus PCCard.  I'm using the LAN part.  I'll have to check it on another laptop - didn't suspect it as most downloads work fine.  Cable has been used with other computers without any problem.

---

### Post by zvacet on 2008-01-10
Did you try another server?

---

### Post by Gina on 2008-01-10
> **zvacet said:**
> Did you try another server?
How do you do that?

---

### Post by zvacet on 2008-01-10
> To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code)

It don´t have to be** your **country code.See [here](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories).

---

