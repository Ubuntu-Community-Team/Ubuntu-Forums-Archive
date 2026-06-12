---
title: "Ubuntu wont start up after one month"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by marc_us82 on 2010-03-11
Hi guys, this has happened two months in a row since i first installed Ubuntu 9.10, at exactly one month after i've installed it, it wont start up properly when i clicked on the Ubuntu option as my OS.

It will bring me to a page with grub> appearing and im meant to type in something but cant figure out what.

so in the end i have to reinstall ubuntu again in my windows OS and this irks me a great deal, as i will have to reinstall my wine and spotify and not to mention losing all the data and pictures that i have saved in Ubuntu.

if anyone can help out or offer advice i'll be most grateful.


Marcus

---

### Post by akand074 on 2010-03-11
> **marc_us82 said:**
> Hi guys, this has happened two months in a row since i first installed Ubuntu 9.10, at exactly one month after i've installed it, it wont start up properly when i clicked on the Ubuntu option as my OS.

It will bring me to a page with grub> appearing and im meant to type in something but cant figure out what.

so in the end i have to reinstall ubuntu again in my windows OS and this irks me a great deal, as i will have to reinstall my wine and spotify and not to mention losing all the data and pictures that i have saved in Ubuntu.

if anyone can help out or offer advice i'll be most grateful.


Marcus

Thats very weird that it does that but you can easily recover all the data in your ubuntu partition before reinstalling. Just boot into the live cd and mount the drive and just copy paste all the data files you want to keep onto a usb stick. Why that is happening I'm not sure. Why are you installing it in the windows OS? boot into the CD and install it. Maybe its a coincidence that every month it stops booting, what was the last thing you did on your ubuntu before it stopped booting?

---

### Post by Kevbert on 2010-03-11
Are you dual booting with Windows or another version of Linux ?

---

### Post by marc_us82 on 2010-03-11
hey guys, thanks for the speedy reply, really do appreciate it. Here's the thing, i dont know why it only happens to me, but one thing im sure of, the OS will fail me again same time next month precisely on the 10th. It's frustrating but there is hardly anything i can do bout it.

so every time i powered my laptop, it offers me two options which is namely windows or ubuntu, and obviously each time i will choose ubuntu because my wifi only works with it, i changed some configuration on my vista and it just wont let me get online anymore but that's another story. 

Anyway im very happy with ubuntu as it works fine except for this little complication.

i will try your suggestion akand, but whenever i try to boot from the live cd it asked me to uninstall my ubuntu in the system first.

obviously i would love for this to not carry on and fix it once and for all.

thanks for the advice guys.


M.

---

### Post by presence1960 on 2010-03-11
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

