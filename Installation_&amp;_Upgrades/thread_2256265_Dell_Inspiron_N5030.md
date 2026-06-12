---
title: "Dell Inspiron N5030"
date: 2014-12-11
forum: Installation &amp; Upgrades
---

### Post by abdallah5 on 2014-12-11
hi ubuntuers

before i stat installing ubuntu i need to know does ubuntu format the hdd and all files or not?

and if it formats the all data .... can i get them back?

---

### Post by abdallah5 on 2014-12-11
guys , any help ?

---

### Post by deadflowr on 2014-12-11
Installing on what? What do you have right now?

And also, please do not bump a thread only 28 minutes after starting it.
(We allow for bumps within several hours, but within half-an-hour is impolite)


Edit: I should point out that I ask what you have now, because What Ubuntu does depends upon the system that is installed.
If you are running Windows and want to install Ubuntu, which you could set up as a dual boot leaving the files for Windows intact on a separate partition untouched by the Ubuntu install, or as a full replacement for Windows in which case Ubuntu's file system type will reformat the partition and wipe whatever was installed.
A program called photorec can help recover files if you do indeed reformat the partition. Recovery though is best done using a live session, like that which comes on an Ubuntu liveDVD, or install disk.

Now if by chance you were reinstalling Ubuntu you would not need to format the partition as it would already be formatted to run Ubuntu on therefore you can reinstall it without formatting and thus keep your files intact. More precisely, you can keep your personal files intact. The Ubuntu installer is smart enough to not touch the users home folder during a reinstall if you use the something else option and do not check it for formatting. Also you need to enter the exact same info for the user as the original system had it.

This is all pretty general, though.
For a pretty general question.

---

### Post by abdallah5 on 2014-12-11
i've a pc and i've already downloaded ubuntu disc image

but i saw many people explained how to install ubuntu and they chose the first option "Erase disc and install Ubuntu" and it surely deletes all the files on my hdd

is there any way to install ubuntu without deleting any data .... or how to recover my data after erasing and installing Ubuntu

---

### Post by lisati on 2014-12-11
There is a process known as "dual boot" which is described [here]("https://help.ubuntu.com/community/DualBoot"). 

Because things can go wrong, even with the most careful preparation, it is really important to backup all your important stuff first.

---

### Post by deadflowr on 2014-12-11
See my post #3 edit
Hope it makes some sense.

But in general, if you want to keep your data intact, you would create partitions where you can keep the data and partitions where you would install the operating system.
Understanding partitions will go a long way to helping you not lose your data.
Little more here, perhaps
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by coldraven on 2014-12-11
You have two choices:
1. Erase everything, after that your data is gone forever, you cannot get it back
2. Use Windows to create some space on your drive and then install Ubuntu there.
If you do not know what you are doing then there is a high chance that you will lose your data. 
[B]In both cases you must backup all your data to an external drive first!
[/B]

---

### Post by abdallah5 on 2014-12-11
sorry guys, but i'm not british or american and i can't understand english well

so please give me the steps 1,2,3 and 4 because i didn't understand what was written in the link above

---

