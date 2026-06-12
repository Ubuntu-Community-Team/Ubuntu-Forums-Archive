---
title: "Need help installing NVidia driver onto 11.10"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by ScientificProp on 2012-02-02
Help. I'm testing / evaluating 64-bit Ubuntu by setting up a USB boot before installing onto my hard drive. I have Ubuntu 11.10 installed, but it didn't recognize the NVidia 520 based graphics card. Searching online I found a .deb file on a PPA site (not sure if terminology is correct, I just learning Ubuntu details). I was unable to install drivers through Additional Drivers since none were listed. I read that I need to install the latest driver to work with the GeForce GT520 based card.
OK. I downloaded the 290.10 driver on a PPA site. I (think) I added the PPA information to the repository listing. I tried to install the driver by opening the .deb file with the Software Center - installation failed (not sure why). Further forum reading suggests that I first need to uninstall the existing Nvidia drivers [is it with code: 
[sudo apt-get remove nvidia-current] 
followed by [sudo apt-get purge nvidia-*]?

Then, install the .deb driver. I assume that either by Software Center or by entering code sudo apt-get update followed by sudo apt-get upgrade is supposed to work.

If it does not work, would I then be without a driver installed which would cause a problem when I tried to reboot. How can I be sure that I can get new drivers installed before removing the existing drivers? [ System Information says that the existing driver is a VESA driver (is that a default ).

For reference: I am installing on an HP Pavillion Media Center PC, model m8100n, with a Zotac GeForce GT520 1MB graphics card installed in the PCI-e slot.

---

### Post by darkod on 2012-02-02
I would recommend visiting the Nvidia website for a driver. You can download the version 290.10 if you read that it's the correct one. Also, usually their website will offer the correct driver according to the card model.

Otherwise, a .deb file should be able to install simply by right-click and select option like Install/Open with Software Centre, or Open with Package Manager, etc, depending on the exact version.

If it's another type of file you might need to install it from terminal. Again, nvidia website would have basic instructions about installation too.

PS. I use ATI so I can't provide more exact support.

---

### Post by ScientificProp on 2012-02-02
Darkod,
I've tried the 1st 2 suggestions; I downloaded a .deb file with driver for 290.10 and I tried installing it with the Software Center. It didn't install. When I read the details, there were some references to devices or stuff it couldn't find. I thought that the Software Center should get what is needed, so does that mean that there is some other issue? For example, did it fail because I didn't uninstall existing NVidia drivers? I'm afraid to uninstall graphics drivers without knowing that I can install new ones, otherwise will I be left with an unusable Ubuntu?

Thanks for responding!

---

### Post by MAFoElffen on 2012-02-02
> **darkod said:**
> PS. I use ATI so I can't provide more exact support.
Whereas I can. Whether ATI or NVidia, I've wriiten down tutorials and tips that include the current workarounds for both ATI and Nvidia's binaries and Ubuntu's debian installation packages.  

In your case:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")** 

[**Installing NVidia Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")

**[Finding the Right NVidia Driver from the Card ID]("http://ubuntuforums.org/showpost.php?p=10910784&postcount=284")** 

PS- I test on Intel, Nvidia and AMD Radaeon... (ATI got bought out by AMD.)
[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by darkod on 2012-02-02
> **MAFoElffen said:**
> Whereas I can. Whether ATI or NVidia, I've wriiten down tutorials and tips that include the current workarounds for both ATI and Nvidia's binaries and Ubuntu's debian installation packages.  

In your case:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")** 

[**Installing NVidia Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")

**[Finding the Right NVidia Driver from the Card ID]("http://ubuntuforums.org/showpost.php?p=10910784&postcount=284")** 
[/SIZE][/COLOR][/SIZE][/COLOR]

And here comes the cavalry... :)

---

### Post by MAFoElffen on 2012-02-02
> **darkod said:**
> And here comes the cavalry... :)
@ Darko-

LOL! Thanks... Been under the weather- Llterally!  Snow, Ice and wind storms... Power outages, etc.  Had to buy 3 power supplies yesterday... revundant server styled = ouch. Have 3 servers up so far, 3 to go.

---

### Post by ScientificProp on 2012-02-02
Thanks MAFoElffen! Looks like I have some homework to do. I quickly reviewed the links you provided; the information looks complete. I must admit, I usually prefer having a better understanding of what commands will do when I enter them, but I won't have time to research all the related commands. I'll enter as instructed and learn in the process. Since the Ubuntu 11.10 I'm working with is on a USB, if a problem develops I can still use my Windows Boot until I get everything sorted. I just need to document everything I do so that I can repeat it when I install Ubuntu onto a hard drive.

I'm not sure if I'll be able to test everything tonight and I'm traveling over the weekend. So, don't take my temporary silence as an indication of lost interest.

Thanks again for your advice!

---

### Post by bogan on 2012-02-02
Hi! **ScientificPro**p.

I Posted a reply to your other Post:" RE: **Driver Problem & several questions to get started w Ubuntu**", giving details for installing the 290.10 nvidia driver, based on what I learned from the help MAFoElffen gave me.

I started, as you are, worried what would happen if  the existing drivers were purged before entering the new  correct ones; but I found my worries were ill founded, the default drivers did all that was necessary.

So don't worry on that account.

Chao! & Good Luck, **bogan**

---

### Post by MAFoElffen on 2012-02-02
> **ScientificProp said:**
> Thanks MAFoElffen! Looks like I have some homework to do. I quickly reviewed the links you provided; the information looks complete. I must admit, I usually prefer having a better understanding of what commands will do when I enter them, but I won't have time to research all the related commands. I'll enter as instructed and learn in the process. Since the Ubuntu 11.10 I'm working with is on a USB, if a problem develops I can still use my Windows Boot until I get everything sorted. I just need to document everything I do so that I can repeat it when I install Ubuntu onto a hard drive.

I'm not sure if I'll be able to test everything tonight and I'm traveling over the weekend. So, don't take my temporary silence as an indication of lost interest.

Thanks again for your advice!
Thanks Bogan.  

@ScientificProp-
Although complete, I understand that there may be questions.  Ask then here or in this forum in my sticky:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

I can translate the "tech'y" into any level from beginning user to programmer.  I can also explain the "between the lines" and what they do.

---

### Post by ScientificProp on 2012-02-02
As far as my "tech'y" level; I've been poking around in computers since before there were PC's. My first computer program was in Tektronix Basic, followed by a Fortran program for a CP/M computer. Mostly worked and programmed computers for scientific work, data acquisition, experiment and process control and data analysis (graphics). Although I've been reading about Linux since I had to stop using OS/2, I'm only just beginning to make time to explore it myself. So, I'm new to the Linux stuff, but not to computers.
@ bogan; from you other post, yes I'm working from a USB stick right now. And you're right, I'm not sure that I can upgrade Ubuntu on a USB. I thought maybe I could since I was able to install a program and it was saved on the USB and was available the next time I booted. That was with Ubuntu 11.04. If anyone knows this won't work - please advise.

I started following MAFoElffen's instructions. The command apt-get install build-essential gcc... produced a few errors, errors while processing linux-image-3.0.0.15-generic and linux-image-generic and linux-generic. It ended with an error code (1).
The next step was the command apt-get install linux-headers-'uname -r' ; this response was <unable to locate package linux-headers...

Are these errors OK? Did I make a mistake typing?

Thanks.

---

### Post by bogan on 2012-02-03
H!!, **ScientificPro**p,

You Posted:>  bogan; from your other post, yes I'm working from a USB stick right  now. And you're right, I'm not sure that I can upgrade Ubuntu on a USB. I  thought maybe I could since I was able to install a program and it was  saved on the USB and was available the next time I booted. That was with  Ubuntu 11.04. If anyone knows this won't work - please advise.**Hopefully**, either **MAFoElffen** or **darkod** - or both - will be able to  confirm just what Driver Installations, or updates via Update Manger, **do**  do when running 11.10 from a LiveCD/USB, and how much survives a reboot.

Edit, later: I just booted from my11.10 Live USB and tried to download the nvidia-29.10.bin driver. It got to one third and halted with an "Not enough space on device". And that is on a non-partitoned 8GB SanDisk USB!! 

You also Posted:> The command apt-get install build-essential gcc... produced a few  errors, errors while processing linux-image-3.0.0.15-generic and  linux-image-generic and linux-generic. It ended with an error code (1). In his magnum opus MAFoElffen explains that errors can be expected from these commands, but not to worry as the intention is to make sure incompatible modules or stray remnants of old nvidia drivers are no longer present, before the correct driver is installed.

*{ I did not include these bits and the purge commands in my procedure in the other post as you indicated there, that no nvidia drivers were installed.* *Though your reference to using 11.04 previously, throws doubt on that assumption.}*

 The last time I ran this particular command I got: "Cant find package 'gcc++-4.5'"; surprising,  but it made no apparent difference.> The next step was the command apt-get install linux-headers-'uname -r' ;  this response was <unable to locate package linux-headers...Try : uname -r and enter the output in the command to replace .....'uname -r'.
ie. if uname -r returns: ```
uname -r 
3.0.0-15-generic 
```the command should read: ```
sudo apt-get install linux-headers-3.0.0-15-generic 
```{ Apologies if I am making this over simplified.]

I fully shared your aversion to using commands I did not understand and had little idea what they mightl do, or how they would do it, let alone what secondary effects they could trigger.
I also tried to keep a record of all the commands I came across, their outputs on my m/cs, and Links to where the info came from. I even set up a Database and SpreadSheet lisiting the Threads and Posts I had started or found useful.  But life is too short, especially when you have passed 87!.

Chao!, **bogan**.

---

### Post by MAFoElffen on 2012-02-05
> **bogan said:**
> H!!, **ScientificPro**p,

You Posted:**Hopefully**, either **MAFoElffen** or **darkod** - or both - will be able to  confirm just what Driver Installations, or updates via Update Manger, **do**  do when running 11.10 from a LiveCD/USB, and how much survives a reboot.

Edit, later: I just booted from my11.10 Live USB and tried to download the nvidia-29.10.bin driver. It got to one third and halted with an "Not enough space on device". And that is on a non-partitoned 8GB SanDisk USB!! 

You also Posted: In his magnum opus MAFoElffen explains that errors can be expected from these commands, but not to worry as the intention is to make sure incompatible modules or stray remnants of old nvidia drivers are no longer present, before the correct driver is installed.

*{ I did not include these bits and the purge commands in my procedure in the other post as you indicated there, that no nvidia drivers were installed.* *Though your reference to using 11.04 previously, throws doubt on that assumption.}*

 The last time I ran this particular command I got: "Cant find package 'gcc++-4.5'"; surprising,  but it made no apparent difference.Try : uname -r and enter the output in the command to replace .....'uname -r'.
ie. if uname -r returns: ```
uname -r 
3.0.0-15-generic 
```the command should read: ```
sudo apt-get install linux-headers-3.0.0-15-generic 
```{ Apologies if I am making this over simplified.]

I fully shared your aversion to using commands I did not understand and had little idea what they mightl do, or how they would do it, let alone what secondary effects they could trigger.
I also tried to keep a record of all the commands I came across, their outputs on my m/cs, and Links to where the info came from. I even set up a Database and SpreadSheet lisiting the Threads and Posts I had started or found useful.  But life is too short, especially when you have passed 87!.

Chao!, **bogan**.
@bogan- Good explaination/good job!  I remember you had that same problem with one of your installs.

On your dl- You didn't mount and chroot to the installed system partition... Instead it tried to go to the LiveUSB's live image, (not setup as a USB drive?).  Look at post 3 of my sticky (instructions for mounting and chroot from a Live Image).

To the OP. 
Lots of similarities. Was a Programmer/Analyst III. Hardware and software. All the above.  Fortran since 1972. Then Assembler, BASIC, PASCAL, C, COBOL, etc. OS'es and applications. Mainframes thru handheld's. Windows since v1.0. Unix since 1988. Etc.

Now I know our similarities and who I'm talking with. lol- I still have my OS/2 in it's box- manuals, floppies and CD's!:)

---

### Post by bogan on 2012-02-05
Hi!, **MAFoElffen**, Thanks for your comments.
You Posted:> On your dl- You didn't mount and chroot to the installed system  partition... Instead it tried to go to the LiveUSB's live image, (not  setup as a USB drive?).  Look at post 3 of my sticky (instructions for  mounting and chroot from a Live Image).I was not trying to add the driver file to the installed system  partition; I was specifically trying out whether the OP could update the LiveUSB with the latest nvidia driver to avoid having to download it each time the installation was used. It appears that it is not possible to add anything, by 'normal' means, as the format is quite different.

Chao!, **bogan**.

---

### Post by MAFoElffen on 2012-02-05
> **bogan said:**
> Hi!, **MAFoElffen**, Thanks for your comments.
You Posted:I was not trying to add the driver file to the installed system  partition; I was specifically trying out whether the OP could update the LiveUSB with the latest nvidia driver to avoid having to download it each time the installation was used. It appears that it is not possible to add anything, by 'normal' means, as the format is quite different.

Chao!, **bogan**.
I don't know that that's going to work that way...

When you start "TRY" you'll see a message that say's "Setting Up The Live Image"- meaning that it sets up a ram disk of it's own determined fixed size, containing the system to run it from and it is non-persistent. I don't think that the media that a  LiveCD/USB is installed on has any relation to the size of that Live Image. That's why it ran out of space trying to install something inside that Live Image.

If it hadn't ran out of space... Or, as far as I know at this point of time, if you created a Custom LiveCD with that driver installed, then you have to mod Equity (the install scripts) for it to actually install. I think the first time we met, I created a custom LiveCD w/ nvidia for you... It boot and ran the Live Image, but the drivers didn't carry over automatically in the install.

If it where set up as a USB drive, then you could install the drivers and it would see whatever space was on your USB device... But it would no longer be a "Install" device.

---

### Post by bogan on 2012-02-05
Hi!, **MAFoElffen**,

Thanks for clarifying things; I had more or less concluded that's how things are, without knowing the specifics.

Really,the solution is quite simple, keep a separate USB Disk with a copy of the latest Driver .run file on it, and copy it over after installation is complete. So the driver could be installed even if the WiFi is not connecting.

Chao!, bogan. and again thanks.

---

### Post by ScientificProp on 2012-02-06
I'm back after the weekend escape and tried to continue installation of the NVidia driver. I think I found an issue trying to install onto a USB booted Ubuntu. When I entered the command to shutdown the X-Session with the command "sudo service lightdm stop". It stopped the GUI, or X-Session, but there was no command prompt to accept further commands. Just a blank screen. I could type and the characters were echoed to the screen, but no system response.
I rebooted the computer from the USB and didn't see a selection to boot into a command prompt. 

Maybe there's a magic keystroke?

@MAFoElffen- I also could not toss my OS/2 disks.

Thanks.

---

### Post by MAFoElffen on 2012-02-06
> **ScientificProp said:**
> I'm back after the weekend escape and tried to continue installation of the NVidia driver. I think I found an issue trying to install onto a USB booted Ubuntu. When I entered the command to shutdown the X-Session with the command "sudo service lightdm stop". It stopped the GUI, or X-Session, but there was no command prompt to accept further commands. Just a blank screen. I could type and the characters were echoed to the screen, but no system response.
I rebooted the computer from the USB and didn't see a selection to boot into a command prompt. 

Maybe there's a magic keystroke?

@MAFoElffen- I also could not toss my OS/2 disks.

Thanks.
If you start in recovery from the grub menu and choose "root"... it will drop you down to a root prompt with root privileges.... You could also edit the kernel boot line in grub with "single" as an option... Detailed instruction for that are linked from Post #2 of my sticky in this forum.

---

### Post by bogan on 2012-02-07
**Hi!, ScientificProp**,
You Posted: >  When I entered the  command to shutdown the X-Session with the command "sudo service lightdm  stop". It stopped the GUI, or X-Session, but there was no command  prompt to accept further commands. Just a blank screen........
Maybe there's a magic keystroke?The magic Keystrokes are: Ctrl+Alt+F1  or Ctrl+Alt+F2.

Afterwards, Ctrl+Alt+F7 will [should] return you to  the graphics screen.
> I could type and the characters were echoed to the screen, but no system response.This suggests there was something else still running in the terminal, but it would still be worth trying the above, as Ctrl+Alt+F1 may show you what is hanging up, whilst Ctrl+Alt+F2 should give you a tty2 login prompt.

Chao!,** bogan**.

---

### Post by ScientificProp on 2012-02-07
Thanks bogan, I'll try that approach, but I'm not optimistic. I'm beginning to think it's because I'm working from a USB boot. I didn't expect it'd be so time-consuming confirming hardware compatibility before doing a full install. After the video drivers, then I still need to get my printer working (which was automatic when I did a live boot of 10.04).
In addition to checking hardware compatibility, I think it'd be a good idea to have a working USB boot as a backup in case problems develop. I'd also like to make a USB boot for my daughter in case her Windows laptop locks-up while she's at college and a big assignment is due.

I'll try Ctrl+Alt+F1 or F2.

---

### Post by bogan on 2012-02-07
Hi!, **ScientificProp**,

When you get that failure to respond to keystrokes in a Terminal, 'q' or 'Ctrl+c' will often close the offending still-running command, and leave the Terminal prompt active.

Whereas, although Ctrl+Alt+Del sometimes does so, it also risks closing down everything.

Good Luck.
Chao!,** bogan**.

---

### Post by MAFoElffen on 2012-02-07
> **bogan said:**
> **Hi!, ScientificProp**,
You Posted: The magic Keystrokes are: Ctrl+Alt+F1  or Ctrl+Alt+F2.

Afterwards, Ctrl+Alt+F7 will [should] return you to  the graphics screen.

This suggests there was something else still running in the terminal, but it would still be worth trying the above, as Ctrl+Alt+F1 may show you what is hanging up, whilst Ctrl+Alt+F2 should give you a tty2 login prompt.

Chao!,** bogan**.
This also may suggest a graphics driver problem or that it's having a problem going from a graphics driver mode to the underlying graphics mode in tty7 that the virtual sessions in tty1 through tty6.  Mine is tty 1-6 & 8-12... with tty7 as Graphical.

That kind of problem will look scrabbled or get a black screen when switching to a virtual session or sometimes when shutting down (during the exit plymouth splash)...

First Concentrate on getting a working driver in the normal tty7 session.  If after that is successful, if it still has a problem going between virtual sessions, then tell me and I'll give yo instructions to correct that (which will be in grub).

---

### Post by bogan on 2012-02-08
**@MAFoElffen**, Hi! As part of what I describe below, running: ```
sudo apt-get remove  --purge nvidia-*
``` it removed nvidia-common; all the other nvidia-* files it looked for were 'not installed', but it also removed ubuntu-desktop.
 
Is that normal? I do not remember seeing it before.
 It does not seem to have made any difference to the Unity Desktop.

Also, I have seen a couple of other threads where it appeared that Fglrx ATI drivers - or remnants of them were interfering with nvidia drivers; and purging them cured things. In view of the error messages I got, is it possible that the ScientificProp's problems are related to a similar attempt to use Additional drivers?

Hi!, **ScientificProp**,

You Posted: P#1>   I'm testing / evaluating 64-bit Ubuntu by setting up a USB boot before installing onto my hard drive. and P#11 >  yes I'm working from a USB stick right now. And you're right, I'm not sure that I can upgrade Ubuntu on a USB. I thought maybe I could since I was able to install a program and it was saved on the USB and was available the next time I booted. That was with Ubuntu 11.04. If anyone knows this won't work - please advise. My Posts up till now have been somewhat confused - as I have been - from my failing to distinguish between creating a LiveUsb and the possibility of updating it or copying correct driver files to it; with, on the other hand, Installing 11.10 on a bootable USB memory stick and updating it and installing drivers in it.

I can now confirm that what you want to do is definitely possible, as  I have just finished creating a fully up-to-date 11.10, 3.0.0-15 8GB USB, with the NVIDIA 290.10 driver installed and the Grub menu customized. 

I suspect, at least some of the troubles you have been having, are because your USB is not big enough. The "How to avoid Wubi & Install Ubuntu on USB drive" Thread,
[http://http://ubuntuforums.org/showthread.php?t=1650699&page=4]("http://http//ubuntuforums.org/showthread.php?t=1650699&page=4")
in the Tips and Tutorials Forum, implies that a 4Gig USB will allow the installation of 10.04 LTS, with a Swap file of 512MB and 1GB freespace. Whereas the 11.10 Installation instructions say "AT Least 4.4GB".

My first attempt, with a 3.5GB partition failed at about 3/4 through the installation, with no error messages, it just quit and froze.

Second attempt with an 8GB Stick; 4.5GB for Ubuntu, 2GB Swap file and a 1GB Switch file (to allow the easy copy/pasting of files - eg Nvidia driver .run file - between installations,) went through without problems.
BTW: mine is a 32bit installation.
My nvidia GT520 video card even worked OK with the nvidia-common included driver. The driver offered from Additional Drivers, nvidia-current, v280.13, showed "Not Activated"; but when I clicked 'Activate', it downloaded it but the installation failed.[ jockey log showed a mass of failed find and load messages, including a lot for Fglrx ATI/AMD drivers, which I have never had anything to do with.]

The NVIDIA 290.10 .run file installed with no problems, except, as it was loading from the USB2.0 drive, not from Ram, it seemed very slow.

After updating more than 320 packages, but before installing and running Gparted, Synaptic Manager, Grub Customizer and Gnome-fallback, I had just over 1GB free space in the Ubuntu partition. So with 11.10, a 4GB USB Stick would be very tight - no space for a Swap file.

BTW: I had a scare in the middle of updating, when my Monitor showed a 'No Signal' message, and I got a black screen. No mouse cursor, no response to keystrokes. About 3 minutes later, I was about to abort when I Clicked 'Enter' and a Window opened requiring a password, and it returned to normal display.!! - Big Sigh of relief!!

Clearly what had happened was that the default Screen Saver time-out had passed, and as there was no ScreenSaver set up, it gave a BLack Blank Screen. The failure to recover with Mouse movement clicks or keystrokes is a known bug.

So don't give up, there is hope yet,!!

Chao!, **bogan**.
Edit: Link added.

---

### Post by MAFoElffen on 2012-02-08
> **bogan said:**
> **@MAFoElffen**, Hi! As part of what I describe below, running: ```
sudo apt-get remove  --purge nvidia-*
``` it removed nvidia-common; all the other nvidia-* files it looked for were 'not installed', but it also removed ubuntu-desktop.
 
Is that normal? I do not remember seeing it before.
 It does not seem to have made any difference to the Unity Desktop.

Also, I have seen a couple of other threads where it appeared that Fglrx ATI drivers - or remnants of them were interfering with nvidia drivers; and purging them cured things. In view of the error messages I got, is it possible that the ScientificProp's problems are related to a similar attempt to use Additional drivers?

Hi!, **ScientificProp**,

You Posted: P#1 and P#11 My Posts up till now have been somewhat confused - as I have been - from my failing to distinguish between creating a LiveUsb and the possibility of updating it or copying correct driver files to it; with, on the other hand, Installing 11.10 on a bootable USB memory stick and updating it and installing drivers in it.

I can now confirm that what you want to do is definitely possible, as  I have just finished creating a fully up-to-date 11.10, 3.0.0-15 8GB USB, with the NVIDIA 290.10 driver installed and the Grub menu customized. 

I suspect, at least some of the troubles you have been having, are because your USB is not big enough. The "How to avoid Wubi & Install Ubuntu on USB drive" Thread,
[http://http://ubuntuforums.org/showthread.php?t=1650699&page=4]("http://http//ubuntuforums.org/showthread.php?t=1650699&page=4")
in the Tips and Tutorials Forum, implies that a 4Gig USB will allow the installation of 10.04 LTS, with a Swap file of 512MB and 1GB freespace. Whereas the 11.10 Installation instructions say "AT Least 4.4GB".

My first attempt, with a 3.5GB partition failed at about 3/4 through the installation, with no error messages, it just quit and froze.

Second attempt with an 8GB Stick; 4.5GB for Ubuntu, 2GB Swap file and a 1GB Switch file (to allow the easy copy/pasting of files - eg Nvidia driver .run file - between installations,) went through without problems.
BTW: mine is a 32bit installation.
My nvidia GT520 video card even worked OK with the nvidia-common included driver. The driver offered from Additional Drivers, nvidia-current, v280.13, showed "Not Activated"; but when I clicked 'Activate', it downloaded it but the installation failed.[ jockey log showed a mass of failed find and load messages, including a lot for Fglrx ATI/AMD drivers, which I have never had anything to do with.]

The NVIDIA 290.10 .run file installed with no problems, except, as it was loading from the USB2.0 drive, not from Ram, it seemed very slow.

After updating more than 320 packages, but before installing and running Gparted, Synaptic Manager, Grub Customizer and Gnome-fallback, I had just over 1GB free space in the Ubuntu partition. So with 11.10, a 4GB USB Stick would be very tight - no space for a Swap file.

BTW: I had a scare in the middle of updating, when my Monitor showed a 'No Signal' message, and I got a black screen. No mouse cursor, no response to keystrokes. About 3 minutes later, I was about to abort when I Clicked 'Enter' and a Window opened requiring a password, and it returned to normal display.!! - Big Sigh of relief!!

Clearly what had happened was that the default Screen Saver time-out had passed, and as there was no ScreenSaver set up, it gave a BLack Blank Screen. The failure to recover with Mouse movement clicks or keystrokes is a known bug.

So don't give up, there is hope yet,!!

Chao!, **bogan**.
Edit: Link added.
Removed ubuntu-desktop?  That's a strange one...

Like I said- You "can" install nvidia to a USB drive, whether a real drive in an external closure connected via USB or a USB key... as they are basically treated as a USB Mass Storage devices. (Phones slip in there also).  Live Images are a little different and treated differently...

---

### Post by ScientificProp on 2012-02-09
OK, Thanks to Bogan and MAFoEllfen, I think my initial mission is accomplished and I've a better appreciation for what I was trying to do.
First, bogan's suggestion to use the hot-key sequence to initiate a full-screen command prompt session worked. I still had to shut down the X-session with the command "sudo service lightdm stop", but this time the command prompt was still working. I verified that the downloaded driver file (NVIDIA....run) was still executable and attempted running it.

Since I'm running from a USB drive created with the Startup Disk Creator and from a try without intalling boot, I had to run the file thus, "sudo sh NVIDIA-Linux-x86_64-290.run". It installed sucessfully. Then I restarted the X-session with "sudo service lightdm start" and was also to switch back to the GUI. It took a couple tries to find where to set the screen resolution. Manually, for some reason Ubuntu is not detecting my 22" LG Flatron LCD monitor (connected with DVI connector).

I verified that the driver and higher resolution setting are active after I reboot from the USB and try Ubuntu again (i.e. without install to hard drive).

So, now I can check out some other aspects of Ubuntu while I decide on the installation configuration I'd like. I'll probably do my taxes before try installing Ubuntu on to the computer. I still haven't figured out how to 'turn-on' Unity, or to verify that it is active. All I can verify is that I have a side panel with icons to launch programs, the Launchbar?

So now in retrospect, maybe I would have been better off to try installing to a USB drive rather than a USB Live boot? I have a 16BG USB drive. One possible consequence I noticed is that the Live boot install from a USB didn't seem to handle Upgrades so well, (did not find root?).

Ultimately, when I install I'll probably add a 2nd hard drive rather than risk messing up the existing hard drive with Windows installed. I saw a recent recommendation of using 4 partitions to setup Ubuntu; /, root, swap and home.

Thanks again.

---

### Post by bogan on 2012-02-10
Hi! ScientificProp,

You Posted:>   I still haven't figured out how to 'turn-on' Unity, or to verify that  it is active. All I can verify is that I have a side panel with icons to  launch programs, the Launchbar? Until you get used to it, it can be quite difficult to tell if Unity is running properly or not. 
One way is to  Alt+Right-Click, on the top bar. If you get a drop-down menu with an option to 'Create New Panel' then full 3DUnity is not running.

There are commands to 'turn-on' Unity, but normally it is done by selecting 'Ubuntu' at the GUI login-screen.
Clicking the 'Gear' Icon will give a drop-down menu.
With a full install, if you have selected 'Auto Log-in', you will only get to see this by booting fully to the GUI screen, and then selecting 'Log-Out...' from the Shut-Down Menu, top-right.

If You are logged in to 'Ubuntu' you are using 3D Unity, and running ps will give you something like this: with each instance of 'unity' highlighted:```
alan@alan-MS-7616:~$ ps ax | grep unity
 2133 ?        S      0:00 /usr/bin/unity-window-decorator
 2136 ?        Sl     0:00 /usr/lib/unity/unity-panel-service
 2203 ?        Sl     0:00 /usr/lib/unity-lens-applications/unity-applications-daemon
 2205 ?        Sl     0:00 /usr/lib/unity-lens-files/unity-files-daemon
 2207 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-music-daemon
 2239 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-musicstore-daemon
 2329 pts/0    S+     0:00 grep --color=auto unity
alan@alan-MS-7616:~$ 
```If You are logged in to 'Ubuntu 2D' you are using a less demanding version of Unity, you will still get a similar LaunchPad on the left, but it can not be edited as can the 3D Unity one, except for content; and running ps will give you something like this:
```
alan@alan-MS-7616:~$ ps ax | grep unity
 2593 ?        Sl     0:00 unity-2d-panel
 2594 ?        Sl     0:01 unity-2d-launcher
 2670 ?        Sl     0:00 /usr/lib/unity/unity-panel-service
 2806 pts/0    S+     0:00 grep --color=auto unity
alan@alan-MS-7616:~$ 
```If You are logged in to Gnome Classic, and choose to run Unity2D-Launcher, you will still get a similar LaunchPad, but you are not using 3D Unity, and will have the Classic Menu headings in the top bar; running ps will give you something like this:
```
alan@alan-MS-7616:~$ ps ax | grep unity
 3140 ?        Sl     0:01 unity-2d-launcher
 3281 pts/0    S+     0:00 grep --color=auto unity
alan@alan-MS-7616:~$
```If You are logged in to Gnome Classic alone, you are not using Unity; If You are logged in to Gnome  it will show "Activities" in the top bar, and in both cases, running ps will give you  just the ps instance thus: 
```
root@alan-MS-7616:/home/alan# ps ax | grep unity
 5094 pts/0    S+     0:00 grep --color=auto unity
root@alan-MS-7616:/home/alan# 
```BTW: the digits in the third column show the actual percentage CPU usage at the time for each app.

I won't comment here on your other points.
Chao!,** bogan.**

---

### Post by ScientificProp on 2012-02-10
Thanks bogan, good information that'll help me get started with the GUI and have some idea what's running. If I interpret the forum procedures correctly, I can mark this thread as solved.

Scientific Prop.

---

