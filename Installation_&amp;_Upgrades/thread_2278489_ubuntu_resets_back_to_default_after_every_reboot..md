---
title: "ubuntu resets back to default after every reboot."
date: 2015-05-16
forum: Installation &amp; Upgrades
---

### Post by courtney5 on 2015-05-16
I had to install ubuntu onto my acer aspire one netbook via unetbootin due to a power surge on hub ports not allowing a usb drive to be supported. when the start up menu appears i have two choices, windows xp or unetbootin. when i select unetbootin, it launches ubuntu perfectly and smoothly with out any problems, but if i make any modifications to my preferences and settings such as changing the time or the desktop backround image or even installing adobe flash player..... all of those things get reset back to the default the next time i reboot or restart my computer.. does this have anything to do with the way i installed it using unetbootin? can this be easily fixed? and how do i permanently remove windows xp from my computer? having xp is completely pointless at this time since it is no longer supported and i have fell in love with ubuntu and never wish to use windows again and would like to better utilize the space its taking up on my computer. 



thank you so much! any help would be greatly appreciated!!! 

Courtney.

---

### Post by ian-weisser on 2015-05-16
> **courtney5 said:**
> does this have anything to do with the way i installed it using unetbootin?
Yes.

> **courtney5 said:**
> can this be easily fixed?
No. Ubuntu must be installed using the normal installer. What you did with unetbootin is to install a compressed read-only snapshot image. You can't change that image.

> **courtney5 said:**
> how do i permanently remove windows xp from my computer?
That's part of the normal install process.

What non-USB media can you boot from on this machine? Netboot? SD Card?

---

### Post by courtney5 on 2015-05-19
well, i tried it again with an sd card and now when i try to boot it says file not found or missing file, so at this point i cant even get ubuntu to launch the try me mode.

HELPPPP

---

### Post by sammiev on 2015-05-19
Hi,

Need more info.
Can you boot into Windows at all?
You should be able to get into your Bois and select how your computer boots.
Can you select your sd card or what other options are available?

---

### Post by courtney5 on 2015-05-20
yes, i can boot windows normally but i cant boot anything else.

---

### Post by ian-weisser on 2015-05-20
> **courtney5 said:**
> well, i tried it again with an sd card and now when i try to boot it says file not found or missing file, so at this point i cant even get ubuntu to launch the try me mode.

Are you saying that when you tell your system to boot from the SD card, the system finds nothing on the SD card to boot from?
If so, please link to the step-by-step instructions you followed to create the SD card.

---

### Post by courtney5 on 2015-05-20
The thing is, i am really not sure, I read about ubuntu in a magazine article a few weeks ago and decided it couldnt possibly be that hard to figure out so, with a very limited background in computers i decided to tackle downloading and installing. well, at first i just saved ubuntu to my hard disk and installed unetbootin and went into what i didnt realize was just the sample testing mode. so when i figured out that i had to install it onto an sd or usb i deleted all my ubunt files and reinstalled them onto the sd card, did the same thing with unetbootin but this time seleceted sd instead of hard disk and when i get to the boot screen and select unetbootin, it says missing or invalid files and takes me back to the boot screen where the only working option is windows.

---

### Post by courtney5 on 2015-05-20
if someone could just give me some start fresh directions to go off of so that i could start all over using the sd card would be great! i know where my bois file is and how to get to that but i dont know what to do once i get there. i know how to download and save to my sd card but i dont know what to do from there either, at this point all i want to do is get a functiong linux os on my laptop and never ever look back at windows again! once i used the sample try me mode i got hooked! it was awesome and i just want to be able to save between sessions.

---

### Post by courtney5 on 2015-05-20
i also just came across a network install version on the ubuntu website. does anyone think that this would be more beneficial to me than trying to use unetbootin?

---

### Post by Vladlenin5000 on 2015-05-20
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by courtney5 on 2015-05-20
i can not install via usb stick because everytime i plug one into my device on windows it says power surge on hub port but i used a usb to view images when i was running ubuntu trial mode. so im pretty sure its not my computer its just a windows issue. however i only have the option to use an sd card.

