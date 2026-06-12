---
title: "MSI Wind - Jaunty, Karmic, or Lucid?"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by kstella on 2010-03-24
My dad and I have an MSI Wind U100 each. Mine's running UNR Karmic, and his is running a SUSE variant that the seller installed. The last time I was home, he looked over my shoulder and saw how cool the UNR interface was. After I answered a few of his questions about media playing, productivity apps, etc., he decided that he wanted to switch to UNR.

The thing is, UNR Karmic is bad on the MSI Wind. There are lots of threads about the flickering, webcam, and USB issues. I'm still putting up with these issues myself. They never released a fix among the official updates, and with Lucid around the corner, it looks like they never will. If I want to preserve my dad's good impression of Ubuntu, Karmic is not the way to go.

I'll be flying home for the Easter weekend, which is one month before Lucid gets officially released, and that's when Dad wants me to make the switch.

So here are the questions.

Should I give him UNR Jaunty, which *just worked* on the MSI Wind but will not be supported after October this year?

Or, should I get him the beta of UNR Lucid? Early posts show that the USB and flickering issues are no longer a problem for MSI Winds on Lucid, but I'm iffy about upgrading early because there might be other bugs to work out.

Or, can anyone tell me how to fix, once and for all, the problems with UNR Karmic, so that when Lucid does officially come out, Dad (and I) can upgrade smoothly? I can't for the life of me understand the bug reports.

Thanks in advance. I really hope someone can help me out. If this works, then my dad will be one more happy convert to Ubuntu. :)

---

### Post by mikewhatever on 2010-03-24
I think your dad should keep Suse till the next time you visit after Easter, and when Lucid will be a viable option. Whatever you do, don't just reinstall, but test first.

---

### Post by kstella on 2010-03-24
Perhaps I should add, one of his main problems with the SUSE installation is that the sellers partitioned the disk so tightly that he can't install any new programs--not even a partitioning program. :/ So there is an element of urgency to his wanting to switch in that he's tired of not being able to do everything he wants with his netbook.

@mikewhatever - I did think of waiting till my next visit, but that will probably be Christmas.

---

### Post by saleminkb on 2010-03-25
I just installed the UNR of lucid on my MSI Wind, the flickering problem still exists and in my opinions its even worse than before.

---

### Post by Eberbachl on 2010-03-25
It's a tough call - the MSI Wind is a great netbook, but not brilliant on UNR without some tweaking unfortunately.

**9.04** - works right out of the box as you said, except that I found the built in mic performance very shaky, it's interface isn't quite as nice as Karmic and the graphics driver doesn't perform well. I upgraded the graphics driver on mine last year which improved UNR 9.04 outta sight - once that was done and I decided to live with the poor performance of the built in mic (or use an external mic) I had a blast with 9.04 UNR.

**9.10** - Sadly, the webcam and brightness flickering were both showstoppers for me. Karmic was lovely, and it was a terrible tragedy that it didn't work nicely on the very popular MSI Wind.

**10.04 Beta 1** - I'm using this on my Samsung n310 netbook (the Desktop edition, not UNR) and I love it. Having said that, as it's a Beta release, there are likely to be bugs and as such it may not be the wisest choice for your Dad right now.

At the moment my Wind is sitting in a cupboard and not getting much love, as I vastly prefer my Samsung n310 which is working beautifully with 10.04 Beta one (and did with Karmic also), except for a few fn keys not working.

In summary - I would not hesitate to recommend that you install 9.04 on your Dad's MSI Wind to get him up and running on Ubuntu. He's likely to have a good experience with that release, and you can upgrade him to Jaunty later on after it's been released and you've had an opportunity to confirm it's compatibility with the Wind.

:D

---

### Post by saleminkb on 2010-03-27
The webcam issue is solved in lucid lynx, and the flicker problem can be solved by updating the bios, (create a freedos live usb stick, with unetbootin; copy the bios files to the usb, they can be downloaded of the MSI site; reboot into freedos, make the AC adapter is plugged in; type "c:", "cd en0311ms.10i/"(or appropriate folder with bios files), "flash.bat";  reboot into ubuntu and the flicker problem should be solved.) Please note the the flash process will not start unless the AC adapter in plugged in.

---

### Post by lucasart on 2010-03-28
Personnaly I highly recomment Karmic Koala. I use Ubuntu 9.10 64 bit, and it works like a charm (almost).

I tried Lucid Lynx and it really is not stable yet, and has a lot of issues. Perhaps these issues won't affect your hardware and only mine, I don't know. But really there is nothing in Lucid more than in Karmic that seems to be worth the switch.

But if you find on your specific hardware Karmic has a lot of issues, then I believe there's only one way to know: try Lucid and see if all the basic things work. And don't forget to test things like stand by/ hibernate/ restart (all these things are completely crashing on Lucid for my hardware).

---

### Post by kstella on 2010-03-28
> The webcam issue is solved in lucid lynx, and the flicker problem can be solved by updating the bios

I have read that a BIOS update would solve the problem. But people also say that a BIOS update is risky. I'm afraid of breaking something. :s

---

### Post by francsal on 2010-03-29
The BIOS update is practically bulletproof, you just have to type "flash" at the command prompt. Just make sure you download the right one for your Wind.

The flickering is corrected with this. In my case, the webcam worked flawlessly in skype. No need to turn it off. 

Regarding Lucid, everything works out of the box. The external display problem I had with karmic is gone (it used to hang whenever I switched)

In short: Update BIOS, install 10.04 and enjoy!

---

### Post by kstella on 2010-03-29
I'll try updating the BIOS on my own netbook before trying it on my Dad's. But in the meantime, I've decided to play it safe and install Jaunty on his Wind. He's pretty happy with it so far, even if the webcam doesn't work. Oops.

It worked fine on my Wind, but I have the Bison cam, and he has the Genesys Logic cam. Trying to find a fix, but it's a little difficult with the Karmic-related posts coming up in the search results also. Oh, well. :o

So, that's two things for me to do now.

---

