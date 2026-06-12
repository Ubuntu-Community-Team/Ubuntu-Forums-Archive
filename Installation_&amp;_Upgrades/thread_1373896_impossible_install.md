---
title: "impossible install"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by Danilo1 on 2010-01-06
I used Ubuntu 8.04 for more than a year and was very happy with it. I wanted to upgrade to the latest version and made the step to upgrade to 8.10 first. 
This appeared to work well (looked a lot like 8.04) so I took the next step to upgrade to 9.04. 
:mad:Then my problems started. 

Though Grub gave me the choice to start my newly installed version, there was just a prompt. Since I don't speak enough Linux I decided it would be a good choice to upgrade directly to version 9.10 by installing it from a live DVD I have.
No way! 
The installation started all right, but stopped at 27% for no obvious reason. 
(I retried to install 9.10 again and again. The farthest I got is that it doesn't go passed the closing ("allmost ready!") screen of the installation when my computer is halted altogether. I can only switch it off)

Now I have a non working computer. It does something with the live Cd, but I can not install any version of Ubuntu any more. Not even the (once working) 8.04 or 8.10.

All my computer does now is start Grub and stop on Error 2. I'm not a Windows fan, but would appreciate a working system. Even if it's only XP. :sad:

How do I uninstall Grub and get the control over my computer back?

---

### Post by presence1960 on 2010-01-06
> **Danilo1 said:**
> I used Ubuntu 8.04 for more than a year and was very happy with it. I wanted to upgrade to the latest version and made the step to upgrade to 8.10 first. 
This appeared to work well (looked a lot like 8.04) so I took the next step to upgrade to 9.04. 
:mad:Then my problems started. 

Though Grub gave me the choice to start my newly installed version, there was just a prompt. Since I don't speak enough Linux I decided it would be a good choice to upgrade directly to version 9.10 by installing it from a live DVD I have.
No way! 
The installation started all right, but stopped at 27% for no obvious reason. 
(I retried to install 9.10 again and again. The farthest I got is that it doesn't go passed the closing ("allmost ready!") screen of the installation when my computer is halted altogether. I can only switch it off)

Now I have a non working computer. It does something with the live Cd, but I can not install any version of Ubuntu any more. Not even the (once working) 8.04 or 8.10.

All my computer does now is start Grub and stop on Error 2. I'm not a Windows fan, but would appreciate a working system. Even if it's only XP. :sad:

How do I uninstall Grub and get the control over my computer back?

I would back up my data and do a clean install of 9.10 instead of dist-upgrades. In case you haven't noticed there are a lot of threads in here about dist-upgrade problems. A clean install of any OS whether Linux or windows is always the best option. There are just too many problems that can & do occur with dist-upgrades. IMHO dist-upgrades are the lazy way of doing things. In order to avoid perceived work we roll the dice and hope it works. Again the safest bet is to back up your data and do a clean install.

---

### Post by Danilo1 on 2010-01-06
But that's what happened. When it seemed to be impossible to start 9.04 after the update I did. I started a complete new installation of 9.10.

---

### Post by kansasnoob on 2010-01-06
> Though Grub gave me the choice to start my newly installed version, there was just a prompt.

That sounds somewhat like a graphics problem. I was lucky with 9.04, not so much with 9.10.

As far as the fresh install failing, did you check the md5sum of the downloaded iso?

Did you select "Check disc for errors" from the initial Live CD boot menu?

If you answer yes to both of those my only suggestion would be to reinstall Ubuntu Hardy (8.04.3). It's still supported until April 2011 and so far Lucid (10.04) is looking fairly promising, and it's also an LTS release.

If at some point you want to just temporarily restore a Windows bootloader that's also possible.

---

### Post by kansasnoob on 2010-01-06
> It does something with the live Cd, but I can not install any version of Ubuntu any more. Not even the (once working) 8.04 or 8.10.

Sorry I hadn't paid attention to that. Can you even boot to a Live Desktop, that is choosing "Try Ubuntu without chages ........"?

If so maybe we should look at the partitioning arrangement:

```
sudo fdisk -l
```

More human readable (if it has only one drive it's likely sda):

```
sudo parted /dev/sda print
```

I recently reinstalled Hardy in a multi-boot with 9.04, Mint Gloria, 9.10, and 10.04 and the only way I could get it to install was to choose to use no bootloader. Of course then I had to fix that after installation.

I also wonder if all installs seem to stop about the same place? It's possible that you have a faulty CDROM drive. They do get dirty, I've more than once had to break things open and bust out the isopropyl alcohol and qtips.

---

### Post by presence1960 on 2010-01-06
if it is a video card problem hit F4 at menu screen when you boot the Live Cd and choose Safe graphics mode. See here for more info and other options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by kansasnoob on 2010-01-06
> **presence1960 said:**
> if it is a video card problem hit F4 at menu screen when you boot the Live Cd and choose Safe graphics mode. See here for more info and other options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

+1! I hadn't thought to mention that.

---

### Post by Danilo1 on 2010-01-07
I also wonder if all installs seem to stop about the same place? It's possible that you have a faulty CDROM drive. 

Thought about that, but I burned 2 iso CD's so if they both stop at about the same level of installing??
Note, on trying to reinstall older, earlier versions I also tried different issues of 9.10 since I got one with a magazine too?????

[quote/]They do get dirty, I've more than once had to break things open and bust out the isopropyl alcohol and qtips.[/quote]

So, to be sure I just cleaned it! \\:D/

If I insert my CD with 9.10 on it an start the installation proces from the main menu (in safe graphic mode as suggested) it seems to start the process. (yesterday, the installation was "almost" complete. 
While saying the process was almost done my computer froze and I could only switch it OFF. 
Ok, I waited about 20 minutes to be sure, but the clock had stopped too so it seemed pretty obvious my system had halted)

After reinserting the CD that seemed to work yesterday. I now have a blinking dsplay. 
It said it was looking for network time, it controlled the drives and it was detecting systems. No further progress.
If I switch the computer off is says: please remove the disc and close the tray (if any) then press ENTER

Now what????

---