---

### Post by Vladlenin5000 on 2015-05-20
I'm yet to find a notebook (or desktop) that boots from a SD in an internal multi-card reader. Most USB adaptors work but not all.
If you're able to run a live session (trial) then you should be able to install it from the exact some drive therefore I don't really understand why are you complicating things?? Is there something I missed?

---

### Post by courtney5 on 2015-05-20
i cant use a usb stick, it has to be an sd card.

---

### Post by courtney5 on 2015-05-20
i ran from the trial mode and went through the installation process but it still reverted back to default settings every single time i turned on my computer. that is the problem. nothing saves. like the time resets, any custom things i have changed such as my background on the desktop, or even my wifi connection. nothing sticks at all. that is the main issue.

---

### Post by courtney5 on 2015-05-20
and its an sd card adaptor that i am using.

---

### Post by Vladlenin5000 on 2015-05-20
You can use the same device, burn the ISO to it correctly - I already posted the links, other tools can be usual as well - then boot from it, tell it to install and make sure WHERE it is being installed. Ask anything you need before doing that. 

Considering you original post no, you haven't installed. You used a live session booting from a USB made with Unetbootin which is roughly the same as booting from a CD/DVD. Are we clear in this topic or you need more details?

---

### Post by ian-weisser on 2015-05-20
Vladlenin5000's second link in Post #10 works for SD cards.
His advice is sound.
If you have questions, please be as clear as possible. Pictures help, too.

---

### Post by courtney5 on 2015-05-20
okay, when you say to make sure where it is being installed what does that mean? at this point all i know how to do is create a live session in unetbootin, and then when i get to the session i can run the install that pops up on the main ubuntu desktop screen and i went through that process and it said installation complete. so i guess it is installing to the wrong place?

---

### Post by courtney5 on 2015-05-20
okay i am running the universal installer that the second link on vladlennin's post said to use and i just clicked create and it is now 8% so when this process is complete what do i do from there?

---

### Post by Vladlenin5000 on 2015-05-20
At some point you're asked where to install. What do you select there? If you have only one physical drive then that's your choice by default. What else happens? What options have you selected? In another step of the installation process you should be presented with 3 or so options and those depend on whether there's an OS already installed or not...
So, in order to understand what might have gone wrong, we need to know how you really installed/tried to. Or, even better, just boot again in a live session, open a Terminal (CTRL+ALT+T or any other method) and copy/past for accuracy (use right-click > Paste or CTRL+SHIFT+V - instead of the usual CTRL+V - to paste in the terminal):
```
sudo fdisk -l
```
Then select what comes up in the terminal and righ-click > Copy (or CRTL+SHIFT+C) and paste here in your next reply.

---

### Post by Vladlenin5000 on 2015-05-20
> **courtney5 said:**
> okay i am running the universal installer that the second link on vladlennin's post said to use and i just clicked create and it is now 8% so when this process is complete what do i do from there?

At the end you'll have a bootable device pretty much like the one you did with Unetbootin. Likewise, boot from it. 

*Do not (re)install just yet*
*Read my previous post and if iot's not too much to ask post the details-

---

### Post by courtney5 on 2015-05-20
okay, i will do that when this the universal installer finishes. but when i was running the live session and it asked me if i wanted to erase the hard disk and delete windows, i selected that option, and then it gave me a drop down menu to select a location and every time i tried i selected the sd card. but i think where i was going wrong now that i think about it... when it would reboot after the final installation and the boot menu comes up it gives me the options of windows or unetbootin, i was not booting from the sd card. does that sound like the problem? and if so how do i make it boot from the sd card since it was not an option?

---

### Post by courtney5 on 2015-05-20
so, the universal installer has finished. and now i rebooted my computer and i got to the boot menu where it asked me to chtoose how i wanted to boot and windows xp and unetbootin were the only two options. I do not know how to boot from this new universal installer? is it supposed to be listed on the boot menu or do i have to go in and manually find it somewhere?

---

### Post by Vladlenin5000 on 2015-05-20
Truth to be told you're a quite complicated person... Please make it simple!

