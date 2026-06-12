---
title: "Aspire 522 install network not working"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by troy7 on 2013-10-20
I'm trying to install Xubuntu 12.04 on an Aspire E1-522-5659.  I am having trouble getting the network to work during install.  I tried plugging a network cable in - still no go.  I am hesitant to continue till I get the network connected.  I have been reading the help at [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522) - put the network boot at the top of the boot order - no go.  My complete boot order is:

1.  Network Boot-IPV4:
2.  USB HDD: Lexam  USB Flash Drive
3.  HDD: TOSHIBA MQ01ABD075
4.  Windows Boot Manager
5.  ATAPI CDROM:
6.  USB FDD:
7.  USB CDROM:
8.  Network Boot-IPV6

Xubuntu does start the steps for installing - just don't have network.  Tried the 'Try Xubuntu without installing' option - can't ping.  Got this notebook free and it came with Windows8 (barf).  However, the network works in Windows8.  If I can get the network going, I feel confident I could solve the rest of my problems (trackpad).  Thanks.

---

### Post by varunendra on 2013-10-22
> **troy7 said:**
> I'm trying to install Xubuntu 12.04 on an Aspire E1-522-5659.  I am having trouble getting the network to work during install.  I tried plugging a network cable in - still no go.  I am hesitant to continue till I get the network connected.

You can troubleshoot the network issue 'after' the installation is finished, and if the rest of the system is working satisfactory enough in the live mode, you should finish the installation.

That being said, let us see which card you have and if it has any known issues. Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
lspci -nnk | grep -iA2 net
```

If the wireless is on a USB bus (some internal cards are) -
```
lsusb
```

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by troy7 on 2013-10-23
Here's what I get from a lspci -nnk | grep -iA2 net

>  
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. Device [1969:10a1] (rev 13)
            Subsystem: Acer Incorporated [ALI} Device [1025:0768]
01:00.1 SD Host controller [0805]: Atheros Communications Inc. Device [1969:3010] (rev 13)
---
05:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)
            Subsystem: Lite-On Communications Inc Device [11ad:0632]


---

### Post by varunendra on 2013-10-23
> **troy7 said:**
> Here's what I get from a lspci -nnk | grep -iA2 net
```
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. Device **[1969:10a1]** (rev 13)
Subsystem: Acer Incorporated [ALI} Device [1025:0768]
01:00.1 SD Host controller [0805]: Atheros Communications Inc. Device [1969:3010] (rev 13)
---
05:00.0 Network controller [0280]: Atheros Communications Inc. Device **[168c:0036]** (rev 01)
Subsystem: Lite-On Communications Inc Device [11ad:0632]
```
You must have been trying an older version of Xubuntu. Try the newer point release (Xubuntu 12.04.3) that comes with kernel version 3.8, both your ethernet and wireless will work out of box with it.

Official Torrent link for Xubuntu 12.04.3 (64 bit) : [http://torrent.ubuntu.com/xubuntu/releases/precise/release/desktop/xubuntu-12.04.3-desktop-amd64.iso.torrent](http://torrent.ubuntu.com/xubuntu/releases/precise/release/desktop/xubuntu-12.04.3-desktop-amd64.iso.torrent)

---

### Post by troy7 on 2013-11-09
Why do people reply without reading the post?  I was trying to install Xubuntu 12.04.3 (64 bit).  

My latest attempt I tried to install Xubuntu 13.10 - but with that I just get a white screen - which has a fair amount of posts, but I already have tried those.  I changed the boot order to all the configurations possible.  Guess I'll go on to other distributions and see what happens.

---

### Post by varunendra on 2013-11-09
> **troy7 said:**
> Why do people reply without reading the post?
Guess they are too stupid to recognize the personality on the other side. Thankfully, some of these stupids learn real fast !

Although even more interesting is - Why do people post **without reading their own posts**? Or why do they expect others to be mind readers?

> **troy7 said:**
> I was trying to install Xubuntu 12.04.3 (64 bit).

Sorry, I don't have microscopic eyes if you had mentioned ".3" somewhere in the 'nano-sized' fonts. With normal eyes, I still can't see that in your original post (or the later one, or the thread title itself) -
> **troy7 said:**
> **I'm trying to install [COLOR="#FF0000"]Xubuntu 12.04[/COLOR]** on an Aspire E1-522-5659.  I am having trouble getting the network to work during install.  I tried plugging a network cable in - still no go.  I am hesitant to continue till I get the network connected.  I have been reading the help at [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522) - put the network boot at the top of the boot order - no go.  My complete boot order is:

1.  Network Boot-IPV4:
2.  USB HDD: Lexam  USB Flash Drive
3.  HDD: TOSHIBA MQ01ABD075
4.  Windows Boot Manager
5.  ATAPI CDROM:
6.  USB FDD:
7.  USB CDROM:
8.  Network Boot-IPV6

Xubuntu does start the steps for installing - just don't have network.  Tried the 'Try Xubuntu without installing' option - can't ping.  Got this notebook free and it came with Windows8 (barf).  However, the network works in Windows8.  If I can get the network going, I feel confident I could solve the rest of my problems (trackpad).  Thanks.

And..
> **troy7 said:**
> Guess I'll go on to other distributions and see what happens.
+100

---

### Post by troy7 on 2013-11-16
Found the problem.  There was security setup - I guess through the uefi (bios).  I found this out when I tried running CloneZilla - got a popup with a one-line statement about USB and security.  To fix this, I had to get into the bios - arrow over to security.  There was a line about clearing USB security, but it was greyed out.  Only after I added a password for security was I able to arrow down to the USB clear security option and run this.  Not only did CloneZilla work after that, but Xubuntu booted with network working.

To be clear - I could boot into the Xubuntu before this change, but regardless if I selected INSTALL or RUN LIVE - I didn't have network.  Only after doing the steps above I have network.

I have both wireless and LAN network now.

I hope this helps the next person that runs into this.

---

