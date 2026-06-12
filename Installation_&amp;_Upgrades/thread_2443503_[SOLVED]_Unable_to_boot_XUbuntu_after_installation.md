---
title: "[SOLVED] Unable to boot XUbuntu after installation"
date: 2020-05-16
forum: Installation &amp; Upgrades
---

### Post by alex5555 on 2020-05-16
I am trying to install Ubuntu 14.04 on a Fujitsu Futro S400 Thin Client computer. The specifications are as follows:

CPU AMD Geode NX 1500 1GHZ 32 bit (Similar to Athlon XP-M)
Chipset SIS741GX
RAM 896MB(1GB)
Embedded Graphic card SIS Mirage 128MB (Shared from RAM)
Compact Flash 32GB that works as IDE HDD

The 32GB Compact Flash already have Windows 98 on a 16GB FAT32 partition. I want to use the other 16GB to install Ubuntu and have a dual boot option.

I boot the XUbuntu Live Image from a USB drive and I can do the installation with no problems. But when I reboot it shows the grub error:

error: unknown filesystem. grub rescue>

If I do "ls" I can see two partitions, msdos1 and msdos2 on hd0. If I do "ls (hd0,msdos1)" and "ls(hd0,msdos2)" it show "unknow filesystem" for both.

I have reinstalled with different partition options xfs+swap, ext4 + swap, ext2 + swap, etx2 without swap. Grub is always installed to sda option. But I obtain the same error always.

I have tried with boot-repair live usb, and repaired it with different options like "purge grub", "legacy grub", "update grub to the last version". All options finish correctly but when I reboot i have the same error again.

If I boot with the XUbuntu live cd after installation with the "Try XUbuntu" option I can mount and see all the partitions correctly with GParted. And when I reinstall the installer can see the previous installation.

I don't know what more to try. I am thinking to try replacing grub by lilo, but I prefer grub.

I have choosen 14.04 because 16 and 18 crash at installation to busybox. I think that my computer is too old for that versions, but I am ok if I can install 14.04.

Thanks and sorry for my bad english.

---

### Post by ajgreeny on 2020-05-16
There is no point in trying to get any further as Xubuntu 14.04 lost any support a long time ago and you will not be able to install any applications, nor update anything already included in the OS and it will be a huge security risk.

Forget about Xubuntu on that old machine and perhaps have a look instead at other small distros such as Puppy with which you may have more success; I suspect, however, that the hardware is simply too ancient for any recent or useful distros to run successfully and maybe the compact flash card is not Linux bootable.

Other forum users may have more experience of such old hardware so keep looking in on this and you may get some other suggestions.

---

### Post by coffeecat on 2020-05-16
Hello, and welcome to the forum.

I think that will be an uphill task getting any currently supported Linux distro to work. You might find some pointers in this sticky thread: [Old Hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640). Bear in mind that that sticky thread is getting old as well - please read it with the understanding that some of the material may be obsolete now. 

Looking at your hardware specifications, I can see three significant challenges. It is a 32-bit system - recent Ubuntu releases are available for 64-bit only, although there are other 32-bit distros out there. You have less than 1GB RAM - Ubuntu and most of the favours are too heavy for that limited mount of RAM. I should imagine your live Xubuntu 14.04 is running very slowly. But the worst is the SIS Graphics. That is a nightmare.

But best of luck. Those with experience in resuscitating old hardware may be able to help.

---

### Post by alex5555 on 2020-05-16
Thanks for your answers. When I run XUbuntu 14.04 from live USB it runs reasonably fast and only consumes 300MB of the RAM. I only want the distro to play music with a player like Cantata. I have a very good Yamaha sound card on this computer and I want to take advantage of it on a modern environtment. My sensation is that this computer is capable to move correctly this distro, not with the best performance, obviously, but enough for my purpose.

---

### Post by CelticWarrior on 2020-05-16
Try Debian 32-bit. Again, do not use unsupported releases.

---

### Post by DuckHook on 2020-05-16
As my compatriots have already stated, use of 14.04 is highly insecure and therefore discouraged. However, if you are completely isolated from the Internet and disable the NIC, it can be reasonably safe. You will never get updates, patches or security fixes, but since your intent is to run this machine as a disconnected and stand-alone appliance, I suppose you can just take your chances.

However, should you wish to connect your machine to any LAN or the internet, then what follows is a technique that might work to keep you safe and your installation current.

**Start with the mini.iso**

