---
title: "Core 2 Duo and Edgy?"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by TrendyDark on 2006-12-02
I just bought a new computer (built it to be more accurate) and everything seems to be working great on Windows, which I installed to use the BIOS update utility. 

I jump over here to see how my new wireless card is going to run and find out that Edgy refuses to work in multi-core mode with Core 2 Duos and P965 Boards?

I have a Gigabyte GA-965P-DS3 (Intel P965 Chipset), Intel Core 2 Duo E6600, G.skill RAM, etc. 

I used Dapper on my other computer and don't think I can live wihtout Linux here. . . please help me understand if I'm either a)screwed until the kernel is fixed or b) good to go with no problems.

---

### Post by pestilence4hr on 2006-12-02
Why do you say that Edgy refuses to work in multi-core mode?  It runs just fine on my dell laptop.

---

### Post by TrendyDark on 2006-12-02
I read it in a thread, just wanted to see if it was a true statement or a hardware-specific thing.

I know I tried installing Dapper earlier and it wouldn't even bring up the LiveCD.

---

### Post by TrendyDark on 2006-12-02
Seeeee:

[https://wiki.ubuntu.com/Core_2_Duo_Support?highlight=%28duo%29%7C%28core%29%7C%282%29](https://wiki.ubuntu.com/Core_2_Duo_Support?highlight=%28duo%29%7C%28core%29%7C%282%29)

---

### Post by pestilence4hr on 2006-12-02
Ah.  A quick search of the forums indicates you can't install dapper on your hardware, due to lack of drivers in the dapper kernel.  [http://ubuntuforums.org/showthread.php?t=238553](http://ubuntuforums.org/showthread.php?t=238553)

Try an edgy live cd...

---

### Post by TrendyDark on 2006-12-02
27% Done with the Edgy ISO. I forgot what I did with the last one I downloaded, which I couldn't use because my last wireless card required ndiswrapper.

What I'm worried about though is that the IDE Drives I have (two daisy-chained DVD/CD-RW Drives) won't work for installation, which would be bad.

---

### Post by pestilence4hr on 2006-12-02
> **TrendyDark said:**
> Seeeee:

[https://wiki.ubuntu.com/Core_2_Duo_Support?highlight=%28duo%29%7C%28core%29%7C%282%29](https://wiki.ubuntu.com/Core_2_Duo_Support?highlight=%28duo%29%7C%28core%29%7C%282%29)

Ok, but that doesn't list your motherboard as having random lockups -- only difficulty in using the IDE controller (thus problems installing off of cd).  So if the cd doesn't work, you could do a number of other things if you really want to have ubuntu, like PXE boot or their knoppix boot-and-switch procedure.

---

### Post by TrendyDark on 2006-12-02
Well, I'll let you know how the install goes. The ISO is almost done, then I'll be installing over my current windows installation (if I even get that far). 

Worst comes to worst, I'll just move over to Debian or Fedora or some distro like that until Ubuntu FF is in full-release (and from what I can tell they fixed my problem in one of the daily builds in Feisty)

---

### Post by dicecca112 on 2006-12-04
I know for a fact of at least 10 people using Edgy with no issues.

---

### Post by psych-major on 2006-12-07
Make that 11...Edgy is running beautifully on my Dell Latitude D820 (core-duo)

---

