---
title: "Install problems, CD integrity test failed"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by Russellkhan on 2005-05-29
Hi there, 

I've recently upgraded one machine here to Kubuntu 5.04 (from RedHat 9) and want to upgrade my main machine to Ubuntu 5.04 (from Gentoo). Since I don't want to end up with a nonfunctional machine, I decided to test things out a bit by running the Ubuntu LiveCD. This failed to complete its boot process, got stuck while trying to load some package (I forget which one now, sorry), then failed the CD integrity check (again, I didn't take note of which file it failed on, sorry - I will probably try it again, and if I do, I'll repost with info about what it failed on.

Since I couldn't run the LiveCD, I decided to just boot from the regular Ubuntu install CD and run the integrity check before allowing it to do anything to my hard disk. I did this, and it failed too. The file that failed to pass the test was 

./pool/main/l/linux-source-2.6.10/linux-image-2.6.10-5-386_2.6.10-34_i386.deb

Wanting to go ahead and make the switch, I decided to abandon my plan to switch to gnome at the same time and popped in my Kubuntu install CD and rebooted. Of course, I ran the integrity check the first chance I could. Interestingly enough, it failed in the very same place. Is there a problem with this particular file on all of the CDs, or is there just something very odd happening with the ones I burned?

I do realize there are other kernel images on the install CD and I could probably get by without that particular file, but the integrity check stops as soon as it runs into the bad file (at around 11% of the way through the check), so I have no way of knowing if the rest of the CD is actually ok.

At this point I'm considering trying the install from Knoppix plan I saw a Howto for on (I think) UbuntuGuide. I'm also downloading a new iso of the Ubuntu install CD.

Any suggestions? Has anyone else run into this? Or even has anyone else run the integrity check in the installer and gotten different results? Scratch that last question, I did run the integrity check on the Kubuntu CD and it passed on my other computer (the one I'm posting from now).

I think I'll try booting from the CDRW drive to see if that makes a difference...

---

### Post by Russellkhan on 2005-05-29
**Update:** Both the Ubuntu install CD and the LiveCD passed integrity check when booted in my CDRW, and the LiveCD just finished booting into gnome. 

I guess my main CDROM drive is going bad. Probably this is also a clue as to why I've been unable to copy some audio CDs that copy just fine in friend's systems.

---

