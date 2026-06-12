---
title: "checking md5sum of a burned CD"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by Bahokan on 2010-12-26
Hi all,

I checked the md5sum of the iso using winMd5Sum utility, it is OK. 

To check the CD, right clicked the md5sum file in it, send to winmd5sum, and then copied the corresponding hash from the ubuntuhashes page into the bottom text box, and compared. The message box says md5 sums are different. Now the question is, have I done it correctly, I mean, is this the way to check a burned CD, OR, is there another way to check md5sum of a burned CD?

Any help appreciated.

---

### Post by Frogs Hair on 2010-12-26
Here is some documentation if haven't viewed it already.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Bahokan on 2010-12-26
I have already checked out that page but if I am not mistaken, instructions given there apply to a linux environment, right? Or is it possible to check the CD under Windows using the ways as instructed there?

---

### Post by Quackers on 2010-12-26
To check the cd for errors tap the F6 key during boot from the live cd/usb and you will be offered that as a screen option.

---

### Post by Bahokan on 2010-12-26
Quackers, sorry I forgot to mention but I have done this too. All I got was a screen full of error mesages. Now, from what I am saying, one may think that the CD is corrupted or something but I am not too sure about this because those error mesages may be the sign of an incompatible graphics card (nvidia GeForce FX 5200). So before attempting to deal with a card related issue, I just want to make sure that CD is OK. Do you have any other suggestion?

---

### Post by Quackers on 2010-12-26
If the errors are Input/Output errors (or I/O errors) or missing files then the cd is likely to be bad. If the errors refer to other things then, no.
Which version of Ubuntu are you installing?
The FX 5xxx cards were certainly supported up to a degree, but I'm not sure if that's still the case.
What is happening exactly when you try to boot from the live cd?

---

### Post by Bahokan on 2010-12-26
It is 10.10. I attached an image of how the screen looks like when I click on the 'try ubuntu' option. You can see the image and some other details as to what I have done to resolve this issue (with no success) in the following link [http://ubuntuforums.org/showthread.php?t=1652098](http://ubuntuforums.org/showthread.php?t=1652098). :)

---

### Post by Quackers on 2010-12-26
It's not good to have two halves of the same problem in two threads.
Why did you disable the Nvidia card? What was happening? What is your onboard video card type? 
What you have on the screen in the other thread is a kernel panic. This could be hardware related, or bios, acpi or many other causes.

---

### Post by Bahokan on 2010-12-26
I thought this thread was different than the other because I was merely asking how to check a Live CD under windows, sorry it was my fault. 

I wanted to disable the Nvidia card because I have seen some users' posts related to this card, [http://ubuntuforums.org/showthread.php?t=1168703](http://ubuntuforums.org/showthread.php?t=1168703). So I just wanted to give it try but couldn't make the onboard card work. I clearly explained why it didn't work in the above link. 

As for my onboard card, in the Device Manager it says Intel 82865G Graphics Controller, Everest says Intel Extreme Graphics 2.

As you say, it could be hardware related or something else. But if it is hardware related then I shouldn't be able to boot from Windows XP cd when installing the XP. There are only three things that I can think of, that may be the cause of the problem: 
1. nvidia card, 
2. bad cd
3. ubuntu is too picky about even very minor issues. 

When you say Bios (maybe acpi?), what do you exactly mean? Can you make it a bit more clear please?

---

### Post by Quackers on 2010-12-26
I would have tried to install Ubuntu on the default system first, then looked for answers if I had a problem. 
A bad cd won't cause a kernel panic, as far as I'm aware.
acpi deals with the way your hardware is handled and is a part of bios, I think!
As you appear to have tried some boot prompts, have you tried acpi=off ?
With regard to the kernel panic the fact is that most people have no experience with one (myself included) and can really only guess.

---

### Post by Bahokan on 2010-12-26
When you say "default system", you mean in windows?

I tried all F6 prompts, as well as

i915.modeset=0
xforcevesa
fb=false

none worked. 

When I try different boot options, the error mesages I receive each time differs than the previous ones. There is one saying "[COLOR=Red](initranfs) Unable to find a medium containing a live file system." [COLOR=Black]and I got this when I delete the last two words from the line reading [/COLOR]
[/COLOR]"file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash--" 
[COLOR=Red][COLOR=Black]Do you know what this message is about?[/COLOR]
[/COLOR]

---

