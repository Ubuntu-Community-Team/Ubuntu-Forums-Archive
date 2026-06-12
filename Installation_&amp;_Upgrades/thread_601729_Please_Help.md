---
title: "Please Help"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by marcopolo1981 on 2007-11-03
Hi,
 I first turned to Ubuntu only a few months ago, so I'm still very new to it and find myself a bit stuck.
I originally installed Fiesty on a Compaq Presario PC with very few problems - the only ones being I had never installed ANY OS before so had a couple of confusing moments. Still, once installed, I was extremely happy with it, finding myself wondering why anybody sticks to Windows - or even worse, actually going out and buying a copy!!
Well anyway, to cut a long story short, I recently recieved a Dell Inspiron 1520 laptop along with a mobile phone contract. It is currently on Vista Basic, 1 Gig of RAM and a Celeron M Processor. It runs rather slow, and I don't like Vista at all. I tried to install Ubuntu but failed time and time again. I don't know what I'm doing different. I did manage to get it started up to find I couldn't connect to the internet wired or wirelessly, had no sound at all, only one of the USB ports worked at a time (there are 4 in total), and the mousepad wouldn't work. I am very disapointed with having to reinstall Vista, but I need a usable machine.
If there are any genius's out there that could point me in the wright direction to have ANY Linux OS fully functional on my laptop, they would find a friend for life!!
Thanks in advance for tips/help.
Mark

---

### Post by marcopolo1981 on 2007-11-03
Ps...

If applicable, an Idiots guide to installation of said OS would also be appretiated.
Thanks again
Mark

---

### Post by cuby on 2007-11-03
Hello,
You tried to install Feisty or Gutsy?

---

### Post by marcopolo1981 on 2007-11-03
It was Fiesty I used. Is there a difference between them?

---

### Post by cuby on 2007-11-04
Gutsy (7.10) is newer. Some recent hardware may work better with it. 
Try it.

---

### Post by candtalan on 2007-11-04
It sounds like you are installing ubuntu into a clean machine - with vista and all partitons deleted? Is this true?
If so, does the live CD work well before installation?
Note: it is highly recommended to at least use the live CD menu option 'check the CD'  before install to verify the CD can be read correctly in the target drive.

With this done ok, does the ubuntu installation go smoothly?

---

### Post by marcopolo1981 on 2007-11-04
I have used the live cd versions, the alternate install versions, fiesty and gutsy. The live cd's had exactly the same problems as the alternate installs. Also, Ive tried clean installation onto a complete hard disk, I tried to upgrade from fiesty to gutsy via apt get, - but had no internet connection. I tried leaving Vista on one partition and ubuntu on a second - but still the same results. I've also tried Xubuntu, Edubuntu, Kubuntu, PCLinux, Damn Small Linux, Damn Small Linux Not, and Ubuntu CE to no avail.
I am totally baffled by it all and don't know what else to try. Thanks for all your replies. I'm not ready to give up yet, so if you have any more ideas, please keep them coming.
Thanks again
Mark

---

### Post by candtalan on 2007-11-05
Well done for your persistence, and sorry to hear of your problems!
Your earlier compaq Feisty install will have given the idea about what to expect generally of course, however, at this stage with a problem it will be best to check on some details:

Are any of the CDs actually booting - so that you see an initial menu within a few seconds after turning the machine on when the Live CD is in the drive? 

If they are not booting, then either the CDs have been burned wrongly - (not as an 'Image' but making an iso) or your BIOS may be set to boot only from the hard drive first and not from the CD drive.

In the initial boot menu with the Ubuntu CDs, you should see an option to 'check the CD' or similar. This is worth doing because it will confirm that the CD is good *and* can also be read fully by the CD drive in question.

Are the Live CDs running successfully?
At what exact stage do you begin to see any problem?
What can you see on the screen, particularly any messages or error messages?

Note - if the CDs are not booting: 
Where did the CDs come from, did you burn them yourself? What do you see on the CD in a (windows) machine when you browse the CD? Please be aware that the downloaded iso files for these live and install CDs are already iso files. They are 'images' of the final CD and most windows users will have burning software which expects to create its own iso files, not be given one ready made. The burning process is to 'Burn an Image' or similar and will probably be in a menu somewhere, you may have to look hard for it. A burning process to create an iso CD will not be correct!!

