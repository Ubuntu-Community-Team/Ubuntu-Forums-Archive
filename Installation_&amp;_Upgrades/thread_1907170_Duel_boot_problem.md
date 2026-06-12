---
title: "Duel boot problem"
date: 2012-01-10
forum: Installation &amp; Upgrades
---

### Post by GeirStenberg on 2012-01-10
I am new to Linux. I have just installed Xubuntu on a computer with a Windows installation.
When I boot the computer Windows starts automatically, I don't get a boot menu, so I'm unable to start Xubuntu.

I suspect it is because I have Windows 8 developer preview installed on my computer and Xubuntu does not recognize the OS.
During the installation Xumbuntu was unable to import settings from Windows. It coudn't find any settings to import. And I didn't get any question regarding the         GRUB boot loader.

Any suggestions on how I can resolve this?

---

### Post by raja.genupula on 2012-01-11
1..Hold your shift key while your system booting up , if you got grub menu then boot into Xubuntu and install the grub customizer and set the grub time to 10 sec . 

2.if you won't get grub menu with shift key then look at my signature for Grub recovery and use that to get back your grub.

If things are not fine even then 

3.Look at my signature for Botinfoscript and give the output in code tags by clicking at # in this window. 

All the best.

---

### Post by Mark Phelps on 2012-01-12
Windows 8 (at least the DP version) has a completely NEW boot loader from Windows 7.  It's not jut the look and feel that has changed, the internals of the boot loader are very different.

It's likely that the os_prober code that GRUB2 uses to find Windows OSs simply can not understand the NEW boot loader in Win8.

After all, Win8 is only in Alpha stage.  I would not expect Linux stuff to work at al with it at this point.

---

### Post by Double.J on 2012-01-12
I've not had any problems dual booting win8 & Mint11 (Ubuntu 11.04)... it sounds like the bootloader isn't installed to /dev/sda have a look at this post and see it you've changed anything?

[How to Geek Tut]("http://www.howtogeek.com/99060/how-to-dual-boot-windows-8-and-linux-mint-on-the-same-pc/")

are you using the GUID Partition Table? (GPT)?

---

### Post by oldfred on 2012-01-12
I would be curious on what boot info script shows. There is a new update with fixes, but I do not know if Xubuntu has some of the bits used.


```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Standard version of boot script note the added programs (gawk, xy) to make it work:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

