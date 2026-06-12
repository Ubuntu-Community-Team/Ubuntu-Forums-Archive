---
title: "Ubuntu installer can't mount cdrom"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by Anagonda on 2005-09-13
I downloaded the newest ubuntu 5.10 preview image, burned it with gnome, k3b. 
The k3b burning software checks the md5sum and it is correct.

After restart the installer starts ok, I choose languages and keyboard layout. Then the installer installs cd-rom drivers etc. and after that it tries to mount it (cdrom). After a few minutes it says it can't mount cdrom.
In the window that appears with F4 I get the message: "Missing modules 'ide-mod, ide-probe-mod, ide-detect' "

I tried to mount the cdrom manually (in F2-console), it takes a few minutes, says nothing and doesn't mount it. At the same time I was googling on my girlfriends laptop about the problem. I found a solution to write in console: "echo 'using_dma:0' > /proc/ide/hdd/settings". But that doesn't help. It writes to settings file that it uses dma 0, but I (or the installer) can't mount the cd.

The first cd I burned was a cd-rw. It works perfectly on my girlfriends laptop (I can install ubuntu with it). The second cd was a cd-r disc, but didn't help. I tried with unplugging hd's and only with pata hd on, but didn't help. Oh, and I tried with my old Plexter cd-rw drive. Didn't help :)

I got a new hd for my system, and want to try ubuntu... And I can't get my cedega to run fast enough on debian. And I don't like mandriva. Cedega runs 20x better on mandriva than debian. And I can't get enough performance with a new kernel on debian. 

My system at the moment is:
Debian, gnome, k3b
Asus P4P800Se motherboard
P4 2400mhz cpu
512mb ram
Samsung 250gb sata
Samsung 160gb pata
Nec dvd-writer
Nvidia ti4200 gpu

---

### Post by joostvdl on 2005-09-16
I too have an Asus MB and a Plextor (only a DVD-RW). It gave me the same problem. I looked at dmesg and it told me to use the option irqpoll when booting. I tried it and the installation is now running.

UPDATE: Install halted at 17% when installing GCC-4.0  ](*,)

---

### Post by Anagonda on 2005-09-19
Hmm, I downloaded Mandriva 2006 rc1 or what ever it was.

It had the same problem, can't mount cdrom. But from bios I found a tag under my cdrom, it was called something like: Type of device: "Auto". I changed it to "CD-rom" and now the mandriva installer can mount my cdrom.

But that didn't help on ubuntu :(

And now my problem is that on every boot I need to press F1 before bios goes further. "Not atapi device". And when I change the device type to auto my debian or mandriva doesn't boot... fucking computers :)

But I still want to try ubuntu... Help? Anyone?

---

### Post by Sabriel Dyrim on 2005-09-19
[QUOTE=Anagonda]Hmm, I downloaded Mandriva 2006 rc1 or what ever it was.

It had the same problem, can't mount cdrom. But from bios I found a tag under my cdrom, it was called something like: Type of device: "Auto". I changed it to "CD-rom" and now the mandriva installer can mount my cdrom.

But that didn't help on ubuntu :(

And now my problem is that on every boot I need to press F1 before bios goes further. "Not atapi device". And when I change the device type to auto my debian or mandriva doesn't boot... fucking computers :)

But I still want to try ubuntu... Help? Anyone?[/QUOTE]
 I'm having the same exact problem...first two steps go fine, and then it dies at the stupid red screen and says it can't mount the cd-rom. And I too have an ASUS motherboard. For the sake of all users with this problem...help!!

---

### Post by Anagonda on 2005-09-20
Hmm, now the installer mounted the cdrom ok.

What I did: I bought a new laptop to my girlfriend, downloaded image again, burned it with nero6316.exe(demo).
First i tried "install irqpoll", mounted cdrom fine, but halted on next screen at 8%(scanning cd, or what ever it was). I could not change screen to see if there where any errors
Ctrl-alt-del
Tried "server irqpoll", crashed on same screen, but at 4%

Then I tried only "server" and it worked fine, but I could not get my network card to work.

Now I take some backups and try to install ubuntu to my hd...

---

### Post by Anagonda on 2005-09-21
Now I'm writing this with ubuntu. But I don't really know what I did :D

My integrated sound or network didnt work so I put in a soundblaster live and 3com network adapter. Network works fine, but sound not... But it will be easy to get working.

Guys, good luck with installation, I really can't help with it. Wrote everything here that I did...

---

