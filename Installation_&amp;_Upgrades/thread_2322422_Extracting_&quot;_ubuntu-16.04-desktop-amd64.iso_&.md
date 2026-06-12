---
title: "Extracting &quot; ubuntu-16.04-desktop-amd64.iso &quot; to a Flashdrive &quot;error.....hardlink&quot;"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by wface89 on 2016-04-27
I am currently using Elementary OS Freya which said that is supported by Ubuntu, Ever since I start using Elementary OS Freya I always encounter errors or bugs and asking for reports and I don't have any idea of those things so I have decided to switch on "Ubuntu 16.04".

I opened the "ubuntu-16.04-desktop-amd64.iso" with the "archive manager" and extract it to my Transcend Flash drive but after the process of extracting, there are some missing files and a dialogue box appear saying


I wish someone to explain me what is a hard link :D ...... don't have any idea...?

[IMG]https://scontent.fceb2-2.fna.fbcdn.net/v/t1.0-9/13076531_1006074742802759_5054044418661834207_n.jpg?oh=2d6986e4a0f28369fdd6d0e8c2e8d379&oe=57A34903[/IMG]


[IMG]https://scontent.fceb2-2.fna.fbcdn.net/v/t1.0-9/13103519_1006074749469425_6128684428609441876_n.jpg?oh=7d68aaf6d0426598fa9627e60ac881a9&oe=57BFBB5C[/IMG]



[IMG]https://scontent.fceb2-2.fna.fbcdn.net/v/t1.0-9/13094144_1006074766136090_1902590465376335282_n.jpg?oh=f5aa604a121192318ced343150cb9837&oe=5772149C[/IMG]

---

### Post by Dennis N on 2016-04-27
A hard link is a type of symbolic link. The FAT32 file system that is probably on the flash drive cannot store symbolic links. You need to write the iso to the drive using one the applications that creates bootable flash drives. See:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by wface89 on 2016-04-28
Thank you sir;:popcorn:

---

