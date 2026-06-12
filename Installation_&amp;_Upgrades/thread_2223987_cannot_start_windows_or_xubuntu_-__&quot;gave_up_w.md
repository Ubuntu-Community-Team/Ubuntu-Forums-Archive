---
title: "cannot start windows or xubuntu -  &quot;gave up waiting for root device&quot;."
date: 2014-05-14
forum: Installation &amp; Upgrades
---

### Post by meself on 2014-05-14
i just installed dual boot xubuntu 14.04lts on my windows7 hp pavilion dv6 laptop.  the menu comes up with both operaing systems and memory tests.  but cannot enter any selection on the menu.  "gave up waiting for root device".

screenshot is at [=92203269&filters[recent]=1&sort=1&o=0"]http://s618.photobucket.com/user/meselffff/media/IMG_20140513_231654.jpg.html?filters[user]=92203269&filters[recent]=1&sort=1&o=0]("http://s618.photobucket.com/user/meselffff/media/IMG_20140513_231654.jpg.html?filters[user)

i'm not an experienced linux command line guy.  just use the gui like windows so i'm in the dark with this.

---

### Post by kc1di on 2014-05-14
Try running boot-repair found [here.]("https://help.ubuntu.com/community/Boot-Repair")
follow the instructions for the CD version when it's done running it will give you a web address copy that down
and if you still can't boot paste the webpage here it will contain a file that may give important clues as to why it won't boot. 
Good Luck

---

### Post by meself on 2014-05-14
Thank you kc1di!  i got both the 64 bit and 32 bit boot repair discs but the screen that comes up when i boot from them is very different from the selections shown on the download page.  the screen i gets these menus with no utility that actually runs from the cd.  screenshot is [http://s618.photobucket.com/user/meselffff/media/IMG_20140514_065333.jpg.html]("http://s618.photobucket.com/user/meselffff/media/IMG_20140514_065333.jpg.html")

---

### Post by kc1di on 2014-05-14
hit enter at that screen see what happens :)

---

### Post by meself on 2014-05-14
Thank you for your helpfulness Dave!  But I think i'm going to take a different route and install just centos on the entire drive for now instead without the dual boot.  And when I have time, I'll pick up an oem copy of windows 8.1 because this hp version of windows 7 makes life pretty miserable for dual booters, then perhaps install dual boot centos.  I remember four years ago when I bought this machine it took two weeks of struggles to get it to dual boot with my old version of ubuntu, perhaps due to the way hp sets things up on the drive.  And when support for that version of ubuntu timed out I tried to install a newer version and lost my entire windows installation and had to reinstall windows7 from the hp disks (an entire day), only to loose it again.  At least centos has six years of update support instead of three so I don't have to go through this again quite that soon.  Hopefully the centos os and software repositories are as good as ubuntu because I really don't look forward to going through this again in three years.  Your kindness is really appreciated though.

---

### Post by oldfred on 2014-05-14
Nothing against Centos, but Ubuntu LTS is 5 years.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

       Versions and release & support until dates:
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by kc1di on 2014-05-14
Well Centos is a fine distro. but you'll have to do some searching for all the desktop packages you'll want if you using this machine for a Desktop. It can be done
But as OldFred point's out Ubuntu 14.04 LTS has 5 years of support and updates.  When you get it up and running it will be good for a long time. 

Good success what ever you decide.

---

### Post by meself on 2014-05-14
Yep.  I installed centos and it's a relatively crude piece of work for my purposes.  The repository had none of the popular software that I run on both windows and ubuntu.  And wifi was not functioning.  The wifi instructions in the centos forum involve command line work that I don't understand and would rather not mess with for just wifi which was working with the ubuntu default installation on this machine anyway.  So I'll pick up a copy of windows8 and try to figure out how to turn off secure boot UEFI next week so maybe a dual boot installation won't be so difficult.  It's a cinch on my two xp desktops but they both have a microsoft copy of windows xp, not an hp version.  Hopefuly it wont' be so difficult with a microsoft copy?  Anyhow, thank you both again for your helpful support!

---

### Post by Mattish on 2014-11-26
II actually managed to get past this by simply typing "exit" without quotes, i got this message after a fresh install of xubuntu and ubuntu 14.04 x64. Hope this helps for you guys some how ^^

---

