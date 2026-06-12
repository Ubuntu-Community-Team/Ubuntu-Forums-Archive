---
title: "upgrade Feisty-Gutsy-Hardy"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2008-06-22
On my main PC I have Feisty installed and want to upgrade to Hardy without formatting, passing via Gutsy if necessary. I have tried using internet upgrade and CD upgrade but both fail. 
It seems as though the sources for upgrading Feisty-gutsy have expired and so the upgrade fails retrieving packages. 

So, I thought I'd upgrade from the CD using the cdromupgrade script on the CD. That opens a small GUI window, runs the first part of the process and then closes itself down.

Is there any other way of upgrading from the Gutsy CD or any way of upgrading via internet with valid sources?

I guess I'm in for a reformat, but just wondering if there's a way of avoiding it.

---

### Post by Pumalite on 2008-06-22
Have you tried this?:
sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 
sudo apt-get update 
sudo apt-get dist-upgrade

(Have your Feisty fully updated. Remove all third parties from your sources.list)

---

### Post by pickarooney on 2008-06-22
I did that and started the upgrade. There was a power cut...
Impossible to boot up into Ubuntu, so I went ahead and did a fresh Hardy Install.
It failed due to a problem with the CD.
So I went ahead and did a Gutsy install.
The CD was OK, the installation seemed to finish OK, but I was not asked to set up a user and as a result I couldn't log into the system, either with my own name or as root.
So I tried to rescue the install, got half-way through and it failed, telling me it couldn't use /dev/sda3 as the system partition, even thought it was the correct / partition. I tried this a number of times, and other combinations from the rescue menu, still with the same negative result.

So, I reformatted / and reinstalled Gutsy. This time it did ask for a user, I set it up and got as far as the base installation. This failed 5 times with a debootrsrap warning (couldn't confgure debootstratp). 

So I got my trusty Feisty install CD and gave that a go. I got as far as the base installation and it failed again on the debootstrap configuration.

So I got out my old Knoppix CD. That failed as it either didn't recognise the PC architecture or the CD was damaged. 

So I fished out an Edgy Live CD and here I am, with no system and no clue how to fix it or how an installation CD could possibly fail to install and configure itself...

---

### Post by Pumalite on 2008-06-22
Maybe you need to download a new iso and burn a new cd after doing md5sum. Clean the lens in your burner, just in case. What are your specs BTW?

---

### Post by pickarooney on 2008-06-22
The CDs pass the test OK and have been used to install in my laptop. It would also be too big of a coincidence for both Feisty and Gusty CDs to have exactly the same problem. And I can't burn a CD from within the live CD environment as I only have one reader/burner unfortunately.

I'm just hoping the power cut didn't irreperably damage something on my PC...

---

### Post by Pumalite on 2008-06-22
Let's hope so.

---

### Post by pickarooney on 2008-06-23
I eventually got it sorted. First I reformatted the /boot partition (should have done that first time around but wasn't thinking straight). Installation hung. Second time around I overwrote the contents of /swap as well for good measure and Gutsy installed all the way. Feeling a surge of bravado I went straight ahead and updated to Hardy and it went like a dream. First time ever upgrading without a hitch, in fact (though I'd had enough hitches for one day!). 

Cheers,
P

---

