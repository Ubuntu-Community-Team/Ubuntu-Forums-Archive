---
title: "commiting to linux"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Fenris_rising on 2008-04-29
well day 5 and my PC with dual boot XP PRO and Linux Hardy Heron is still running fine. There are minor problems such as when i try to access some areas I.e. synaptic software management, administration starts but fails open for me to enter my password. **any clues any one?** yesterday i dual booted my laptop with xubuntu, fiesty fawn, it was free with a linux mag. got my wireless usb dongle going with posts on this forum no problem and real player is installed to. oddly that works fully with the bbc iplayer but not on the pc with Hardy (iplayer) but using realplayer as stand alone gets round this. ive made copious notes for future reference and even have my PCB software running under wine. so at this point it all looks good for my longest venture into linux. 
so my plan.......i have a 320GB IDE HDD coming, what to do then? my current PC setup is;
A8V-VM motherboard
1GB DDR400 stick of ram
80GB SATA HDD (primary) both OS's on here
80GB IDE HDD as backup and store.
SAMSUNG DVD RW
Gigabyte X300 PCIE graphic card
onboard ethernet (u/s)
pci NIC
PCI wireless network card.
Do i use the new drive as storage, and have Hardy Heron on the SATA drive and XP PRO on the IDE. or vice versa.
Have both OS's on the new drive and use the other 2 as storage? any words of wisdom out there? i still have a lot to learn but so far im really impressed it all works (barring the niggles with HH) and ive managed to do some fairly lengthy work in the terminal to solve some problems and use ndiswrapper on the lappy to get the dongle going.

regards

Fenris

---

### Post by Pumalite on 2008-04-29
Install both OS's in your primary SATA drive. Keep the others for storage and/or /home for Ubuntu.

---

### Post by Fenris_rising on 2008-04-29
sounds like a plan. i'll have to read up on how to make the 'home' on a seperate drive. perhaps i'll even set the 80GB IDE as a dual boot and use it as an emergency backup should anything go wrong. so its 80gb sata as dual boot primary drive the 320gb as my store/home and the 80gb ide as backup. i'm in danger of becoming a linux junkie!

cheers for that

Fenris

---

### Post by Pumalite on 2008-04-29
If you use Vista; give 'unallocated space' for Ubuntu with Vista partitioner. If XP; you can 'shrink' it with Gparted Live CD. In any case, when you make the partitions, you can just pick the HDD in question and assign it a /home mount point.

---

### Post by RATM_Owns on 2008-04-29
Also, you could just use the GParted in the Ubuntu Live CD.
Under System->Administration->Partition Editor.

---

### Post by gaylapdancer on 2008-04-29
Or you could install GParted from the repos, via synaptic or via the command:

```
sudo apt-get install gparted
```

As seen above the package name is 'gparted' so if you use synaptic search for that :)

Either way it will appear as 'System -> Administration -> Partition Editor'

---

### Post by Fenris_rising on 2008-04-29
cheers chaps

i will investgate gparted and read up on installation options and techniquies. i havent had this much fun since i was forced to learn all about win 98 cos i broke it in 2 days. at least i take a more measured approuch these days :lolflag:

regards

Fenris

---

### Post by Pumalite on 2008-04-29
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Fenris_rising on 2008-04-30
Thanks for all the info gentlemen. im reading lots and lots. today i am also reading about DVD playback. AVI's and of course how to get my DVD RW burner going (PC) and on my laptop the CD RW/DVD player. avi is working on the laptop now. yayyyyyy!!!!
looking at it i need to learn the above, i can run a particular win prog i need in wine, setting up a network under linux (wireless) between PC and Lappy. also running my xbox through my PC as i do now (xbox is modded i go online with xconnect) wired connection. really theres nothing there i havent had to learn in windows, i spose the only twist is i may have to at times go the extra mile in terminal or find the right software for my needs. of course the 'syntax' is a bit different so a bit of learning there as well. i'll just make lots of notes as i go along learn what i need and then learn some handy extras i guess. still loving it. im prepping my PC today to do a proper install of HH. so ill delete it from within windows as thats how i set it up, defrag the drive do a chdsk partition and install fresh. its an 80GB sata drive so i think just splitting it 50/50 on the partition would be fine. the new 320GB HDD when it arrives will be my store/backup. the SATA drive will just be home to the OS's. my other 80GB IDE drive im going to setup a dual boot again and then store that HDD safe for emergency use. am i over egging the pudding do you think? if i can get DVD viewing and CD RW going on my laptop i'll make that a single boot machine. should i upgrade it to gutsy gibbon? HH wont go on it due to memory restrictions but hey so long as its linux its cool.

cheers all lots to read!!!

Fenris

---

### Post by Pumalite on 2008-04-30
You have 1 GB of memory; you can put anything you want in there, and certainly Hardy Heron. Make a 2 GB /swap partition if you are preoccupied.

---

### Post by Fenris_rising on 2008-04-30
hi m8
 i meant my laptop has a small amount of ram, less than required by HH for install purposes, i tried the alternate HH to but no go. i did get gutsy gibbon working as a live cd but gain it wouldnt install, something to do with my laptop being an 'unknown chassis'?? its a dixons cheapy sold by PC world 3 years ago.........sheesh for what i paid for it then i can get one now thats 3-4 times the spec lolol.

regards

fenris

---

### Post by Pumalite on 2008-04-30
You could try 8.04 Xubuntu Alternate CD.

---

### Post by Fenris_rising on 2008-04-30
i am infact right at this moment reburning 8.04 i386 and the alternate i386. also going to try a reburn of gibbon 7.10 for my laptop if HH wont go on. if all else fails and gustsy still wont install i'll continue to use FF which seems quite happy. 

cheers

Fenris

---

### Post by Fenris_rising on 2008-07-14
3 months roughly and my PC is still up and running 8.04 like a dream. I have the occasional problem where Fire fox seems to lock up but other than that everything is great. The childrens PC has started playing up so i have assembled a make do unit from spares and at first i tried XP but i had problem lockating the drivers for the on board audio. Mainly sites wanting me to pay for the right to download the required item even the Via site seems to have handed over their archives to some money grabbing %$^%^&^%*s
So the phrase 'bugger that, the kids can like it or lump it' passed my lip0s in a heavily whispered aside and my 8.04 disk went into the drive. Oh boy i should have done that first. everything works out of the box. I setup pidgin for them and instructed them that there might be a request for java and flashplayer at some point come and get me. I am even tempted to lose my XP disk and fix the failing PC with an OS of quality.........ubuntu of course. brilliant OS, brilliant forum heres to all the hard working chaps and chapesses that work so hard to bring us this 'box of delights'.

---

### Post by Fenris_rising on 2008-10-15
Hello All

Well 6 months down the line My PC is still purring along with HH. I had a slight problem with the PC hard locking from time to time and at one point it seemed to be Fire fox related but then it didn't :D . Any way touch wood it seems to have cleared up so alls tickety boo. My laptop I'm afraid has gone back to windows for now and will probably stay that way until it finally expires. However when I replace it with a new laptop, which wont have all the 'stack em high flog em cheap' innards which seems to be the problem overall, I will go linux on that one. The biggest problem I have had though.................Remembering what to do, particularly after an updated kernel is downloaded, to edit my menu.lst lolol. Which is more of a compliment to the stability of Linux and the fact that I so rarely have to look any deeper than the GUI. It's still the best thing I ever did, changing to Ubuntu.

regards

Fenris

---

