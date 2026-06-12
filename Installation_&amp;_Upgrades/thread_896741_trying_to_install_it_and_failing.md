---
title: "trying to install it and failing"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by murphy25 on 2008-08-21
hi.
im trying to install ubuntu 8.04 on my wifes old laptop its an acer aspire 1350 but i only get so far into the installation and it gives an error.
the HDD is completly blank as ive used dban to wipe it.
i put in the ubuntu cd start up and i get the choose language screen,i move down to install ubuntu and it starts installing i think well im on a screen that has the logo +ubuntu plus a bar with an orange bit moving back and fore,then it stops and the whole bar fills with orange,that lot disapears then some errors come up but they are gone before i can read them.
i end up on a page with the heading--
linux ubuntu 2.6.24-16-generic #1 smp then the date

then there is a bit about warranty and then this line--

to run a command as an administrator (user "root"),use "sudo <command>".
see "man sudo_root" for details

ubuntu@ubuntu:`$

im a complete noob when it comes to linux so havent a clue what to do i asked on a forum i use and one person said the problem was with the monitor and i had to add the refresh rates but i couldnt get the way he said to do it to work.
the acer laptop as far as im aware is in its original state except for a bigger HDD and 1gb ram.
i have been trying to get it to work for 2 days and i cant get past this screen because i dont know what to do:(:(

help please and thank you in advance

---

### Post by megauser on 2008-08-21
I am a noob too but are you sure you can install what ever OS you want on your Acer? I remember my sister had an Acer laptop and could not install any other OS then the company's own. They had to send it in and get them to install it again. Well might help some for you.

---

### Post by Vivaldi Gloria on 2008-08-21
I don't know anything about that computer but here is a standard list of things to try in your situation:

--------------------------------------------------

**1)** Make sure that your sytem satisfies the minumum specs:

> Ubuntu is available for PC, 64-Bit PC and Intel based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space.

Also make sure that you don't have a bad ram stick.

**2)** Check the cd you are using:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

and burn it slow.

**3)** Google your computer model and ubuntu. May be there's a fix. Seach launchpad bug reports and ubuntu forums.

**4)** In the ubuntu install menu press F6 and play with boot options:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

**5)** Try alternate cd. You can download it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box "Check here if you need the alternate desktop CD".

**6)** Install a cli-only system using the minimal cd:

[http://ubuntuforums.org/showthread.php?t=882596](http://ubuntuforums.org/showthread.php?t=882596)

And then add a desktop environment. For example:

sudo apt-get install ubuntu-desktop.

**7)** If nothing works file a bug report.

--------------------------------------------------


I suggest you try option 5 - the alternate cd. The reason I'm suggesting this is that you cannot get a graphical user interface (gui) with the regular desktop cd and the alternate cd doesn't use a gui.

---

### Post by murphy25 on 2008-08-21
thanks vivaldi i googled the make of the laptop and someone has managed to install ubuntu using the alternate cd so im downloading it now:)

---

### Post by Vivaldi Gloria on 2008-08-21
> **murphy25 said:**
> thanks vivaldi i googled the make of the laptop and someone has managed to install ubuntu using the alternate cd so im downloading it now:)

Hope it works. :-)

---

