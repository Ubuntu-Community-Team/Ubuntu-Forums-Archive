---
title: "Firefox painfully slow after upgrade (Not DNS issue)"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by ZenBeam on 2010-01-02
I recently upgraded from 9.04 to 9.10, and Firefox is painfully slow to use.  Changing between already loaded tabs takes almost a second.  Scrolling through a loaded tab is also slow and jerky.  Other programs (e.g. Thunderbird, or just browsing the filesystem) also seem slower when Firefox is running.

I'm running Firefox 3.5.6.  My PC is Compaq Presario 2200 laptop (about four years old) with 768 MB RAM.  As another data point, I also have the most recent version of Linux Mint installed on the same PC, running Firefox 3.5.3, with no problems.

I've searched, and some problems have apparently been due to DNS problems, but I have problems when I'm offline (wifi physically removed), looking at webpages saved on my disk, which are already fully loaded, so it's not a DNS problem.  I did try steps 1 - 7 in [this post]("http://ubuntuforums.org/showpost.php?p=8365269&postcount=25"), but no help.

---

### Post by tripolitan on 2010-01-02
Firefox should be running excruciatingly slow on your laptop, regardless. How did you go about the upgrade? 

Exit Firefox, in your home directory (folder) rename .mozilla to .mozilla_orig and start Firefox (you'll have a fresh profile), check the speed. If good, keep it, if the same, look somewhere else, start with addons, some addons could make firefox crawl like turtle...

---

### Post by cpplinux on 2010-01-02
My laptop has the same problem after the upgrade. Not only the Firefox, other applications are slower than before, including the terminals. And the longer things run, the slower they get.

---

### Post by tripolitan on 2010-01-02
I have never had a completely successful "upgrade", there is always problems. That is why I stick to LTS versions of Ubuntu and do a complete install once every 3 years...I keep a seperate /home directory and install the essentials (Firefox/OpenOffice etc from the website, not the repositories). So far,  I found that upgrades, WINE and compiz are a comnplete waste of time.

---

### Post by ZenBeam on 2010-01-02
> **tripolitan said:**
> Firefox should be running excruciatingly slow on your laptop, regardless. How did you go about the upgrade?I assume this is meant as a jab at my computer, but given that Firefox works fine on Mint, and worked fine on 9.04, I'll instead take your comment as a jab at 9.10.  I upgraded from 9.04 to 9.10 using the "Upgrade to 9.10" button in the package updater (not sure what it's correctly called, and I'm back to Mint, so I can't check.  I also can't rename .mozilla right now, I'll try it next time I boot Ubuntu.

---

### Post by tripolitan on 2010-01-03
It was meant for 9.10 :] 
to rename the hidden mozilla folder, exit fire fox, open terminal and type:
mv .mozilla .mozilla_orig
start Firefox
if it was the same (slow), then close firefox and rename back
mv .mozilla_orig .mozilla

---

### Post by ZenBeam on 2010-01-03
Renaming the .mozilla folder and letting Firefox recreate it didn't help.

---

### Post by markowe on 2010-01-03
I just had the same problem and narrowed it down to an add-on (one called SEO Toolbar in my case). I turned off all add-ons, established that FF was now working properly, and then started turning them back on one by one until I found the offending one. To be honest I was surprised that worked, since I have had FF slowdown problems before, on Windows too, but it's worth trying anyway. However, if you created a new profile that probably cleared all your add-ons anyway?

Some people have also mentioned a problem with the Compiz effects clashing with FF - you could try deactivating those and see if that is to blame...

---

### Post by Andrew_Grant on 2010-01-03
After upgrading FF to 3.5 I found that turning off add-ons seemed to work, but had a good look at the OS and found remnants of FF3.0 still in place. apt-get autoremove cleared up the problem.  A further tip, just tried it, and a peer into the software centre may reveal that FF 3.x is still installed; remove it and things should go back to normal.  Not promising though, same problem on Windows Vista and 7 and on a Mac.
Oh, this can also work if FF keeps taking you to the wrong site...

---

### Post by tripolitan on 2010-01-04
Installing deborphan helps Synaptic in finding out useless packages, running sudo orphaner will display orphaned libraries (leftover and no longer in use)

---

### Post by ZenBeam on 2010-01-05
Well I installed and ran deborphan, and ran sudo apt-get autoremove.  Both found and removed stuff, but still no joy.

---

### Post by tripolitan on 2010-01-06
A shot in the dark: download and install the Mozilla.org version, unpack it in a separate folder on your desktop and start it from there, see if there is any difference...

---

