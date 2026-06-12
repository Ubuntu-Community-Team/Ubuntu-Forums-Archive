---
title: "Corrupt Ubuntu Server ISO even after downloading twice"
date: 2014-02-19
forum: Installation &amp; Upgrades
---

### Post by kristian3 on 2014-02-19
[SIZE=2][FONT=arial][COLOR=#333333]I've twice downloaded ubuntu-12.04.4-server-amd64.iso from the Ubuntu site, and when I'm somewhere through the installation, I get the message in the screenshot below. How do I get past this? The image cannot be corrupted twice. What am I doing wrong? Or are the iso images themselves corrupt?[/COLOR]
[/FONT][/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=2][FONT=arial]I'm doing all this on a Dell Laptop with 4GB RAM running Windows 7 Home Premium 64. I'm using Oracle VirtualBox.
[/FONT][/SIZE][IMG]http://i.imgur.com/E5nfZFY.png[/IMG]

When I run check cd-rom, I get this: 

[IMG]http://i.imgur.com/QxdURng.png[/IMG][/FONT][/COLOR]

---

### Post by sudodus on 2014-02-19
1. Did you check with md5sum, that the download was correct? See this link [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2. Did you burn the iso file to a CD or DVD or did you flash it to a USB pendrive?

*. You can try ***torrent*** instead of regular downloading. Then the md5sum should be checked as part of the process.

---

### Post by kristian3 on 2014-02-19
The ISO is saved to a drive on my PC. I did not burn it to a CD or DVD.

---

### Post by sudodus on 2014-02-19
OK.

1. I suggest that you check the md5sum with the command

```
md5sum filename.iso               # using the actual filename of your iso file
```

2. How did you run the computer to get the screenshots in post #1? Did you boot from CD, DVD or USB?

*Edit*: or did you boot from the iso file (when it is sitting on your hard disk drive)?

---

### Post by kristian3 on 2014-02-19
The MD5 Sum do not match. I wonder how this happened. Does this mean I need to re-download the file? I was reading a few posts that said Windows Changed the file extentions. Could this be the problem?

---

### Post by kristian3 on 2014-02-19
That's Oracle Virtual Machine in the Screenshots. I'm doing this using Oracle VM.

---

### Post by Kr0nZ on 2014-02-19
try downloading via torrent as it does extra checking to verify file integrity

---

### Post by sudodus on 2014-02-19
You need to get an iso file, that matches with the md5sum. If the internet connection is flaky (somewhere, maybe far from your house), it is better to use torrent. Scroll to the chapter about **BitTorrent** in this link

[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

---

### Post by sudodus on 2014-02-19
> **kristian3 said:**
> that's oracle virtual machine in the screenshots. I'm doing this using oracle vm. ok :-)

---

### Post by kristian3 on 2014-02-19
One of the things I noticed, is that files in the ISO all have extensions .deb, where as the file in md5sum.txt all have the extensions .udeb

---

### Post by sudodus on 2014-02-19
You should check the md5sum of the entire iso file.

Run 
```
md5sum filename.iso               # using the actual filename of your iso file
```

*Edit*: what is the actual filename of your iso file?

Then check with the value found at this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by kristian3 on 2014-02-19
It's  ubuntu-12.04.4-server-amd64.iso

---

### Post by sudodus on 2014-02-19
In linux, run the following command in the directory where you have the iso file

```
md5sum ubuntu-12.04.4-server-amd64.iso 
```

and  you should get this output

```
e83adb9af4ec0a039e6a5c6e145a34de  ubuntu-12.04.4-server-amd64.iso
```

In Windows, you can use ***md5summer*** according to this link

[http://www.md5summer.org/](http://www.md5summer.org/)

---

### Post by coldraven on 2014-02-19
Download the torrent file here: [http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-amd64.iso.torrent](http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-amd64.iso.torrent)
Then, presuming you have a Windows torrent client, just double click the downloaded file to start torrenting. That's if torrenting is actually a word :)

---

