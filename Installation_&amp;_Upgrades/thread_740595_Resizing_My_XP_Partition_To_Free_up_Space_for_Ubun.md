---
title: "Resizing My XP Partition To Free up Space for Ubuntu/Kubuntu"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by theravenproject on 2008-03-30
I am currently running two windows installs on a 20 gb harddrive (Dell Optiplex Computer)-a 2 gb Windows 98 se partition (Fat) and a 17 gb Win XP partition...what I want to do is to delet the win 98 se and then resize the Xp down to an 10 gb partition and use the other 9 gb to set up mu kubuntu on...I just got my two live cds in the mail-the new Ubuntu and Kubuntu cd's!  Anyways, I read in a different thread somewhere that the Ubuntu set up allows you to resize an existing windows partition...this is my drive schema as is now
[B]
C:\ Healthy FAT 2 gb Win 98 SE
E:\ Healthy (Yeah Right) 17 gb Win XP

This is what I want:

C:\ 10gb Healthy Kubuntu Partition
E:\ 10 gb Healthier Win XP partition
[/B]
ANY AND ALL HELP WILL BE GOBBLED UP BECAUSE I AM DYING TO GET LINUX INSTALLED AND BEGIN RUNNING IT!!!!!!!!!

I have to keep the XP because I have my whole C programming IDE on xp and I need that right now as well as some of my other programs such as Wireshark/NMAP, etc...Until I get back into the swing of Ubuntu I need that xp but I need a smaller one so that I can make a beefy Linux part....

---

### Post by Pumalite on 2008-03-30
Memory? Graphics?

---

### Post by theravenproject on 2008-03-30
Oh yeah,[B]

