---
title: "Frustrated with 9.10 and 10.04 a3 installs..."
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by fragzem on 2010-03-02
Hey guys.. 

I love Ubuntu, been running it since Gutsy on a computer in my basement, used as a server. 

Also just installed 9.10 on my uncle's older gateway m-series laptop because he was having problems with Vista, and he's very happy.

Today I've been trying to get either 9.10 or 10.04 to work on my main PC. For the life of me, I can't figure out what's wrong, I've never experienced a problem with ubuntu installs before.

It's giving me a flickering screen while I try to install from the live-cd. I tried No APCI, and a few other options in the F6 menu to no avail. I figured "Well, sometimes this just happens, so I'll leave it alone" - left it alone for 45 minutes, still flickering and no progress when I came back. 

My PC:

msi k9n platinum nForce 570 mb
AMD Athlon 64 X2 6000+ processor
eVGA GeForce 8800 GTS 640mb card
8gb ocz gold ram
1 160gb IDE HDD, 1 500gb SATA-II HDD

Am I missing anything? I haven't bothered to "show off" my computer specs in a while.. as you can see the system is about 4 years old now.

---

### Post by dabl on 2010-03-02
First suspect is the CD that you burned.  Did you burn it slow (4X) and "DAO" mode?  Does it boot and run in "Live" mode on your computer? Can you verify it on another computer?

---

### Post by darkod on 2010-03-02
Also, did you try Safe Graphics? In the main menu, F4.

---

### Post by fragzem on 2010-03-02
I'm able to get wubi.exe to work on Windows 7 and it appears that it is working correctly. (So I'm thinking it's not the disc?.. I did burn DAO however @ 8x) 39 minutes to download some torrent.. -- I canceled that install. Obviously I don't want it to install through windows, in fact, I am dual booting Server 2008 and Windows 7 right now... and I want to erase and install ubuntu on the partition where Windows 7 is.

Don't ask me why I'm in Windows 7.. I guess I wanted to say farewell to it before I erase it! (I haven't booted into Win7 since April 2009)  I'm going to re-start my PC and see if "Live Mode" works for the whole "Try Ubuntu Without Installing". Then I'll come back into Server 2008 and check this thread again.

Thank you for the suggestions. Anything else?


::edit:: Safe Graphics? All I saw was.. OEM Install, and 2 other options.. I couldn't find Safe Graphics mode? is that in 9.10 only? Because right now I've been trying 10.04.

---

### Post by darkod on 2010-03-02
Not sure about 10.04 because it's Alpha, but in 9.10 at the main menu if you press F4 you should have Safe Graphics option.

It sounds like video driver issue.

---

### Post by fragzem on 2010-03-02
hmmmm.. Okay I'm going to burn off a 9.10 disc again.. at 4x.. and DAO
and see what happens with safe graphics mode.

One thing I have plenty of..  is discs to burn. :)

I knew ATI gives issues with linux in general, but I always assumed Nvidia would work fine.. especially considering my graphics card is pretty old now.. and the drivers for it are the same driver for about 20 other popular nvidia cards..

I'll update you guys in a few min..

And yeah, "Try Ubuntu without Installing" didn't work.  Gave me the flickering brown screen, which then changed to a flickering white screen... and then nothing.

---

### Post by darkod on 2010-03-02
> **fragzem said:**
> hmmmm.. Okay I'm going to burn off a 9.10 disc again.. at 4x.. and DAO
and see what happens with safe graphics mode.

One thing I have plenty of..  is discs to burn. :)

I knew ATI gives issues with linux in general, but I always assumed Nvidia would work fine.. especially considering my graphics card is pretty old now.. and the drivers for it are the same driver for about 20 other popular nvidia cards..

I'll update you guys in a few min..

And yeah, "Try Ubuntu without Installing" didn't work.  Gave me the flickering brown screen, which then changed to a flickering white screen... and then nothing.

Actually there were issues with FX 5500 in a thread I remember recently. I have ATI and don't know how old 5500 vs 8800 is, but just to mention that. And I think the safe graphics mode actually worked for that person. If you manage to boot the live desktop like that (Try Ubuntu), click the Install icon on desktop and I think it should work.
Strangely enough, after installing like that he didn't say he had to even update the driver afterwards.

---

