---
title: "Installing 13.10 without formatting hard disk"
date: 2014-02-19
forum: Installation &amp; Upgrades
---

### Post by jesse13 on 2014-02-19
Hi, I'm new to ubuntu and am trying to install it on an old dell that is loaded with viruses and won't launch windows xp anymore. I used unetbootin to make a usb drive and got the ubuntu installation to load. I'm not comfortable with losing all the files on my hard disk, so I would like to not reformat the disk and partition ubuntu to only the free space. When I select the "something else" option it takes me to a screen where I see the flash drive and the internal hard disk. 

From the reading I've done on the forum, I think it's the "swap" option that I need to select, but when I click that and press install, it says "no root file system is defined." I'm sorry for the noob question, if you could, please point me in a direction to try to find which options to select. Any help is greatly appreciated!

Thanks,
Jesse

---

### Post by varunendra on 2014-02-20
Welcome to the forums Jesse !

Swap is just a raw space that is used as a virtual RAM (when your system needs more memory than the Physical RAM has), it is not necessary to be created separately.

The system is installed on "EXT(2/3/4)" partition(s) which must be created separately and one of such partitions must be selected as a "Mount Point" for root (/).

If you need specific and safe instructions, please post either screenshot of "Gparted" (showing your system's hard disk), or open a terminal (Ctrl-Alt-T) and post back the output of the following command -
```
sudo parted -l
```

You can do both from a Live CD/USB from which you have booted and are going to install Ubuntu.

If posting the command output, please wrap it within 'Code' tags to preserve its formatting. To see a quick "HowTo" with screenshots on using 'Code' tags, please follow the link in my signature.

---