First of all, and to avoid further confusion, please confirm: That SD you so often mention is the one where you're burning now with the tool? The same you used before with Unebootin?
If so, then you can't install to the same drive you're booting from - and you don't want that!!! **You want to use it to install Ubuntu in your computer's internal drive**. Therefore, you DON'T select it from that dropdown menu you remember, you select your internal drive* (HDD or SSD, doesn't matter). As soon as the installation is done you should remove it. You won't need it any longer.

* If your intention is to have Ubuntu only then the option to "erase and install Ubuntu..." is the correct one.

---

### Post by courtney5 on 2015-05-20
I know, i am quite the complicated person. however i think that has alot to do with i am pulling my hair out with this! I have no idea what i am doing and thought this was going to be just a simple little click of the button type deal but i am now learning that there is far more involved. and now i see where i went wrong, it is the same sd card. so there is my first problem!

---

### Post by Vladlenin5000 on 2015-05-20
> **courtney5 said:**
> so, the universal installer has finished. and now i rebooted my computer and i got to the boot menu where it asked me to chtoose how i wanted to boot and windows xp and unetbootin were the only two options. I do not know how to boot from this new universal installer? is it supposed to be listed on the boot menu or do i have to go in and manually find it somewhere?

How have you booted the installer made with Unetbootin? It's the same way. Usually we use the one time boot menu to select the external drive we just made to be the first boot device... Or we go to the BIOS settings and change the boot order there. Haven't you done that before? Has it booted straight away? If so, it must now boot the exact same way.

And please, actually read what we've been posting, think about it, take note of the questions and answer them if you can, instead of making post after post without waitng for feedback. It makes the whole thing even harder than it already is. This is a forum, not a chat, whatsapp, whatever... A forum and as such posts should be organized with a minimum of logic so outsiders can read it sequentially and *understand* what going on.

---

### Post by courtney5 on 2015-05-20
how do i attach a screen shot to my reply so i can show you what i am looking at right now?

---

