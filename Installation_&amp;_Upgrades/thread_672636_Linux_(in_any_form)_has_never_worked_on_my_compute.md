---
title: "Linux (in any form) has never worked on my computer."
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by Mikeyv4198 on 2008-01-19
Okay, I should start from the top. I've used Windows all my life, but as a tech geek I feel compelled to use Linux in some form, just to try it out and see if I like it. However, the computer I currently have has never agreed with me when I try installing Linux. 

My system specs are as follows:

Compaq Presario S6020WM
2.6Ghz Intel Celeron Processor
1GB (512 x 2) DDR SDRAM (I recently upgraded from 512MB)
GeForce FX 5200 Graphics Card

As for the hard drives, I'm not sure the exact specs on them. I have a 60GB Hard Drive that has Windows XP Pro SP2 installed, and a 40GB Hard Drive that I've been using as extra storage, but I formatted to install Linux.

Several months ago, I attempted to install RedHat onto the alternate hard drive, but it wouldn't successfully install for some reason (I can't really remember). A few months after that, I tried installing Fedora 7 to the drive, but after hitting "install" on the boot screen I was confronted with an endless wall of scrolling white text that seemed to repeat itself. This happened every time I tried installing Fedora.

Over the course of last night and today, I've been trying to install Ubuntu (Gutsy), and no matter what I've tried, it won't work. I used the desktop boot disk, checked the hash after download, and checked disc integrity at the boot screen, and everything worked fine. 

I tried installing it with the hard drive connected in various methods (as a slave of my XP Pro hard drive, on CS, as a standalone master, etc.) and every time I booted from the Ubuntu CD, I would get to the boot screen fine, and when I hit "Start or Install Ubuntu" it would bring me to a screen with the Ubuntu logo and an orange bar bouncing back and forth. The bar would eventually disappear and start slowly filling up from the left like a loading bar. This is where the problems started. Every single time, no matter what my settings, the bar would stop in the exact same place (about 4/5 of the way through the Ubuntu circle logo). It would stop there and after a minute my computer stopped making noises. I tried installing in Safe Graphics Mode, as OEM, everything. Nothing worked. I've tried it at least ten times now.

Any help would be amazing. I'm excited to join the Ubuntu community, if my computer would just install it. Keep in mind, I have no hands-on experience with Linux, so I might not understand some of the usual user jargon. I just want to learn :D

---

### Post by EXCiD3 on 2008-01-19
Try adding "noapic" or "nolapic" or a combination of both at the initial menu. I'm not sure if this will help or not, but many HP/Compaq booting issues are/have been fixed by using this, especially using Feisty Fawn.

---

### Post by Mikeyv4198 on 2008-01-19
> **EXCiD3 said:**
> Try adding "noapic" or "nolapic" or a combination of both at the initial menu. I'm not sure if this will help or not, but many HP/Compaq booting issues are/have been fixed by using this, especially using Feisty Fawn.

Where would I do that? Like I said, I have no Linux experience.

---

### Post by EXCiD3 on 2008-01-19
At the menu press F6 and add the parameters.     
You may also want to try these, however they are intended for use on Feisty.
```
noapic irqpoll noirqdebug
```

---

### Post by Partyboi2 on 2008-01-19
To try and get some more info about what might be causing it to stop when you press F6 at the main menu you will see a line  with  > splash change that to ```
nosplash
``` and delete the word > quietand press enter. You will no longer see that orange bar moving, instead you should see a whole lot of text displayed on the screen, when it stops post back what it says.
Have you tried booting in safe graphics option? (option 2 at the main menu)

---

### Post by Ocxic on 2008-01-19
try the alternate cd

---

### Post by wolfen69 on 2008-01-19
also, dont be afraid to try out other distros as well. [www.distrowatch.com](www.distrowatch.com) is a good place to see all the major distros. linuxmint may be worth a try. it's  very newbie friendly.

---

### Post by Mikeyv4198 on 2008-01-19
> **EXCiD3 said:**
> At the menu press F6 and add the parameters.     
You may also want to try these, however they are intended for use on Feisty.
```
noapic irqpoll noirqdebug
```

I just finished trying all of those, I got the same results. 

> **Partyboi2 said:**
> To try and get some more info about what might be causing it to stop when you press F6 at the main menu you will see a line  with   change that to ```
nosplash
``` and delete the word and press enter. You will no longer see that orange bar moving, instead you should see a whole lot of text displayed on the screen, when it stops post back what it says.
Have you tried booting in safe graphics option? (option 2 at the main menu)