### Post by presence1960 on 2010-03-02
> **fragzem said:**
> I'm able to get wubi.exe to work on Windows 7 and it appears that it is working correctly. (So I'm thinking it's not the disc?.. I did burn DAO however @ 8x) 39 minutes to download some torrent.. -- I canceled that install. Obviously I don't want it to install through windows, in fact, I am dual booting Server 2008 and Windows 7 right now... and I want to erase and install ubuntu on the partition where Windows 7 is.

Don't ask me why I'm in Windows 7.. I guess I wanted to say farewell to it before I erase it! (I haven't booted into Win7 since April 2009)  I'm going to re-start my PC and see if "Live Mode" works for the whole "Try Ubuntu Without Installing". Then I'll come back into Server 2008 and check this thread again.

Thank you for the suggestions. Anything else?


::edit:: Safe Graphics? All I saw was.. OEM Install, and 2 other options.. I couldn't find Safe Graphics mode? is that in 9.10 only? Because right now I've been trying 10.04.

10.04 is in alpha stage and currently does not have the safe graphics mode. Lucid 10.04 alpha is meant for those willing to test the OS, rather than those looking for a stable OS. When the final stable version is released it will contain all the things necessary. Right now in alpha stage it may not have everything and may change from alpha version to the next alpha version. Stick with 9.10 or 9.04 in a production machine.

---

### Post by fragzem on 2010-03-02
> **darkod said:**
> Actually there were issues with FX 5500 in a thread I remember recently. I have ATI and don't know how old 5500 vs 8800 is, but just to mention that. And I think the safe graphics mode actually worked for that person. If you manage to boot the live desktop like that (Try Ubuntu), click the Install icon on desktop and I think it should work.
Strangely enough, after installing like that he didn't say he had to even update the driver afterwards.


I was able to get 9.10 working but now I'm having trouble figuring out how to sort the partitioning out.  That being said and my Windows Server 2008 doesn't seem to want to load now. Not that i care, it's been 3 yrs since I did a re-format and it's about time.. but still..... 

Anyway, I guess this problem has been resolved. The partition stuff would just mean I have some reading to do. Maybe I'll just buy a new hard drive later. I just want to install on what windows sees as drive F, a 55.9gb partition on a 120gb hdd. However.. the linux partitioning confuses me with root partition ex4 etc etc etc.




Gotta think.

Thanks for the help guys!


> **presence1960 said:**
>  Lucid 10.04 alpha is meant for those willing to test the OS, rather than those looking for a stable OS


And yes, I did kinda wanna test it out! Shame I can't get it running to even test it, though. <grin>

---

### Post by darkod on 2010-03-02
If by "able to get working" you mean running the live desktop, the most trouble free way to install in place of particular ntfs partition is:

From the live desktop open Gparted (System-Administration) and delete the partition you want to install in place of. Of course make sure you copy your data from that partition first. Click on the green button in Gparted to execute the command. Leave the space as unallocated after deleting the partition.

Then click the Install icon on the desktop and in step 4 of the installer tell it to Use Largest Available Free space. That will be the unallocated space you prepared. The installer will take care of everything after that. Hopefully it will boot after the restart after the install. If it doesn't you might need to add a driver in recovery mode or similar.

Actually I think linux names partitions much better than windows, the name of the disk /dev/sda, /dev/sdb, etc, and a number to mark which partition on the disk it is. While in windows the drive letter means nothing at all, you can even change them around. But of course it takes some time getting used to. :)

---

### Post by fragzem on 2010-03-03
> **darkod said:**
> If by "able to get working" you mean running the live desktop, the most trouble free way to install in place of particular ntfs partition is:

From the live desktop open Gparted (System-Administration) and delete the partition you want to install in place of. Of course make sure you copy your data from that partition first. Click on the green button in Gparted to execute the command. Leave the space as unallocated after deleting the partition.

Then click the Install icon on the desktop and in step 4 of the installer tell it to Use Largest Available Free space. That will be the unallocated space you prepared. The installer will take care of everything after that. Hopefully it will boot after the restart after the install. If it doesn't you might need to add a driver in recovery mode or similar.

Actually I think linux names partitions much better than windows, the name of the disk /dev/sda, /dev/sdb, etc, and a number to mark which partition on the disk it is. While in windows the drive letter means nothing at all, you can even change them around. But of course it takes some time getting used to. :)

I wanted to drop a note and let you know I'm going to give it a try. (Sometimes people ask a question a forum and disappear forever.. not me, I'll let ya know what happens)

---

