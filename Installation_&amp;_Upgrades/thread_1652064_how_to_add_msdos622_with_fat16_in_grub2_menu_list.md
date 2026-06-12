---
title: "how to add msdos622 with fat16 in grub2 menu list"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by manasye on 2010-12-24
Dear all,
sorry for my noob question, but i really really new in ubuntu (linux),
i just finished installing my ubuntu 10.10 desktop edition. after restart for the first time
i can see my windows xp and windows 7 os were in the menu list but not my msdos 6.22 with fat 16 partition.

I try to edit grub.cfg to add but i am not sure what the command line should i use in menu entry, could someone give an example.
I really need that since i still make a programming project using C++ dos and Clipper.

Thank you in advance for your patience and attention (sorry for my English)
Best Regards
linux eager

ps : here my partition map
sda1 - fat16 2gb
sda2 - ntfs -25 gb
sda3 - ntfs -35 gb
sda4 - ubuntu 20gb
sda5- swap
sda6 - ntfs extended

---

### Post by dino99 on 2010-12-24
the whole doc:

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

maybe you need to mount the dos partition (/media/xxxx), look at 4.1.2 into the above doc

---

### Post by coffeecat on 2010-12-24
> **manasye said:**
> I try to edit grub.cfg to add but i am not sure what the command line should i use in menu entry

You shouldn't edit grub.cfg directly because this will be rewritten every time there is a kernel update and you will lose your ms-dos entry. You need to put a special stanza in /etc/grub.d/40_custom. I've adapted a Windows stanza from the link that the previous poster posted, but I don't know whether it will work. But try it anyway. This is what you need to do. First make 40_custom executable:

```
sudo chmod +x /etc/grub.d/40_custom
```Now open 40_custom in a text editor with root privileges:

```
gksudo gedit /etc/grub.d/40_custom
```Add a couple of blank lines to the end of the file and then add this stanza:

```
menuentry "msdos622 on sda1" {
    insmod chain
    insmod fat
    set root=(hd0,1)
    chainloader +1
}
```Save the file and close the text editor. Now regenerate grub.cfg with:

```
sudo update-grub
```Now reboot and see if the new stanza - which will be the last - boots you into msdos. Let us know how you get on.

---

