---
title: "Why is 32 bit the recommended install?"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by Rich.d.berry on 2011-01-05
I am brand new to Linux. My brother is trying to convert me. He gave me an Ubuntu 9.10 disk which he got packed with a magazine. It installed relatively easily but I had some issues. I decided to try a fresh installation to the latest version.

I have an AMD Athlon II X2 64 bit processor in my new desktop PC. My first Ubuntu download installation was the 32 bit 10.10 version. I selected this because it was "recommended" on the download page. Unfortunately there is no information given as to why it is recommended. Can someone please explain?

Following recommendations on this forum I am considering installing the 10.04.1 LTS version, but would go 64 bit instead. Would I stand to gain anything over the 32 bit version by doing so?

 I have Windows XP Professional waiting in the wings should it be  required. Early indications are good that I will keep Ubuntu. 

Thanks in advance.

---

### Post by fballem on 2011-01-05
> **Rich.d.berry said:**
> ... 
I have an AMD Athlon II X2 64 bit processor in my new desktop PC. My first Ubuntu download installation was the 32 bit 10.10 version. I selected this because it was "recommended" on the download page. Unfortunately there is no information given as to why it is recommended. Can someone please explain?
...

This is my personal opinion, based on my own experience (2+ years running ubuntu). The main reason for the 32-bit recommendation is that most current software - especially third-party products, such as sun java, flash, and lightscribe - are built to be installed on a 32-bit system (the lowest common denominator). There may be other reasons as well.

What you lose by going 32-bit is access to RAM above 3 gigabytes.

There are relatively easy ways to install the software correctly on a 64-bit system. Software that is in the main repository, such as OpenOffice, installs without issue on a 64-bit system. Depending on what else you are installing, there may be some different ways of installing items. Common third-party software includes Flash, Skype, and, in my case, Lightscribe.

Flash has a plugin called Flash-Aid (found here: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)) that will install the correct version of Flash.

If you enable the 'partner' repositories, then you can install the version of Skype that is found there. Otherwise, you may install Skype from the Skype website. I believe in easy, whenever possible, so I install it from the partner repositories.

If you have a lightscribe-enabled drive, then there are instructions for setting this up on a 64-bit system here: [http://ubuntuforums.org/showthread.php?p=10319102#post10319102](http://ubuntuforums.org/showthread.php?p=10319102#post10319102)

I am currently running 10.04 on a Desktop system and 10.10 on a Laptop. Both are running 64-bit and both have been running without any problems. I would suggest that you might want to run a 64-bit installation and only go to a 32-bit if you run into any issues.

Hope this helps,

---

### Post by cascade9 on 2011-01-05
> **fballem said:**
> This is my personal opinion, based on my own experience (2+ years running ubuntu). The main reason for the 32-bit recommendation is that most current software - especially third-party products, such as sun java, flash, and lightscribe - are built to be installed on a 32-bit system (the lowest common denominator). There may be other reasons as well.

What you lose by going 32-bit is access to RAM above 3 gigabytes.

Actually, you can see 3GB+ with 32bit, you need a PAE kernel. 

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

In general I agree with pretty much everythig else you posted (though there is 64bit native java and flash..no idea on lightscribe, but IIRC lightscibe on linux is a bit of a hack)

---

### Post by Rich.d.berry on 2011-01-05
Indeed it does help, thanks.

However, it leads me to another question. Since I only have 2 GB of RAM will I not be better off with the 32 bit version?

I too am a firm believer in simple, hence the wish to go for the LTS version, which I assume has fewer updates and is reportedly more stable. 

If I gain no advantage by going 64 bit, and potentially give myself compatibility issues to contend with, then the recommendation seems entirely justified. Thanks again.

---

### Post by nomko on 2011-01-05
> **Rich.d.berry said:**
> Indeed it does help, thanks.
 
However, it leads me to another question. Since I only have 2 GB of RAM will I not be better off with the 32 bit version?
 
I too am a firm believer in simple, hence the wish to go for the LTS version, which I assume has fewer updates and is reportedly more stable. 
 
If I gain no advantage by going 64 bit, and potentially give myself compatibility issues to contend with, then the recommendation seems entirely justified. Thanks again.
 
Just use the 32-bit version of Ubuntu. The main reason is mentioned i the first respond of fballem. And it's also my experience (3+ years ubuntu) that 32-bit is mostly better then 64-bit. And with the PAE kernel there's no problem of using 32-bit ubuntu on a 64-bit system.

---

### Post by Rich.d.berry on 2011-01-05
> **cascade9 said:**
> Actually, you can see 3GB+ with 32bit, you need a PAE kernel. 

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Brilliant link, Thanks! Haven't read it all yet but learned a few things from the get go.

---

### Post by fballem on 2011-01-05
> **cascade9 said:**
> Actually, you can see 3GB+ with 32bit, you need a PAE kernel. 

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

In general I agree with pretty much everythig else you posted (though there is 64bit native java and flash..no idea on lightscribe, but IIRC lightscibe on linux is a bit of a hack)

Thanks - I do have a couple of questions, if I may.

The Sun Java does exist (and can be easily installed) from the Partner repository. It has worked well. I don't know if that is the 64-bit version or not. If you know how to tell, then I would very much appreciate instructions to check whether I am using the 64-bit or 32-bit version of the Sun Java. There is also the open java, which is generally very usable, although there are some subtle differences that may cause problems with Eclipse. (I think that's right, but additional clarification would be really helpful).

