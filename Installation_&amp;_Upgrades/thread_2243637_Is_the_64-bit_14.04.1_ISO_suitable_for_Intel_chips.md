---
title: "Is the 64-bit 14.04.1 ISO suitable for Intel chipsets?"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by klundermann on 2014-09-10
The [Ubuntu desktop download page]("http://www.ubuntu.com/download/desktop") offers three flavors and three corresponding ISO files:


  64-bit                           [FONT=system]ubuntu-14.04.1-desktop-amd64.iso[/FONT] 
  32-bit                           [FONT=system]ubuntu-14.04.1-desktop-i386.iso[/FONT]
  64-bit Mac (AMD64)    [FONT=system]  ubuntu-14.04.1-desktop-amd64+mac.iso[/FONT]

If I'm running a 64-bit machine with Intel chips, do I actually want the ISO with "amd64" in the name, or would I be better off with the 32-bit version?

P.S.  I could have sworn that a couple of days ago, the 64-bit option provided the same file as the 32-bit option, namely [FONT=system]ubuntu-14.04.1-desktop-i386.iso[/FONT].

---

### Post by coffeecat on 2014-09-10
i386 = 32 bit version for both AMD and Intel processors. i386 has never been 64-bit.

amd64 = 64 bit version for both AMD and Intel 64-bit processors. The amd64 designation is simply a historical quirk reflecting the fact that AMD were first with 64-bit processors.

---

### Post by klundermann on 2014-09-10
Thanks very much, coffeecat -- it makes perfect sense now.

---

### Post by RobertoRecordo on 2014-11-16
I believe coffeecat's answer is correct, but wish to add a comment.
I came looking for an answer, even though I am quite familial with the historical usage of AMD64 designator for all 64 bit processors. In the past it was very clear in the release page which to use, but now the description is less clear:
from [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)
> 
Desktop image

PC (Intel x86) desktop image
    For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure.
64-bit PC (AMD64) desktop image
    Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead.



When I read the above, and did not see my i5 processor in the AMD64 section, I began to think that the historical usage had changed, and that AMD64 had become AMD only. Indeed, when I found this reference to EM64T  [http://www.intel.com/support/processors/xeon/sb/cs-012580.htm?wapkw=em64t](http://www.intel.com/support/processors/xeon/sb/cs-012580.htm?wapkw=em64t) it appeared that it is not inclusive of newer processors.
Finally, Wikipedia  [http://en.wikipedia.org/wiki/X86-64#Intel_64](http://en.wikipedia.org/wiki/X86-64#Intel_64) to the rescue, the best single suggestion of how to identify Intel 64 bit processors:
> Intel 64 (not to be confused with IA-64 (also called Intel Itanium architecture)) is Intel's implementation of x86-64. It is used in newer versions of Pentium 4, Celeron, Celeron D, Xeon and Pentium Dual-Core processors, the Atom 230, 330, D410, D425, D510, D525, N450, N455, N470, N475, N550, N570, N2600 and N2800 and in all versions of the Pentium Extreme Edition, Core 2, Core i7, Core i5, and Core i3 processors.
I believe that the application information in the Ubuntu Release should say "AMD64 and Intel x86-64 processors" and avoid using the EM64T label, given that Intel does not seem to refer to the newer processors as EM64T. It would be best to link to an up to date list of 64 bit processors for which the release is intended than to name the vendors products here.
Big Disclaimer: I do not know that all of the processors listed above are supported by Ubuntu, particularly unfamiliar with ATOM .

Your comments, especially if I am the only person on the planet that does not know what EM64T means, and if you agree, where to post this that will influence a change, are welcome.

---

### Post by oldfred on 2014-11-16
If you watch entire video, it seems like they may still offer 32bit with 16.04, but you will have to search for it, and it may be what they call "smoke tested" or that it does not burn up your system. But not fully tested like the 64 bit version.

 Developer's discussion of deemphasis of 32 bit Ubuntu - Nov 2014 
[http://www.phoronix.com/scan.php?page=news_item&px=MTgzODE](http://www.phoronix.com/scan.php?page=news_item&px=MTgzODE)
[http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/](http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/)

---

### Post by grahammechanical on 2014-11-16
The i386 ISO image will run on almost all machines whether the CPU is 32 bit or 64 Bit and that is why we are advised to choose that one if we are not sure. We at least get a working Ubuntu.

The varying terminology of CPU manufacturers is not the responsibility of the Ubuntu developers. That page will need to be constantly updated. And then someone will complain that the list is not complete because their particular device is not listed.

Did you follow the session on the Ubuntu Online Summit where is was debated whether to drop 32 bit ISO images completely? That would certainly avoid confusion. It i s at the online summit that we can create a session to discuss making the changes suggested. Posting suggestions on the forum will not bring about change.

I have heard the the amd64+mac ISO is no longer being created. I once installed an amd64+mac on my self-build Intel CPU machine and it worked just fine. There is no real need for a Mac version of the ISO image as Apple now use Intel CPUs.

[http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/](http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/)

Regards.

---