If the burning process is correct, and the CDs do actually boot in some machine somewhere, then the BIOS may not be set to boot from the CD drive. in this case you would need to enter the BIOS settings and carefully change the Boot priority sequence to be CD first, then hard drive second or last. If the bios is set to boot from the CD drive first and still they are not booting, none of them, I would suspect the CD drive in some way, because you are trying so many different CDs - Having said this though, it is possible that you are creating the CDs incorrectly.

---

### Post by marcopolo1981 on 2007-11-05
candtalan;
Yep, persistant is my middle name! 
All the disks I use, I burned myself. The thing is though that the all work perfectly in my Presario. Just to be sure though, I burned new copies in case the discs had been damaged at all.
Also, I have had Ubuntu on the Dell laptop, only there are no drivers installed, rendering my beloved new machine as useful as a glorified typewriter and picture viewer. 
When the discs first go in and I power up, it automatically boots via disc. I didn't have to change that setting at all. I get the splash screen to install/boot live disc. Live cd has exactly the same problems as complete install. I have used the disc checking option and everything is good, but I knew that because they worked perfectly on Presario. I don't get error messages, only that nothing works. I'd prefer error messages coz at least I could look them up to find a solution.
I think the problem is down to the machine being so new and all the hardware was built for Vista drivers. I reverted it to XP to test this theory and I had to manually search online at Dell support for Dell Inspiron XP drivers for everything down to the sound drivers. MS auto update couldn't find the neccessary drivers. Eventually, I had it fully functional. But still, I'm using MS rubbish when I want Ubuntu. In installing Vista and XP, it shows that theres nothing wrong with the disc drive either.
I believe Ubuntu is going to release Hardy Heron In the new year, so I'm Hoping that is going to have all the basic drivers to get me online at least so as I can use apt get for the rest. I'll keep trying for the time being, but I'm not quite so hopeful now.
Mark.
Ps I really do appretiate your suggestions. Thank you

---

### Post by marcopolo1981 on 2007-11-05
Ok, I've done some sniffing around at Dell's site and found a new lead. Dell have remastered Fiesty for some of there notebooks - but not specifically for 1520. The closest match is 1505, but surely they can't be that different?? I'm currently downloading the iso. As long as it will let me get online wirelessly and have sound, I can live with the rest being out of action for the time being. In fact, even the sound isn't all that important at the moment. Will keep you posted.
Mark

---

### Post by phrostbyte on 2007-11-05
Cool, thanks for the update. If you also have a chance please let us know what hardware the machine has internally if possible.

---

### Post by candtalan on 2007-11-06
> 
The thing is though that the(y) all work perfectly in my Presario.

Yes so you are confident the CDs are ok in themselves, however, the additional check in the *actual* target laptop also verifies that the known good CD can actually be read fully by the unknown CD drive.
> 
I have had Ubuntu on the Dell laptop, only there are no drivers installed, rendering my beloved new machine as useful as a glorified typewriter and picture viewer. 

(which ubuntu version was this?)
When ubuntu was on the Dell, note that the video chip *was* recognised and the correct video driver was used automatically, because you could see the display normally. This is useful because the same video driver will be needed when you use ubuntu 7.10. And you could identify it if necessary by noting it when you have ubuntu on the Dell as you did earlier.
> 
When the discs first go in and I power up, it automatically boots via disc. I didn't have to change that setting at all. I get the splash screen to install/boot live disc.

good, so it boots ok
> 
I have used the disc checking option and everything is good

great, so your dell laptop 1520 CD drive is reading the full CDs ok, that is important.
> 
I don't get error messages, only that nothing works

I do not understand what 'nothing works' means. Do you see a running ubuntu desktop where things dont work, or a simply a blank display with a flashing cursor, or a totally blank display with no flashing cursor, or a command line prompt on an otherwise blank display or what?. 

> 
I think the problem is down to the machine being so new and all the hardware was built for Vista drivers.

