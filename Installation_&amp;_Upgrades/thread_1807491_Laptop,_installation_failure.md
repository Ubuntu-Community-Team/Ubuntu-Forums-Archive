---
title: "Laptop, installation failure"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by CM7 on 2011-07-19
Hello!

My old ibm R32 laptop specification:
CPU Type: Pentium 4
CPU Speed: 1.60GHz
Installed memory: 512MB

I have intstalled ubuntu 10.04 (a bit modified by different country team). Everything was fine but i wanted to try other os (i'm not sure if the word is correct). So i downloaded xubuntu 11.04 (original, this time). I've checked the image with mdk5sum or sth like that, burn cd as slow as possible and boot it. I've chosen install xubuntu, wait a few moments and i've seen sth like this: "Unable to find maintain live system file".

Afther that i've burned lubuntu 11.04 image but it ended up the same. Debian 6.0.2.1. installation stop during cd-rom check. So i wanted to use pendrive and boot it but my laptop doesn't have an usb boot option. OK, maybe it have but it doesn't work. 
1.Removable devices
I have enabled support usb too but it just didn't want to boot.

I thought that unetbootin may help. And success! Cd booted and i've choosen install xubuntu. It was OK until the partition part showed up. I couldn't go further because sth was wrong with partition. So i wanted to change it but: "ubi-partman exit code 141".

I'm sick of fighting with it by myslef. Can you help?
I apologise for my poor language :). And this is the [COLOR="Red"]first[/COLOR] time when i'm trying to use linux.

---

### Post by gex3 on 2011-07-19
unfortunately i don't know such a problem - actually i successfully installed ubuntu for many times on different pc's and laptops like R32 as well as newer and much older ones, but if you search google for "ubi-partman exit code 141" there is a plenty of info..

---

### Post by CM7 on 2011-07-19
I wanted to run gparted live and format everything (i don't care about the data) but i got the message that boot failed.
The error message was: Unable to find a medium containing a live file system.
I got the same error during installs without unetbootin.

---

### Post by 2F4U on 2011-07-19
I guess that there is something wrong with the boot medium. I've installed Xubuntu and several other Linux distributions on a ThinkPad X31 without problems (even posting now from that machine), which should be as old as your machine. Both 10.04 and 11.04 run on that hardware. Could it be that the hdd is broken?

---

### Post by CM7 on 2011-07-19
Actually, the HDD is the newest thing in this laptop because the old one broke a few months ago. From this time i wasn't much using this laptop. Sth like one week ago i started my experiments with linux. I can check HDD by a program in Ubuntu. I am preety sure there is sth like that. Meanwhile, do you have any other suggestions?
--------------------------------------------------
OK i've just started the test (with SMART thing).

---

### Post by 2F4U on 2011-07-19
Another thing that comes to my mind is that the lenses of the cd reader may be dirty and therefore causing errors. They can be cleaned with a little bit of alcohol. I am wondering why you are unable to boot from usb since this is not a problem on my X31. I just press F12 during the early stages of the bios message and get to a temporary boot menu.

---

### Post by CM7 on 2011-07-19
No errors during test.
I don't know why i can't boot from usb too. I have tried temporary boot and going to BIOS where i change boot order. Maybe this is because pendrive but it was working in ubuntu - i mean i could have open it and copy data for example.

Cd reader is dirty? Very possible. I have never cleaned it but i can try. It will probably take me a while.

---

### Post by CM7 on 2011-07-20
I've cleaned cd reader. Nothing changed.
Other thoughts?

---

### Post by CM7 on 2011-07-22
I have deleted swap partition and made /boot instead. And it worked! I have installed xubuntu 11.04 by removing ubuntu 10.04. I had report about a crash during the installation but it has ended succesfully. This time i have made partitions: /boot, swap, /home and /. Afther that i must have restarted laptop so i could not have chcecked why the crash showed up.

Now i can't do anything because black screen shows:
"error: file not found.
grub rescue> "

I will try solving this by myself. When i get tired i will make new thread.

Thanks everyone for help :).

---

