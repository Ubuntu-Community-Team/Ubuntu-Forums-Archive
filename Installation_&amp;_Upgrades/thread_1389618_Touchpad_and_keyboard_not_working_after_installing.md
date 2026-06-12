---
title: "Touchpad and keyboard not working after installing Karmic 9.10 on EEE 1005"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by doctehroc on 2010-01-24
I bought a new Asus EEE 1005-PAB. It has a Atom n450 prcessor that runs in 64 bit so I want to install a 64 bit distro so netbook remix is out of the question, I decided to go with Kubuntu 9.10. Everything works perfectly in the live cd but after install my touchpad and keyboard dont work..i can use a usb mouse and keyboard to get around. my xorg has no entries for input or keyboard, im guessing because it cant load the driver modules. 

I installed jaunty and they work fine but jaunty is not optimized for netbooks and I couldnt get my wirless or wired internet to work, so I really want to get karmic working. Any thoughts?

---

### Post by omskates on 2010-01-25
Maybe try running the standard build of KNR.  Your 64bit will run it.  I've experienced good performance with Kubuntu Netbook 9.10 32bit on a SanDisk Cruzer flash drive; Asus Eee 900 with >1GB RAM.  Only problems I came across was attempting to do a > sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
 after enabling 3rd party software and medibuntu repositories renders flash drive unbootable.  I believe it was likely the dist-upgrade that should be avoided.  Otherwise everything was working.

---

### Post by doctehroc on 2010-01-26
I tried KNR it worked perfectly in the live cd until I installed it to the hard drive then I had the same problem after installing to the hard drive. My aim was really to run a 64 bit OS and the only buntu that installed and worked was Jaunty but it wasn't well suited to the netbook and took some work to get my ethernet and wirless to work. 

Ive had my eee for 2 days now and the first day I installed or attempted to install at least 5 different distros and none went smoothly at all and the only one to install was kubuntu 9.04 but like I said it wasnt well suited for netbooks. I ended up installing windows 7 ultimate x64 version and contrary to all of my previous windows experiences it installed front to back with no issues and all my hardware worked from the get go all i installed afterwards was the power saving and Fn key proggys from asus site. I hate to be the guy that praises MS on the ubuntu forums, especially because Ive been a linux user for a long time now, but I have to say score one for Winblows.

---

### Post by doctehroc on 2010-01-26
I dont mean to kill the thread with that last post lol. I still want to run ubuntu on my eee so If anyone knows how to solve the touchpad / keyboard problem in karmic plz, Im open to suggestions

---

