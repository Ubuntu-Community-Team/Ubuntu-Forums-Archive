---
title: "hmm ok ubuntu wanabe"
date: 2006-04-14
forum: Installation &amp; Upgrades
---

### Post by brumovich on 2006-04-14
Hey kinda new to this linux stuff, 

can some of you guys help me get linux up and running on my home pc.

I have a few questions which need answering.

   # Is ubuntu the best linux to install ?.
   #If i put it onto a partion of my hard-drive will i be able to delete if i re sell my pc.
   #Can some one tell me step by step how to install it and what disks i will need,
   # Where can i download the english version to put onto disk
   #how much of the hard drive will this take up, can i limit how big it can get up to ?.
   #If it all goes well what is the linux browser called and will i be able to run my sagem fast 800 adsl modem on it.
   # If this helps my pc specs are . 3ghz P4 ht, 1024mb ram, and intel integrated graphics card (wrecks my set up tbh)

 Thanks in advance......

---

### Post by dermotti on 2006-04-14
What are you planning on using linux for?

---

### Post by Scunizi on 2006-04-14
If you're just wanting to play and see if Ubuntu is a viable replacement for what you're currently using... here's a few answers
1> Is it the best? - It's the only one I've tried, it's currently ranked #1 in downloads, I found it easy to install after understanding the partitioning portion of the install (some info here [https://wiki.ubuntu.com/Installation/I386)](https://wiki.ubuntu.com/Installation/I386)). 

2> You can always delete it.

3> Installing is very straight forward.  Partitioning without losing your windows is a little different. Here's how to keep your windows partition and create new partitions for Breezy/Dapper. [https://wiki.ubuntu.com/HowtoPartition?highlight=%28partition%29](https://wiki.ubuntu.com/HowtoPartition?highlight=%28partition%29)

What they don't mention here is before you have the installer automatically create the remaining needed partitions for the install you should manually create a small vFat partition (3gig or so) as a storage area for files/downloads/data that you want to exchange between a NTFS partition (windows typically) and Ubuntu.  Ubuntu cannot reliably write to a NTFS partition and windows doesn't see Ubuntu's file system at all. After that just tell it to automatically create the remaining partitions.

4> The ISO file for Dapper (the next release) is available here.  [http://cdimage.ubuntu.com/releases/dapper/flight-6/](http://cdimage.ubuntu.com/releases/dapper/flight-6/)
This is an Alph release that (for me) has been very stable.  You must burn it SLOWLY using the ISO option in your software.  I found buning it faster than 12x created errors for some reason.
If you just want to see if Ubuntu will even work on your system try the Breezy LIVE cd.  I will load the system while booting from the CD and not touch your harddrive.  It'll be a little slow but you'll get the idea.  You can find that here.. [http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/5.10/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/5.10/)

5> My first link mentioned will answer this.  It might be a little off because of the version.

6> Firefox - it works on windows & linux - integrated don't try to delete it.

7> Modem - ? maybe someone else will help with that one.  Try the Live Cd first and see if it works.  You may have to search these boards for your modem to get answers for it.

Impressions?  I like Ubuntu.  Use(d) windows & dos for a long time and find this a very intreging environment with a lot of potential, flexibility and best of all, real help from the users.  Just have some patients.  It's a different environment.

---

### Post by brumovich on 2006-04-16
yeap thanks.... got the iso yea 

but i dont understand the bit where it says.

Verify the ISO. [WWW] Instructions available at OpenOffice.org

can someone help me about this bit....

---