256 mb of ram
Rage 128 ultra something or other graphics card
LiteOn Cd burner
Ethernet Connection TO Cabler Modem-Am using 5 meg Cable Internet...
Compaq Monitor[/B]
 (My last monitor was the reason that I didn't have Linux yet-I had the "Display Out OF Range Problem" but this monitor loads up my live cd so I know it's ready to install-although I did get th "Failure to Initialize Hal" error and that scared the living bejesus out of me!  I am hoping that I can install it in spite of Hal's failure and Iron hal out later?  MORE WORRIED ABOUT MY 1ST QUESTION 1ST...one thing at a time right?

---

### Post by housam on 2008-03-31
Instead of C: , you have to create 2 partitions. 0.5 GB swap and 9.5 GB ext3 format for the root ( / ). use Gparted tool ( in the live cd ) to make them ( delete C: and resize E: to 10 Gb ) then when it comes to partitioning during installation, assign them manually.

Also I think Xubuntu is more suitable for your ram.

---

### Post by prismpirate on 2008-03-31
Based on my experience, Ubuntu runs sluggish on 256 of ram, Try Xubuntu, like housam mentioned. To resize it, when booted into the live desktop, go to

System > Administration > Partition Editor

Choose the NTFS  or FAT volume, (you didn't specify which one your windows xp is running on), right click, and press shrink.

Should be pretty self explanatory for that. 

After shrinking the XP volume, you can install.

When selecting partitions, delete the FAT partition, and create a 0.5gb swap partition and a 9.5gb ext3 partition.

The mount point should be /.

Install, and enjoy

---

### Post by Pumalite on 2008-03-31
Make sure you use the Alternate Xubuntu CD: [http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by theravenproject on 2008-03-31
Man, I crashed and missed all of your replies-if anyone is on this evening...first of all-I don't have Xubuntu and no way of burning one for a while...by the way-what is the difference between Ubuntu and Xubuntu?  One of the reasons why I why I became interested with Linux in the first place is because I was told (Here on these forums a couple years ago as a matter of fact; that Linux was not Memory intensive and that actually-it was more suited to minimalist set-ups like mine...Will Ubuntu still run reasonably welll on my rig?  I have just these two distros and am very tired of waiting=each day I stay only using windows is a painful day of Windows only limitation and a day wasted without learning Linux...I am running out of time -I could get hit by a car tomorrow and then what?  I will have died w/o utilizing the Linux world and will have missed out on the joys of utilizing the Hacking Capabilities and Programming capabilities of Linux!  Besides-if Ubuntu will run on my rig-I can always wipe it and install something more suited to my cpu that still meets my needs...I am very interested in software development. web development...my next goal was after getting Linux on clean was to begin building some of my own Firefox extensions as well as my own website and an app or two in perl/python/c each...I am ambitious and I need my Linux fix-|THANK YOU ALL SO MUCH FOR YOUR TIME AND CONSIDERATION FOR THIS PATHETIC NOOB!!!!!!!!

---

### Post by Pumalite on 2008-03-31
Xubuntu is Ubuntu in a 'lighter' flavor. Is a lighter Desktop and more adecuate for the amount of RAM you have. 'Alternate' because you might confront some graphic problems.

---

### Post by theravenproject on 2008-03-31
[FONT="Comic Sans MS"]Okay Pumalite-I see where you are coming from...can you tell me why I would confront some issues graphically?  I did before but now I have a new monitor and it booted up both my Ubuntu and Kubuntu "Live" cds fine...**anyhow-back to my question-do you think that I can pull off the Ubuntu installation for now?  I have now way to create a bootable media in order to burn/install Xubuntu**...I checked up on Xubuntu a little bit but like I said before.._.I thought Linux was the less "Hardware Intensive" os?  If I am running xp okay on this old girl without a hitch-will Ubuntu be fine?_
[B]
THANK YOU PUMALITE!!![/B]  [SIZE="3"]By the Way-Anyone know what the "Spilled the beans" under my user name means?  I am guessing that it is a step down from "First cup of Ubuntu"????[/SIZE][/FONT]

---

### Post by Pumalite on 2008-03-31
Is you 'insist' on booting a Live CD, you can do so by making a 500 MB /swap partition ahead of time. You can use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Ubuntu will be so slow; it'll make you cry.

---

### Post by theravenproject on 2008-03-31
[FONT="Comic Sans MS"][SIZE="3"]No; I am simply talking about doing exactly as you said earlier-**deleting the C:\, shrinking my xp partition and then creating a new partition for Ubuntu and installing Ubuntu on to that partition from the live cd**....what do I need the swap partition for-what is it and what does it do?

Please Advise[/SIZE][/FONT]

---

### Post by Pumalite on 2008-03-31
I think you need around 340 MB of RAM to boot a Live CD.

---

### Post by theravenproject on 2008-03-31
[FONT="Comic Sans MS"]Well, it is working with only 256 mb of ram currently and I did install ubuntu on this very same computer a couple of years ago (Before I retired it and moved away from home) and now have moved home and began my quest for knowledge-I started out with XP because my old Linux distro (Ubuntu's last full release before this current one) ceased working-the cd got damaged but anyways-on my xp partition I have been coding in c with the MinGW IDE for C/C++ and what not and so I don't want to lose my win partition because it will be useful while I am making the transition but anyeays...I was running the Kubuntu live CD from this cpu when we first spoke last night...this thing does have a pentium 4 in it!  Is it that the new releases of the Ubuntu based Distros are being made more to fit the newer trend of "Uber-Hardware"-ie. Dual Core cpu's and Graphics Cards and DDR2 Ram?  Whatever the Case I will be putting my gaming machine together in about one month or so and that will run whatever I want to throw on it so I'll run a dual config then too-I just wanted to get a head start with Ubuntu now.[/FONT]

ONCE AGAIN_Thanks PUMALITE...boy you sure don't waste many words do you?

---

### Post by Pumalite on 2008-04-01
Good luck.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by theravenproject on 2008-04-01
[FONT="Comic Sans MS"]Ok Pumalite-I know I am stubborna nd probably really annoying the crud out of you-I am beginning to see things your way...since I cannot get an xubuntu cd sent to me via mail and I cannot burn it onto a cd at the time being-could I conceivably make an Xubuntu installation Floppy with the text installer?  Lastly-AND PLEASE ANSWER THIS!  Does Xubuntu have the same capabilities for Programming/Software Development/Website Development..Ethical Hacking/Cracking etc....and does it come with the ability to script with Python on board?[/FONT]

---

