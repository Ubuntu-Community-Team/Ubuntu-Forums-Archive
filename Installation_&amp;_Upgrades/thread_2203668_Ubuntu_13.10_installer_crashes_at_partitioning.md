---
title: "Ubuntu 13.10 installer crashes at partitioning"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by t0X1c_bt on 2014-02-04
So, I've been trying to install ubuntu 13.10 along side my windows 8, but I couldn't because it is getting stuck at the partitioning part of the installation.
Here is the thread at askubuntu: [http://askubuntu.com/questions/416263/unable-to-installing-ubuntu-13-10-alongside-windows-8-1](http://askubuntu.com/questions/416263/unable-to-installing-ubuntu-13-10-alongside-windows-8-1)
I am running on an HP laptop ENVY dv6.
I really need to get the ubuntu running.
I tried with several other distributions, fedora and mint, and I get the same error.
Please help me, I'm desperate.

---

### Post by sudodus on 2014-02-04
Welcome to the Ubuntu Forums :-)

We need to know more in order to give good advice. Please describe the computer details

- CPU
- RAM (size)
- graphics chip/card (very important)
- wifi chip/card

And it is also important to get a description of the partitions on the internal drive (where you have Windows). Please boot a live session from the CD/DVD/USB drive and run the following command in a terminal window ('space minus ell' at the end)

```
sudo parted -l
```

and post the output in a reply.

---

### Post by t0X1c_bt on 2014-02-04
[COLOR=#3E454C][FONT=lucida grande]These are the full specs:
```

dv6t Quad
&#8226; Windows 8 64
&#8226; 3rd generation Intel Core i7-3630QM Processor (2.4GHz, 6MB L3 Cache)
&#8226; NVIDIA(R) GeForce(R) GT 635M Graphics with 2048MB of dedicated video memory
&#8226; 8GB DDR3 System Memory (2 Dimm)
&#8226; 1TB 5400 rpm Hard Drive&#8226; 32GB mSSD Hard Drive Acceleration Cache
&#8226; 6 cell + 9 cell Lithium Ion Battery
&#8226; SuperMulti 8X DVD+/-R/RW with Double Layer Support
&#8226; Intel 802.11b/g/n WLAN and Bluetooth(R)

```[/FONT][/COLOR]
[COLOR=#3E454C][FONT=lucida grande]And I got an error while running the command, I will post a screen of it[/FONT][/COLOR]:
[IMG]http://i.imgur.com/CI5DEhM.jpg[/IMG]

---

### Post by sudodus on 2014-02-05
> **t0X1c_bt said:**
> [COLOR=#3E454C][FONT=lucida grande]These are the full specs:
```

dv6t Quad
&#8226; Windows 8 64
&#8226; 3rd generation Intel Core i7-3630QM Processor (2.4GHz, 6MB L3 Cache)
&#8226; NVIDIA(R) GeForce(R) GT 635M Graphics with 2048MB of dedicated video memory
&#8226; 8GB DDR3 System Memory (2 Dimm)
&#8226; 1TB 5400 rpm Hard Drive&#8226; 32GB mSSD Hard Drive Acceleration Cache
&#8226; 6 cell + 9 cell Lithium Ion Battery
&#8226; SuperMulti 8X DVD+/-R/RW with Double Layer Support
&#8226; Intel 802.11b/g/n WLAN and Bluetooth(R)

```[/FONT][/COLOR]
[COLOR=#3E454C][FONT=lucida grande]And I got an error while running the command, I will post a screen of it[/FONT][/COLOR]:


The computer should work well. Maybe you need a proprietary driver for the nvidia graphics. Intel wifi is usually working with a built in driver.

But Windows 8 and UEFI make it complicated to install Ubuntu. Maybe you can start by reading this link

[http://https://help.ubuntu.com/community/UEFI](http://https://help.ubuntu.com/community/UEFI)

Edit: Please avoid inserting big images. When text information, cut and  paste and post between code tags like the first chunk of text. When  'real' pictures, 'go advanced' and manage attachments (so that a  thumbnail is shown until the reader clicks on it to see the whole  picture).

---

### Post by t0X1c_bt on 2014-02-05
I did everything from the guide and I still can't get pass that screen...
Can you tell me what is the error about int the terminal window?
Because when I tried to 'fix' it, it actually screwed up my SSD partitions...

---

### Post by sudodus on 2014-02-05
It is possible that your new nvidia card is not supported 100% (yet) by the built in driver. Maybe you would have better luck with an nvidia proprietary driver. Start with a live session booted from the CD/DVD/USB drive and use the boot option ***nomodeset***.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

And try the following command

```
sudo apt-get install nvidia-current
```

or one of the other nvidia drivers.

---

