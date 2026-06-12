---
title: "Installation issues."
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by The Squig on 2008-11-12
Im having some major problem with the ubuntu 8.10 install cd. Im using the alterenate version btw.

Problems:

1. when booting from cd and having selected install i get bombared by some buffer i/o error message. After about 2mins it gives up and im presented witha blackscreen for about 2-3min. After that gui gets loaded.

2. The installation process is extremely slow. every little step/page takes ~3-4 mins to load. whole installation took me over 1h. 

When the installation was removing temporary files i noticed something. It was removing "Broken:_cdreader_driver" (my dvd reader is 1yr old and ive had no problems with it) ([COLOR="DarkRed"]SOLVED, drive was in fact damaged, probably from esd damage on my old motherboard.[/COLOR])

3. After the system was finally installed it seemed to work fine. then i lost my interenet connection after a few seconds.([COLOR="DarkRed"]solved, see my last post[/COLOR])

Ran dhclient and got an error dealing with having no buffer. then some looping error saying message to long. 

-----------------

Things ive tried to solve the problem.

1.redownloaded the iso file
2.Burned at lowest speed possible (8x)
3. tested two computers, got some io error in the beginning (never finished install on the other pc).
4. on the second computer i tried using 3 different cd/dvd readers.


Computer spec

main pc:

e6750
2gb ddr2
samsung cd/dvd writer (sata)
1x wd sata 500gb hdd
1x wd sata 320gb hdd
gigabyte p45 ds3 mainboard
radeon 4850

win xp sp3

this pc had no trouble running8.04 in the past

edit: forgot, motherboard and grahpiccard has been switched since i last usedubuntu (8.04)

old compnents: gigabyte p35 ds3 and radeon x1950pro

---

### Post by The Squig on 2008-11-14
sorry for this bump but i really need help..

---

### Post by littlebat on 2008-11-14
It seems your "samsung cd/dvd writer (sata)" read your intallation cd-r disk is very difficult. Try install Ubuntu from downloaded ISO image file in hard disk directly.
Read my diary for detail: Install Ubuntu on Old Computer: [http://www.learndiary.com/en/2008/11/install-ubuntu-on-old-computer.htm](http://www.learndiary.com/en/2008/11/install-ubuntu-on-old-computer.htm) . Read the section "2, The choice of installing methods", change "hardy" in the download link of "vmlinuz" and "initrd.img" into "intrepid" for your Ubuntu 8.10 .

---

### Post by The Squig on 2008-12-07
reinstalled for the third time. this time I used the regular desktop isntall cd.

The installation still went extremely slow. I had no problems with this dvd drive with 8.04. the only hardware changed has been my motherboard so I guess ubuntu just doesnt like it.


anyway. reason for me updating the thread is bevause ive solved the internet access problem.


Here is the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377)

problem was solved by using this command 


sudo update-rc.d -f NetworkManager remove
([http://ubuntuforums.org/showthread.php?t=963335&page=10):](http://ubuntuforums.org/showthread.php?t=963335&page=10):)

now the only problem I have is that I have to manually type sudo dhclient everytime i boot the computer.

---

