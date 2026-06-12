---
title: "Ubuntu will not load from DVD+RW"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by Twinn87 on 2011-03-18
Hi,

I have just burnt Ubuntu iso to a DVD+RW which is brand new, I checked on my windows laptop to see whether the files burnt to disc correctly like on your websites support page and it did. So I loaded up my other laptop which I rebooted and completely wiped, it now has no operating system and so I would like to install Ubuntu on it. So I put the DVD+RW into the cd drive and we go through the usual boot screen... a black screen appears (only with the Ubuntu cd in the drive) which has symbols similiar to what I describe below.

It has a rectangular box on the left hand side then next to that it has a = sign and then on the right of the equals sign it has a stick man figure... after this disappears all I get is a black screen with a flashing _ cursor and nothing more happens.

Can anyone please help me to get this working? I downloaded the Netbook Ubuntu 10.10. 

Thankyou for your help :)

---

### Post by HannuMR on 2011-03-18
"So I put the DVD+RW into the cd drive.."

Maybe a stupid question, but is there in laptop DVD+RW drive, or should you burn ISO-image to CD?
Are you sure, that in BIOS startup order DVD/CD-drive is first?

---

### Post by Twinn87 on 2011-03-18
Thank you for your reply HannuMR. 

Just checked the drive and it is a DVD Rom/R/RW drive. In the bios start up the dvd/cd drive is second in the selection of options, I wouldn't know how to make it priority.

---

### Post by ronparent on 2011-03-18
> It has a rectangular box on the left hand side then next to that it has a = sign and then on the right of the equals sign it has a stick man figure... after this disappears all I get is a black screen with a flashing _ cursor and nothing more happens.

The fact that this option appears means that it is booting on your DVD. It means to hit the spacebar to bring up a boot menu.

The fact that it isn't going further either means that the dvd isn't being read correctly or that your computer hardware isn't completely compliant with what the Ubuntu will run on. Almost all the time it can be fixed. 

The cd or dvd is not read properly for many reasons. Some times its because of an error when burned. Sometimes it is because of the inability of the reader to read some dvd's burned on another burner! This requires you to check the mdsum you get on the reader with the published one for the image you are trying to load.

If the image checks out OK but you still can't boot then then the fault may be the non-compliance. This requires inserting a boot parameter into the boot line that will work around this issue with your hardware. This reference will guide you: [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Don't give up. Most of these issues are trivial but can be a real pain to identify. Study this and try a few things. Post any problem you run into here and someone who has dealt with this type problem before often can help you over the hurdle.

---

### Post by Twinn87 on 2011-03-18
I didn't realise I had to hit the space bar to boot the cd, I will try that now and see if it works.

Thank you for your advice ronparent, if I used a USB stick would that maybe work easier than the DVD option?

---

### Post by ronparent on 2011-03-18
It would probably by pass the reading issue but if there a boot options needed you would still have to slough through the boot issues.

---

### Post by KegHead on 2011-03-18
Hi!

The USB option always works for me.

I've never booted from my dvd drive. (in Ubuntu)

KegHead

---

### Post by KegHead on 2011-03-18
Hi!

Just an update:

Today's iso is 700mb------won't fit on a cd.

You must use a dvd or USB stick.

KegHead

---

### Post by Twinn87 on 2011-03-21
Thanks, I got to the screen which had the rectangle with the = sign and the human stick figure, I hit the space bar and it came up with the language selection which I chose as English. Then it had a menu such as (not exact, my memory can't remember).

Run Ubuntu and Install Later
Install Ubuntu
Test CD
Memory
Hard Drive

I tried ALL options and every option leads to the same path, it just moves on to a black screen with a flashing _ and then the cd drive goes quite and nothing happens. No option works for me? very strange as I would have thought after getting to langauage selection the whole CD would have worked... any advice from this stage? Thank you. :)

