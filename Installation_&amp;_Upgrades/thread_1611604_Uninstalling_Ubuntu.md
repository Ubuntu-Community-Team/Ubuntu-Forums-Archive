---
title: "Uninstalling Ubuntu"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by bigtel on 2010-11-02
I have installed Ubuntu on my Vista Laptop to see what the latest version performed like. It's running fine as a duel boot system...but I now want to uninstall Ubuntu to leave just Vista again.

Can you tell me how is this done?

Thanks.

---

### Post by cpmman on 2010-11-02
Did you install using Wubi or did you use a live cd to install into its own partition(s)?

---

### Post by bigtel on 2010-11-02
I used the live CD to install

---

### Post by bcbc on 2010-11-02
> **bigtel said:**
> I used the live CD to install

First thing is to replace the bootloader in the drive MBR. Right now you will have grub2 pointing to the ubuntu partition. Replace it with the windows bootloader by booting a recovery CD and running:
bootrec.exe /fixmbr

If you don't have a windows repair, lilo works well enough. Boot your ubuntu from the live CD and run from terminal (CTRL-ALT-t)
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Ignore warnings as it relates to booting linux, not windows. (PS change /dev/sda if for some reason your main drive is shown as /dev/sdb etc. Usually it is /dev/sda)

Then once you've replaced the bootloader, you should always boot straight into Windows. Reboot to test. At this point, you can just use the vista disk utility to reformat the ubuntu partition(s) and then combine it to the windows partition or leave it separate.

---

### Post by bigtel on 2010-11-03
Thanks for your help. I will give this a go.

If I install Ubuntu on my main PC,is there a way of changing the grub order so that it will automatically boot to Vista rather than Ubuntu?

---

### Post by wilee-nilee on 2010-11-03
> **bigtel said:**
> Thanks for your help. I will give this a go.

If I install Ubuntu on my main PC,is there a way of changing the grub order so that it will automatically boot to Vista rather than Ubuntu?

Look in Ubuntu's synaptic for startup manager this will let you default the boot and change the time out.

---

### Post by bcbc on 2010-11-03
> **bigtel said:**
> Thanks for your help. I will give this a go.

If I install Ubuntu on my main PC,is there a way of changing the grub order so that it will automatically boot to Vista rather than Ubuntu?

There are a number of options. The thread "[Grub2 title tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")" is a good place to start. One of the links on this page ([meierfra's custom menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")) is one I've used and it works well.
You could also keep the windows bootloader and use easybcd to boot ubuntu - I've never done this.

---

### Post by Quackers on 2010-11-03
Yes. The easiest way is probably by installing Startup Manager via Synaptic.

---

### Post by bcbc on 2010-11-03
> **Quackers said:**
> Yes. The easiest way is probably by installing Startup Manager via Synaptic.

It's the easiest - but you have to keep updating it every time you install a new kernel. Otherwise it might just run the memory check instead ;)

---

### Post by wilee-nilee on 2010-11-03
> **bcbc said:**
> It's the easiest - but you have to keep updating it every time you install a new kernel. Otherwise it might just run the memory check instead ;)

I always forget to mention that part, I wasn't sure if it was still reading the same line, thanks.

The other links are excellent ones for learning. I do some grub2 customizing, I don't use startup manager in general.

---

### Post by Quackers on 2010-11-03
> **bcbc said:**
> It's the easiest - but you have to keep updating it every time you install a new kernel. Otherwise it might just run the memory check instead ;)

Yes you do :-) It's true.

---

### Post by bigtel on 2010-11-03
Thanks for your help on this.

I am thinking I may leave Ubuntu installed and just change the boot order. (I always feel safer surfing and e-mailing while using Ubuntu rather than windows based systems.)

Big Tel

---

### Post by Advait on 2010-11-03
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr 
What do I do if my main drive (that has my Win 7 partition) shows up on  grub as "Windows 7 on /dev/sdb1" AND "Windows 7 on /dev/sdb2"? 

Do I type in 

sudo lilo -M /dev/sdb1 mbr
sudo lilo -M /dev/sdb2 mbr

???

I'm new to Ubuntu and the command line. Thanks, -Tom

*******************
> **bcbc said:**
> First thing is to replace the bootloader in the drive MBR. Right now you will have grub2 pointing to the ubuntu partition. Replace it with the windows bootloader by booting a recovery CD and running:
bootrec.exe /fixmbr

If you don't have a windows repair, lilo works well enough. Boot your ubuntu from the live CD and run from terminal (CTRL-ALT-t)
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```Ignore warnings as it relates to booting linux, not windows. (PS change /dev/sda if for some reason your main drive is shown as /dev/sdb etc. Usually it is /dev/sda)

Then once you've replaced the bootloader, you should always boot straight into Windows. Reboot to test. At this point, you can just use the vista disk utility to reformat the ubuntu partition(s) and then combine it to the windows partition or leave it separate.

---

### Post by Quackers on 2010-11-03
> **Advait said:**
> sudo apt-get install lilo
sudo lilo -M /dev/sda mbr 
What do I do if my main drive (that has my Win 7 partition) shows up on  grub as "Windows 7 on /dev/sdb1" AND "Windows 7 on /dev/sdb2"? 

Do I type in 

sudo lilo -M /dev/sdb1 mbr
sudo lilo -M /dev/sdb2 mbr

???

I'm new to Ubuntu and the command line. Thanks, -Tom

*******************


As bcbc showed there is no number after sdb !!! Just the letters, otherwise you will be trying to install it to a partition instead of the MBR of the drive.

---

