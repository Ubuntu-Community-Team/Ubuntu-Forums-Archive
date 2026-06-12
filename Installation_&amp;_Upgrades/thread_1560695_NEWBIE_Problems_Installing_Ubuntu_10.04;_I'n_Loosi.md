---
title: "NEWBIE: Problems Installing Ubuntu 10.04; I'n Loosing Patience"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by marine02xx on 2010-08-25
All,
  I'm new to Linux and Ubuntu. I recently downloaded Ubuntu 10.04 to an older computer. Here's info on the hardware:

Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
Multimedia audio controller: Yamaha Corporation YMF-740C [DS-1L Audio Controller] (rev 03)
Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
VGA compatible controller: S3 Inc. Savage 4 (rev 02)

PROBLEM: I get the "black screen" like everyone else has received when loading Ubuntu to an older machine. I have been using the Boot CD for days and I really need to get this machine running. I have over 600mb of RAM, so running the OS should be no problem. I have tried a number of possible fixes, and none seem to work. I'm thinking it's a video driver issue, but I am unable to upload drivers for the Savage4 video card (it's old, I know!)  Common Kernel parameters modifications (i915,modeset=1 and 0, nomodeset, xforcevesa) have not worked for my machine. What else do I need to do?

I only have Ubuntu 10.04 as my only OS, I have been dealing with this for 4 days, and I am running out of patience. As a newbie, the language in some of these forums are confusing. If you want people to use the OS instead of Windows, SPEAK ENGLISH THAT WE NEWBS CAN UNDERSTAND!!! In my opinion, the Linux community is not doing a very good job communicating fixes well in these forums.

**_QUESTIONS_**
- What do I need to do to get Ubuntu 10.04 to work on MY specific system?
- Based on my CPU, should I use another Linux OS?
- Should I use Linux at all?

HELP!!!

marine02xx

:mad: :twisted:

---

### Post by lombaardcj on 2010-08-25
I know you don't want to hear this, but like everyone else using these forums, we all have to apply ourselves with some patience.

As a community member I have found plenty helpful people who are willing to share their knowledge for free.

I'm sure if you want help urgently, a better attitude towards a working solution would be good.

As for your problem,  You might have to look at a slightly lighter distro ito display resources.  You can also look at using another window manager instead of gdm.

I have spoken to many people who rather use Xubuntu for lower-spec PC's.  Goto: [http://www.xubuntu.org/](http://www.xubuntu.org/) and check it out!

Please let me know if this was of any help, or complications you still experiencing. 

:)

---

### Post by thegod_slayer on 2010-08-25
hello
i also had a display problem with 10.04 on my laptop.
my cd won't boot.
then i tried 9.10 (karmic) and wola it runs fine.
i think you should try 9.10 or 9.04.
if you are using windows or any other operating system then just download the .iso files 
and burn them to a disk.
your boot cd is ready now try to boot all over again.
keep patience.

---

### Post by nerdy_kid on 2010-08-25
i wouldn't try Lucid on a machine with that low specs, maybe go Lubuntu of Xubuntu.

---

### Post by mörgæs on 2010-08-25
600 MB memory should be fine for Ubuntu. As said earlier, just burn a few live CD's and install the one which works best.

Remember to have wired internet access while installing.

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

### Post by marine02xx on 2010-08-25
[COLOR=black][FONT=Verdana]lombaardcj,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]  Thank you for those words of encouragement. I have a rather healthy attitude and really want to be a contributing member of the Linux community. That said, I don't think an initiation in patience is a selling point! I've been kacking at this for over four days. Is that enough? I will keep trying as I'm neither a quitter nor one for instant gratification. I have taken your advice and downloaded Xubuntu; hope it works...[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]thegod_slayer,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]  Thanks for your feedback. I burned the .iso and will run it as soon as I'm done here. Take it easy on the newb!!! Thanks fellas/ladies![/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]marine02xx[/FONT][/COLOR]

---

### Post by dekinstoke on 2010-08-25
Pretty much stands to reason that 10.04 would have problems with an older machine .... a parallel would be trying to run Windows 7 on a PIII ...

