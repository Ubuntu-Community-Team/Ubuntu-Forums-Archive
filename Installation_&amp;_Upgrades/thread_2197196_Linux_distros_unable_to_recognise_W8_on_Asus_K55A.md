---
title: "Linux distros unable to recognise W8 on Asus K55A"
date: 2014-01-02
forum: Installation &amp; Upgrades
---

### Post by s0563764 on 2014-01-02
Hi,

I've been struggling with the windows 8 and installing Linux distros. I had managed to install Xubuntu on to the laptop, but after a bad update I decided to erase the partition. I managed to install Linux Mint, but on the boot menu it said it was missing (tried boot repair etc). As I generally only use Linux distros in everyday, bar games and a few things I decided to reinstall W8 and start from scratch. The reinstall restored the Windows OS, Data and recovery partition. But still left linux partition intact, so I erased it and resized my data partition of windows, making it 500gb again.

My issue now, no matter if I try Zorin OS, Linux Mint, Lubuntu etc, I can't get them to "see" the windows being on the laptop when I try to install. If I look at my boot options there is still an "ubuntu" option, but there is currently nothing in place. Any ideas what I should do to get a dual boot back in?

Thanks

---

### Post by fantab on 2014-01-02
You have to [disable 'fast startup']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html") in Windows8.
More details [HERE]("http://ubuntuforums.org/showthread.php?t=2147295&p=12657352#post12657352").

---

### Post by s0563764 on 2014-01-09
> **fantab said:**
> You have to [disable 'fast startup']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html") in Windows8.
More details [HERE]("http://ubuntuforums.org/showthread.php?t=2147295&p=12657352#post12657352").
Thanks for the reply. I don't have fast start up enabled. What I noticed is I still have ubuntu showing if I go to the boot menu, however, if I try booting this it goes to grub rescue. I'm aware I have erased the partition previously. I thought by reinstalling W8 the system would be back to factory settings. Any ideas? I installed it before, but now I am unable to do so without erasing Win8.

---

### Post by Mark Phelps on 2014-01-10
>  I don't have fast start up enabled. Actually, unless you made the effort to manually disable it, then yes, you DO have Fast Startup enabled -- as that is the default with Windows 8.

---

### Post by fantab on 2014-01-10
Do you still have Ubuntu installed? 
You have reinstalled Win8, right? How did you install it? Did you install it in UEFI mode or 'legacy/BIOS/MBR/CSM' mode?

Can you run a Live Ubuntu DVD/USB, without installing? 
If you can then boot it, download and install [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair") utility, run BR to '***Create a Bootinfo Summary***'. Note the Link it creates and post back that LINK here.

---

