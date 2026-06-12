---
title: "Install Problems"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by Ttrain15 on 2009-12-03
Hello. I am having trouble installing Ubuntu 9.10 on my system. I did install it as a dual boot type, but every time I click on Ubuntu out of the two choices it brings up what looks to be a command prompt thing. I then pressed F12 and chose the CD drive and it brings up the Ubuntu main page, but it won't let me choose any of the available options, such as 'Install Ubuntu' and whatever other choices there are. Any help would be appreciated.

---

### Post by darkod on 2009-12-03
Download and run the script in my signature. It will show your whole boot process. If it's downloaded for example on desktop you can run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file. Copy the content of that file here but please put CODE tags around it. You can do that by selecting the whole text and hitting the # button in the toolbar here when you write the post. It makes it easier to read because it's long.

---

### Post by Ttrain15 on 2009-12-03
Ok, I downloaded it, but how do I run it?

---

### Post by darkod on 2009-12-03
Open terminal, (Applications -> Accessories -> Terminal) and depending where the script is run:
sudo bash ~/Desktop/boot_info_script*.sh

Or if it's in your Downloads folder
sudo bash ~/Downloads/boot_info_script*.sh

If it's easier for you first just move the script to your Home folder and in terminal just run:
sudo bash boot_info_script*.sh

---

### Post by Ttrain15 on 2009-12-03
I am running Vista currently, and its in my downloaded folder. See, I have Ubuntu on a Cd that I burned it to, and I installed it inside of Vista. Every time I try to boot Ubuntu, it brings up a boot menu/command prompt looking thing. I tried picking the CD drive after pressing F12 after rebooting, and it brings up Ubuntu. The problem is that it wont let me choose any of the available options, but it will let me press any F-x I want. So I haven't even got Ubuntu running yet.

---

### Post by darkod on 2009-12-03
OK, common misunderstanding. In your first post you said you have dual boot, if you installed with wubi (inside windows) that is a different ball game. And you should have marked the post with "wubi" not "ubuntu".

As for ubuntu not running, you can always boot with the cd and select Try ubuntu option and that will open a fully working ubuntu running from the cd with internet access and everything. I thought that's what you are doing.

If you indeed used wubi and installed inside Vista, I'm sorry but I do not know that setup good enough to give you advice. My only advice would be to consider removing wubi (in add/remove programs) and do a so called "proper" install side-by-side. But the choice is up to you, entirely. That is just my personal opinion.

---

### Post by Ttrain15 on 2009-12-03
Actually, I've tried clicking on that, and it still doesn't work. None of the options when I do that work. Could you please clarify what Wubi is?

---

### Post by darkod on 2009-12-03
Wubi stands for Windows UBuntu Installer. You can read more here: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
In short, it makes it possible to install ubuntu inside windows, sort of like "virtual" ubuntu. It will dedicate a certain amount of space on one of your partitions for ubuntu, and install it there simulating dual boot. But it is NOT what is usually referred to as dual boot, having two operating systems next to each other on your hdd on separate partitions.
The easiest way to check if you have wubi is in Vista go into Control Panel, Programs. Look towards the bottom, if there is Ubuntu entry, then that's wubi install. Windows can't see any linux installation if it's done as dual boot on separate partitions. If it has Ubuntu entry then it's wubi install inside windows.

Just for the record, you do not install ubuntu or any other OS from inside an already running OS. If you started your Vista, then put the ubuntu cd in and just selected to start the installation process, that's only wubi installing inside windows. You need to actually boot from the installation media, for any OS.

---

### Post by Ttrain15 on 2009-12-03
Ok, so how exactly do I install side by side?

---

### Post by darkod on 2009-12-03
First step, remove wubi with add/remove programs (control panel, programs) just like you remove any windows application. That will delete the folder (space) dedicated to wubi and free that space.

The second step is to defragment your hard drive to make shrinking vista easier. Vista partition(s) will have to be shrinked in order to make free unpartitioned space for ubuntu.

