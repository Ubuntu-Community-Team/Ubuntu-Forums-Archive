---
title: "Replacing XP Without Killing Ubuntu"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by frank cox on 2010-01-05
Hi:
 
  I managed to blow up windows XP and I want to replace it without blowing up Ubuntu on the same drive,. I understand that grub is in the mbr of the harddrive and should not be affected by removing the damaged Windows installation.
My question is that since the grub still thinks XP is there if I reformat the first partition , the XP partition , and reinstall XP will it work or will it be a disaster?
What is the best way to go about this?
 
Thanks!

---

### Post by SteveDee on 2010-01-05
I had to do the same thing over the weekend on a friends computer. WinXP trashed its self, so after a few unsuccessful attempts to repair using Recovery Console from the WinXP install CD, I just went ahead and reinstalled it.

With XP re-installed on the 1st partition the pc booted directly into XP, so the next step was to reinstall Grub 2. I followed the "Simplest" method using a Ubuntu 9.10 LiveCD as described here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
At step 6 in this procedure be sure to boot back into Unbuntu and do: sudo update-grub before trying to boot into Windows.

Incidentally my friend does not use Ubuntu, but the next time her WinXP trashes itself I'll be able to get straight into her file system via Ubuntu to retrieve her work files.

---

### Post by phillw on 2010-01-05
Hi,

just as a little foot-note. There's an excellent tutorial on recovering both grub and win mbr's over here -->  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)   It's a good one to bookmark for dual booters.

Regards,

Phill.

---

### Post by frank cox on 2010-01-05
Thanks guys!

For what its worth I found Puppy Linux is much faster running off cd than Ubuntu and for file recovery works as well. 
There are so many distros and who can try them all? 
I am almost done with Windows as I can do almost everything I want in Puppy and Ubuntu. I am still not happy with Internet Explorer under wine but I am pretty sure the WINE people will solve that as well. It works on many programs and most of the time there is a Linux replacement as good or better. 
I needed to redo windows anyway so I can use the stripped down version I made with 
nlite. 

Is there are a similar program to remaster Ubuntu and get rid of the locals and other stuff I don't need in Ubuntu? That is where Puppy lives and I really like that one but Ubuntu is better for somethings but not nearly as fast.

---

### Post by SteveDee on 2010-01-06
> **frank cox said:**
> Thanks guys!

For what its worth I found Puppy Linux is much faster running off cd than Ubuntu and for file recovery works as well. 
There are so many distros and who can try them all? 
I am almost done with Windows as I can do almost everything I want in Puppy and Ubuntu. I am still not happy with Internet Explorer under wine but I am pretty sure the WINE people will solve that as well. It works on many programs and most of the time there is a Linux replacement as good or better. 
I needed to redo windows anyway so I can use the stripped down version I made with 
nlite. 

Is there are a similar program to remaster Ubuntu and get rid of the locals and other stuff I don't need in Ubuntu? That is where Puppy lives and I really like that one but Ubuntu is better for somethings but not nearly as fast.

There seem to be lots of sites on remastering Ubuntu including: [http://shibuvarkala.blogspot.com/2009/11/remaster-ubuntu-910-karmic-koala-with.html](http://shibuvarkala.blogspot.com/2009/11/remaster-ubuntu-910-karmic-koala-with.html)  ...and... [http://brainstorms.in/?p=356](http://brainstorms.in/?p=356)
Whether its worthwhile I guess is up to you.

Puppy is great as a recovery tool and for using ancient hardware (e.g. as web kiosks) but I'm happier with Ubuntu as a regular desktop system.

Why use IE at all (especially via Wine) when Firefox is better & safer?

I only really use Wine for NotePad++

---

### Post by frank cox on 2010-01-07
> **SteveDee said:**
> There seem to be lots of sites on remastering Ubuntu including: [http://shibuvarkala.blogspot.com/2009/11/remaster-ubuntu-910-karmic-koala-with.html](http://shibuvarkala.blogspot.com/2009/11/remaster-ubuntu-910-karmic-koala-with.html)  ...and... [http://brainstorms.in/?p=356](http://brainstorms.in/?p=356)
Whether its worthwhile I guess is up to you.

Puppy is great as a recovery tool and for using ancient hardware (e.g. as web kiosks) but I'm happier with Ubuntu as a regular desktop system.

Why use IE at all (especially via Wine) when Firefox is better & safer?

I only really use Wine for NotePad++

Thanks for the links!

Sadly I have no choice but to use IE sometimes because some sites I must use block Firefox intentionally. 95% of the time I use FireFox in ubuntu and Windows and fireDog [a Firefox derivative] in Puppy.

Ubuntu is a good system if you have enough ram and broadband so I use it on my newest machine.  . For old machines and dialup I like puppy better.

---