The hardware is new, however, vista drivers are *not* used when you run ubuntu, so do not worry. Ubuntu looks at the hardware, and will get the correct driver from its own software or kernel - or at least, it should! 
> 
In installing Vista and XP, it shows that there's nothing wrong with the disc drive either.

good so it looks like your hardware is probably all ok

FWIW I think I have a similar problem (which I solved) on my dell inspiron 1100 with ubuntu 7.10. If I use the live CD it boots and works for a while then ends up with a totally blank (black) display.
If I try again and choose the Safe Graphics option, a similar thing seems to happen, however, it actually does get to a command line prompt on the blank display. Then I can edit the necessary file and see that it has just chosen the incorrect video chip driver name, so I change the name, and can then get a perfect display and system!  If you can help me understand what you actually see - as asked above - it would be useful.

> 
I believe Ubuntu is going to release Hardy Heron In the new year, so I'm Hoping that is going to have all the basic drivers to get me online at least so as I can use apt get for the rest. I'll keep trying for the time being, but I'm not quite so hopeful now.
Mark.
Ps I really do appretiate your suggestions. Thank you
No problem, glad to try to help. I would be hopeful even for this version. Let us know what you see on the display as asked above.
And also try the safe graphics option (and talk about what you see on the display too?

---

### Post by marcopolo1981 on 2007-11-06
candtalan,

_***The things that don't work are:***_

Mousepad - I have to use an external mouse.

Sound - Neither the system sound or the head phone socket (Says no sound hardware installed).

Wlan card - Says none installed.

Lan card  - can't connect at all, though does recognise that it is present.

Only one of the 4 USB will work at a time - but that is used by the external USB mouse (It works in all USB ports, but not if my cam, external HDD is attached).

Built-in mic  -  Doesn't recognise its presence.

Mic socket - Doesn't recognise its presence.

None of the multimedia hotkeys , play, pause, stop or skip. (re. Sound keys, can't be sure as can't use sound anyway)

_***Things that DO work:***_

Graphics - Have full resolution at what I think is the same as when running Vista/XP.

Keyboard - All exept Hotkeys (see above).

So as you can probably guess, I have a glorified typewriter! I can use is for Open Office apps and viewing photos, but nothing more because movies need sound and web needs internet access. Like I said before though, I can live without everything but the internet. If I can get the WLan to work I'll be able to work on the Dell and carry on using Presario for entertainment.
[U][I][B]
Update on the Dell Ubuntu Installation[/B][/I][/U]
Had exactly the same problems as the other live cds. Nothing worked still. But when I tried to actually install to hard disk, it gets to 78% them stops, saying that the disc may have an error and to try burning image at lower speed. But when the disc was checked, it said it was ok? Well,  I'm going to try a lower speed burn next.

The disc checks have been done in both machines and all ok. 
The versions used are 7.04 and 7.10, on Xubuntu, Ubuntu, Kubuntu, Ubuntu CE. The version that fully installed successfully (even though limited) was Ubuntu 7.04 Live cd. None of the others get more than 30% complete on the install process.

phrostbyte, I don't know off hand, but I will get back to you.

Wish me luck please.
Mark

---

### Post by marcopolo1981 on 2007-11-06
phrostbyte, I used an app called DriverMax to get a driver report within Vista. I assume this is showing what you asked for, please let me know if you need more info.

Standard 101/102-Key or Microsoft Natural PS/2 Keyboard, 6.0.6000.16386, 6-21-2006, Microsoft, Unsigned

SigmaTel High Definition Audio CODEC, 6.10.0.5609, 9-7-2007, SigmaTel, Signed

Conexant HDA D330 MDC V.92 Modem, 7.59.0.0, 11-16-2006, Conexant, Signed

Ricoh Memory Stick Host Controller, 6.0.1.4, 11-14-2006, Ricoh Company, Unsigned

SDA Standard Compliant SD Host Controller, 6.0.6000.16478, 6-21-2006, Microsoft, Unsigned

Ricoh MMC Host Controller, 6.0.1.4, 11-14-2006, Ricoh Company, Unsigned

Ricoh xD-Picture Card Controller, 6.0.1.5, 11-14-2006, Ricoh Company, Unsigned

Broadcom 440x 10/100 Integrated Controller, 4.60.0.0, 11-21-2006, Broadcom, Signed

Dell Wireless 1390 WLAN Mini-Card, 4.102.15.61, 12-19-2006, Broadcom, Signed

Intel(R) ICH8M LPC Interface Controller - 2815, 8.3.0.1013, 2-28-2007, Intel, Signed

Intel(R) ICH8 Family PCI Express Root Port 1 - 283F, 8.3.0.1013, 2-28-2007, Intel, Signed

Intel(R) ICH8 Family PCI Express Root Port 2 - 2841, 8.3.0.1013, 2-28-2007, Intel, Signed

Intel(R) ICH8 Family PCI Express Root Port 4 - 2845, 8.3.0.1013, 2-28-2007, Intel, Signed

Mobile Intel(R) PM965/GM965/GL960 Express Processor to DRAM Controller - 2A00 , 8.2.0.1000, 9-15-2006, Intel, Signed

Mobile Intel(R) 965 Express Chipset Family, 7.14.10.1272, 5-8-2007, Intel Corporation, Signed

---

### Post by marcopolo1981 on 2007-11-06
This is step by step detail of what I'm getting on my Dell while trying to install the newly burned disc for Ubuntu on Dell.


Start up and boot from disc = fine

Use check disc facility = all good

Reboot from disc = ok

Select Install/Start Ubuntu in vga mode= works and now got the loading image

ALL STOPPED.   Screen gone blue with error message.  

Message;  Failed to start the x server. It's likely that it's not set up correctly. Would you like to veiw the x server output to diagnose the problem? (I'll say no because I haven't got a clue what it is.)
Before I selected anything, some sort of script has appeared over the top of the error message saying:
bcm43xx_microcode5.fw error and has been repeated.


Safe mode returns the same errors.

Worked better with the fast burned disc!
Note, the first disc was burned at 4x (max on this drive for dvd) and the new disc was burned at 3x (min on this drive for dvd).

Back to the drawing board then.
M

---

### Post by marcopolo1981 on 2007-11-09
Update:

Failed on every hurdle on the Ubuntu scene and have decided to have a break for a while. (I've had Dell for nearly 3 weeks and done nothing but keep trying to get Ubuntu to work and try various other OS's)
I have tried the newest version of OpenSuse 10.3 and everything but WLan worked straight from the install. It's not my favourite OS, but it is far better than Vista and it is fully usable while using ethernet cable. 
Did more research into the Wlan situation and apparently I'm not the only having problems with Dell 1390 chip. I followed instructions on how to use ndiswrapper to install the correct firmware, but I'm obviously not that good with the command line.
I looked into what other non-command line users had done and most changed the chip to an Intel Pro/Wireless 3945a,b,g and it worked like plug and play.
It should be the same with Ubuntu, but I like having sound, mousepad and an option to use ethernet for downloading, and all 4 USB ports functional at the same time. Maybe the next release will be more compatible. If so, I'll definately be coming back to Ubuntu!
Thanks again
Mark

---

### Post by Rev60073 on 2007-11-18
Maybe try Fedora :popcorn:

Before installing, I think it's a good idea to try the live CD for a while and see what are your compatibility issues and such, and decide if you wanna install it or not afterwards.

---

### Post by marcopolo1981 on 2007-12-01
Final Update.

I downloaded the alternate install disc this morning direct from ubuntu's home page. I thought I'd have another go. By 5pm, I had managed to Install direct to the hard disk, although it did take 4 attempts! Anyway, the new intel wifi worked immediately, all 4 usb ports work at the same time, ethernet works, well virtually everything but sound! 
I looked up some posts regarding the sigmatel gadget and found a list of solutions. It was the second attempt that worked, so all in all, I'm over the moon!
And to top it all off, Media direct works too! I had to leave a tiny vista partition for that tho.
I can't remember what thread the sound fix was in, but if anybody else is having sound trouble that comes across this post, use the search engine from ubuntu forum page.
Thanks all
Mark

---

