---
title: "hda mistaken for sda at install"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by thefirstbruce on 2007-02-19
Today I downloaded ubuntu-6.10-alternate-i386.iso and have just installed successfully onto an 18 mth old Dell D610 laptop. 

I downloaded the 'alternate' version because I needed to do an expert install, where I needed the option to direct Grub to be installed on the Ubuntu partition, and not the MBR. 

I understand the standard desktop Ubuntu version doesn't provide an option to put grub anywhere else but into the MBR. (though if it sees another bootable partition, it will provide an option to do so. 

Anomalies I have noted so far are:

- my hda was mistakenly recognized by the install process as sda. The only reason I can think it might be mistaken as scsi is because I am using BootIt as a boot manager, and have my hda split into 9 primaries, 7 of which are hidden from ubuntu boot item. This was a nerve racking thing for me, as I didn't know where Grub might be put. Also, I tried directing first off that grub bed down in hda2, but it didn't recognise the partition. But did when I directed it to sda2. 

- the second issue is that when setting up networking, my intel 9515abg was recognised straight up, but I wasn't offered WPA encryption, only WEP. This would seem archaic considering the weakness of the WEP protocol. And I have my Billion router requiring WPA encryption. 

- apart from that, after first boot, I am presented with 200MB of updates to download. That seems like an awful lot considering the dist is updated every 6 mths. 

So here I sit in Australia, waiting the hour it will take on adsl to download the upgrades. 

Apart from that, I like the GUI. Very professional intuitive design. 
I am a linux newbie, so will take a while to get used to the wierd names for linux processes and software. 

BTW, I was motivated to try Linux because I feel there's a chance Vista's ridiculous drain on resources will open the door for Linux to pick up commerical and domestic market share. Especially in the developing world, and moreso in the developed.

My primary use of computers is internet and excel. I have noted that Open Office isn't that compatible with Excel on rendering graphs. 

Apart from that, will be back with more questions I suppose over the next few weeks of use. 

Regards
Bruce

---

### Post by Kateikyoushi on 2007-02-19
> **thefirstbruce said:**
> BTW, I was motivated to try Linux because I feel there's a chance Vista's ridiculous drain on resources will open the door for Linux to pick up commerical and domestic market share. Especially in the developing world, and moreso in the developed.

The exact same reason why I tried Ubuntu, while I used Linux for years I did not switch our home computers to it, with feisty that might also change.

---

### Post by thefirstbruce on 2007-02-20
Yes Kate. I think we are entering an interesting time regarding OSs. 
Microsoft just keep making things more difficult and continuously changing. This imposes a significant investment of time and resources in the commercial and domestic computing worlds. 

With the rise of Chinese and Indian economies, there is an opporunity for cheaper computing power, and more intuitive computer user experience. Microsoft definitely do not prioritize this. 

However, I would argue that the Linux community don't have it right either. The existence of 200 odd different distributions is just not the way around it. Nor is the naive use of arcane terminology for software and processes. If linux is to gain market share significantly, then it has to reduce the learning curve and leverage off computer terminology and processes that are well known. 

so 24 hours after my first install, I have given up. I couldn't get the wireless network to work because Ubundu doesn't offer WPA encryption. (and there are many university students living around me who like to sniff networks). I couldn't play a dvd movie because the Ubundu bundled software doesn't decypt commercial movies. Though I was directed to download a file  and install it. I got as far as downloading, then gave up after getting to a terminal screen and trying to uncompress and install the file. Why should newbies have to do anything at a command line? especially when the commands are different to DOS. I also tried a drag and drop of the compressed file's contents to the desktop, and that froze the machine dead, and I had to turn off the power to get out of the freeze. 

So not a compelling experience for me. 
Sure I can see Linux's potential.....but until the Linux community join forces and resources and get one decent distribution out that just "WORKS", then they continue to miss the opporunity the world is throwing at them. 

BTW, this isn't meant to be a negative rant. I believe in the Linux ideal. It just frustrates me that Linux groupies feel threatened by taking some  of the elitist and arcane-ness out of using the system. Dumming down linux isn't stupid. Is is one of the smartest things Linux and Ubundu could do. 

Meanwhile, I'll let it go another 2 years before I try a Linux dist. Maybe then I'll be able to watch a DVD and surf the net without chewing up yet another night of down time.

---