Not sure about the Flash as native 64-bit. At one point, the version that was in the repositories was 32-bit with an NDIS (? I think that's right) wrapper that caused no end of problems. Someone had posted a link to Flash Aid and that installs a native 64-bit version of Flash.

I have heard of a PAE kernel, but I have never needed it, since I have been running 64-bit for a couple of years and have never had an issue with it.

By the way, for the Original Poster, I think you said you had Windows XP in the wings. That is a 32-bit operating sytem (although I think there is a PAE version that will recognise RAM above 3 gigabytes). I had Windows 7 64-bit running on my laptop, but the applications including Office Professional and Internet Explorer are 32-bit. I am now running ubuntu 10.10 64-bit on that laptop and I have been very happy with it.

---

### Post by howefield on 2011-01-05
> **Rich.d.berry said:**
> I have an AMD Athlon II X2 64 bit processor in my new desktop PC. My first Ubuntu download installation was the 32 bit 10.10 version. I selected this because it was "recommended" on the download page. Unfortunately there is no information given as to why it is recommended. Can someone please explain?

The reason for 32 bit being recommended on the the download page is simply to "protect" novice users. People who want 64 bit will likely be aware of the issues and go get it. Others can use 32 "safely" and probably have fewer issues.

The "recommended" message has been toned down from the last release when it actively discouraged against 64 bit. If you want to read the bug report, here it is...

[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940/+index?comments=all](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940/+index?comments=all)  

Basically it comes down to personal choice, in your case I'd probably go for 32 bit, whilst there are still benefits to be had from 64 bit even with 2 gig of RAM, they will most likely be negligible for you. I say that as a 64 bit user of some years.

---

### Post by fballem on 2011-01-05
> **Rich.d.berry said:**
> Indeed it does help, thanks.

However, it leads me to another question. Since I only have 2 GB of RAM will I not be better off with the 32 bit version?

I too am a firm believer in simple, hence the wish to go for the LTS version, which I assume has fewer updates and is reportedly more stable. 

If I gain no advantage by going 64 bit, and potentially give myself compatibility issues to contend with, then the recommendation seems entirely justified. Thanks again.

LTS (Long-Term Support) has more to do with how long the version will be supported. A normal release (like 10.10) will continue to be supported (and have updates) for 18 months on a desktop. An LTS release (like 10.04) will continue to be supported (and have updates) for 3 years on a desktop.

Ubuntu is fairly conservative in terms of what versions of software are included. For example, OpenOffice 3.2.0 is in ubuntu 10.04, but OpenOffice 3.2.1 is in ubuntu 10.10.

When a new ubuntu release comes out, I back up my data (Documents, Pictures, Music, Videos, and Templates) to an external drive, then do a clean installation to my computer. I have heard of too many problems with just doing an upgrade. I also enable backports in the repository (see the Unsupported Updates on the attached screenshot).

Whether you choose to go with 32-bit or 64-bit, and whether you choose to go with 10.04 or 10.10, you will need to remember that Linux may look like Windows, but it is not Windows. Some things will be done a little differently (it took me about 2 months to become comfortable). Having said that, I have to use Windows at work, and I do find it primitive compared to Ubuntu. Be patient with yourself and ask lots of questions here. People will help.

---

### Post by cascade9 on 2011-01-05
> **nomko said:**
> Just use the 32-bit version of Ubuntu. The main reason is mentioned i the first respond of fballem. And it's also my experience (3+ years ubuntu) that 32-bit is mostly better then 64-bit. And with the PAE kernel there's no problem of using 32-bit ubuntu on a 64-bit system.

PAE has nothing to do with 64bit. 

All AMD64/inel 64 CPUs  (or x86-64 if you prefer) run 32bit just fine, as it is 64bit extensions to 32bit x86. 

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

> **Rich.d.berry said:**
> Indeed it does help, thanks.
 
 However, it leads me to another question. Since I only have 2 GB of RAM will I not be better off with the 32 bit version?
 
 I too am a firm believer in simple, hence the wish to go for the LTS version, which I assume has fewer updates and is reportedly more stable. 
 
 If I gain no advantage by going 64 bit, and potentially give myself compatibility issues to contend with, then the recommendation seems entirely justified. Thanks again.
 
 I've never found anything that cant be installed with the --force architecture option. Like fballem posted on this thread on lightscribe- 
 
 [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1647147](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1647147)

64bit does have minor speed improvements pretty much everywhere, and for things like video and audio encoding, 64bit is much, much faster than 32bit. 

> **fballem said:**
> Thanks - I do have a couple of questions, if I may.

The Sun Java does exist (and can be easily installed) from the Partner repository. It has worked well. I don't know if that is the 64-bit version or not. If you know how to tell, then I would very much appreciate instructions to check whether I am using the 64-bit or 32-bit version of the Sun Java. There is also the open java, which is generally very usable, although there are some subtle differences that may cause problems with Eclipse. (I think that's right, but additional clarification would be really helpful).

