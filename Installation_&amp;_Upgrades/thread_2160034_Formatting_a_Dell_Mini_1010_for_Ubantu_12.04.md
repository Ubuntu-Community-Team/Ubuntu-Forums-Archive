---
title: "Formatting a Dell Mini 1010 for Ubantu 12.04"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2013-07-05
I have a dual boot Ubuntu/Win XP on a Dell Mini 1010 with no CD/DVD drive.

I now wish to reformat the hard drive do a clean install of Ubuntu using a bootable USB.

1. I assume I need to create a linux universal USB installer on the Scandisc Cruzer 8GB Flash Drive that I have just purchased.

2. How do I start the reformatting to clear everything from the HDD ( Is this the same as returning to factory settings) - I do not need any of the information as it is backed up on my main desktop.

3. How do I check that the Dell will accept the flash drive.

Some guidance and links would be appreciated.

---

### Post by snowpine on 2013-07-05
Just follow the easy instructions here: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

I recommend to Try Without Installing first for a few days, to make sure your hardware is well-supported and that you like the current release. :)

---

### Post by DeathByDenim on 2013-07-05
1. Correct
2. During the installation, you have the option of using the entire disk. This will reformat the entire hard drive, erasing everything that was on it (including Windows).
3. If you plug in the USB and it doesn't boot from it, you need to check the BIOS. I'm not sure which key you need to press to enter it, but it's usually <F2> or <Del>. It might even indicate so on the screen when you boot the computer. Once you are in, there should be a menu where you can configure the boot order. Make sure the USB is on top.

If there is no option to boot from USB, you will have to burn the iso to a CD and use that, but most computer should be able to use the USB.

(or do what snowpine suggested, who beat me to this post by two minutes :) )

---

### Post by ajgreeny on 2013-07-05
If the Dell Mini 1010 is a small Atom cpu netbook, as I believe it is, you will probably do a lot better running Xubuntu or even Lubuntu; I suspect that Ubuntu with unity will be too resource hungry for that hardware.

---

### Post by angel mike on 2013-07-05
Thanks for all your contributions - very useful.
I have been running Ubuntu 12.04 for about a week in dual boot with Windows XP with no problems apart from the wireless which was sorted by the community. I use it mainly for internet search and gmail. Pics and other medis are done on my main computer.
Is the single boot version of ubuantu much larger than the one I am using?
I like the idea of a fully supported OS until at least 2017 - the reason I am leaving XP is it only supported until April next year and Window 7 is too big.
Your right about the net book Dell Mini 1010 has Intell(R) Atom(TM) CPU z530 @1.60 GHZ 797 M Hz 0.99GB of RAM.
How different is the other version and does it have long term support. Would I be able to try it though my dual boot?

Thanks.

---

### Post by snowpine on 2013-07-05
I am confused... if you already have Ubuntu 12.04 installed and functional, then you're good to go. There is no need to do anything special; it's the same Ubuntu whether you are dual booting or single booting. :)

---

### Post by angel mike on 2013-07-05
> **snowpine said:**
> I am confused... if you already have Ubuntu 12.04 installed and functional, then you're good to go. There is no need to do anything special; it's the same Ubuntu whether you are dual booting or single booting. :)

Thanks snowpipe but I read a response on the board that it was better to have a single boot. Although the system functions ok I feel it would probably be quicker with a reformat - which it is probably due for as I have used it for the last 4 years.
I have looked at Xubuntu and see there is a similar version with support - but some of the reviews say there is not a lot of difference. If I removed xp that would free up more space than changing to the X version - or do you disagree.

PS I am impressed with the response speed to these posts - you must live in your computers !

---

### Post by snowpine on 2013-07-05
You can install the X version with a few mouse clicks by following this guide (you do not need to reinstall): [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

I bet Xfce desktop will make a noticable boost in performance on your hardware; try it now! Another good one to try is LXDE (lubuntu-desktop). 

If it were me, I would wait until April 2014. That is when Windows XP hits its "end of life" and it is also when Ubuntu will release 14.04, the next long term support (LTS) release. You could do a fresh reinstall at that time (instead of upgrading). 14.04 will be supported until 2019, which is probably past the life of your hardware.

---

### Post by angel mike on 2013-07-06
Thanks again snowpine - especially about the April release. I think I will take your advice and just play around with the dual boot ubuntu version. Presumably I could try Xubuntu and then switch back to ubuntu if need be.

---

### Post by ajgreeny on 2013-07-07
> **angel mike said:**
> Thanks again snowpine - especially about the April release. I think I will take your advice and just play around with the dual boot ubuntu version. Presumably I could try Xubuntu and then switch back to ubuntu if need be.

Yes you can.
First use terminal to produce a list of all the packages that will be installed with ```
sudo apt-get -s install xubuntu-desktop > /home/username/de.txt
``` which will quickly simulate the installation and produce a text file called **de.txt** in your home folder which will include a long list of the packages to be installed.

If you subsequently decide afetr installing it and trying for a while that you don't want to keep xubuntu-desktop you can copy the list of packages from that file and use ```
sudo apt-get purge <copy-of-list-of-packages>
```

I am sure there must be other ways of ensuring that all the packages needed for xubuntu-desktop are removed when you want to do so, but this is certainly one way to do it that will work.

---

