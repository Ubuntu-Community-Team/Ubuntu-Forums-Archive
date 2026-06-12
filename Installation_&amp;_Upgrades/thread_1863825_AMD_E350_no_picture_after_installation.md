---
title: "AMD E350 no picture after installation"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by tristanbleijie on 2011-10-18
hello 

can someone please help me ? 

I've got an server with a Asus E35M1-I deluxe motherboard with a AMD 350 cpu/gpu (HD6310 graphics) and I wanted to install ubuntu server 11.10 64 bits.

The installation went perfectly everything installed as it should but when i tried to start the server for the first time I had no picture what so ever my monitor still gets a signal from the server or it would have said that it had no signal but I only get a black screen and nothing else 

If you need more information just ask 

with regards 

Tristan

---

### Post by nsbutgs on 2011-12-18
I have exactly the same. I think it tries to disable video card by turning off video signal (something like sleep mode). Or maybe is trying to enable graphics mode and cannot. I thought that Server runs in console mode only.

Anyways if you hit Ctrl + Alt + F1 (or F2 - F6) you you'll get one of text consoles where you can login. Clicking Alt + F7 will bring you back to black screen with no video.

Or you can ssh to your server from another box.

---

### Post by MAFoElffen on 2011-12-18
> **tristanbleijie said:**
> hello 

can someone please help me ? 

I've got an server with a Asus E35M1-I deluxe motherboard with a AMD 350 cpu/gpu (HD6310 graphics) and I wanted to install ubuntu server 11.10 64 bits.

The installation went perfectly everything installed as it should but when i tried to start the server for the first time I had no picture what so ever my monitor still gets a signal from the server or it would have said that it had no signal but I only get a black screen and nothing else 

If you need more information just ask 

with regards 

Tristan
On both of you, what is your video chipset?

From Server 11.04 on, server tweaked the VGA graphics for console theming. Grub 1.99 and the kernel also had graphics related changes. Anyways, the short of is, even though server is text, now it's text plus. Now you have to tweak some settings if you have a Video GPU that has above VGA Graphics capabilities.

Use "nomodeset vga=791" using these instructions (never mind that it was written for a desktop):
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]


Then login. After that
```

sudo nano /etc/default/grub

```Look for the line that starts with "GRUB_CMDLINE_LINUX_DEFAULT" and change it to 
```

GRUB_CMDLINE_LINUX_DEFAULT="vga-791"

```Then go to the end of file, add a line saying 
```

GRUB_GFXPAYLOAD_LINUX=text                      

```Save and exit.
```

sudo update grub

```Tell me how it goes.

---

