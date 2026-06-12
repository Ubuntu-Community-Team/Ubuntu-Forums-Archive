---
title: "balenaEtcher attention something went wrong pop up, trying to install ubuntu 20.04"
date: 2021-12-01
forum: Installation &amp; Upgrades
---

### Post by ruby9 on 2021-12-01
Hi, I'm trying to install Ubuntu 20.04 LTS onto a laptop and am following this tutorial here: [https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview) 
I'm up to the step of using balenaEtcher however after it's done this message is popping up after it's finished:

attention something went wrong. If it is a compressed image, please check that the archive is not corrupted.
Cannot read property 'message' of null

Not sure what I did wrong here?

---

### Post by ActionParsnip on 2021-12-01
Did you check that the file you transferred wasn't corrupted by using SHA/MD5?

---

### Post by ruby9 on 2021-12-01
I'm not sure what SHA/MD5 is, I ran checksum on the iso file and that turned out ok.

---

### Post by sudodus on 2021-12-01
You can find the checksums via [https://releases.ubuntu.com/](https://releases.ubuntu.com/) usually the same directory as the corresponding iso files.

**In Ubuntu** you run for example
```

sha256sum ubuntu-20.04.3-desktop-amd64.iso
# or even more conveniently

<<<'5fdebc435ded46ae99136ca875afc6f05bde217be7dd018e1841924f71db46b5 *ubuntu-20.04.3-desktop-amd64.iso' sha256sum -c

```
in the directory where you store the iso file. (Copy and paste from here or from the web page with the iso file to a terminal window.)

In order to know details about your computer, please [download and run the **[FONT=Courier New]system-info[/FONT]** script](https://github.com/UbuntuForums/system-info/). Run it when the USB drive is connected. Let it upload the result to a pastebin and paste the link into a new reply here. It will make it much easier to help you.

[hr][/hr]
**In Windows** you can try using [Rufus](https://rufus.ie) to create the USB boot drive.

Rufus has also a built-in checksum tool.

---

### Post by ruby9 on 2021-12-02
mia@mia:~/Desktop$ <<<'5fdebc435ded46ae99136ca875afc6f05bde217be7dd018e1841924f71db46b5 *ubuntu-20.04.3-desktop-amd64.iso' sha256sum -c
ubuntu-20.04.3-desktop-amd64.iso: OK
mia@mia:~/Desktop$ 


When I run the system-info script this turns up:
Running Script: system-info Version: 01.00-01, Script Date: 2021.09.30
 --- Some Programs This Script Uses Were Missing --- 
'curl' is not installed.
 -------------------------------- 
 --- Some Programs This Script Uses Were Missing --- 
'pastebinit' is not installed.
 -------------------------------- 

The Script 'system-info' uses  some very basic Linux utilities. 
Some of these utilities were not found.
<E>xit and install the program(s) or <C>ontinue anyway? <E/C> 

Can I still run this or will it not work with the missing utilities?

---

### Post by sudodus on 2021-12-02
Yes, you can still run it.

A simpler uploading tool will be used, but it should still be possible to get the report uploaded to a pastebin. (If you wish, you can also install curl (or pastebinit), but it is not necessary.)

---

### Post by ruby9 on 2021-12-02
When I run it it asks 'Please provide some "Basic Information"...
What is the Main Complaint (summarized)?' I'm not sure what to write there.

---

### Post by sudodus on 2021-12-02
Type anything for example 'a' (not really relevant in this case).

---

### Post by ruby9 on 2021-12-02
Thank-you, here is the report: Uploaded Report: 2021-12-02  20:04:04 AEDT (+1100):
View at: [https://termbin.com/sdio](https://termbin.com/sdio)

---

### Post by sudodus on 2021-12-02
```

...
ubuntu-20.04.3-desktop-amd64.iso: OK

```
Your downloaded iso file is OK :-)

I'm looking at the uploaded system-info report file.

- The overall specs of the computer shows that it works with the installed Ubuntu 16.04.7 LTS, but maybe the current version, Ubuntu Desktop 20.04.3 LTS wants more 'horsepower'.

- The USB pendrive, the Cruzer Glide looks OK according to the output from 'lsblk'.

- The CPU, Intel(R) Celeron(R) CPU  J1900  @ 1.99GHz, was released Q4'13 (that is near the end of 2013). It is 8 years old, and I think the computer would work much better with a light-weight community flavour of Ubuntu: Lubuntu, Ubuntu MATE or Xubuntu, that you can find via **[releases.ubuntu.com/](releases.ubuntu.com/)**.

I would recommend that you download version 20.04.3 LTS of Lubuntu, Ubuntu MATE or Xubuntu (more than one if you have a good internet connection and compare them). Flash them into your USB drive and **try live**. I think Balena Etcher can do it (your problem is somewhere else).

Otherwise (if still problems) you can try another tool, the built-in Ubuntu Startup Disk Creator or [mkusb](https://help.ubuntu.com/community/mkusb). If still problems, you can use mkusb to wipe the whole device, which makes the pendrive more responsive, and after that clone from the iso file to the pendrive again. If still problems, please try with another pendrive.

Edit: You can also try with the pendrive in different USB ports. I think only one is USB 3, but it *might* work better in one of the other USB ports (slower but maybe more reliable).

---

### Post by ruby9 on 2021-12-02
Thank you so much :) I'll be taking a look into the lite versions.

---

### Post by sudodus on 2021-12-02
You are welcome. Please let us know how it works (whatever the result) :-)

---

### Post by tea for one on 2021-12-02
It is nice to see that [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info) is getting some traction.

The advice offered by [COLOR="#0000FF"]sudodus[/COLOR] will undoubtedly be useful for the OP.

---