Not sure about the Flash as native 64-bit. At one point, the version that was in the repositories was 32-bit with an NDIS (? I think that's right) wrapper that caused no end of problems. Someone had posted a link to Flash Aid and that installs a native 64-bit version of Flash.

I have heard of a PAE kernel, but I have never needed it, since I have been running 64-bit for a couple of years and have never had an issue with it.

By the way, for the Original Poster, I think you said you had Windows XP in the wings. That is a 32-bit operating sytem (although I think there is a PAE version that will recognise RAM above 3 gigabytes). I had Windows 7 64-bit running on my laptop, but the applications including Office Professional and Internet Explorer are 32-bit. I am now running ubuntu 10.10 64-bit on that laptop and I have been very happy with it.

I actually dont know how to tell if your installed version of java is 64bit, sorry. I could probably find out witha  bit of searching, but hopefully somebody else answers this and saves me the trouble ;) 

Yeah, the flash for 64bit in the repos is (or at least was) 32bit flash in a wrapper. Flash aid is a much better way to do things. You can also install 64bit flash manually, if you want. 

There is XP 64, but no PAE for XP AFAIK.

---

### Post by wojox on 2011-01-05
```
java -version
```

```
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.3) (fedora-49.1.9.3.fc14-x86_64)
OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)
```

---

### Post by TBABill on 2011-01-05
> **nomko said:**
> Just use the 32-bit version of Ubuntu. The main reason is mentioned i the first respond of fballem. And it's also my experience (3+ years ubuntu) that 32-bit is mostly better then 64-bit. And with the PAE kernel there's no problem of using 32-bit ubuntu on a 64-bit system.
 
This was a very uninformed direction to give to the OP. The question was about differences and why 32 bit is recommended. "Just use the 32 bit version" is not an answer in any way and it's more than the OS just seeing more RAM. 
 
Phoronix did a test of the 3 different kernel version (32 bit, 32 bit PAE and 64 bit). If you look at the test results, the PAE did little to help the results even if able to address all the RAM, but 64 bit did outperform both others in every test. Sometimes the margin was negligible, but it still was faster. To me that says a lot about 64 bit's capabilities. [http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
 
Lastly, what is your experience that shows 32 bit to be superior? Old versions of flash that have been fixed now? Incompatibilities that don't exist today? I have seen one post by a user unable to use a 32 bit app on their 64 bit system and I cannot recall the reason, but extensive work was done to get it to go. It was an app from outside the repos and was little known to most who tried to help. Other than that single instance I cannot think of a case where either a 64 bit version is not available or a 32 bit version won't work just as well on the 64 bit OS.
 
My recommendation to the OP is to read all you can and decide what you think may be best for you based on other's experiences. I have a laptop with 1GB RAM and an older Intel dual core processor running 64 bit Ubuntu and it runs fast like my other machines with more RAM and faster processors. But your experience may differ. It never hurts to try, but equally as easy to stick to the 32 bit version you know works well for you. Choice is wonderful!
 
Edit: in some cases of the Phoronix testing the PAE kernel actually performed slightly slower than the standard 32 bit even though the test system had 4GB of RAM, which is more than the standard 32 bit system will address.

