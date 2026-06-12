---
title: "how can i install ubuntu over my redhat-8?"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by kline on 2005-05-22
People,
 
On an old 400MHz box I have W2K and RedHat-8.0 installed.  ((For a few years I only let my daughter use the Linux installation for security reasons;  I also wanted her to learn on a unix-type system.  ))   It's time to blow away the RH stuff and use something that looks much better.  Ubuntu.   Is there a way that the Ubuntu disc can determine the windoze stuff  -- and where it ends?   From my first try on another server, it seemed as though Ubuntu only saw the entire drive(of my native FreeBSD ).
 
thanks in advance,
 
gary kline

---

### Post by bored2k on 2005-05-22
[QUOTE=kline]People,
 
On an old 400MHz box I have W2K and RedHat-8.0 installed.  ((For a few years I only let my daughter use the Linux installation for security reasons;  I also wanted her to learn on a unix-type system.  ))   It's time to blow away the RH stuff and use something that looks much better.  Ubuntu.   Is there a way that the Ubuntu disc can determine the windoze stuff  -- and where it ends?   From my first try on another server, it seemed as though Ubuntu only saw the entire drive(of my native FreeBSD ).
 
thanks in advance,
 
gary kline[/QUOTE]
 The ubuntu disc will recognize the existing Windows partitions and setup GRUB/LILO according to what it finds. No data will be lost unless you want to.

---

### Post by kline on 2005-05-25
[QUOTE=bored2k]The ubuntu disc will recognize the existing Windows partitions and setup GRUB/LILO according to what it finds. No data will be lost unless you want to.[/QUOTE]
 

Will the ubuntu install CD install *over* my RH partitions?  Or will I have to use tools to delete the Redhat stuff first?
A final question is: Does Ubuntu recognize any partitions  other than  Windows?  (( A future test system will have
W2K --maybe-- along with one of the Berkeley distributions and Darwin, and SuSE or Ubuntu.  I'm just wondering how
difficult this will be. ))

gary kline

---

### Post by bored2k on 2005-05-25
[QUOTE=kline]Will the ubuntu install CD install *over* my RH partitions?  Or will I have to use tools to delete the Redhat stuff first?
A final question is: Does Ubuntu recognize any partitions  other than  Windows?  (( A future test system will have
W2K --maybe-- along with one of the Berkeley distributions and Darwin, and SuSE or Ubuntu.  I'm just wondering how
difficult this will be. ))

gary kline[/QUOTE]
 It will install over. Unless you want to keep the filesystem intact.
It recognizes windows or any other OS partitions and will install proper boot loader.

---

### Post by kline on 2005-05-27
[QUOTE=bored2k]It will install over. Unless you want to keep the filesystem intact.
It recognizes windows or any other OS partitions and will install proper boot loader.[/QUOTE]
 Great!  I already have  ubuntu going on another spare server.   Much nicer than I had expected.  How to I pull down other 
packages: like ctwm, KDE,  bonnie++ and others?

gary kline

---

### Post by bored2k on 2005-05-27
[QUOTE=kline]Great!  I already have  ubuntu going on another spare server.   Much nicer than I had expected.  How to I pull down other 
packages: like ctwm, KDE,  bonnie++ and others?

gary kline[/QUOTE]
 Use apt-get or synaptic package manager.

sudo apt-get install kubuntu-desktop for KDE
other files, read man apt-get ;)

---

### Post by mohaham on 2005-05-27
synaptic is an excellent graphical  tool  to install new packages..
Start ''Synaptic Package Manager'' from the ''Computer''->''System Configuration'' menu->Synaptic Package Manager

if you dont find what you are looking for you can always add extra repositories like this..
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by kline on 2005-05-29
[QUOTE=mohaham]synaptic is an excellent graphical  tool  to install new packages..
Start ''Synaptic Package Manager'' from the ''Computer''->''System Configuration'' menu->Synaptic Package Manager

if you dont find what you are looking for you can always add extra repositories like this..
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)[/QUOTE]
 There are some few apps where a GUI makes sense--even a hardcore CLI hacker like me admits that :-)  For me,  these are mostly tools that in their command-line invocations require endless flags and  switches to do juat what the user wants.
Using apt-get was just one reason I gave up on Debian circa 1997-8.  synaptic is a good example of where GUI rules;  and where using apt-get would give me carpal tunnel syndrome, and fast!  ((Also, I couldn't find the list of installation packages to use with apt-get.))  Thanks to synaptic, I'm well on my way toward fine-tuning my home and root directories the way I want.

Eventually I  will see if I can login to root with ctwm with a few Workspaces; then have accounts for myself and others with the window  managers of their choice.  I'll always use FreeBSD on my DNS server.  Gotta see just how flexible Ubuntu is, though.  So far,  it's the best version of Linux ever.

--gk

PS: thanks for the pointer to the extrarepositories.  I can't find the mplayerplugin port/packer for site that *force* me to use windoze audio.  -g.

---

