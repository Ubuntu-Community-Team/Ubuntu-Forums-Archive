---
title: "how to make ubuntu run on another computer that it wasnt installed on"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by hazman on 2010-03-04
just installed 9.10...but had to use the hard drive in another computer as it had no disk drive.just wondered how you make it run. is it something to do with xsever-xorg...i have done it b4 but forgot how

---

### Post by Mze on 2010-03-04
Boot into recovery mode and run xfix - try to fix X server.

should detect your graphics adapter and then resume normal boot.

---

### Post by BastardNamban on 2010-03-04
If I were to answer based on your thread tagline alone, take an existing linux system and install remastersys ([http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html)), and make a backup .iso of your install with the first option- backup with user data. then get unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)), and use that to copy your remastersys .iso to a USB thumb drive at least 4 GB big. From there, take any computer, even a computer without a hard drive, and at the motherboard's boot menu (usually F2 at turn on), set the boot order of devices so that USB devices are first, save the changes, and shut down.

Plug in your USB thumb drive, turn the computer on, and select live option from Unetbootin's list- congrats, you have a fully portable custom linux distro of your choice working on ANY computer with a USB port, even if it has no hard drive.

Now, based on what you wrote, I'm confused- you installed 9.10 on the hard drive from another computer, and you took it out to put into your computer temporarily to make it work? Can you be a bit more specific? Maybe I missed something.

---

### Post by ram2500 on 2010-03-05
I have done something similar (running Ubuntu temporarily on another computer) with success, but I have had some failures too. I had a spare PC with Fedora Core 4 (this was a Pentium III machine) and so I had to recover some files for one of my coworkers. My coworker had a Athlon 64, but ran 32-bit Windows XP. For the life of me, I couldn't boot the disk with Fedora on that machine. Needless to say, I just installed his hard drive into my other computer and recovered the files.  I presumed that even though I was using 32-bit Fedora and and he was using 32-bit XP, it was because Fedora was installed on an old Pentium III and was for some reason confused when run on the A64. This was several years ago, and I'm sure the newer kernels would make this a seamless process. 

Ubuntu "live" flash drives are more or less portable in my experience. A great tool for when I have to fix my friends or family's PCs. ;)

---

### Post by hazman on 2010-03-05
Sorry was a bit vague.The problem was the cd drive on the computer i want to install ubuntu on was broken, so removed the hard drive and placed it in a computor with a working cd drive and installed it on that.Now i put hard drive back in original computer,but it wont load,,i have done this with an earlier version of ubuntu with succsess, but forgotten how i did it...

---

### Post by hazman on 2010-03-05
decides to install ubuntu 8.10 same way and that worked fine

---

