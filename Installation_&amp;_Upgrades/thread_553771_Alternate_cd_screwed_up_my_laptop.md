---
title: "Alternate cd screwed up my laptop"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by epithet on 2007-09-18
So I was trying to install Ubuntu Feisty Fawn on my Laptop which as Vista preinstalled and I used the shrink manager that came with Vista to get a spare 15 gig partition. The original cd did not work so I tried the alternate cd and half way through the installation  when it's trying to install Ubuntu a lot of errors come up and I'm guessing it was a corrupted disk. So I tried to abort the install even though it warned me it may screw up my whole system. 
And it did.
I can't boot into Vista (it doesn't detect it) and I just crashed a $1200 laptop in 3 days. Any help to get vista back running would be appreciated(or ubuntu for that matter). If you need more specs just tell me. It's a dell inspiron 1420 running windows vista.

---

### Post by Herman on 2007-09-18
Hello epithet,
I'm sorry to read of your troubles. Things like that are rare, but they can happen. You should be able to return your computer to its original condition with TestDisk, here's a link that shows a couple of illustrated examples of how to use TestDisk, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html")  Using TestDisk to Recover from partitioning disasters demonstrated,(Edited on Friday the 13th!).
That should fix it for you. If not then you'll just have to restore Vista with your whatever Windows installation disks you have and whatever backups you made before you used the disc partitioning software. 

If you have trouble with Ubuntu CDs not working try cleaning the lens in your CD drive. Similar problems as you described have happened to me and a few other people too, and the CD drive lens being dirty seems to be one of the main causes, although since problems like these are fairly rare it's hard to know for sure, but cleaning your CD lens shouldn't hurt, and might help. Or it could be caused by letting Windows apps touch your partition table, that's dangerous too, but from your description of the problem I'd blame the CD lens first.

TestDisk is on  [GParted -- LiveCD]("http://gparted.sourceforge.net/"), which is free, and only a small download. It's in several other Linux LiveCDs, as well, and can be 'installed' in the Ubuntu LiveCD too, and used for as long as the Ubuntu LiveCD is booted. It will disappear of course, when you shut down the LiveCD operating System.

---

### Post by epithet on 2007-09-18
Thanks a lot I'll download testdisk over night and let you know how it goes tomorrow! I think my problem was using an old blank cd that was like 2 years old -_-. Not smart of me. Thanks again in the meantime.

---

### Post by epithet on 2007-09-18
This is probably a really stupid question, but i booted into gparted live cd went into terminal and typed testdisk and it said terminal must be resized to have 25 lines. I tried using the resize line, but I can't figure out how to make it work. Any help would be appreciated.

---

### Post by Herman on 2007-09-19
Okay, so I have booted up my own GParted LiveCD in my Acer 3003WLMi notebook and opened a terminal and typed;  testdisk, to start testdisk and I have a black  termainl now and it does say ,
> TestDisk need 25 lines to work,
Please enlarge the terminal So, I simply enlarged the terminal and everything is fine, I can't see a problem here, at least not in my computer. 
I can only guess the GParted might be appearing differently in your computer than it does in any of my computers. What do you mean when you say "I tried using the resize line"? What resize line are you referring to?

In my computer I have the usual three window buttons in the top left had corner of the terminal window. The first one has a line symbol on it and it's for minimizing the window to the panel (or taskbar if you're a Windows user), the next button has a small rectangle in it, that one resizes the terminal window and the third one, with the X in it, closes the termianl window. So in my computer it's just another windows like any other window in any computer.

I can think of something that might make GParted come up differently in your computer, and that is is if your Xserver has been misconfigured somehow. During the boot-up of the GParted LiveCD, there are different options you can use for  the xserver (drivers for your video card and monitor, etc). Maybe try booting up your GParted  LiveCD again and  instead of letting it  'Do X Configuration = mkxf86config', select the next line down: auto-configuration, and see if that helps you get the right picture in GParted.   Another option you might try is 'Force VESA driver'. 
I'm only guessing something like that might be your problem, epithet. If I guessed wrong, can you please try to describe your problem again and I'll see if I can understand what you mean again.
Regards, Herman :)

EDIT: Actually, you don't even need to boot into the GUI at all to use TestDisk, so if you make sure you choose something ridiculous when booting up to make sure the xserver won't work at all so you'll end up with no GUI, but the bash shell for GParted LiveCD instead, you'll be able to run diskdisk fine from there.

---