But just to make sure I give you good advice, please post a screenshot of the Disk Management in windows, it will show your current partitions. You can open disk management by pressing the windows button + R, and in the small window type diskmgmt.msc and hit enter.

Attach that screenshot to check your partitions if you want to.

Otherwise, check here how the process looks like, what to expect later: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Ttrain15 on 2009-12-03
For some odd reason, it doesn't seem to want to uninstall. Some other way to uninstall it?

---

### Post by darkod on 2009-12-03
Not really. You see this is one of the reasons I don't recommend wubi. And this can't be blamed only on ubuntu. It's not easy to make linux and windows "play" together.
If you remember which partition (C:, D:, E:) you instructed it to install onto, you can go there and there should be large folder called ubuntu. Just delete it.
But the entry in your bootloader will remain that way. You will have to boot with your vista dvd and repair the bootloader to the default one that will just boot vista straight away.

---

### Post by Ttrain15 on 2009-12-03
Actually, I went to command prompt and deleted it, then went to the c drive and deleted the folder. I have finally removed it.

---

### Post by darkod on 2009-12-03
Do you have only one single partition on your hdd, only C: ?

---

### Post by Ttrain15 on 2009-12-03
I only have one, the other one is only 102 MB.

---

### Post by darkod on 2009-12-03
Open the link I gave you for the graphical install, look at the screenshots to get familiar with the process a little bit.
Then put the ubuntu cd in the cd-rom and if it pops-up with any install message just close that. Restart the computer and upon the boot it should start with the Ubuntu install screenshot. From there just follow the guide. Before starting it calculate how much space you need for your vista, how much space you want to dedicate to ubuntu. The installer will ask you that.
Any specific questions, ask.

---

### Post by Ttrain15 on 2009-12-03
So what do I do if it doesn't start up with the ubuntu logo screen?

---

### Post by darkod on 2009-12-03
It will, don't worry. Just make sure you are booting from the CD-ROM and not the HDD. I don't know if you are familiar with BIOS settings but you might need to set CD-ROM to boot first.
In fact, once you have booted with the ubuntu cd the menu will also show Try Ubuntu option. You can use that first and that will load working ubuntu running from the cd. You can even have internet, look around how you like it, test audio, video, networking. Basically that will show if any of your hardware doesn't work correctly.

Then either double click the icon Install on the desktop or reboot again with the cd inside and this time select Install Ubuntu option at the menu.

---

### Post by Ttrain15 on 2009-12-03
Ok, I did what you said to do, but when I get to that main screen, it will not let me choose any of the options. What is wrong with it?

---

### Post by darkod on 2009-12-03
Hmm... Pressing the up/down arrows doesn't work? You might need to go into BIOS and enable USB Legacy support. If you have usb keyboard it might no work properly without usb legacy enabled.

---

### Post by Ttrain15 on 2009-12-03
No, the up and down arrows work, its just selecting the option that wont work. Say I have 'Try Ubuntu...' highlighted, when I press ENTER, it wont do anything.

---

### Post by Ttrain15 on 2009-12-03
So, do you have any idea's on how to make this work??

---

### Post by darkod on 2009-12-03
No idea. :(
You can try selecting the Install Ubuntu option, and if you click Quit on any of the steps it will continue and load Ubuntu from the cd just to try it, basically like the Try Ubuntu option. I'm curious if the same wil happen after hitting Enter on the Install Ubuntu option. If it does, I really have no idea except to try burning another CD at very low speed, 8x or 4x. It might be error on the cd.

---

### Post by Ttrain15 on 2009-12-03
Alright, thanks I will try to burn a new cd. If it doesnt work still, then I will stay with vista :/

---

### Post by Ttrain15 on 2009-12-03
Well, I burned it to a new disc at a slower speed, and it still won't let me choose an option when I press ENTER. Still no idea's?

---

