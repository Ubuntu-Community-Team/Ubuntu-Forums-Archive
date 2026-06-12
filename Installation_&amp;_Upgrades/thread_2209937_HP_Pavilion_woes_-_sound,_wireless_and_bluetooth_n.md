---
title: "HP Pavilion woes - sound, wireless and bluetooth not working"
date: 2014-03-08
forum: Installation &amp; Upgrades
---

### Post by ojdfpiv on 2014-03-08
I bought a new [HP Pavilion 15-e026ax]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c03965151") . Since it comes with Free DOS, my plan was to install Ubuntu on it as soon as it arrived. After installing Ubuntu Release 12.04 (precise) 64-bit on it, I am left without the ability to play any sound, use bluetooth or wireless on the laptop. The bluetooth settings panel is greyed out, no sound is heard when I play some audio (volume settings are ok) and I am not able to detect any wireless networks. The wireless radio switch (Fn F12) stays permanently orange, and I don't know whether it is on or off.

Since there seem to be some [Ubuntu versions]("http://www.ubuntu.com/certification/make/HP/") that are specifically certified for HP computers, can someone help me find the right one for me. There are several versions for AMD processor laptops, but mine isn't listed there.

dsv

---

### Post by varunendra on 2014-03-08
All three are unrelated and independent problems, best to be asked individually in separate threads in suitable forum areas. Mixing problems only makes it difficult to get or offer any help.

For example, I may be able to help with the Wireless, the suitable place for it is the "Wireless & Networking" section of the forums.

The Bluetooth question may be asked in either "Hardware" or "General Help" section.

The Sound issue should be discussed in "Multimedia & Video" section of the forum.

Of course a suitable title is also a very important aspect of a thread. Make it such that it clearly indicates the nature of the problem, so that it can attract the right people who can help with it.

You may edit your first post to change the question to ask any one of the problems, then request the mods (using the "Report Post" button) to change the title accordingly and move it to a suitable place.

---

### Post by Mark Phelps on 2014-03-08
> The wireless radio switch (Fn F12) stays permanently orange, and I don't know whether it is on or off.


Unfortunately, every thread I've see about this (including my own experience with a Presario laptop) indicates that there is NO support in Linux for the WiFi switch on these laptops.  You have to be in MS Windows to activate that switch as it requires special drivers -- which are not available for Linux.

---

### Post by varunendra on 2014-03-08
It may also happen if the required driver or firmware is not available in the system. In that case, just installing the required stuff makes it work. These can be common linux drivers/firmware, proprietary, or open-source possibly not included in the running kernel.

Another common case, although may be with other brands, is when the card's firmware has either stuck, or has been sent to a 'Forced Sleep' state by windows driver during shut down. In the former case, resetting BIOS can fix it. In the latter case, windows may be required to enable it again (IF resetting BIOS does not help).

The case when windows is required to bring the firmware out of its 'Sleep' state is only applicable to some particular vendors/models and I'm not sure if even that is a permanent state. I believe either a capable and fully functional driver/firmware or a complete power drain can reset the cards, but haven't yet found a chance to test that.

In any case, requiring windows to enable a card is a firmware bug, not a deliberate feature, and that is rare as far as I have seen.

---

### Post by ojdfpiv on 2014-03-09
I installed the version of Ubuntu certified for a HP Pavilion Sleek 15 (closest approximation to my laptop at least in the name). Then I went to the BIOS and did a reset to defaults. This got the audio working. One down, two to go. 

Both my wireless and bluetooth are apparently made by a company called Ralink Corporation as mentioned in the output of the command lspci -nn. My best guess is that the Ralink drivers are not installed in this distribution of Ubuntu. They are not there on Synaptic either.

Does anyone know about these Ralink drivers and where I can get them? I prefer getting them via Synaptic, but can live with a manual installation in this case.

---

### Post by varunendra on 2014-03-10
Instead of guessing, why don't you start a thread dedicated to wireless, and post technical details in it.

Or you can ask the mods (using the "Report Post" button) to change the title of this one, and post the same here?

I am emphasizing it because a thread with clear indication of what it is about is much more useful later, if it gets solved. With a confusing title, it won't be as much useful.

For posting technical details about the wireless setup, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by ojdfpiv on 2014-03-13
Finally some relief. I used to think that LTS versions of Ubuntu are more desirable than the new ones. Today I upgraded to the latest version of Xubuntu, 13.10. My problems disappeared. 

Prior to that on Ubuntu 12.04 LTS, I had tried downloading the wireless driver from the Ralink website. Upon installation, Wireless did work and I could ping yahoo.com successfully from a terminal. However, Firefox would just freeze as soon as it was started. A few reboots later, the entire system would be frozen immediately upon login, thanks to the wireless driver. 

I am appreciative of Ubuntu having incorporated the missing drivers in its latest release.

---

### Post by varunendra on 2014-03-13
That's a great news. :)

Updates automatically fixing everything is the best thing we can expect. Please mark the thread as [SOLVED] using "Thread Tools" link above the first post.

---

