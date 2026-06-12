---
title: "Vista/Ubuntu dual boot issues"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by TBK50 on 2007-09-06
Ok, so I have 3 hd's, a 74 gig one that vista sits on, and a 400gb one and a 500gb one.  I want to install ubuntu as a secondary OS so I partitioned off some space from my 500gb hd for ubuntu and swap space.  I installed ubuntu fine but when I restarted vista botted up normally not even giving me the option to boot into ubuntu.  

Is there a way I can add my ubuntu install to the vista boot manager so that it will pick up the installation, because honestly right now I don't even know how to boot into my new ubuntu install.

---

### Post by merlinus on 2007-09-06
You might try changing the boot order of your hdds so the ubuntu one is first.

-merlin

---

### Post by TBK50 on 2007-09-06
That could work but that'd only be a temp fix, cause it would be annoying to have to do that everytime I wanted to switch OS's, I assume you change the boot order of the hdd's in bios, I must have glossed over it when I was checking before.

The best thing would be to somehow get the bootmanager to see ubuntu or grub to see vista since I assume that is auto-installed with ubuntu.

---

### Post by merlinus on 2007-09-06
It may well be that grub created an option to run vista.  Change the hdd boot order and see.

-merlin

---

### Post by rmbendeavors on 2007-09-06
I believe what you need is EasyBCD. It's a free application that allows you to configure the Vista bootloader, among other things.

---

### Post by Steve1961 on 2007-09-06
> **TBK50 said:**
> Ok, so I have 3 hd's, a 74 gig one that vista sits on, and a 400gb one and a 500gb one.  I want to install ubuntu as a secondary OS so I partitioned off some space from my 500gb hd for ubuntu and swap space.  I installed ubuntu fine but when I restarted vista botted up normally not even giving me the option to boot into ubuntu.  

Is there a way I can add my ubuntu install to the vista boot manager so that it will pick up the installation, because honestly right now I don't even know how to boot into my new ubuntu install.

Just install EasyBCD in Vista, you can then add Ubuntu to the Vista boot manager in a couple of clicks:

---

### Post by rsambuca on 2007-09-06
Grub probably just installed to the wrong drive.  You can fix it from the live CD.

---

### Post by Pumalite on 2007-09-06
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ssican on 2007-09-06
Information about EasyBCD 1.7   [http://neowin.net/index.php?act=view&id=42412](http://neowin.net/index.php?act=view&id=42412)

For download of EasyBCD 1.7 (858KB) click on the link of download.

EDIT:Links for BCD(BOOT CONFIGURATION DATA)
1)[http://en.wikipedia.org/wiki/Windows_Boot_Manager](http://en.wikipedia.org/wiki/Windows_Boot_Manager)
2)[http://knowledgebyte.spaces.live.com/blog/cns!6F1742E22E12F5F0!860.entry](http://knowledgebyte.spaces.live.com/blog/cns!6F1742E22E12F5F0!860.entry)
SCREENSHOTS  of EasyBCD
1)[http://knowledgebyte.spaces.live.com/blog/cns!6F1742E22E12F5F0!860.entry](http://knowledgebyte.spaces.live.com/blog/cns!6F1742E22E12F5F0!860.entry)
2)[http://www.softpedia.com/progScreenshots/EasyBCD-Screenshot-45820.html](http://www.softpedia.com/progScreenshots/EasyBCD-Screenshot-45820.html)

---