**Update:** ok... I read this page... [https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)
It told me to remove the "quiet splash--" which I did... It then moved on to another screen where it displayed some text, after this it repeatedly displayed the following text over and over. (I didn't write it all, it was too much, but I got the beginning)

Ata3:00: status (DRDY ERR)
Ata3:00: errpr (UNC)
Ata3:00: configured for UDMA/133
Ata 3: EH complete

and then the code carried on...

---

### Post by Hakunka-Matata on 2011-03-21
Sounds like a/the Video driver issue.
Everything is working properly, except that once you start either the Install or Try Ubuntu, video driver selected renders your display DOA.  
I'm not able to tell you @ the moment how to change the startup command line to add the 'nomodeset' suffix after the -- quiet splash, but that probably will fix your display and you'll be off and running.  I'll get back with the "how to" in a moment, maybe somebody else will jump in and tell you how to do that

---

### Post by Hakunka-Matata on 2011-03-21
Here you go:

> **Installation**

 All started when, full of confidence, I booted the usb stick with the  Linux install expecting everything to work as a charm and ended up  staring at a black screen. After a bit of research it seems the problem  is related to the i915 (see [this thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561802") for full details). In short the solution has 3 steps:
 
[LIST]
[*]install: press Esc when booting to go to the menu, select English then press F6 for extended options and select the **nomodeset**  option. Optionally you can enter it by hand on the kernel parameters.  This will start the livecd and the installer in a very low resolution.  You can now install your system.
[*]reboot: you need to edit the kernel parameters in grub to add the  nomodeset option in order to be able to boot your newly installed os
[*]persist: after you got in you need to install the nvidia proprietary  drivers to fix the low resolution problem and change your grub  parameters. Edit **/etc/default/grub** and change
[/LIST]
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

---

### Post by Hakunka-Matata on 2011-03-21
> It has a rectangular box on the left hand side then next to that it has a  = sign and then on the right of the equals sign it has a stick man  figure...Hit [**TAB**] key to edit options, or something like that, **that's what you do Twinn87**

---

### Post by Twinn87 on 2011-03-21
Thank you for the quick response [Hakunka-Matata]("http://ubuntuforums.org/member.php?u=735950")

I look forward to hearing from you soon. :)

---

### Post by Hakunka-Matata on 2011-03-21
I look forward to hearing from ***You ***soon

---

### Post by Twinn87 on 2011-03-21
I just went to the Ubuntu install menu.

Hit F6... clicked the nomodeset option which it but a x next too.

I then removed "quiet splash--" and hit the install ubuntu option... I still get the same errors?

Here is the rest of the code.

ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0

ata3.00: irq_stat 0x40000008

ata3.00: failed comman: READ FPDMA QUEUED

ata3.00: cmd 60/08:00:a8:4b:f9/00:00:0d:00:00/40 Emask 0x409 (media error) <f>

---

### Post by Hakunka-Matata on 2011-03-21
Just use the F6 nomodeset option in your case, Sometimes people don't have the F6 option visible

What Release Ubuntu are you installing?

---

### Post by Twinn87 on 2011-03-21
Hi. I am using 10.10

I just tried leaving the quiet splash and only selecting nomodeset and I get a screen that reads, 

6.666326 Disabling IRQ #10

When I try removing the quiet splash and only selecting nomodeset I get the same error code as I previously posted.

---

### Post by Hakunka-Matata on 2011-03-21
Full Disclosure:  I don't have any immediate suggestion on what to do here.  But let's see if you can get a bit more information first..........

10.10 32-bit Desktop I'm guessing?
What are you left with after dropping out with the IRQ #10 error msg?

Do you have a tty logon screen then?

If so, logon and have a look @ dmesg, find the IRQ # 10 line and see if something makes sense around there?  

dmesg | grep IRQ #10 will show you that line, but not many lines before and after it.

---

### Post by Twinn87 on 2011-03-21
I just downloaded the ubuntu netbook download from the ubuntu site, I assume it is 32 bit I had no option of choosing otherwise.

When I get to the screen you asked about it just remains with the ICQ code and that is all, it has nothing or does nothing more.:confused:

---

### Post by Hakunka-Matata on 2011-03-21
Is your computer a netbook?  Look @ post #18 too, I just edited it

---

### Post by Twinn87 on 2011-03-21
Its a laptop... I assumed a netbook and laptop was the same? Did I make a mistake? Should I get desktop?

---

### Post by Hakunka-Matata on 2011-03-21
netbook and notebook and not equal.  Netbooks usually run a less capable CPU like N-270, I'm drawing a blank on what the N is right now.

the 'netbook' release can be installed on any type of computer, it's a slimmed down version of Ubuntu.  It certainly does not hurt to install it, it should work just fine. 

I'd however prefer regular "Desktop 32-bit".  If your CPU is a 64bit CPU, you could also choose "Desktop 64-bit", but that gets a bit dicey because some apps don't run correctly on 64 bit install.  

Try the 32 bit version first.  Later, install the 64 bit version as a multi-boot system (if your CPU supports) and see how it goes.

---

### Post by Twinn87 on 2011-03-21
I just tried the same ubuntu disc on my friends laptop, he loaded up his wondows OS and we clicked 'demo and full installation'... It told us to reboot with the cd still in the drive we did and it just loaded windows with no ubuntu at all.

Could this be a indication the disc is also faulty?

I will download desktop as well if I can to see if it works.

---

### Post by Hakunka-Matata on 2011-03-21
The LiveCD is good I think.  You're able to get all the way to the Start up menu, just go back and do that again, but use the **F6 key** and select the **nomodeset option** and try "Try Ubuntu without installing" option, see what you get.

---

### Post by Twinn87 on 2011-03-21
Ok I am not at home at the moment as I went to try it on a friends laptop so I will try your new idea when I reach home.

I just find it strange how it didn't load up ubuntu as it should on my friends windows OS when we clicked the 'demo and full installation' button on his loaded windows OS.

---

### Post by Hakunka-Matata on 2011-03-21
that's another kettle of fish or pot of Tea

---

### Post by Twinn87 on 2011-03-21
I tried your suggestion with the "try ubuntu without installation" and it still had the same error... I am really confused now and really hope I can figure this out... maybe I might need a new laptop?

My friend will be trying to install from the same disc soon, so as soon as we try this week I will let you know how that goes as well... any suggestions sdtill is much appreciated, I want to keep trying to get ubuntu on my laptop... thank you all! :)

---

### Post by agent-orange2 on 2011-03-21
I've just had this very problem, I get to the boot menu, but can't get it to boot from the disc. I formatted the disc into NTFS before putting ubuntu 10.10 iso on it and it works fine! I thought the drive was knackered but realised it wasn't when I put the windows recovery disc in.

---

### Post by Twinn87 on 2011-03-21
Hi agent-orange, it is comforting to know someone else is experiencing a similiar problem, of course not a good thing lol... 

Have you managed to find a way to work around this issue we are currently having? 

I burnt the iso straight to a dvd-rw and it seems to be working fine, right up to the menu and then I get the error

---

### Post by Hakunka-Matata on 2011-03-21
have you done the 'check cd' option as well?

and the F6 'nomodeset' right?

---

### Post by Twinn87 on 2011-03-21
I have tried every way, I have tried with nomodeset checked, without it checked and all the others checked and then removing "quiet splash--" it does exactly the same with any combination I use... and even when I do the same with the "check disc" option.

---

### Post by Hakunka-Matata on 2011-03-21
Can you post the output of
```
lspci
```

---

### Post by Twinn87 on 2011-03-21
> **Hakunka-Matata said:**
> Can you post the output of
```
lspci
```

Sorry for not understanding, is **lspci **located under the same F6 menu?

Thanks.

---

### Post by Hakunka-Matata on 2011-03-21
run that code in a Terminal

Oops, maybe you're on a windows machine???

---

### Post by Twinn87 on 2011-03-21
It is a laptop which had a pre-installed Windows XP OS on it, I then later installed Vista on to the machine as it is capable of both. I now have no OS on the machine hence why I am trying to install Ubuntu :D

---

### Post by Hakunka-Matata on 2011-03-21
[http://www.puppylinux.com/](http://www.puppylinux.com/)
OK, here's a suggestion, get PuppyLinux and see if that will start up on the machine.  It's very smart, and small.

---

### Post by Twinn87 on 2011-03-21
> **Hakunka-Matata said:**
> [http://www.puppylinux.com/](http://www.puppylinux.com/)
OK, here's a suggestion, get PuppyLinux and see if that will start up on the machine.  It's very smart, and small.

Ok, I will do that as soon as I can and report back.

Thanks for the suggestion. :o

---

