---
title: "dual boot woes"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by isandir on 2005-10-19
Hey guys,

I've been trying to get ubuntu to dual boot with gag and windows.
I have windows on my primary drive with GAG loaded on the MBR.
I've been doing the normal basic install and i found a post by linuxlizard
saying exactly what i want to do.



"Unfortunately I don't have any advice for how to recover from your present situation, but I do have some very useful advice for how to avoid it, so that you and others reading this can prevent problems in the future.
This used to happen to me almost every time I tried and installed a new distro- grub would mess up windows and I'd have to go in and fix it after the fact. It got very frustrating to have to go in and fix things afterwards. It never happens any more for the past couple of years because I use GAG now. GAG is free.

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

GAG is a boot manager that installs to the mbr. Or to a floppy. You can test it first on a floppy or run it on a floppy forever, and then with a couple of keypresses install it to your mbr once you know it is set up and working properly. 

With GAG installed, you then install linux and write grub to / (root) rather than to the mbr, and then you tell grub to boot linux from /. 

Writing grub to root is very easy with ubuntu. When you are partitioning the drive, choose to manually edit the partition, rather than automatic. When you set up your root partition, make boot flag active (it's an option you will see).
Later when the installer is ready to write grub, it will ask you if you want to install grub to the mbr. Choose no, and it will then write it to your root partition. When you reboot, you can then set gag up to boot to your root partition (If ubuntu is on your second hard drive (slave), and nothing else is on there, once you are in GAG press s a 2 b n, name it (add description), skip the password setup, press d for the linux icon, press h and save gag, press r and then your setup and ready to run).

Once in ubuntu if you want you can edit grub so there is zero countdown from grub to load up, which makes the grub screen vanish from the boot-up process. You can do this graphically from the administration menu before you ubdate ubuntu for the first time, but for some reason the icon for whatever the app is dissapears once you update, along with the boot splash (LOL). You can however still go into a terminal, enter 

sudo gedit /boot/grub/menu.lst 

enter your password, scroll down just a tiny bit to the section that looks like this:
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

and change the last line to

timeout 0

That's it, now you will have smooth booting.
Before GAG installing linux for me was always a bit scary because I didn't know what would be involved in getting windows back, and I was always afraid of loosing it forever (I did twice too, when I was a noob to linux). Since GAG installing is no big deal, I just make sure to always put grub on the root partition rather than the mbr. I can't believe a couple years after finding GAG grub is still messing up people's windows partitions. It's about time that was fixed. But until then, there's always GAG. Mean linux geeks have given me a hard time about using it, but when I still go to boards and see windows boots dying from grub, I sure am glad I use it. It really makes life safe and simple. It's really easy to set up - a couple of minutes.

That's the end of my commercial, I'll move along. LOL"


Anyhow... I tried makeing a primary partition of 40gb named root
and bootable set to on.  The install completed and still stuck grub
into my mbr.  When i try to set up gag to boot into ubuntu it works 
fine in gag, but when i press the button to boot my screen just fills up
with.  "99 99 99 99 99" over and over  I dont know how to fix this but i would
really appreciate any insights you guys have.

Thanks!!
Tim

---

### Post by weijie90 on 2005-10-19
now, it looks like your mbr has grub installed in it.
umm... what do u want to use for your system? 

personally, i installed grub onto a floppy during the ubuntu install, and it left windoze alone. i just have to boot from my floppy to enter grub.

---

### Post by isandir on 2005-10-19
Hey, i have 2 hard drives.  One 80gb with windows and GAG as the booter.  My second drive is 200gbs and i am currently in the ubuntu install on it.  I made one partition names "/" with expert mode to have 40 gbs and be bootable.  I am currently in the "install the grub bootloader on a hard disc" section.  I am trying to enter the right arguements to make grub install on the 40gb partition i made instead of the mbr.  I need to do this so i can tell GAG to point to the partition to boot ubuntu.  So far (hd0,1) is not working and i dont know what to do.  I dont want to do (hd0) because that is the mbr, but grub isnt actually on my harddrive yet.

---

### Post by Herman on 2005-10-21
Thanks, isander, for your helpful post about GAG.

I had never heard or GAG before this.
I have a GAG CD now that I can boot from, others can easily do the same thing if they need to. It's not too difficult either, here's what I did:

I just downloaded the file gag45d.zip for free from the link isander provided:
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)
Then I extracted it in a directory and found the gag.iso file in it.
I copied the gag.iso to a CD.
I left the CD in the drive and rebooted.
There were some instructions there to read.
I selected item 4 off the main menu to install GAG. (I planned to install it on a floppy, not to my hard drive, there's nothing wrong with my hard drive, and as they say "if it ain't broke, don't fix it").
Next I chose a keyboard, language, and then got a panel where I selected 'S' for 'set up GAG'. (The other option was to 'boot from disk, key 1, so I imagine that would have got me booted if I wanted).
On the next panel I chose 'A' option for 'add new operating system'.
I got a partition table with the bootable partition shown in black type and the non-bootable ones shown in blue.
For each operating system I chose to add I was asked to type in a description (eg; Ubuntu Hoary, etc),  a password (********), and pick an icon.

Unfortunately for some unknown reason I was unable to get all this saved to a floppy at this time, but will try again later.
I didn't want to save it to my hard disk either, but that might be an option for people having trouble with GRUB to consider. (Not recommendable yet by me unless you really feel you have to or are the adventurous type).

The next few steps I'm not exactly sure of the precise sequence or details, but something like this:
I pressed 'B' for 'Boot timer, and set a boot time for each OS. (I'm not sure if this is the correct thing to do or not, I think maybe just for the default operating system would make more sense in hindsight, (but anyway).
Then I got a panel with my operating system 'keys' (or buttons), each with their icons I had chosen. 

Then I just booted off it (the CD) to try it out. It had no problem booting Windows.
I  set everything back up again each time I re-booted. One odd thing I noticed was it had 'ext2' file system listed for my Ubuntu partitions in the partition table. (I have ReiserFS). It failed to boot my Ubuntu partition. I'm not sure why yet, but  I'm just playing with it at this stage anyway, I don't really feel too depressed about that yet. (Maybe it's something I didn't set up right). 
I removed the CD and used GRUB to boot into Windows instead.

So now I have a CD I can at least boot Windows from if I had a laptop without a floppy drive and was having GRUB problems after a new install. Probably if I had bothered to take the risk and install it to my hard disk it would work properly and boot Ubuntu. I'm getting my experimental computer going again next week I hope, and don't want to try it out on my good computer when I can wait a few days for my destroyable one to be ready. (It's hard disk was over five years old and died a natural death) (old age).

I realize I am probably a bit premature in posting all this before I get it all completely sorted out, but I wanted to share the info I've learned so far as soon as possible in case I get called away and get busy and can't get anything more done on this for a while.

I would not advise anyone to install GAG to their hard disk yet, not based on the amount I know about it at this early stage anyhow. But it didn't do any harm having it on a CD and experimenting with it, and seems to be an interesting subject for further investigation. It might be an easy solution for people having problems with GRUB. 

Has anyone else got more info on GAG that they can share, like someone who wants to give it a try or someone who has been using it successfully for a while? (Herman).

---

### Post by Herman on 2005-10-21
More on GAG:
 You need to have LILO installed in the boot sector of each Linux partition in order for GAG to work for Linux OS's.  That's why it wouldn't boot Ubuntu for me. So I guess that means you have to plan on using it a bit more in advance, it isn't something you can just switch to quite as quickly as I though. 
Also, my computer still refuses to install it to a floppy, no matter how hard I try. Maybe other computers can do that though. 
Conclusion: I don't think GAG is for me, especially since I've never had one single problem ever, with GRUB. But if there is anyone who really feels keen to try something different, it would be interesting to read a review about it.
"Different strokes for different folks, (or computers)".
It does boot Windows alright from the CD if someone has a laptop with no floppy drive and they are stuck and in a panic.

---

### Post by Herman on 2005-10-21
Curiosity got the better of me and I just had to try this out. I  re-installed a new Ubuntu install that didn't have any files in it yet and when I got to where it says  'Install GRUB to MBR', I selected 'Go Back' instead, to bring me to the Ubuntu installer Main menu. From there I just went down one line to 'Install Lilo Boot Loader on Hard Disk'. Then I chose to install Lilo on /dev/hda7: new Ubuntu partition, (not the MBR).
It's important to let anyone who might try this know they will need their new GAG CD to be ready and know how to use it when the install CD gets ejected and the system reboots for the first time. You will need GAG to re-boot into the new system to finish installing it! So you swap CDs, and set GAG to boot the new partition from the CD. Then you finish your install as normal. 
Now I have still got GRUB to boot my other two operating systems as normal, with one 'secret' partition that doesn't appear in GRUB.
Only when I insert the GAG CD, can I boot the new 'secret' Ubuntu system that has Lilo in it, or of course Windows.
So it is possible to get Ubuntu set up to use GAG, but personally I still prefer GRUB. It seems like a few computers and/or  their owners are not liking GRUB though, so GAG with Lilo could be an alternative choice for some. I'm not planning on writing GAG to my MBR though. (Herman).

---

### Post by isandir on 2005-10-21
Herman, Thanks for going working through and figuring out GAG.  I hadn't thought to try lilo instead of grub.  I ended up just using plain grub instead of gag to boot both windows and ubuntu.  Your information is really good.  I prefer the intuitiveness of GAG for other people that want to use my computer.  Now that i know how i can get it to boot ubuntu i think i reinstall with lilo.  

Tim

---

### Post by Herman on 2005-10-21
Thanks, isander, please keep us posted on how you get along because I'm really finding this GAG subject of ours extremely interesting! I'd like to learn more about it, and I'll try it out next week properly by installing it to the MBR, floppies and CDs when I get my experimental computer working again. I will really give GAG a good testing! I'll put lots of different operating systems on one hard disk and give it a good hammering! Cheers! (Herman). :D

---

### Post by Herman on 2005-10-22
It's actually very easy to make GAG boot floppies, (and, as many as you need), (My problem in the earlier post was just a bad batch of old floppy disks). 
The 'install .txt', inside the gag45 file tells you how. After reading it I just opened a terminal, stuck in a (new!) floppy disk, formatted it, and copied and pasted the command provided in 'install .txt' into my terminal.
Then I closed everything and re-started my computer and booted into the floppy's GAG set-up options. It has easy instructions to follow. This time, unlike with the CD (earlier post), after configuring GAG, you can write your configuration to the floppy disk and save it to that. Now we have a GAG boot floppy!
Now that I have a couple of GAG boot floppies made, I'm starting to like GAG. I can see that it has a few advantages over GRUB. One is you can easily make more that one floppy disk. Another (BIG ONE), is that you can avoid having your original MBR written over unless you decide to, so it won't cause people so much trouble booting their original operating system if they are dual booting. You can use it from floppy disks as long as you like, but the option is there to add it to your MBR if you want. Thirdly, it should be possible to add and remove operating systems as many times as you please and you only need to re-configure the GAG floppy disk, (or MBR) and that's pretty easy. 
Also, it's claimed to be able to handle multiple hard disks pretty well.
Disadvantages are it makes installing for the first time a bit more complicated, and for most people (I don't know what percentage), GRUB is good enough. So, you wouldn't know you need GAG until it's too late. I wouldn't imagine it's possible install Lilo any more easily than re-installing GRUB. 
Conversely, if you need to re-install GRUB anyway, you might as well go to Lilo and GAG, because you'll be more sure of a cure by trying something different than repeating the same mistake. In that case, you'd install GAG to your MBR, not mess around with floppies, to overwrite the botched GRUB MBR.
I'd say GAG would be worth a try for those having problems with GRUB. (Herman)

---

### Post by linuxlizard on 2005-10-26
Hey guys,
First- I'm the guy who recommended GAG and provided the directions. 
Second, lilo is not necessary for GAG to work. I don't use lilo, I use the ubuntu default.
Here is what you guys are doing wrong-
When partitioning when you first install ubuntu, you have to make your root partition bootable.
Then when ubuntu installer asks you several steps later if you want it to install grub to the mbr, you should say no. Do not select go back and do not select yes. If you select go back, grub is not written. If you select yes, grub will be written to the mbr instead of the root partition. If you select no, it will automatically write grub to the root partition instead of the mbr. It isn't asking you permission to write grub, it's asking if you want it on the mbr. What it isn't telling you is that it is really asking if you want it on the mbr or the root partition at this point. So select no and it will write to the root partition which is where you want it for GAG to use it.

Sorry for not checking back in on this thread sooner.
Cheers!

---

### Post by Herman on 2005-11-10
Hello, linuxlizard, thank you for your comments, and for being the first one to recommend GAG and provide the directions. I'm sorry I missed your original post, so I though isander might have got it from some other forum or somewhere.
I just think it's simpler to use Lilo with GAG, and have not had any problems, the GAG instructions say Lilo, but it's nice to know we can use GRUB too. Anyway, the main thing is it works very well! Thanks again, it might help quite a few people! I have included better instructions for it in my signature link.  :D  (Herman)

---

