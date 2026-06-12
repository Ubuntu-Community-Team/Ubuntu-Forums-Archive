---
title: "P3 laptop install"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by Mecht_Engnr on 2010-02-22
I am trying to install a linux distrobution on a laptop that can only boot off a cd or harddrive (or network? not sure), except that it has no cd drive and no operating system.  That's right, no floppy no USB no CD.  

I read on the internet a chap installed Ubuntu with these conditions by taking out the harddrive and installing an old copy of Ubuntu on it on another computer with a disc drive, and then putting it back in his laptop and upgrading.

Now I have installed DOS 7.10 before on this laptop hard-drive and it worked, but it wasn't very useful:), being a text based system.  I have tried installing Windows XP (only because I am familiar with it) but my installation CD is OEM, and doesn't seem to like it.

So I put the ubuntu 4.10 cd in my desktop with the CD drive after clearing all data off the laptop hard-drive (DOS 7.10).  Then the cd boots and I am given the menu to install ubuntu.  So I press Enter, it starts installing and then **freezes at the language selection screen**.  

So what is my problem?  I have pressed lots of keys in order to get some response, but nothing.  I waited 10min for something to happen, but nothing did.

Could someone please help?

---

### Post by ubunterooster on 2010-02-22
did you "check CD for defects" before attempting install?

---

### Post by Joe Ker1086 on 2010-02-22
have you tried booting into the live OS? might want to try that then try installing from there.

---

### Post by ubunterooster on 2010-02-22
You should: one check CD for defects (always do this before a first use of the CD or if CD has not been checked for over a year) then, 2, go into live CD and install from there (thanks joe). Try that in that order and then report back, please.

---

### Post by hansdown on 2010-02-22
Hi Mecht_Engnr.

Do you mean 4.10 Warty Warthog?

That version is way past end of life.

It won't receive updates any longer.

Can you download a newer version?

[http://www.ubuntu.com/news/410eol](http://www.ubuntu.com/news/410eol)

[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

---

### Post by ubunterooster on 2010-02-22
oops; I mentally saw "4" as '9'.

If it is 4.10, it looks like you found one of the "warts"

---

### Post by snowpine on 2010-02-22
Welcome to the forums!

I agree that "move the hard drive to a working computer" is a good approach. A few considerations first:

1. Does your computer meet the minimum specs for Ubuntu? If not, you are wasting your time.

> Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection

2. The oldest release that's still supported is 8.04. There is no reason or benefit to install anything older. (If you don't meet the minimum requirements, better to go with something like Puppy than an unsupported ubuntu.)

3. Check the CD for defects as mentioned above.

4. What is it that you hope to accomplish with this outdated (and slightly broken) computer? Will Ubuntu realistically help you achieve these goals?

Good luck!

---

### Post by ubunterooster on 2010-02-22
+1 for puppy 

[also: puppies are cute. Irrelevant; I know]

---

### Post by Mecht_Engnr on 2010-02-23
> **snowpine said:**
> 1. Does your computer meet the minimum specs for Ubuntu? If not, you are wasting your time.

1.7Ghx CPU
256MB RAM - I could get some more!
30GB hard drive
Resolution unknown but looks like it is at least 1024x768.


> **snowpine said:**
> 2. The oldest release that's still supported is 8.04. There is no reason or benefit to install anything older. (If you don't meet the minimum requirements, better to go with something like Puppy than an unsupported ubuntu.)

Ok, thanks.  I may do that - but see below.

> **snowpine said:**
> 3. Check the CD for defects as mentioned above.

So, put the burnt CD in another computer and boot off the CD or do I just load it in Windows.  Sorry, I am not familiar with the term "Live CD", other than I know it is a way to test out an OS.

> **snowpine said:**
> 4. What is it that you hope to accomplish with this outdated (and slightly broken) computer? Will Ubuntu realistically help you achieve these goals?

Well, what I really want is a machine that can web browse and type word documents.  Nothing beyond this really.  So I am sure a laptop with the specs above are ideal!  I am not gaming, and I am not doing any video-processing or large image manipulation.

> **snowpine said:**
> Good luck!
Thanks.  I'll need it.  I'll also depend on you generous people for help!

---

### Post by Mecht_Engnr on 2010-02-23
Hmmm...Looking up a bit more about the live CD it seems as though a ubuntu version as old as 4.10 would not have that function.

I have found this site which seems to talk about my issue:
[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)
[http://ubuntuforums.org/showthread.php?t=782603](http://ubuntuforums.org/showthread.php?t=782603)

But I haven't found a site that explains how to install GNU GRUB on a hard drive from a Windows machine.  Can someone help me here?

---

### Post by snowpine on 2010-02-23
[Xubuntu]("http://xubuntu.com/") might be a better choice with onlly 256mb of ram.

[Here are the]("http://www.ubuntu.com/getubuntu/download") easiest install instructions I've seen. (1, 2, 3!) The instructions are basically the same for Xubuntu, too. The option to check the CD for errors is on the first screen when you boot from the Live CD.

(Grub is set automatically during the install process.)

---

### Post by ubunterooster on 2010-02-23
snowpine's reccomendation of xubuntu is not a bad one, I actually use it more than I do ubuntu. But puppy is still good, lubuntu is better (personal opinion), and you should reall look into U-lite: "ubuntu for low powered machines"

---

### Post by Joe Ker1086 on 2010-02-23
Honestly, I saw the 4.10 but though it a typo.....shame on me. You are probably right when it comes to 4.10 not having a live version but it would still have the check for defects...also your theory on upgrading from an older distro might work if you were to install something still supported. Don't think it would work with with 4.10. If all you need is internet browsing and basic look into crunch bang linux. still a debian base and really its just a lightweight ubuntu using the xfce desktop.

---

