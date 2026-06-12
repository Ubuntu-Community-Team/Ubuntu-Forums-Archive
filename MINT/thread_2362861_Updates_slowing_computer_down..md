---
title: "Updates slowing computer down."
date: 2017-06-02
forum: MINT
---

### Post by Camilia on 2017-06-02
I bought my HP Pavilion computer in 2005. Have ubuntu 16.04 OS. Lately after updates my computer is getting slower and slower. When I have time I am going to upload Mint 17.3. 

Just wanted worn others about problems that can occur with old computers.

---

### Post by Irihapeti on 2017-06-02
You could try Lubuntu or Xubuntu, which will be lighter than standard Ubuntu. Of the two, Lubuntu will be the lighter.

---

### Post by gordintoronto on 2017-06-03
Mint Cinnamon is as heavy as Ubuntu, but Mint Mate is a lighter option. I'm running it on an eight-year-old laptop which was no powerhouse when it was new.

There's also Ubuntu Mate.

---

### Post by Camilia on 2017-06-03
I have Mint 17.3 disk. I think that is the cinnamon version. My PC has Memory 2.7 GIB and Processor AMD Athlon(tm) II X2 250 Processor × 2  and Disk 627.0 GB. Requirements of mint 17.3 are 512MB RAM (1GB recommended for a comfortable usage). 9GB of disk space (20GB recommended).

---

### Post by Dennis N on 2017-06-03
> **Camilia said:**
> I have Mint 17.3 disk. Anybody know if that will work better with an old computer?

What is the Desktop Environment? Mint 17.x XFCE would be much like Xubuntu 14.04.x. in most respects. I use Mint 17 XFCE on my 2007 Dell with no difficulty.

---

### Post by Camilia on 2017-06-03
> **Dennis N said:**
> What is the Desktop Environment? 
What are you referring to? 

Read - [Linux Mint]("https://ubuntu-mate.community/t/why-use-ubuntu-mate-16-04-instead-of-linux-mint-18/6783/4") is not as free as Ubuntu. Mint "locks down" the system and makes it incompatible with certain tools like live iso creation. Linux Mint is slightly heavier with some unidentified (at least I don't know) processes sometimes running. Some people say it's not as secure as Ubuntu, but I think it's mostly FUD.

---

### Post by Dennis N on 2017-06-03
Linux Mint comes in Cinnamon, XFCE, or MATE and maybe other editions - those are desktop environments, like Unity is a desktop environment. Your Linux Mint 17.3 disk is one of these editions. Check the name on the ISO you made the disk from. It will give the desktop to be installed.

---

### Post by Camilia on 2017-06-03
> **Dennis N said:**
> Check the name on the ISO you made the disk from. 
I bought the disk so that info does not apply.

---

### Post by Dennis N on 2017-06-03
> **Camilia said:**
> I bought the disk so that info does not apply.

Then I suggest you boot the disk and see which edition you have.

---

### Post by poorguy on 2017-06-03
I'm using this old relic with Lubuntu 16.04 and have no complaints.
```
 Dell XPS 200 / Dell DXC051 (10/28/2005).
 Intel Pentium D 820 Smithfield processor 2.8 GHz @ 800 MHz FSB. 
 DDR2 Memory 3.0 GB @ 800 MHz FSB.
 NVIDIA Graphics Card [GeForce 210 / GT216].
 Hard Drive 80 GB SATA.
```

---

### Post by Camilia on 2017-06-03
> **Dennis N said:**
> Then I suggest you boot the disk and see which edition you have.
Ok I booted it. Now where do I find the edition? Googled it and the result:
mint@mint ~ $ cat /etc/linuxmint/info
RELEASE=17.3
CODENAME=rosa
EDITION="MATE 64-bit"
DESCRIPTION="Linux Mint 17.3 Rosa"
DESKTOP=MATE

I finding I can not add chrome search engine. Yahoo is default and I hate that search engine. Also can't get it to stop asking me to save passwords.

---

### Post by poorguy on 2017-06-03
Go into the terminal and copy and paste this command.

*lsb_release -a*

---

### Post by Dennis N on 2017-06-03
> Ok I booted it. Now where do I find the edition? Googled it and the result:
mint@mint ~ $ cat /etc/linuxmint/info
RELEASE=17.3
CODENAME=rosa
[COLOR="#FF0000"]**EDITION="MATE 64-bit"**[/COLOR]
DESCRIPTION="Linux Mint 17.3 Rosa"
DESKTOP=MATE

Great -  you have it! You are using Linux Mint MATE.

> I finding I can not add chrome search engine. 

Did you mean Google search engine? I don't know of chrome search engine.

---

### Post by howefield on 2017-06-04
Thread moved to the "*MINT*" forum.

---

### Post by Camilia on 2017-06-04
> **Dennis N said:**
> Great -  you have it! You are using Linux Mint MATE.

Did you mean Google search engine? I don't know of chrome search engine.
I am probably using the terms wrong. I like to chrome web browser sometimes for with it I can call my cell phone when it is lost it via google voice. I like using firefox web browser better than chrome web browser but google voice does not work on firefox. Searching via anything but google search gets me more links to go to for info.

---

### Post by Camilia on 2017-06-04
> **poorguy said:**
> Go into the terminal and copy and paste this command.

*lsb_release -a*
what is that command for?

---

### Post by vasa1 on 2017-06-04
> **Camilia said:**
> what is that command for?

See *man lsb_release* for details:```
DESCRIPTION
       The  lsb_release  command  provides  certain LSB (Linux Standard Base) and
       distribution-specific information.

```

---

