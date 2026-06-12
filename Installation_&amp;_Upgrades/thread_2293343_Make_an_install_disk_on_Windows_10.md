---
title: "Make an install disk on Windows 10?"
date: 2015-09-04
forum: Installation &amp; Upgrades
---

### Post by heather6 on 2015-09-04
Good morning,

I have no idea what I'm doing, but I thought I'd convert an old laptop to Edubuntu for my daughter.  I've been having trouble making an install disk using my Windows10 laptop, as the "Create an installation disk" instructions for Win7/8 don't quite match up with my user experience in Win10.  The target computer is running Windows XP, and I wouldn't trust it to handle the job of making it's own demise.

I only have 5 total blank DVDs available and have already burned two unusable ones.  I figure it's time to seek some expert help. :) 

Is there a resource someone can point me to?

Thank you!

---

### Post by ajgreeny on 2015-09-04
If the old machine boots from USB, use that to install the OS, as that it usually quicker to make and use than a DVD/CD.

What is the spec of the XP machine?  Does it have enough RAM? What about graphic card?

If it will boot from USB I think there are several applications available to produce a live bootable USB using WinXP, but the only one I have ever used (in Ubuntu, I must admit, never Windows) is unetbootin.

See [http://unetbootin.github.io/](http://unetbootin.github.io/) and [http://launchpad.net/unetbootin/trunk/613/+download/unetbootin-windows-613.exe](http://launchpad.net/unetbootin/trunk/613/+download/unetbootin-windows-613.exe) for the application itself.

---

### Post by yancek on 2015-09-04
I would not expect windows software to be able to create a bootable Linux system and I think you would save yourself a lot of grief if you take up the suggestion above to use unetbootin to create the bootable flash drive.  Just make sure you select the correct version if you are doing it on windows  as there are versions to run on Linux, windows and Mac.

---

### Post by heather6 on 2015-09-04
It's starting to sound like "you must have ubuntu to GET ubuntu"...  hahahahaha *sob*

I'll check it out...  I've got a few more things I can try...  I do have another really slow machine running Windows7, so worse come to worse, I will move the downloaded file over there and use THAT machine to follow the windows7 directions.  Problem is, it's also super slow and I was likely going to put some other version of ubuntu on that machine after I got the old laptop on Edubuntu for the kiddo.

I have not specifically "checked the specs", however I have anecdotally heard from several of my far-nerdier friends that the Dell D610 is perfectly suited for what I'm trying to do.

I'm more of a "take stuff apart and build ham radio things" sort...  software and operating systems are not strong with this one.  But, the kiddo wants to be a programmer, so I figured I would give it a shot.

Thanks for the help, and if more suggestions come to mind, please post them.  Worst case scenario, I'll be working on this all weekend.  :P

---

### Post by Geoffrey_Arndt on 2015-09-04
There is a program in WIndows to make bootable usb-flash-stick for a Linux Live distro (aka distribution or version). 

It's called "Pendrive Linux" [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

But, before you do, most really old PC's do not boot from usb-stick.   A CD or DVD is much easier.

So, any good disk burning program will create an "iso image" and burn it to disk (this is NOT the same as "copy" which won't work).    Nero, ImgBurn  or many such programs are available for Windows (google is your friend - kinda).

Also, I don't know much about Edubuntu . . . but any of the lower hardware "buntu's" are easier to install on an old machine (by far) than Ubuntu proper.   I like Ubuntu Mate or even Linux Mint Mate 17.2.    Then just install all the education programs you want.      I'm not suggesting however, to give up on Edubuntu, _try it first_, but just be aware there are many Linux distros that are good for older PC's.   

See [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by yancek on 2015-09-04
> It's starting to sound like "you must have ubuntu to GET ubuntu"...  hahahahaha *sob*

No you don't.  You've had two options suggested, unetbootin (which has a windows version) and pendrivelinux (which only runs on windows) and will create a bootable flash drive which you should then be able to use to install Edubuntu.  For that to work, your old computer would obviously have to be capable of booting from usb which many older computers are not.

---

### Post by heather6 on 2015-09-04
I  know.  I was just being a bit tongue in cheek.  Like the old "you can't get a job without experience, and you can't get experience without a job" problem we faced as younguns.

I believe I have found Windows 10's version of what the "[how to burn a disk image in windows 7/8]("https://help.ubuntu.com/community/BurningIsoHowto")" is referring to...  failing that, I will try to get that program suggested above.

I have been told I should be able to boot that computer from a USB, however I don't want to count on that in case it fails.  But, after this attempt, I have two more disks...  AND several other ideas to try.  I'm just a bit hesitant to try the USB route for several likely unfounded concerns and other nonsense reasons.  

In all honesty, I should me making the tween do this part, but she's in the middle of Minecraft and cannot be bothered.  :P

I appreciate the help, and will report back once I figure out what works for me.

---

### Post by heather6 on 2015-09-04
SUCCESS

WINDOWS 10 - 

Right click your downloaded iso file > View Disc Image > that opens Power2Go CyberLink ISO Viewer.  Then, up in the top left, there is a menu of icons... the second to last is the "burn to disc" command.  

That particular method has yielded us a bootable CD!  Hooray!  

And now the fun part. 

Thanks everyone, and I hope I have maybe helped a future someone with this entire thread!

---

