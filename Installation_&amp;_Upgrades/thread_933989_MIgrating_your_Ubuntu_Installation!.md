---
title: "MIgrating your Ubuntu Installation!"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by ezek1el on 2008-09-30
[FONT="Lucida Console"][SIZE="3"]**I want to migrate my ubuntu installation from desktop to my laptop! That means i'll be keeping ubuntu on both of my computers!**[/SIZE]
[SIZE="2"]*Why Migrating? Because on desktop i've updated ubuntu and it runs fine & i don't want 2 install updates again on laptop![/FONT]*[/SIZE]
[SIZE="2"]*Why not clean install on laptop? Because ive installed XP-SP2 & MAC OS X Leopard 10.5.2 on my Laptop(dual boot)! I want 2 triple boot but when installing ubuntu, also i am getting stupid "_Soft Lock On CPU #0(1) Error!_"!*[/SIZE]
[I]**Here is Desktop Config:**
*Q6600-2.4Ghz x 4CPU's
*4 GB DDR2 800MHz.
*XFX 8800GT
*XP-SP2 + Vista + Ubuntu(i386)![/I]
[I]**Here is Laptop Config:**
*Core 2 duo (1.6 Ghz x 2 CPU's)
*1 GB DDR2 500 Mhz
*Model: Sony Vaio VGN-N27GH!
*Intel Chipset + Intel Wireless!
*XP-SP2 + MAC OS X + ?(Your Help!)[/I]
**[SIZE="4"]Please Help Guys I don't want 2 install all my programs all over again on my laptop! [/SIZE]**[-(

---

### Post by Greyed on 2008-09-30
> **ezek1el said:**
> [FONT=Lucida Console][SIZE=3][/SIZE][/FONT]**[SIZE=4]Please Help Guys I don't want 2 install all my programs all over again on my laptop! [/SIZE]**[-(

Er, why not?  The programs are fairly static.  What you really want to move over is your preferences.  IE, your configuration.  Those are stored mainly in two locations.

/etc
~

/etc you don't want to move over since the system wide preferences on a desktop are going to differ from those of a laptop.  Besides, unless you've done a lot of heavy modification in /etc (doubtful unless you run a server) chances are you can safely ignore any changes there.

That leaves your home directory.  That's a simple copy operation once your laptop is on the network.

The last hurdle is matching the the applications that are installed on your desktop.

```

dpkg --get-selections | grep -v deinstall > packages

```

That will store your current list of installed packages.

Copy that file over to the laptop then run these commands.

```

dpkg --set-selections < packages
sudo apt-get dselect-upgrade

```

Tadaaaa, your programs are automatically installed to match what you have on your desktop.

Of course I wrote those ideas out of order.  So here they are in order.

1: Install a base [K|X]Ubuntu of your preference.
2: Get it on the network
3: Run the dpkg --get-selections command on your desktop.
4: Copy the packages file to your laptop and probably /etc/apt/sources.list as well.
5: Run the dpkg --set-selections & apt-get commands.
6: Copy over your home directory.
7: Log out of and back into your GUI.  You should have a system set up pretty much identically to your desktop without all the heartburn of trying to copy over settings which aught not be copied.

---

### Post by cariboo on 2008-09-30
Can I ask why you are running a 32bit distribution on a quad core computer with 4GB ram?

Jim

---

### Post by MrFSL on 2008-09-30
> **cariboo907 said:**
> Can I ask why you are running a 32bit distribution on a quad core computer with 4GB ram?

Jim

Kudos - people actually read other people's system specs. I normally just blindly gloss over them.

---

### Post by ezek1el on 2008-09-30
[B]THANK YOU!Well thats what i was looking for, if u confirm that all programs on my laptop will be as same as on my Desktop!
[I]Well isn't there any way that i could burn complete ubuntu install on Dual layer DVD so i just have to put it in tray & bang! Installed, on my Laptop!
Just wondering, cuz Fedora 9 sulphur has some anaconda install error, morever ubuntu 's giving me soft lock error! So my laptop is just not taking it![/I]
[/B]_And i don't want 2 install open suse!_

---

### Post by ezek1el on 2008-09-30
> **cariboo907 said:**
> Can I ask why you are running a 32bit distribution on a quad core computer with 4GB ram?

Jim

[SIZE="3"][I]Well sir, as u can see i am "First cup of Ubuntu!" :D
So i got ubuntu 8.04 i386 dvd & ive installed it! If u can help, then tell me, that developing graphics on open gl with i686 will be easy or not or something different! I am a windows guy with DX knowledge on x64 vista![/I][/SIZE]

---

### Post by ezek1el on 2008-09-30
> **MrFSL said:**
> Kudos - people actually read other people's system specs. I normally just blindly gloss over them.

[SIZE="3"]*Actually, i thought u might know more about my system coz u know both are having 3 Operating Systems! :) - Kudos :)*[/SIZE]

---