Okay, I'll try that out and repost my results. Yes, I have tried it in safe graphics mode, it gave me the same problem.

---

### Post by EXCiD3 on 2008-01-19
> **wolfen69 said:**
> also, dont be afraid to try out other distros as well. [www.distrowatch.com]("http://www.distrowatch.com") is a good place to see all the major distros. linuxmint may be worth a try. it's  very newbie friendly.

Agreed, Ubuntu isnt for everyone. However the large userbase and amazing community is definitely a plus! :)

---

### Post by Mikeyv4198 on 2008-01-19
[IMG]http://i72.photobucket.com/albums/i174/freakshow_4198/IMG_0177.jpg[/IMG]

Okay, I took a picture of my screen when it stopped. Any suggestions?

---

### Post by enchesss on 2008-01-20
Pretty sure that my system has a similar problem. If you wait a couple of minutes it should bring up another error: see my post below. If you find a solution plese let me know.


Posted on debian help forums:


Have successfully installed several debian versions such as pclinuxand mint. Ubuntu is the main version used though and all of these run well on my internal video card.

It is an asus p5gx-mx motherboard (with several bios video settings) with a built in intel 3d chipset and graphics accelerator.

When attempting to install any of these versions with a video card they will not boot. They all lock up and verbose mode says kernel panic not syncing fatal exception in interupt. Have tried nvidia 6200 and ati radeon HD2600 with all deb versions of linux and none work.

winoze works well and have installed card with smooth transfer of drivers and updating to DVI out - works perfectly.

I am keen to figure out the problem here becuase how can windows work so well but debian cant work at all - even live versions lock up or reboot the computer with the fatal exception.

so:

1. what is the syncing error ?

2. Is it a debian fault with the detection procedure of identifying the video card?

3. How can the correct software be installed using the internal video card (so the card can then be installed and booted) or will the next version of deb support video card identification on installation?

Have attempted to install drivers from terminal and also using envy but after putting the card in and booting it locks up again with teh fatal exception.

Ideally though I need to know why the error occurs with the live cds when windows works fine.

Here are the last two procedures that show up after a long wait and then there is a lock up:

[316.496553] EIP: [] native_apic_atomic x0x6/0x10 ss:ESP 0068:c2oe5e64
[316.496730] Kernel panic - not syncing: Fatal exception in interrupt
[316.496845] - (blinking cursor)

Cheers big ears.

---

### Post by Mikeyv4198 on 2008-01-20
I tried running Ubuntu again. It's still giving me trouble. Anyone have any ideas?

---

### Post by EXCiD3 on 2008-01-20
Have you tried different versions of Ubuntu such as Feisty, Gutsy and even Hardy Alpha 3? I agree with enchesss that it looks like you are having a kernel panic and that is why it is locking up.

---

### Post by pietjanjaap on 2008-01-20
Search forum and google with "the name of your motherboard+ubuntu+problem", maybe you have to change something in your bios(setup).

Try bios default, and check everything.
Search for ide/sata make this "native" (not sure if this is the wright name)
Disable networkcard in bios.
Disable everything in bios you do not need.

---

### Post by rosegarden78 on 2008-01-20
I had this problem when I burnt the Ubuntu disc too quickly.  Although the checksum was OK I don't think the pits were deep enough at 16x burn speed.  When I burn an Ubuntu disc at 16x I always burn frozen and corrupted installation discs.

However - when you burn the LiveCD at 4x or the lowest possible speed, you get a perfect installation disc that never hangs on setup.  If the whole batch of discs are bad you might consider asking Ubuntu to send you free discs from the factory.

That's the feeling I get from this thread ... but it could also be hardware compatibility.  I'd stay away from other distros because they're not #1 anymore.  Ubuntu is the best, easiest and most powerful.  Plus you can run KDE and XFCE without a hitch.  There's a reason why Ubuntu is the #1 Linux distribution in the world ...

... if it's hardware compatibility you may send a letter to Ubuntu engineers asking them to include support for your hardware in the next release.  Although Ubuntu runs all my hardware, including Wacom tablet and HP All-In-One, straight out of the box faster and better than Windows.  And I have an IntelGM915 graphics card on an Inspiron 1200 CeleronM and 512MB RAM.

If Ubuntu Gutsy Gibbon 7.10 doesn't work at slow-burn, and neither does the next release of Hardy, I would consider giving up on the hardware at that point.

---

