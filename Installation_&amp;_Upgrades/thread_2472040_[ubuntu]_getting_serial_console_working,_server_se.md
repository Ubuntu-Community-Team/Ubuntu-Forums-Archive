---
title: "[ubuntu] getting serial console working, server setup?"
date: 2022-02-16
forum: Installation &amp; Upgrades
---

### Post by breakdaze on 2022-02-16
Oh shoot, I just typed forever, then accidentally closed the tab. I don't suppose this board has automatic draft saving?

Basically, I'm getting close to getting 2 Linux boxes linked with a full duplex null modem, but it's not quite right yet.

Cable is this, so it should be correct: [https://www.tripplite.com/null-modem-serial-db9-serial-cable-db9-female-female-6-ft~p450006](https://www.tripplite.com/null-modem-serial-db9-serial-cable-db9-female-female-6-ft~p450006)

I'm using ssh over Ethernet to configure both the Server (Ubuntu 21.10 Desktop) and Client (Live w/ persistence Lubuntu 20.04 made with Rufus).

For the ssh to work on the Live USB I had to make a new user. I called that user remote, and created a password.

Both Linux boxes don't have a monitor, keyboard, nor mouse, but they have Ethernet. The Lubuntu Live USB is in a PC with no hard disk.

On the Live USB, I ssh in, installed minicom, and did some stuff as described here: [https://roll.urown.net/server/serial-console.html](https://roll.urown.net/server/serial-console.html)

Mainly configured minicom with the settings; 115200,8N1, device is on ttyS0, and saved the config. Added my user to the dialout group. chmod 666 the /etc/minicom/minirc.dfl because while running and saving new configurations, it would not write the file.

launch minicom --coloron

Edited my grub.cfg on the server side:
```

set pref=/EFI/boot
set default="0"

# Load graphics (only corresponding ones will be found)
# (U)EFI
#insmod efi_gop
#insmod efi_uga
# legacy BIOS
#insmod vbe

if loadfont $pref/unicode.pf2; then
  set gfxmode=auto
  insmod efi_gop
  insmod efi_uga
  insmod gfxterm
  terminal_output gfxterm
fi

serial --unit=0 --speed=115200 --word=8 --parity=no --stop=1
terminal_input console serial
terminal_output gfxterm serial

set timeout="10"
set hidden_timeout_quiet=false

#insmod png
#if background_image $pref/ocswp-grub2.png; then
#  set color_normal=black/black
#  set color_highlight=magenta/black
#else
  set color_normal=cyan/blue
  set color_highlight=white/blue
#fi

#insmod play
#play 960 440 1 0 4 440 1

menuentry "Ubuntu 21.10 Desktop" {
  set root=(hd1,2)
  linux /vmlinuz root=/dev/sda3 ro vga=normal console=tty0 console=ttyS0,115200n8
  initrd /initrd.img
}

```

Reboot, and I do see some dmesg stuff come through, but also the formatting is off, then I can't login. It's as if my client side is sending characters to the server, or something.

I looked at this page, to see about setting up the server side better, but it seems old: [https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

What's the current correct server setup for Ubuntu 21.10?

I tried turning the hardware flow control on or off in mincom, but that didn't fix it.

Should I append an 'r' to the linux string for flow control? i.e. console=ttyS0,115200n8r

Mind you, I'm using putty from Windows 7 to ssh into the client, then in the client running minicom. I hope that doesn't foobar it.

Thanks!

---

### Post by MAFoElffen on 2022-02-16
> **breakdaze said:**
> Should I append an 'r' to the linux string for flow control? i.e. console=ttyS0,115200n8r
No you should not. It looks OK there above
> **breakdaze said:**
> Mind you, I'm using putty from Windows 7 to ssh into the client, then in the client running minicom. I hope that doesn't foobar it.
NO, you should not use SSH through Serial Console. Seria Console assumes you are only so many "feet" from the source host, and that you have physical control... 

Instructions for Putty to a Serial Console:

[LIST=1]
[*]Figure out the COM port you&#8217;ll be using. 
[*]Run PuTTY. 
[*]Switch the Connection Type to Serial. 
[*]Edit the Serial Line to match the COM port you want to use. 
[*]Edit the Speed to match the BAUD Rate you want to use. 
[*]Select the Serial category from the menu on the left. 
[*]Make sure all of the settings are correct. 
[*]Enter a Profile Name (because since connected to a serial console, you will use this again and again) 
[*]Save the settings... 
[*]Select the Open button to start the session. 
[/LIST]
Notice that these instructions for PuTTY do not say Connection Type SSH? That would be the wrong "Connection Type" for the connection...

---

### Post by breakdaze on 2022-02-16
> **MAFoElffen said:**
> No you should not. It looks OK there above

NO, you should not use SSH through Serial Console. Seria Console assumes you are only so many "feet" from the source host, and that you have physical control... 

Instructions for Putty to a Serial Console:



Hi MAFoElffen!

No, you misunderstood me. I wasn't trying to use SSH through the serial console. Simply put, I used putty to connect via ssh over Ethernet to the Lubuntu box, then once logged in through ssh, I used minicom to start my serial connection. So, the null modem cable isn't in play with putty. Then null modem cable connects Lubuntu client with Ubuntu server. The ssh is just a way to get into the client and do stuff.

So;
[LIST=1]
[*]Windows 7 putty ssh port 22 over Ethernet/IP -> Lubuntu Live USB session (login with a user that has a password).
[*]Once in Lubuntu, start minicom on PC with serial port (3F8, IRQ4)
[*]Fire up Ubuntu server, and the other end of the null modem cable is connected to this PC. Minicom starts to show output once grub is reached
[/LIST]

I scrounged up a keyboard, monitor, and mouse, but it is still funky when these are connected to the Lubuntu PC (client for null modem). putty/windows 7 is no longer in the picture, but still NG.

I'm not sure what could be wrong. I believe I have the settings matched.

Once upon a time, I got this to work using a usb to serial adapter, and I was able to see the dmesg and login to the server just fine.

I do realize the settings have to match, and they seem to. Perhaps I will try 9600 baud. Hardware flow on or off? Anything I should comment out of the grub.cfg?

Could the fact that I have to use sudo on the client be a factor? The guides say you shouldn't have to once you are part of the dialout group. Perhaps chown minicom? When I try to run without sudo:
minicom: cannot open /dev/ttyS0: Permission denied
new user I created is part of the dialout group, and dialout exists

Anyway, when the server starts, minicom shows grub> continuously then can't load command Ubuntu, then the cursor goes crazy.

Null modem cable is 6 feet, and wired: 1+6 - 4, 2-3, 3-2, 4 - 1+6, 5-5, 7-8, 8-7 allegedly. Perhaps I should confirm with an ohm meter.

Thanks so much. :)

---

### Post by breakdaze on 2022-02-16
OK, I'm making progress, I guess. I commented out this stuff:
```

#if loadfont $pref/unicode.pf2; then
#  set gfxmode=auto
#  insmod efi_gop
#  insmod efi_uga
#  insmod gfxterm
#  terminal_output gfxterm
#fi

```

And actually saw readable dmesg stuff, but then the output is restricted to the right column, and the cursor stays in the lower right corner.

[[img]https://i.postimg.cc/DWnQQMs9/screen.jpg[/img]](https://postimg.cc/DWnQQMs9)

---

### Post by MAFoElffen on 2022-02-16
> **breakdaze said:**
> minicom: cannot open /dev/ttyS0: Permission denied
new user I created is part of the dialout group, and dialout exists

And you are logged in as that user right?

On the Lubuntu machine... Please post the results of
```

groups ${USER}

```

---

### Post by breakdaze on 2022-02-17
Ya, logged in as.
```
remote@lubuntu:~$ groups ${USER}
remote : remote dialout sudo

```

Originally added to the group like this:
```
sudo usermod -a -G dialout remote
```

I'm seriously beginning to think it's hardware (the cable, the UART, the physical connectors). Results seem to vary each boot. I tried 9600 baud, software flow, hardware flow options in minicom. Tried removing and adding gfxterm from the terminal_output in grub.cfg, but it *seems* to work better with gfxterm. Although, that really shouldn't matter, I don't think. Maybe the 2 UARTS don't like each other. Seems like a noise on the line, or something because sometimes I get stopped at grub and it thinks I'm trying to give it commands.

Check out all these attempts:
[[img]https://i.postimg.cc/6yY8qVNh/screen2.jpg[/img]](https://postimg.cc/6yY8qVNh)

[[img]https://i.postimg.cc/yDxkZJ1C/screen3.jpg[/img]](https://postimg.cc/yDxkZJ1C)

[[img]https://i.postimg.cc/v4KDLQTg/screen4.jpg[/img]](https://postimg.cc/v4KDLQTg)

[[img]https://i.postimg.cc/wy8vZ0h9/screen5.jpg[/img]](https://postimg.cc/wy8vZ0h9)

[[img]https://i.postimg.cc/7G36k0V0/screen6.jpg[/img]](https://postimg.cc/7G36k0V0)

[[img]https://i.postimg.cc/yJSxLw3f/screen7.jpg[/img]](https://postimg.cc/yJSxLw3f)

I might have to just try another client PC and/or cable.

Software setup on client seems ok (I also installed setserial to get more info):
```
remote@lubuntu:~$ sudo setserial -a /dev/ttyS0
[sudo] password for remote: 
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
        Baud_base: 115200, close_delay: 50, divisor: 0
        closing_wait: 3000
        Flags: spd_normal skip_test

remote@lubuntu:~$ dmesg |grep ttyS0
[    0.633777] 00:03: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A

```

---

### Post by MAFoElffen on 2022-02-17
Yes. Agreed. It's getting corrupted stdin from somewhere(???)

That is crazy. LOL

---

### Post by breakdaze on 2022-02-18
Well this is embarrassing. The cable I thought I had, isn't. I was so excited to think I picked up the Tripp Lite P450-006 from a thrift store for $1.50US, but in reality, someone had put a Star Tech null modem cable in the Tripp Lite P450-006 bag. I looked closely and noticed the Star Tech logo on the end. So then I got out the meter and found that instead of : 1+6 - 4, 2-3, 3-2, 4 - 1+6, 5-5, 7-8, 8-7, it's actually wired : 1-1, 6-4, 2-3, 3-2, 4-6, 5-5, 7-8, 8-7. Oops! Looks like I'm going to have to slice and solder this. So, yeah, don't go with this one: [https://www.startech.com/en-us/cables/scnm9ff](https://www.startech.com/en-us/cables/scnm9ff)

In my research I found some good info on all of this serial, RS-232C, pinouts, and null modem stuff. From what I gather, the RS-232 never intended for this, it's by definition a hack.

Really, the Italian Wikipedia has the best details about the 7 wire asynchronous null modem configuration:
[https://it.wikipedia.org/wiki/Null_modem](https://it.wikipedia.org/wiki/Null_modem)

For more background and pinouts, pinouts.ru can't be beat. The real RS-232 used 25 pin D sub-miniature connector with 23 pins having a contact. However, microcomputers only used a simplified version, with a lot less pins, hence the migration to the RS232C DE-9 connection, using 9 pin D sub-miniature connectors on PCs. For a time, I had external modems that used a 25 to 9 pin D sub straight through cable, but that was only because the US Robotics modems came with the 25 pin D sub port on the back. Really, only 9 pins were used.

[https://pinouts.ru/SerialPorts/Serial9_pinout.shtml](https://pinouts.ru/SerialPorts/Serial9_pinout.shtml)
[https://pinouts.ru/SerialPorts/RS232_pinout.shtml](https://pinouts.ru/SerialPorts/RS232_pinout.shtml)

The Linux Documentation Project explains the cable you need for the Linux kernel (figure 11-1):
[https://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/serial-pc-terminal.html](https://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/serial-pc-terminal.html)
Main Index of Full article:
[https://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/index.html](https://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/index.html)

And remember folks, baud means the symbol rate, NOT bits per second!
Even this, doesn't explain it correctly. [https://tldp.org/HOWTO/Modem-HOWTO-23.html](https://tldp.org/HOWTO/Modem-HOWTO-23.html)

Start with the guy baud is named after: [https://en.wikipedia.org/wiki/%C3%89mile_Baudot](https://en.wikipedia.org/wiki/%C3%89mile_Baudot)
Then the math: [https://en.wikipedia.org/wiki/Baud](https://en.wikipedia.org/wiki/Baud)

But, I digress...

---

### Post by MAFoElffen on 2022-02-18
LOL. Yup.

I do mod-tap style 25 pin and 9 pin to RJ45 connectors. Then I've made up normal, null, and roll-over Cat 6 UTP cables. All put into a jump kit. That way I always hay something to work temporarily.

---

### Post by breakdaze on 2022-02-19
That's a good idea, so you can always reconfigure to suit your needs. The 9 pin to RJ45 is the Cisco Console cable, I guess. I have a ready-made one that's baby blue, but I haven't played with routers since I took the CCNA classes. I guess for USB to RS-232 serial, the FTDI chips and drivers are getting better and better. I have an FT231x breakout board I use to bit bang microcontrollers and other things. Technology these days is pretty good.

---

### Post by MAFoElffen on 2022-02-19
I can do Cisco Console from that kit, but no. All my plugs themselves adapters: DB to RJ45 (themselves), with no cable. The only cables I use are standard, null and rool-over Ethernet cables. See the attachment.

---

### Post by breakdaze on 2022-02-19
Oh very nice. I do a lot of work testing printers from a laptop, and the adapter I have is a Ethernet crossover male to female that you can just plug a regular patch cable into. The nice thing about the adapter is that it unplugs more easily from the Ethernet port on the laptop than some patch cords I run into out in the field. However, these days, most NICs are Gigabit and they automatically cross-over, but I like to have the adapter to be extra certain. As an aside, I think the design of the RJ connectors is less than ideal. The tab can break off, or be difficult to actuate. Too bad we are stuck with it at this point!

[https://cablesupply.com/cat5e-and-cat6-crossover-adapter-commercial-grade/](https://cablesupply.com/cat5e-and-cat6-crossover-adapter-commercial-grade/)

---

### Post by MAFoElffen on 2022-02-19
Agreed on the 'tab'... They are easy to connect, but not that durable in the long-run, when you are doing it repeatedly, all the time. 

Many of my temporary, self-made adapters for diagnostics are short RJ45M-RJ45M UTP cables only 3 inches long plugged into an RJ45F-RJ45F adapter plugged into one side of an Ethernet cable. 

I also make up Ethernet 'tap' adapters to listen into networks and network connections with WireShark, that way I can diagnose traffic that is going on from a specific problem location. Reminds me that physical security is everything. And that you should disable any ports on a switch or router that are not being used in the config's..

---

### Post by breakdaze on 2022-02-19
True physical security is important. Nice, a tap should let you see noise on a segment, unlike some other more fancy things. There doesn't seem to be such a thing as a true hub at gigabit. So are the plans for such a tap basically like 3 RJ45F connected together? I looked and looked for an off the shelf thing like that to use with Wireshark...

---

### Post by MAFoElffen on 2022-02-20
I had been doing it since the early 90's, when I designed my first Enterprise  multi-media cabling system. Then later took a Mod-Tap Modular Cabling Design course. They later used to give tours through a project I designed, to sell their own products. Later, College CNA Classes, which included Cisco NetAcad courses for CCENT and CCNA, and for MCSA/MCSE courses. 

We were taught to make our own cables and taps for WireShark. Yes, three to four RJ45 plugs. depending what you wanted to do...so that the extra MAC address doesn't confuse things with switches and is hidden. I found an Instructable for you for an easy to make breakout box Ethernet tap, with the same pinouts, that should help you: (and some other links) 
[https://www.instructables.com/Ethernet-Tap/](https://www.instructables.com/Ethernet-Tap/)
[https://janitha.com/articles/passive-splice-network-tap/](https://janitha.com/articles/passive-splice-network-tap/)
[https://null-byte.wonderhowto.com/forum/building-tap-passive-sniffer-by-mohamed-ahmed-0180143/](https://null-byte.wonderhowto.com/forum/building-tap-passive-sniffer-by-mohamed-ahmed-0180143/)
[https://greatscottgadgets.com/throwingstar/](https://greatscottgadgets.com/throwingstar/)

Also, with a null modem Ethernet cable, setting up static IP's on both to setup an ADHOC network between the two as a way to do "things". Yes, Hubs are hard to find anymore and not gigabit. And sometimes you don't have a spare switch lying around for something you need to do in a hurry.


> **breakdaze said:**
> True physical security is important. Nice, a tap should let you see noise on a segment, unlike some other more fancy things. There doesn't seem to be such a thing as a true hub at gigabit. So are the plans for such a tap basically like 3 RJ45F connected together? I looked and looked for an off the shelf thing like that to use with Wireshark...

---

### Post by breakdaze on 2022-02-22
Ah, I see, you want a separate connection for TX and RX! Snip wires to force 10/100 instead of Gigabit! Thanks for the links.

---

