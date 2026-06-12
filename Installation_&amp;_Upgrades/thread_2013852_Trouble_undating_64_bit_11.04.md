---
title: "Trouble undating 64 bit 11.04"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2012-07-01
For the last couple days I keep having a strange problem trying to update 64 bit 11.04. 

Right now it says there are 16 updates available. Try to update, 11.04 starts downloading them then stops, then says to insert an install CD/DVD of 64 bit Precise Pangolin to continue and get the needed updates off that Precise Pangolin CD. I put in the Precise Pangolin install CD and nothing happens! I only keep getting a message there is no Internet connection!  I do have an Internet connection. Tried repeating the update a few times only to have the above keep repeating. First time this has ever happened. 

What is needed to get these updates?

---

### Post by cybrsaylr on 2012-07-02
Bump!

Same thing happened today.
Attempted to download what is now, ~60megs of updates and at the end of the download Ubuntu tells me to install the Precise Pangolin install CD to complete the updates and nothing happens!

What is needed to update now?

---

### Post by cybrsaylr on 2012-07-03
Bump.
Well now I have 37 updates for 11.04 that won't update. Keep getting that message to insert the Precise Pangolin install CD to complete the updates and nothing happens on my desktop!

FWIW I booted up my laptop in my sig below that is also running 11.04. Haven't run laptop in ~40 days and update manager said I had 195 megs of updates waiting. Let Ubuntu 11.04 do its thing. It flawlessly downloaded all 195 megs, then installed them with no mention to 'insert the Precise Pangolin install CD to complete the updates'!

Why does this happen?
Laptop updates with no problem but my desktop won't update anymore....

---

### Post by cybrsaylr on 2012-07-05
Bump!

Come on guys, anyone got an idea on how I can get 11.04 to update on my desktop like it did on the laptop?

---

### Post by plucky on 2012-07-06
> **cybrsaylr said:**
> Bump!

Come on guys, anyone got an idea on how I can get 11.04 to update on my desktop like it did on the laptop?

Open **Software Sources** and disable the CD as a source. (i.e un-tick the box for the CD.)

If you cannot find **Software Sources**,you can use Synaptic Package Manager and search for the Repositories button to open **Software Sources**.

Then open a terminal and run ```
sudo apt-get update && sudo apt-get upgrade
``` and post back the output to the forum if there are any errors.

Good Luck

---

### Post by cybrsaylr on 2012-07-06
> **plucky said:**
> Open **Software Sources** and disable the CD as a source. (i.e un-tick the box for the CD.)


Thanks plucky, that did the trick....):P

Went into Update Manager > settings >  Software Sources > other software, and CD as a source was right at the top of the list. I unchecked it. Then 11.04 went on to install what is now 35 updates normally, like it did on my laptop which is also running 11.04.

---