Why not try an older version of Ubuntu? ....8.04 (Hardy Heron I think) would probably be a good choice and perfectly usable still

---

### Post by loren45 on 2010-08-25
I don't think you should be using Ubuntu on an older machine like that. 

I highly recommend Lubuntu. I'm also a linux newb but I've tried several distros and older machines and Lubuntu outperforms them all by far in my experience. (Ubuntu runs like *** with 1/2 a gig ram in my experience) I haven't tried Xubuntu but it seems the general census is that as a "light" distro, its not light enough. 

I've installed Lubuntu on a few machines, on the 4th one I ran into problems but I received a very helpful solution. 

Here is the thread. 

[http://ubuntuforums.org/showthread.php?p=9766910#post9766910](http://ubuntuforums.org/showthread.php?p=9766910#post9766910)

Seriously it consistently runs circles around XP on one of my machines even after doing a fresh install of XP. 

Good luck.

---

### Post by Maverick_Meerkat on 2010-08-25
I was unable to install from the live CD. I ran WUBI and the ISO directly from my HDD. Additionally, I had to use the esc key to boot into safe graphics mode to complete the install. After that, everything booted normally and worked flawlessly. Except of course for the sleep/suspend/resume... which seems to be a problem on many laptops.

---

### Post by GenBattle on 2010-08-25
Ubuntu is the most unstable release of Ubuntu i've ever known with my own hardware.

I would suggest you read my post at:
[http://ubuntuforums.org/showpost.php?p=9766336&postcount=8](http://ubuntuforums.org/showpost.php?p=9766336&postcount=8)

I realize you have tried some of these already, but if you read carefully you will also find some you have not.

To answer some of your other questions:

> Based on my CPU, should I use another Linux OS?
Just to be clear, a CPU is a Central Processing Unit. Retailers mistakenly call your box/case a "CPU", but this is misuse of a technical term. You haven't specified your CPU in the list of specifications in your original post. I would imagine it would be something like a Pentium II or similar. I would suggest a much smaller distribution than ubuntu. Xubuntu uses a much lighter interface system, which may run faster on old hardware. Otherwise i woudl suggest Puppy Linux [http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm) which is ubuntu-based these days, so has the same sort of setup.

> Should I use Linux at all?
That is up to you. At this stage Linux is still very technical. Canonical and Ubuntu have done a great deal to further the usability of Linux, but there is still much resistance to this from some of the more traditional and hardcore components of the  traditional "hacker" community. Some see Ubuntu as an usurper of all their work thus far in progressing GNU/Linux, and criticize them for worrying too much about the users and their perception of Linux, and not enough about the technical aspects of the operating system.

In the end using Ubuntu is your choice, and it is that choice which is why some of us choose Ubuntu, because we are happy to fight our way out of a walled garden or something that is boring/less useful for us. To each their own.

---

### Post by marine02xx on 2010-08-25
Gen Battle,
  Thanks. I loaded Xubuntu 10.04 and got the same results; black screen, no joy. I'll try your fix. I'm thinking it's a graphics card issue. What other choice do I have at this point? Will keep you all posted...

marine02xx

---

### Post by mörgæs on 2010-08-26
> **marine02xx said:**
>  What other choice do I have at this point?

As stated above, trying a few different versions (9.10 first of all) of Ubuntu is a good approach. 

In Ubuntu, new does not mean best. There are four supported versions (10.04, 9.10, 9.04 and 8.04), each with their personality and each an equal candidate for installation.

Before speed optimisations (swapping Ubuntu for Lubuntu and the like) let's focus on getting the standard Ubuntu to work.

---

### Post by marine02xx on 2010-08-26
Thank you. I am currently focused on the Savage4 video card as the culprit. It is old and there appears to be an issue with ANY Ubuntu load recognizing it. I have the Linux drives, but I am unsure on how to upload them. I have tried the GRUB method with no luck. I am not an idiot and consider myself computer literate. Has anyone seen any other work arounds for addressing the Savage4 video cad issue with Ubuntu? Thanks!

---