---

### Post by wkulecz on 2011-01-05
IMHO PAE is best relegated to the dustbin of computing history with all the other kludgey bad ideas like "memory banks" from the S-100 Bus days, DOS HiMem, near and far pointers of the 16-Windos and other sins of the father from Intels segmented architecture of which PAE is hopefully the final chapter.

If you have more than 4GB RAM use 64-bit OS, it you have less than 4GB RAM use 32-bit OS.  Forget the PAE and other kludges!

The 32-bit layer on 64-bit Ubuntu has not let me down at all.  I'm running some commercial 32-bit (that dates back to 6.06) software on my 64-bit system just fine.

---

### Post by Rich.d.berry on 2011-01-05
Thanks for all the input people. It is much appreciated

I suppose that if I was hoping for a black and white answer then I am out of luck. But, being a realist, I know that life, and software, does not come in black and white (unless it's some much hyped, but failed, Microsoft game that I seem to recall from about a decade ago).

I think I'll give the 64 bit version a go. I have nothing to lose since my data is all backed up and safe on a separate machine. The worst that can happen is that I have to re-install with the 32 bit version.

---

### Post by TBABill on 2011-01-05
Agreed. Experimentation is the best way to really learn and understand how things work and why they work the way they do. Worst case is a reinstall. Best of luck with Ubuntu!

---

### Post by presence1960 on 2011-01-05
> **cascade9 said:**
> Actually, you can see 3GB+ with 32bit, you need a PAE kernel. 

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

In general I agree with pretty much everythig else you posted (though there is 64bit native java and flash..no idea on lightscribe, but IIRC lightscibe on linux is a bit of a hack)

If you install a PAE enabled kernel you will lose some performance, hardly a good trade-off just so you can see more than 3 Gb of RAM. Keep it simple and go with 64 bit. 64 bit is mature now and all those software issues have been resolved. Don't believe it? Then look at the x86-64 bit users category on the forum main page. Note it is grayed out.[ Here]("http://ubuntuforums.org/announcement.php?f=343") is the explanation of why the 64 bit users category has been closed by bodhi.zazen

If you have a 64 bit CPU then go with 64 bit OSs. You paid for the technology so you may as well use it.

---

### Post by presence1960 on 2011-01-05
> **wkulecz said:**
> IMHO PAE is best relegated to the dustbin of computing history with all the other kludgey bad ideas like "memory banks" from the S-100 Bus days, DOS HiMem, near and far pointers of the 16-Windos and other sins of the father from Intels segmented architecture of which PAE is hopefully the final chapter.

If you have more than 4GB RAM use 64-bit OS, it you have less than 4GB RAM use 32-bit OS.  Forget the PAE and other kludges!

The 32-bit layer on 64-bit Ubuntu has not let me down at all.  I'm running some commercial 32-bit (that dates back to 6.06) software on my 64-bit system just fine.

+1

well said!

---

### Post by cascade9 on 2011-01-05
> **presence1960 said:**
> If you install a PAE enabled kernel you will lose some performance, hardly a good trade-off just so you can see more than 3 Gb of RAM. Keep it simple and go with 64 bit. 64 bit is mature now and all those software issues have been resolved. Don't believe it? Then look at the x86-64 bit users category on the forum main page. Note it is grayed out.[ Here]("http://ubuntuforums.org/announcement.php?f=343") is the explanation of why the 64 bit users category has been closed by bodhi.zazen

If you have a 64 bit CPU then go with 64 bit OSs. You paid for the technology so you may as well use it.

I agree, I was taking the 'soft' route on this thread (search for my username and 64bit, I've been saying '64bit CPU, use 64bit' for ages)

---

### Post by presence1960 on 2011-01-05
> **cascade9 said:**
> I agree, I was taking the 'soft' route on this thread (search for my username and 64bit, I've been saying '64bit CPU, use 64bit' for ages)

:) No problem was just letting OP know that there is a downside to PAE, which in my opinion is not worth the performance loss just to see over 3 GB of RAM.

---

### Post by johncc on 2011-01-05
> **wkulecz said:**
> IMHO PAE is best relegated to the dustbin of computing history with all the other kludgey bad ideas like "memory banks" from the S-100 Bus days, DOS HiMem, near and far pointers of the 16-Windos and other sins of the father from Intels segmented architecture of which PAE is hopefully the final chapter.



I don't know anything about the subject topic or PAE, but this paragraph sure took me back to my Cromemco days and then 8086, msdos, and DesQ!!!

Cheers,
John

---