### Post by sudodus on 2014-12-11
Hi [**[COLOR=#000000]abdallah5[/COLOR]**]("http://ubuntuforums.org/member.php?u=1959557"),
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1959557") 	 

You are welcome to the Ubuntu Forums :-)

We can try to help with simple text, but if you still have problems to understand, there is a risk that your data will be destroyed in the installing process. ***Please search for instructions via the internet in a language, that you know better than English, or ask a friend, relative, colleague, who can help you take the first steps.*** That way you can also learn some important words about computers and linux, and after that you will be able to use the information from our Ubuntu Forums.

---

### Post by abdallah5 on 2014-12-11
ok thanks 
it was my fault to post my problem here

---

### Post by deadflowr on 2014-12-11
I would say, disregard everything posted so far and tell us everything you know about the machine and what operating system you are using right now.
Is it running windows right now? if so which version.
Do you know the name of the machine? This can help us possibly determine if Ubuntu can even be installed.
And probably of greatest help, what do you know about the hard drive that the machine has? If the machine has too small a hard drive, resizing and making partitions or even a dual boot might not be possible, or at least difficult or not worth it.

I think these three things should be a good starting point to get you on the way.

---

### Post by Elfy on 2014-12-11
Maybe have a look here and see if there are more suitable support options for you.

If not - come here - people WILL help you. 

[http://loco.ubuntu.com/teams/](http://loco.ubuntu.com/teams/)

---

### Post by sudodus on 2014-12-11
> **abdallah5 said:**
> ok thanks 
it was my fault to post my problem here

I repeat, that you are welcome here. But do not rely only on information in English, if you feel that you do not quite understand it. Try to get information about the same things in your own language. This will make the installation safer.

Installing operating systems is risky, even for people who have done it many times, so please make a backup copy (alias security copy) in a separate disk. At least make copies of your most important personal files: documents, pictures, video clips. But the best way is to backup 'everything' including Windows itself or make a recovery disk for Windows.

And please give the information to *deadflowr* to make it possible to help you, at the same time as you look for information in your own language :-)

---

### Post by abdallah5 on 2014-12-11
as for the language that i understand better than english , i'm arabic and i can find the solution by arabic 
but i came here because it is the forum itself (i mean it is a trusted source)
there is no any arabic source that i trust to post my problem 
i didn't think of finding the solution by arabic because many people will compose and act as they know the solution

---

### Post by sudodus on 2014-12-11
> **deadflowr said:**
> I would say, disregard everything posted so far and tell us everything you know about the machine and what operating system you are using right now.
[COLOR=#006400]1. Is it running windows right now? if so which version.[/COLOR]
[COLOR=#006400]2. Do you know the name of the machine?[/COLOR] This can help us possibly determine if Ubuntu can even be installed.
And probably of greatest help, 3. [COLOR=#006400]what do you know about the hard drive that the machine has?[/COLOR] If the machine has too small a hard drive, resizing and making partitions or even a dual boot might not be possible, or at least difficult or not worth it.

I think these three things should be a good starting point to get you on the way.

I high-lighted the questions with green.

> **abdallah5 said:**
> as for the language that i understand better than english , i'm arabic and i can find the solution by arabic 
but i came here because it is the forum itself (i mean it is a trusted source)
there is no any arabic source that i trust to post my problem 
i didn't think of finding the solution by arabic because many people will compose and act as they know the solution

Then let us start - and let us be careful - to avoid mistakes :-)

We are already a handful of people ready to help you. We live in different time zones and speak different native languages. I'm Swedish (and live in Sweden).

A. Please post as much information as possible about your computer. It will help us help you. Start with a reply to *deadflowr*'s questions :smile:

Then I suggest that you to prepare to do things safely:

B. Have you got or can you get an external drive, where you can backup your personal data (documents, pictures ...)?
C. Have you created a recovery disk for Windows?

-0-

You might want to read a few more links (in English) - read quickly to get an overview, and then, read more carefully, and ask questions about details, where you need something explained.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
[/URL]For rather new computers:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

For old computers:

[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by abdallah5 on 2014-12-11
ok thank u very much for your time
but i sacrificed by my hdd and lost my all files and everything 
know i'm working with ubuntu with no files as i've already bought a new pc
thaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaanks

---

### Post by sudodus on 2014-12-11
Does this mean that you want to install Ubuntu into the whole internal hard disk drive? In this case it will be much easier than to make a dual boot (install Ubuntu alongside Windows). Installing into the whole drive is a simple and standard option.

There might still be problems depending of the computer's hardware parts. Please tell us about the computer, because different kinds of computers need different versions and flavours of Ubuntu!

---

### Post by abdallah5 on 2014-12-11
i've a Dell Inspiron N5030 Laptop

Ram 4GB
CPU Intel Pentium Dual-Core 2.30 GHz
HDD 250GB

---

### Post by sudodus on 2014-12-11
Did you wipe Windows from this computer? Or do you want to keep Windows and install Ubuntu alongside Windows (dual boot)?

-o-

The computer should be new and powerful enough for any flavour of Ubuntu: Standard Ubuntu, Kubuntu (fancy desktop environment but heavy footprint), or Xubuntu (medium light desktop environment) or Lubuntu (ultra light desktop environment).

According to this link, there is Intel graphics, which should work with the built-in linux driver. I did not find anything about wifi, but wired internet should work at once.

[http://www.cnet.com/products/dell-inspiron-n5030-15-6-pentium-t4500-windows-7-home-premium-64-bit-4-gb-ram-320-gb-hdd/specs/](http://www.cnet.com/products/dell-inspiron-n5030-15-6-pentium-t4500-windows-7-home-premium-64-bit-4-gb-ram-320-gb-hdd/specs/)

So [try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

Download the iso file(s), check the md5sum, create DVD or USB boot drives. I recommend using a USB pendrive. See this link and links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by abdallah5 on 2014-12-12
but how to install the graphic card on ubuntu ??? and also i want to download high graphic games but i can't find it in the ubuntu software centre

---

### Post by sudodus on 2014-12-12
Intel graphics usually work with the built in free drivers, you need not install anything. This is different from Windows.

Many other graphics chips also work with the built in free drivers. Some nvidia and amd/ati/radeon chips work, but work better with proprietary drivers, some such chips have problems in linux.

Some 'high graphics games' work better in Windows. I'm no gamer, so ***I hope other people can chip in and help*** you sort out what is possible in your computer.

---

