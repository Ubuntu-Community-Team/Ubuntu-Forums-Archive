---
title: "remove the Grub 9.10 the text old"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by n3wguys on 2009-11-30
hello dear all,
my name's amril and i am newbie for using ubuntu 9.10 the karmic kaola(get ubuntu latest from shippit site).i very glad because laptop i can at install ubuntu 9.10 and previous the installed linux ubuntu can not be done because driver not yet available.
but at ubuntu 9.10 the karmic kaola all can be done. :)

after i was upgraded and installed update 9.10 the karmic koala,
the next position grub installation, i was choose default the list information from combo list("blablabla installation localdrive").
when reboot my laptop, grub loader that displayed there two versions information when reboot:

------------------------------------ 
ubuntu, linux2.6.31-15-generic 
ubuntu, linux2.6.31-15-generic (recovery mode) 
ubuntu, linux2.6.31-14-generic 
ubuntu, linux2.6.31-14-generic (recovery mode) 
memory test(memtest 86+) 
memory test(memtest 86+, serial console 115200) 
xp(on dev/sda1)
-----------------------------------

my question is:
how to remove safe the text from the grub:

ubuntu, linux2.6.31-14-generic 
ubuntu, linux2.6.31-14-generic (recovery mode)
memory test(memtest 86+, serial console 115200)

or if can remove, what's the effect from ubuntu 9.10

thank you so much for information and i am very hope to get that information.:)

---

### Post by audiomick on 2009-11-30
Hallo.
The text is referring to an older version of the Kernel, and a memory testing program. I assume you mean removing the files that are referred to, and not just the line of text in the boot loader.

The older kernel is the one from the installer CD, and during the updates after the  installation a newer one has been added. The updater doesn't remove older kernels

It is possible to remove them, but I would suggest not to.

They are not taking up very much room, really very little.

If you try and remove them and mess it up, you could break the computer.

It is recommended to keep  at least 2 kernels on the computer. That way, if the newest one develops a problem somehow, one can still boot into the old one and save data and so on.

I would suggest to just leave things alone for now.

If you just want to edit the text in the bootloader, instructions are here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by darkod on 2009-11-30
Keep the older kernel entry definitely.
You could remove the memtest though, it's not like you are testing the memory every week. You can still enable it later or run memtest from the LiveCD.
To disable memtest from grub2 menu in terminal execute:
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub

You can enable it with the same command just use +x instead of -x. And you need to run update-grub after any change to grub2 config files.

---

### Post by n3wguys on 2009-11-30
hooo.... i understood..thanks brother..
but if i wanna to be remove/hide the text line only, not any else, where i setting the grub??

this is i wanna be hide the text line
-------------------------------------
ubuntu, linux2.6.31-14-generic
ubuntu, linux2.6.31-14-generic (recovery mode)
memory test(memtest 86+, serial console 115200)

---

### Post by darkod on 2009-11-30
You can not simply "hide" it. For memtest, if you execute the command I wrote, it will disable it from showing in grub2 menu, in other words, hide it.
For the 2.6.31-14 kernel it's not that easy, plus if something happens to 2.6.31-15 and you can't boot it, you can select the other one. That's why it's not recommended to remove it yet. 31-15 can be corrupted but 31-14 will work usually.
You can't just go into grub config and delete them, doesn't work like that.

---

### Post by n3wguys on 2009-12-01
mmmm.... okay.. thank you so much...:)
i will forget the problem that..
ones again, thanks all brother:)

---