Ubuntu Bionic still has 3 years of support left. Its 32-bit mini.iso image is available here: [http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/installer-i386/current/images/netboot/)

A mini.iso install is command line only. It is very stark and primitive, but since it installs so little, this is not usually a problem. Just follow the command line prompts, answer the usual questions about language, keyboards and locale, and you should have a simple command line interface up and running with no issues.

From here, you have two very different options:

**Option 1: Keeping it Simple**

The approach that is most likely to work is to keep your installation command line only. A number of ncurses and CLI music players work quite nicely from the command line. Among them are CMUS, MPD and MPG123. They aren't pretty, but if your main objective is to use your existing sound card, then they do this very well and your quality of sound is every bit as good as what you would get from the far more bloated GUI clients.

With a bit of post install configuration and tweaking, you could have a nice lean mean music player that not only runs well on your resource&#8209;challenged box, but does not rely on finicky GUIs, is secure and current, and is a breeze to maintain and update because it is so lean.

You won't have a GUI though. This is a deal-breaker if you wish to surf etc, but you did say that all you wanted to use it for was as a music playing appliance.

**Option 2: A Minimal GUI**

coffeecat is correct in citing your GPU as the weak point in your system. Therefore, it is not advisable to install a full DE of any kind. I would suggest a simple window manager. See my link "The Best 'buntu Flavour" for more details.

Let's say that you select Openbox. If you want the GUI to launch at login, it is probably advisable to use lightdm rather than gdm3. The latter may choke on your old GPU.

Next, you install the apps that you want, including Cantata. Please note that Cantata will drag in not only a bunch of gcc stuff but a massive number of qt libraries. You may wish to explore leaner GTK-based music player alternatives. Quod Libet immediately comes to mind, but it's easy to explore for others with a web search.

BTW, there's nothing preventing you from using CLI-only music players in a GUI setting.

**Dropping Ubuntu Altogether**

The last option is to go outside of the 'buntu ecosystem entirely. As CelticWarrior notes, some distros still maintain 32-bit images. Puppy and pure Debian have already been mentioned. I would add to these Slitaz and Bunsenlabs. Bunsenlabs is especailly interesting because, unlike Puppy and Slitaz, it installs as a traditional full installation on disk, but development seems to have slowed down recently.

---

### Post by CatKiller on 2020-05-16
> **DuckHook said:**
> BTW, there's nothing preventing you from using CLI-only music players in a GUI setting.

To add to this, the GUI that you use to control your CLI media player doesn't have to be on the same machine. 

Same use case, different hardware: I use volumio on a raspberry pi. That's MPD as the command-line media player and a lightweight webserver to pass commands to it. So I can control it from anything with a browser: phones, tablets, other computers in the house. I can also pass random things to it over DLNA if I want to.

---

### Post by alex5555 on 2020-05-17
Thanks for all replies. But I think that nobody has read my message completely. I have a problem with grub not recognizing the filesystem. Thanks and regards.

---

### Post by DuckHook on 2020-05-17
I have read your message completely, but perhaps I did not answer it frankly enough.

It is almost impossible to help you. No one uses 14.04 anymore. Because dead versions are so dangerous, I do not even have that ISO around to experiment with. And I won't put any time into re-learning 14.04 because such knowledge is dead knowledge and not worth investing in.

This is yet another reason why dead releases are so bad: no one can help.

If you try to install a supported release, then the chances for help go up greatly.

But like all things Linux, the choice belongs to you.

---

### Post by alex5555 on 2020-05-18
Finally installed XUbuntu on a usb pendrive. Removed all unnecessary startup tasks and applications. Now it's only using 4GB of disk and 500MB of ram with cantata running. It don't run with a great performance but enought for my purpose.

I tried to install XUbuntu to a different compact flash and it booted fine too. It seems that the problems is related to having the linux partition after the fat32 one on this machine. When the linux partition is positioned first, grub runs well. If I feel like it, maybe one day I will try to replace it with lilo.

The solution that I have accomplished is not the best but I'm content. Regards.

---

### Post by ActionParsnip on 2020-05-18
Could always drop gdm/lightdm and go with slim instead

---

### Post by alex5555 on 2020-05-19
@DuckHook, thank you very much for recommending me using Openbox. I have installed it and now the systems runs faster and with a low cpu consumption.

Thanks to all, I will mark the post as solved.


[https://i.postimg.cc/nc3LSFHZ/Screenshot.png](https://i.postimg.cc/nc3LSFHZ/Screenshot.png)

---

