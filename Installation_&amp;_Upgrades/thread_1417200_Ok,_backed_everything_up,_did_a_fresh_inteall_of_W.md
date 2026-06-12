---
title: "Ok, backed everything up, did a fresh inteall of Windows 7, need help"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by IcyRhythms on 2010-02-27
i also created a partition on my D:

i just don't know how to find it. i labled it Ubuntu (F:)

i want to install ubuntu on that partition, is there a step by step with pictures and such for this?

---

### Post by BenAshton24 on 2010-02-27
1) Delete the partition that you made for Ubuntu.
2) Boot your Ubuntu CD and go through the install process.
3) When you get to the partitioning section, It should say that you have windows 7 installed aswell, select "Install them side by side, choosing between them...", and click next.
4) Finish the installation process and when you reboot you should be presented with the option to boot windows or Ubuntu.

Here is a step-by-step guide on installing...
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
I can't find a tutorial that is specific to what you are looking for but I reckon that you will have no trouble merging this with the instructions above. (basically, when you get to this section [http://www.psychocats.net/ubuntu/images/installingkarmic09.png](http://www.psychocats.net/ubuntu/images/installingkarmic09.png) select the top option instead...)


Hope this helps :)
Ben.

---

### Post by IcyRhythms on 2010-02-27
ben, when choosing your suggestion, the installation wants to seperate win 7 and ubuntu with HUGE differences in size. 713GB for win7 and 699GB for ubuntu. i think you want me to go ahead and select the first option which is to install them side by side...do i really need that much free space for ubuntu?

---

### Post by IcyRhythms on 2010-02-27
ok, i've got it all installed, but i have no sound at all. i tried setting my sound blaster xfi card as the output device, and i still get nothing.

edit:damn, just realized i can't watch youtube videos either. it won't let me install adobe.:(

---

### Post by wilee-nilee on 2010-02-27
> **IcyRhythms said:**
> ok, i've got it all installed, but i have no sound at all. i tried setting my sound blaster xfi card as the output device, and i still get nothing.

edit:damn, just realized i can't watch youtube videos either. it won't let me install adobe.:(

I assume your talking about youtube in Ubuntu. Find in synaptic ubuntu restricted extras that will install most of what you need. You also might want VLC and smplayer as well for media players.

---

### Post by underquark on 2010-02-27
Next you'll be asking about playing DVDs.  You might need this:

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

---

### Post by BenAshton24 on 2010-02-27
Hey, first time Linux is the worst part. Nothing works and you tear your hair out trying to fix everything only to discover that the thing you were trying to fix wasn't actually broken :P stick with it and you'll get the hang of it.

If you wanted to install ubuntu on a smaller section of your hard drive, the easiest way, if you are new to Linux, is to create another partition leaving the amount of space you want to put Ubuntu on unpartitioned.

For your sound, follow these instructions: [http://www.fusetext.com/2009/05/ubuntu-linux-creative-sound-blaster-x-fi-driver-installation-how-to/](http://www.fusetext.com/2009/05/ubuntu-linux-creative-sound-blaster-x-fi-driver-installation-how-to/)

For adobe flash, you want to do the following. In the menu's on the top bar, click on System -> Administration -> Software Sources. You may be prompted to enter your password, after this, check the box that says "Software restricted by copyright or legal issues (multiverse)" now click close. A dialog box should appear asking you if you want to reload the repositories. Click "reload" and wait 'till it's finished. Now, on the top menu, click, Applications -> Accessories -> Terminal. A terminal window should now open (you will become more familiar with this further into your Linux journey :P) Type the following and press enter:
```
sudo apt-get install flashplugin-nonfree
```
You will be prompted to enter your password, however, note that no text will show up whilst you are entering it. The above command simply install flash player.

Also, note that you can find lots of useful information in the Ubuntu wiki: [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

Hope this helps,
Ben.

---

