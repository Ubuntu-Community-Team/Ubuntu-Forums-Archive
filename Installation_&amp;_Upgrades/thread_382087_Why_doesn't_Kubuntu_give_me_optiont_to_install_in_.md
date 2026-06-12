---
title: "Why doesn't Kubuntu give me optiont to install in SDA2?"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by Duffy on 2007-03-11
I have a newly built computer. Asus P5LD2 motherboard, E6300 processor, 1GB memory and 250GB Western Digital Disk.

I partitioned the drive into two partitions of about 125GBS each. Vista is now installed on SDA1 and I am trying to install Kubuntu onto SDA2. The options I get from the installer are to resize SDA1 (no, don't want to do that), reformat the entire drive and install (don't want to do that either), or three, manually partition the drive. So I select manually partition. From the CD, I am using QTParted. It will allow me to format SDA2, but I cannot resize it to create the swap partition. Is there any way to tell Kubuntu to install into SDA2 and create the needed partitions itself (while leaving SDA1/Vista alone and configuring Grub to give me a choice in booting)? Very frustrating.

---

### Post by Captain_Riker on 2007-03-12
Hello,

There was an article in a local Magazine (Linux User),I don't have that article here. When I'm back Home I'll go through it once again. First thing is, I can't recall (at the moment) why or how, but it is not that easy to run a Linux with Vista on another Partition!!! It's either the Vista files in the MBR that blocks grub from working properly, or it is that Vista wont boot after being called by grub. The Headline (German) of the Article was "Vista sperrt Linux aus!" (Vista locks out Linux!).
 So how did you partition the Disk in the First Place? With the Installer of Vista or another programm? Because you should be able to run gparted or qtparted from the launched live system to delete the partition and then create a new partition layout, then start the installer and start the install process. But mark my words: It'll screw up your Vista anyway!

BTW: Why would someone install "things" such as Vista and then Linux? I mean haven't you read the EULA of VISTA? Hey, I had a test installation of, first RC1 and then a Licensed Version in our Company. It's useless. Eats Hardware, is just clicky'n'colorfull, theres a lack of drivers for common and widely used Hardware. It also Lacks Software thats made for it other than itself that makes it in some kind of Beta-state like.

But to summon the advices:
1. Try to delete sda2 in order to create a custom partition layout for linux
2. If that fails: Which programm did you use to partition into sda1 and sda2
3. I'll give further advise on how to get vista and Linux working together. According to the article.

Don't take offense in what I wrote. Running Linux and WinXP as Dual boot is what i'm doing at work too (though not at home:) ) but Vista and Linux gives me a Headache. For the time has come were one has to decide either to switch to Linux OR to Let Microsoft (read the EULA!!) finally take control over your PC.

Greetings and Cheer up
We'll get it to work

---

### Post by Duffy on 2007-03-17
Well Cap, it's a pretty easy answer. No I don't read the EULAs of ANY software.  Second, it is unfortunate, but there are some applications for which there is no Linux equivalent. I have to use Vista. The reason for the dual boot, is to start using Linux as the main OS and Windoz when I need it.  I ended up just partitioning half the first drive, install Windoz on it first, and Linux on it second. Kubuntu installed grub with the Windoz boot option. So far it is working great.

---

