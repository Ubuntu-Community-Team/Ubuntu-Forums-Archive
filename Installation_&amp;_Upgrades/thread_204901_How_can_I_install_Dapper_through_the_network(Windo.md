---
title: "How can I install Dapper through the network?(Windows Machine)"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by AMCDeathKnight on 2006-06-27
How can I install Dapper through the network? All tutorials I have found are only for breezy.

Thanks I hope I get an answer this time.

---

### Post by John.Michael.Kane on 2006-06-27
[[COLOR="DarkOrange"]**Netboot**[/COLOR]]("https://help.ubuntu.com/community/Installation/Netboot")
[[COLOR="Blue"]**WindowsServerNetboot**[/COLOR]]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot")

---

### Post by AMCDeathKnight on 2006-06-27
Where is the Dapper Netboot Image?

---

### Post by John.Michael.Kane on 2006-06-27
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
** [COLOR="Red"]Under Setup DHCP-BOOT[/COLOR]**
[[COLOR="Purple"]**Ubuntu Dapper netboot archive**[/COLOR]]("http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/netboot.tar.gz")

---

### Post by AMCDeathKnight on 2006-06-27
Awesome thanks

---

### Post by AMCDeathKnight on 2006-06-27
Will it work the Windows netboot way? Also why is the netboot image 7 megs when the CD is around like 700. What is it missing?

---

### Post by John.Michael.Kane on 2006-06-27
AMCDeathKnight you shoukld be fine using the dapper net boot. just follow the info posted on those pages, and make sure all your data is backed up before starting.

---

### Post by AMCDeathKnight on 2006-06-27
Hmm, it wouldnt be the full Ubuntu thou wont it? With Gnome etc

---

### Post by John.Michael.Kane on 2006-06-27
It is installing the full ubuntu gnome ect. I'm not sure what else to tell you. other then you have to try it for yourself.

---

### Post by AMCDeathKnight on 2006-06-27
Ok lol, I just find it hard to beleive a 7 meg file has all of Ubuntu init lol

---

### Post by John.Michael.Kane on 2006-06-27
AMCDeathKnight if i'm not mistaken the file gathers the info from the net, and installs it that way.

---

### Post by AMCDeathKnight on 2006-06-27
I got this error:


The network autoconfigureation was sucessful. However no default route was set: the system does not know how to communicate with hosts on the Internet, This will make it impossible to continue with the installation unless you have the first installation DC-ROM, a 'netinst'CD-ROM or packages avaliable on the local network


I am currently at computer course, with a domain: Mordor, but I need to do it heere as the internet will not be avaliable at home.

---

### Post by John.Michael.Kane on 2006-06-27
Heres more info on this topic. There should be no need for a cd-disk. 

[**Install GNU/Linux without any CD**]("http://marc.herbert.free.fr/linux/win2linstall.html")

[**Network-booting Your Operating System**]("http://osdev.berlios.de/netboot.html")

---

### Post by AMCDeathKnight on 2006-06-27
Thanks, it didnt really help me probably, I tried the Insta Linux thing and it didnt work properly hmm

---

### Post by MetalMusicAddict on 2006-06-27
Is there a Ubuntu "net-boot: .iso? A cd image that pulls its packages from the net instead of cd?

---

### Post by AMCDeathKnight on 2006-06-27
Not that I could see, only a tar file.

---

### Post by John.Michael.Kane on 2006-06-27
[[COLOR="DarkOrange"]**Dapper netboot iso**[/COLOR]](ftp://ftp.ubuntu.com/ubuntu/dists/dapper/main/daily-installer-i386/current/images/netboot/mini.iso)

---

### Post by AMCDeathKnight on 2006-06-27
lol, how does that work with the ISO one? I am having so much trouble lol

---

### Post by John.Michael.Kane on 2006-06-27
during the install it should gather the packages from the net.

---

### Post by MetalMusicAddict on 2006-06-27
[QUOTE=SD-Plissken][[COLOR="DarkOrange"]**Dapper netboot iso**[/COLOR]](ftp://ftp.ubuntu.com/ubuntu/dists/dapper/main/daily-installer-i386/current/images/netboot/mini.iso)[/QUOTE]
WOW! 7 megs. Tiny. :) Thank you sir. I would guess this would still need a **dist-upgrade** after install?

---

### Post by John.Michael.Kane on 2006-06-27
Your welcome. i hope it helps you both.

---

### Post by AMCDeathKnight on 2006-06-27
So, does the DHCP tool point to the ISO instead of the netboot image instead?

---

### Post by gbw69 on 2006-06-29
[QUOTE=SD-Plissken]Heres more info on this topic. There should be no need for a cd-disk. 

[**Install GNU/Linux without any CD**]("http://marc.herbert.free.fr/linux/win2linstall.html")

[**Network-booting Your Operating System**]("http://osdev.berlios.de/netboot.html")[/QUOTE]
The instructions on this page works great with hoary.
I tried to use the linux kernel and initrd files from the dapper mirror but it gives me a persistant ramdisk error 'RAN OUT OF COMPRESSED DATA'
My goal is to install XUBUNTU, because of limited hardware and disk space, but I can't find a specific netboot kernel or initrd or download location.
Can someone please help me with this one?#-o

---

### Post by jniamehr on 2006-07-07
My web install keeps freezing, any tips for this... Im on a very high speed connection too (verizon fios)

---

