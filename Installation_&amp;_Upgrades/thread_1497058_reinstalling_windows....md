---
title: "reinstalling windows..."
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by Goldenbogey on 2010-05-30
I have Ubuntu installed inside of windows. The problem now is that I wish to reinstall my windows operating system. 

Is this going to create a problem and, if so, how do I get around it? I have noticed that 2 files were put into the main C:\ drive directory but I would imagine that there would be more to it than just placing those files into the same place of the new install of windows.

Can I just make the Ubuntu install completely separate? I have PCLinuxOS installed as well. That is a separate install and has the nice boot manager on it. Maybe I can just add Ubuntu to that boot menu. At the moment it is a bit odd anyway (but functional :P)... I have to select windows boot and then windows (or ubuntu) boot again. Hope that makes sense.

I am using XP btw.

---

### Post by ronnielsen1 on 2010-05-30
If you installed through wubi, a reinstall of windows will wipe out ubuntu. Yes, you can install ubuntu like pclinux (recommended over wubi - just boot with the live cd and install from there)

---

### Post by ronnielsen1 on 2010-05-30
> . I have to select windows boot and then windows (or ubuntu) boot again. Hope that makes sense.
Because of wubi, a new regular install of ubuntu will give you 3 to choose from - windows, pclinux and ubuntu

---

### Post by Goldenbogey on 2010-05-30
> **ronnielsen1 said:**
> If you installed through wubi, a reinstall of windows will wipe out Ubuntu.

It wont do that completely because I have Ubuntu in its own partition. I would have thought that all that will be in the windows partition/ OS will be some method of it recognising that Ubuntu is there. 

I was hoping for a method of allowing the existing Ubuntu install to be recognised in its own right. Technically speaking, I was under the impression that it was more or less self contained anyway, but that it was loosely tied to the windows OS because that was where the installation was initiated, and for boot purposes as well of course. I reckon that I will most likely need to do a new install anyway. 

Many windows programs, especially games, can be installed on a separate partition and will still work fine when you reinstall the windows OS. You can even take the HD drive from another computer and play a game installed on it using a different computers OS. The programs are normally self contained. I only use that as an example of program installations.  

I don't see any real reason why Ubuntu would have installed anything into the **registry** of the windows OS. More than likely it would just install the Ubuntu OS in the same way as when You install it from when it is booted from the CD. It would just be using the windows OS to extract the files and put them in the right place in the Ubuntu folder instead of doing it in black screen bit with white text (sorry my knowledge of technical words is somewhat limited!!)

---

### Post by darkod on 2010-05-30
This is exactly where you are wrong. Wubi is very different from stadard full install on its own partition, and its own filesystem. Like you have for PCLinux.

You should have done that from start.

Even though it's on different partition and won't be wiped when you format the C: partition, I am not sure you can just add it to the new windows install.

In fact, what you mentioned about the games, software installed in windows can very rarely work like you said, simply by moving the hdd or adding already installed software to a new clean windows install. Maybe games and software which are not really deeply installed, just started from executable file. Yes, that will work.

But usually windows reinstall does need you to reinstall your software too. And you installed wubi just like software, inside windows.

And yes, it does put keys in the windows registry. Which you will lose with the reinstall. Not sure if you can copy them and somehow add them later. But that's quite a lot of hassle.

---

### Post by Goldenbogey on 2010-05-30
Ok, I will definitely reinstall it then. It's just a hassle re-doing it all over again :(

On the subject of self contained programs like games and stuff... I was surprised at how many programs will still work when you reinstall the OS. Microsoft office and anything like that obviously won't work but many games will run fine. They protect their copy write by making it so that you need the disk in the drive to play the game (unless you make an ISO image and mount it on a virtual CD drive :KS).

---

### Post by Goldenbogey on 2010-05-31
I completely stand corrected and I understand now. When Ubuntu is installed inside windows it is just put inside a standard NTFS format which is completely different to the exp4 formats used by linux!!

I should have realised that already considering that I had done an install of PCLinuxOS previously :P.

---

### Post by darkod on 2010-05-31
> **Goldenbogey said:**
> I completely stand corrected and I understand now. When Ubuntu is installed inside windows it is just put inside a standard NTFS format which is completely different to the exp4 formats used by linux!!

I should have realised that already considering that I had done an install of PCLinuxOS previously :P.

It's never too late to learn. :)

I'm still not 100% sure but I think wubi has at least small performance hit because in a way it's working like virtual machine/OS. You can install another OS in Virtual Box for example, any time you want.
Personally I prefer a full install of ubuntu on its own filesystem and partition.

---

