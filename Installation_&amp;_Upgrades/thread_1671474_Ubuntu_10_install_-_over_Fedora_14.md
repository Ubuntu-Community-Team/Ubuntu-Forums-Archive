---
title: "Ubuntu 10 install - over Fedora 14"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by sumitk on 2011-01-20
Hi All,

I have recently started working on Ubuntu & really liked it :KS**awesomeness!!:KS** But few days back, just out of curiosity I thought of trying the new fedora14:-s. So I tried the live CD but since my dvd rom is not in a good condition, the whole thing was really slow. So I thought of installing it along with my other OS. 

Previously I had Ubuntu10.10 & win xp. So I went ahead, backed up all my data from Ubuntu, and installed fedora14. My partitions were like this:

/dev/sdb2       ----  Extended
   /dev/sdb5    ----  Fat32  (common partition for Ubuntu & Win xp)
   /dev/sdb9    ----  ext4   (Fedora  "  /  "  )
   /dev/sdb10  ----  linux-swap  (Fedora's swap)
   /dev/sdb7    ----  linux-swap  (Ubuntu's swap)
   /dev/sdb8)   ----  ext4   (Ubuntu   "  /  "  )

While in the middle of installation, it asked me about the grub configuration. It had option like this:

Other (/dev/sdb1)
Fedora (/dev/sdb9)

I was confused as it didn't recognise my Ubuntu partition which was** /dev/sdb8**. 

So I used the _**Add**_ option visible there and named it Ubuntu, picked /dev/sdb8 from the location drop down menu, and made it the default boot option. So now the list becomes like this:

Other (/dev/sdb1)
Ubuntu (/dev/sdb8)
Fedora (/dev/sdb9)
 
I also kept the **Grub install location as the default** which was the name of my laptop hard drive. The installation went as usual but when I rebooted the system, the Grub of Fedora comes up and when I choose Ubuntu my Ubuntu doesn't starts. Instead I am getting a message which goes something like this "Wrong executable selected..." So now I had Win xp and Fedora working on my laptop. 
[B]
_Ques1:_ Is there any way I can configure the grub of Fedora to boot Ubuntu just like win xp is getting booted up.?[/B]

Then I thought I might have overwritten the previous grub. So I did the other way round. I have already installed Fedora14 so I then started installing Ubuntu. It still doesn't recognise my previous partition. So I went ahead with full new installation of Ubuntu on the same location. Now I can see the grub of ubuntu but Fedora is not booting.

_**Ques2: **_**Is there something obvious that I am doing wrong? I think it has something to do with the Grub so could anyone please explain me how I need to configure it.?**


Thanks a lot!!
The forum is gr8 as this is my 1st question ever. I got all my answers here!:)

---