### Post by courtney5 on 2015-05-20
> [COLOR=#000000]How have you booted the installer made with Unetbootin? It's the same way. Usually we use the one time boot menu to select the external drive we just made to be the first boot device... Or we go to the BIOS settings and change the boot order there. Haven't you done that before? Has it booted straight away? If so, it must now boot the exact same way.[/COLOR]


Okay, so before when i was booting with unetbootin.. i was getting a black screen, with white letters and i used the arrows to select between unetbootin, or windows. with windows being listed first. now after using this universal installer... i am not seeing anything different. is there supposed to be a new option since i am no longer using unetbootin? i am still seeing the same screen but now when i click on unetbootin i cannot even get a live session anymore it says missing or invalid files. i have never gone into the bios and changed a boot order and do not know how to do so. i am currently looking at the following screen. i attached an image of what it looks like.  [ATTACH]262102[/ATTACH]

---

### Post by Vladlenin5000 on 2015-05-20
Thank you for posting the screenshoot. The old adage must be re-written: Your picture is better than 2.000 word!! :p

Now... [B]Please stop everything you're doing... right... NOW
[/B]Here's why:
1. What you're attempting to do is to install Ubuntu like a regular Windows software with an outdated tool called Wubi. Its purpose at the time it was being developed was to **test** Ubuntu by installing what can be referred to as a "pseudo-dualboot", for clarity sake. Don't do that, tha's not what you want.
2. Installing an OS - *comme il faut - *is not the same as installing something you download in Windows, not even Windows is installed that way. As a matter of fact, Windows installation is pretty much the same process.Here's what you should do: Post here at least the brand/model of your computer (a notebook, I presume). I'll try to find out exactly what key you should press during boot to either access the one-time boot menu or the complete BIOS settings. And yes, you NEED one or the other.

---

### Post by courtney5 on 2015-05-20
Okay, great! I have an acer aspire one  a150 netbook. And im not sure if it matters or not but i have the 10 inch size.

---

### Post by Vladlenin5000 on 2015-05-21
According to the [service manual]("http://tim.id.au/laptops/acer/aspire%20one.pdf") (page 29), this are the keys:

**F2** - BIOS settings
**F12 **- one-time boot menu (ACER names it "multi-boot menu")

You want F12* with the SD connected. If you're using an USB adapter one of the entries should be something like "USB: Generic SD/MMC..." You can first without it connected just to know what are the option there; then booting again with it you immediately see the new entry.

* Start pressing it repeatedly as soon as you see the initial splash screen. The menu I'm referring to usually appears blue over a black background. Navigate the option with cursor keys and enter to confirm.


Assuming everything else is fine it'll - finally - boot the *come il faut*. Then you'll be in a proper live session. Double-click "Install..." on your desktop and follow the wizard. Should be intuitive. 
Now, as I mentioned before, at some point you'll be asked where to install and what kind of installation. You should decide beforehand what do you intend to do: Ubuntu only or dual-boot.
Ubuntu only is the easiest way to install but it'll replace Windows entirely and also delete everything that's stored in the Windows partition(s). ***BACKUP*** everything you need before starting the process, otherwise it'll be too late.
Dual-boot requires planning (and the same backup): You want to shrink the Windows partition in order to have unallocated space to install Ubuntu and you should do that in Windows first, using the disk management tool and allow it to reboot twice to correct logical error. Proceed with the regular installation the same way at this point. Instead of choosing "Erase and install Ubuntu" you'll be choosing "Install alongside" (actual text may vary). All the rest is the same.

---

### Post by courtney5 on 2015-05-21
bad news, when i pulled up f12, the sd card was not an option. there were two options available and both of them took me into a windows launch when i selected them.

---

### Post by Vladlenin5000 on 2015-05-21
> **courtney5 said:**
> bad news, when i pulled up f12, the sd card was not an option. there were two options available and both of them took me into a windows launch when i selected them.

Sorry to hear that... There's no way unfortunately. The drive must be recognized as a bootable device. Assuming it was done correctly - the SD - it should work as long as the BIOS recognizes it as such, but it doesn't.
A regular USB pen should work. Try making one in another computer, if available.

---

### Post by courtney5 on 2015-05-21
well, now i have some good news! Today on a whim i bought a new flash drive and plugged it into my computer and did not get the power surge hub port message and the computer recognized the device just as it should. 


so would i have to delete all the stuff you walked me through last night to start over or can i make a bootable usb the same way you showed me last night without having to delete and re-download anything?

---

### Post by Vladlenin5000 on 2015-05-21
You can make the same way and using the same ISO you already have.

---

### Post by courtney5 on 2015-05-21
I have made great progress. I just pulled up the boot order f12 and booted from the usb. It gave me a menu and I selected try ubuntu without installing. Was this correct?

---

### Post by Vladlenin5000 on 2015-05-21
Yes, that's correct :p.
That's exactly where we should be... In a live session. At this point nothing was changed in your computer. Ubuntu isn't installed, it's merely running from the USB flash drive. You should be able to repeat the process anytime you need/want.

Now it's time for tests and decisions.
By "tests" I mean simply using it in a live session (open programs, confirm internet connection, etc.); if it works fine in a live session it'll work even better when actually installed. I'm sure it works fine in spite of your Aspire One being far from a powerful machine. Its age and common hardware is an advantage, everything should have solid support by now. 
By "decisions" I mean whether to install or not and, should you choose to install then whether or not to keep Windows. Regardless of the decision, make sure you have a good backup of everything you want to keep, just in case, before starting the actual installation.

---

### Post by courtney5 on 2015-05-21
Okay, thank you so much for all your help!!! i have fully installed ubuntu and i completely wiped windows. i love it. it seems so much faster and way more user friendly than windows could ever be! 

agian thank you so much for your help and especially for your patience!!!

---

### Post by Vladlenin5000 on 2015-05-21
Lovely :p

I agree entirely, it is much faster and productive (also user friendly). Happy ubuntuing.

PS - You can now use the thread tools in your first post to mark this one as solved so other may benefit.
PSS - My patience is for those who deserve it ;) (just minutes ago I had to say good-bye and wish good luck to someone who didn't)

---

