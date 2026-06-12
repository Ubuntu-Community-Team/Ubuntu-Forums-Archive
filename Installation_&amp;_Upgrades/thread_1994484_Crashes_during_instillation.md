---
title: "Crashes during instillation"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by Revv on 2012-06-02
Hows it going?

I have an older laptop that I am trying to install ubuntu on because the version of windows xp that was on it died and can't be recovered. So the computer has no operating system and doesn't ever get past the BIOS screen because it says no OS detected. Its a 3Ghz P4 processor, 1gb ram, 120gb HDD space and an ATI Radeon X800 video card.

I am trying to instal the newest version of ubuntu on it (12.04) but every time the process starts it only gets to the first purple loading screen. At this point it shuts itself off, not even a reset, just shuts down. I don't even make it to the screen where I can pick to run from cd or install. I am using a live CD that I know works because I tested it out on other (newer) computers and it loaded fine. I have also tried running from a USB and that didn't work either. I created both the cd and usb the way that the main ubuntu sight instructs you too.

I have been playing with it for a few days now but I don't know what to do because the BIOS is the only thing I can get into. Any help would be appreciated.

---

### Post by Paddy Landau on 2012-06-03
As yours is an older computer, may I suggest you try [Lubuntu]("http://lubuntu.net/"). It's an official Ubuntu variant but runs better on older hardware. You may have better luck.

---

### Post by Revv on 2012-06-03
Thanks for your reply. I tried that version of linux that you listed, however I seem to be running into the same problem. With this version it lets me pick my language and what I want to do (install/ memory check/ live cd boot) but whatever I do it still crashes right after I pick anything except for memory check. I ran a memory check and did not have any problems. 

I am beginning to suspect that it is a hardware problem but the only thing I can think of is it being the video card. However if it is the video card would it be possible that it works for some amount of time before crashing the computer? The only thing that seems to be out of the ordinary is when I start to install and it goes through the BIOS screen letting me know what it is installing, it starts off normal but then shrinks and stays in the upper left hand of my screen like someone changed the resolution size on the display.

If I leave the computer in the BIOS I can poke around there as long as I want without the computer crashing. So I don't think it is an overheating problem, which that computer and processor are known for. I have checked all the fans and thoroughly cleaned them and the heat sinks so I know all of that is working (I applied new thermal grease to them after cleaning.). I just cant figure out what exactly is the cause, maybe its a bad MOBO from sitting in storage without use for a year or two?

---

### Post by btwThieves on 2012-06-03
> **Revv said:**
> I am beginning to suspect that it is a hardware problem but the only thing I can think of is it being the video card. However if it is the video card would it be possible that it works for some amount of time before crashing the computer?

It's quite common that your display adapter would work for some time in the early boot stages and not in the later ones - the early boot stages (BIOS, GRUB, boot splash screen) use a generic driver (usually VESA) whereas the later ones try to use drivers with 2D acceleration available (open-source Radeon/nouveau drivers or closed-source alternatives). Therefore I suspect that it's not a hardware problem, but a driver issue with the acceleration-enabled drivers Ubuntu is autoloading for your card.

To get through the install process, I suggest you force Ubuntu to use those generic VESA drivers for the entire setup process. To do this, select (DON'T hit "enter) "Try Ubuntu without Installing", hit F6, followed by ESC. You should now be editing the boot command. Delete "quiet splash" (you'll see more information this way) and add the following before the "--":
```
nomodeset xforcevesa
```
This should get you into a live GUI environment where you can at least proceed with your installation. Troubleshooting the alleged real problem -- graphics drivers -- will be easier from there because you'll have a persistent system.

Good luck,
betweenThieves

---

### Post by Revv on 2012-06-04
Thanks for the advice btwtheives but I am still running into the same problem. It pulls up the loading screen for much longer now but still crashes before I get to the next step. Now, sometimes it crashes when I am just in the lubuntu screen typing in the codes you suggested. Also when this is happening the fan that cools the video card goes from stopped to full force in increments. Right before it crashes the fan is at full speed and is audably loud. So I am pretty sure its something to do with the videocard whether it issoftware or hardware related.

---

### Post by marinara on 2012-06-04
i've had hardware problems with my pc, newer kernels won't install.  you might check your motherboard and video card for compatibility with the kernel you are installing

---

### Post by Revv on 2012-06-04
I am pretty sure its hardware problem at this point, I was able to borrow a XP pro OS disk from a friend. The computer originally had XP Pro on it so I know it should work but the same thing happens, gets part way into the installation process then crashes.

---

### Post by Revv on 2012-06-04
After trying a few more time the display wont work at all. I tried to re-seat the video card but no luck. The computer makes noise like it is booting, spins the fans and any disks in the disk tray so it looks like it was the video card. Guess it was the video card the whole time and it finally just gave up. Thanks for your guys help.

---

### Post by Paddy Landau on 2012-06-05
> **Revv said:**
> Guess it was the video card the whole time and it finally just gave up.
I had a similar problem with my old computer. I'm glad you managed to at least find the problem with the XP CD.

Guess you'll have to change your card or get a new computer. :(

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by Lars Noodén on 2012-06-05
Have you tried the Alternate images yet?  They offer more flexibility during the installation than the Desktop images.  They have better support for odd hardware, too.

---

