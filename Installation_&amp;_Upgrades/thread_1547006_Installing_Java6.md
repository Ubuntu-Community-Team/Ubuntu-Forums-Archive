---
title: "Installing Java6"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by trophy1990 on 2010-08-06
I've got an old laptop and decided to put ubuntu 6.10 on it and it works fine. However, when it comes to intalling java I am at a complete loss. I download the self extracting file off java and then follow the instruction but all I get is directory/file not found. The file however is clear as day on my desktop. 
So I decide a different approach by using the add and remove software. It has got java5 available for me but I can't download it as there is a repository index download problemy thing. I have got access to the internet as I can browze firefox.
So I search for another solution and find that get-apt command thing. It doesn't work though as I haven't recieved one update due to error 404. 
 
So now after hours of searching I am still asking "How the hell do I get java on Ubuntu?" It has xfce desktop btw if thats any help.
 
Keep in mind before you answer I know nothing about the terminal, what a repository is or anything really to do with ubunu.
 
Thanks in advance, Trophy1990.

---

### Post by sikander3786 on 2010-08-06
Hi.

At first I want to ask why are you using 6.10? Ubuntu 10.04 is out and working great for most of the hardware. In addition there is another version [Ubuntu Netbook Edition]("http://www.ubuntu.com/netbook/get-ubuntu/download") specially developed for laptops and netbooks.

I am not sure if JAVA6 can be installed on 6.10 as that is pretty much old and is no longer supported.

Regards.

---

### Post by trophy1990 on 2010-08-06
I'm using 6.10 as I have a very old dell latitude cpx. I did get java to run on it a couple of years ago (that took forever) but I think it was java5. Thanks for the reply though, I'm looking into ubuntu 10.04.

---

### Post by sikander3786 on 2010-08-06
Ubuntu 10.04 I think will be able to run pretty well on your laptop. It is not a resource eater. Here are the system requirements for Lucid.

[https://help.ubuntu.com/10.04/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/10.04/installation-guide/i386/minimum-hardware-reqts.html)

---

### Post by Spice Weasel on 2010-08-06
Right, here's how to add the newer Ubuntu repositories and install Sun Java 6.

Open up a terminal, and type "sudo gedit /etc/apt/sources.list" into it without the quotes.

A text file should come up, copy and paste this:

> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
(would someone like to verify this? I'm unsure and using Fedora at the moment.)

Next, type "sudo apt-get update" into a terminal without the quotes, followed by "sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-jdk" without quotes.

Good luck, and post any errors. You might also want to reinstall Firefox from the new repositories.

---

### Post by trophy1990 on 2010-08-06
When typing the first bit I'm getting the message no such file or directory

---

### Post by Spice Weasel on 2010-08-06
In that case, try "sudo nano /etc/apt/sources.list". Middle click pastes.

---

