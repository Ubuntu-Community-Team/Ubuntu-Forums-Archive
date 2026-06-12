---
title: "Soundcard not detected..."
date: 2005-09-19
forum: Installation &amp; Upgrades
---

### Post by mztriz on 2005-09-19
Hey, my name is Ava. I have a question about my soundcard... it's not being detected. I'm not exactly sure what to do or where to start. 
```
0000:00:00.0 Host bridge: Intel Corp. 440LX/EX - 82443LX/EX Host bridge (rev 03)0000:00:01.0 PCI bridge: Intel Corp. 440LX/EX - 82443LX/EX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)
0000:00:0d.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
0000:00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X (rev 5c)
``` 

Could anyone please help me?

Thanks, Ava.

---

### Post by skoal on 2005-09-19
Seems like you started the right way by posting the 'lspci' output.  However, since I now know you use the 440EX chipset, I assume your sound card is occupying an ISA slot, right?

What kind of ISA sound card is it?

You can try [here](https://wiki.ubuntu.com/forum/hardware/OldSoundCard), first.

Been a while since I've configured one of these bad boys.  I don't think you need to install the 'isapnptools' package.  I believe you can just record what IO and IRQ settings are given in your BIOS, and then (by knowing your sound card chipset), issue something like this:

sudo modprobe <alsa/oss sound driver> <IO> <IRQ>

\\//_

---

### Post by mztriz on 2005-09-19
The sound card is build into the motherboard. It worked when I used fedora core, so I  know its not defective.

---

### Post by skoal on 2005-09-19
[QUOTE=mztriz]The sound card is build into the motherboard. It worked when I used fedora core, so I  know its not defective.[/QUOTE]
On a 440EX? Hmm.  I thought you would need a separate sound chip installed by the mobo manufacturer for embedded sound with a 440.  I may be wrong.  Do you remember what fedora reported that chipset (sound driver) to be?  Who's the manufacturer of your motherboard, and do you have a model number (with revision number, if possible)? I can check their website and maybe figure it out for you...

\\//_

---

### Post by mztriz on 2005-09-19
[QUOTE=skoal]On a 440EX? Hmm.  I thought you would need a separate sound chip installed by the mobo manufacturer for embedded sound with a 440.  I may be wrong.  Do you remember what fedora reported that chipset (sound driver) to be?  Who's the manufacturer of your motherboard, and do you have a model number (with revision number, if possible)? I can check their website and maybe figure it out for you...

\\//_[/QUOTE]

Sorry, I'm not exactly sure what Fedora said, but I do remember it was a bunch of numbers lol.
My motherboard is.... Dell? I thought it was intel but I just opened the case and it says "dell" on it.  It came from a Dell OptiPlex.

As for the Model number... I don't  know I painted over the case... :(

Is there a number or somthing on the motherboard itself I could find?

Thanks for you help

---

### Post by skoal on 2005-09-19
What does 'dmesg' from a terminal report?  It should show that device (under ISA) even though it's integrated.  You can post back here that information (in quotes, please) or just provide that snipet.

You could try:

dmesg | grep -i "isa\|multi\|sound\|audio"

and maybe it will return (a more precise snipet) of the card info you are looking for.

Outside of not knowing that information (and you looking at the motherboard and reading off chipset numbers to me, which are on top of big black "squares"), you could try to install the 'isanpnptools' package, and do the following:

pnpdump > /etc/isapnp.conf

Then check that file (using an editor) and find the name of that sound card.

After you determine what that sound card is, then follow that original link I provided on our Wiki.

\\//_

---

### Post by mztriz on 2005-09-19
```
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[  227.919147] SELinux:  Disabled at boot.
[  231.111651] EISA bus registered
[  231.129710] ACPI: Interpreter disabled.
[  231.129786] pnp: PnP ACPI: disabled
[  231.154784] audit: initializing netlink socket (disabled)
[  231.156968] isapnp: Scanning for PnP cards...
[  231.260872] isapnp: Card 'CS4236B'
[  231.260898] isapnp: 1 Plug & Play card detected total
[  231.478662] EISA: Probing bus 0 at eisa.0
[  231.478780] EISA: Detected 0 cards.
[  231.515913] input: AT Translated Set 2 keyboard on isa0060/serio0
[  232.165369] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  276.713529] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[  293.849872] Yenta: ISA IRQ mask 0x0000, PCI irq 11
[  361.583140] Disabled Privacy Extensions on device c02eb280(lo)
```

---

### Post by mztriz on 2005-09-19
Sorry, I didn't read the in quotes part... so here it is again. > [4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[  227.919147] SELinux:  Disabled at boot.
[  231.111651] EISA bus registered
[  231.129710] ACPI: Interpreter disabled.
[  231.129786] pnp: PnP ACPI: disabled
[  231.154784] audit: initializing netlink socket (disabled)
[  231.156968] isapnp: Scanning for PnP cards...
[  231.260872] isapnp: Card 'CS4236B'
[  231.260898] isapnp: 1 Plug & Play card detected total
[  231.478662] EISA: Probing bus 0 at eisa.0
[  231.478780] EISA: Detected 0 cards.
[  231.515913] input: AT Translated Set 2 keyboard on isa0060/serio0
[  232.165369] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  276.713529] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[  293.849872] Yenta: ISA IRQ mask 0x0000, PCI irq 11
[  361.583140] Disabled Privacy Extensions on device c02eb280(lo)

---

### Post by skoal on 2005-09-20
Ahh, we struck gold.  You will use the 'snd-cs4236' module.  Just refer back to my first post and follow that link (from the Wiki).

\\//_

---

### Post by mztriz on 2005-09-20
[QUOTE=skoal]Ahh, we struck gold.  You will use the 'snd-cs4236' module.  Just refer back to my first post and follow that link (from the Wiki).

\\//_[/QUOTE]


Thank you!!  :)

---

### Post by skoal on 2005-09-20
Did you get the sound working?  If not, maybe I can step you through that wiki part.

\\//_

---

### Post by mztriz on 2005-09-21
[QUOTE=mztriz]Thank you!!  :)[/QUOTE]
 I read everything from the website you sent but I still have no idea as to what I'm suppose to do :(

---

### Post by skoal on 2005-09-21
Just for starters, open up a terminal, and type this:

sudo modprobe snd-cs4236

then,

alsamixer

then, try turning up the volumes and unmuting what you need to.

If you don't hear any sound, then you may have to add some BIOS related IO/IRQ/DMA settings.  If that's the case, record what those IO (port)/IRQ/DMA settings are in your BIOS and post back...

You will still have to modify a few things to make this permanent on subsequent reboots...

1. sudo gedit /etc/modules
2. Add the line 'snd-cs4236' (no quotes) in there somewhere...
3. save the file.

If you do need to add those BIOS related parameters, then just make that line (from step 2) as 'snd-cs4236 <io> <irq> <dma>' insead. Refer back to the wiki as an example...

\\//_

---

### Post by mztriz on 2005-09-21
[QUOTE=skoal]Just for starters, open up a terminal, and type this:

sudo modprobe snd-cs4236

then,

alsamixer

then, try turning up the volumes and unmuting what you need to.

If you don't hear any sound, then you may have to add some BIOS related IO/IRQ/DMA settings.  If that's the case, record what those IO (port)/IRQ/DMA settings are in your BIOS and post back...

You will still have to modify a few things to make this permanent on subsequent reboots...

1. sudo gedit /etc/modules
2. Add the line 'snd-cs4236' (no quotes) in there somewhere...
3. save the file.

If you do need to add those BIOS related parameters, then just make that line (from step 2) as 'snd-cs4236 <io> <irq> <dma>' insead. Refer back to the wiki as an example...

\\//_[/QUOTE]


```
mztriz@ubuntu:~$ sudo modprobe snd-cs4236
sudo: timestamp too far in the future: Sep 22 05:44:52 2005
```

---

### Post by mztriz on 2005-09-21
[QUOTE=mztriz]```
mztriz@ubuntu:~$ sudo modprobe snd-cs4236
sudo: timestamp too far in the future: Sep 22 05:44:52 2005
```[/QUOTE]
 ```
alsamixer: function snd_ctl_open failed for default: No such file or directory
mztriz@ubuntu:~$ 
```

---

### Post by skoal on 2005-09-21
[QUOTE=mztriz]```
mztriz@ubuntu:~$ sudo modprobe snd-cs4236
sudo: timestamp too far in the future: Sep 22 05:44:52 2005
```[/QUOTE]
Wow. Looks like you're running one of those next generation computers, or you're typing to me from inside a wormhole...

muahaha...

Argh, why do I always stumble across these unique support type posts?  I really don't know why you would be getting that particular message.  I think this may be some kind of sudo voodoo going on here.  I really don't know.

Just login as root in a terminal then, and try it out that way.  Then, fire up alsamixer and try 'er out.  If that works, still as root, go back to steps 1-3 and edit that file...

\\//_

---

### Post by mztriz on 2005-09-21
ahhhh it doesnt let me log in as root!?

I have to type in su
then my password right?

---

### Post by mztriz on 2005-09-21
You know what, I'm going to try to reinstall ubuntu and then try this again... lol

---

### Post by skoal on 2005-09-21
[QUOTE=mztriz]ahhhh it doesnt let me log in as root!?

I have to type in su
then my password right?[/QUOTE]
oops. yes, sir.  Just do this:

sudo passwd root

then, type in your regular user password first, then your root password twice...

Then, just type in:

su -

to login as root.

We'll get ya going, brother.  No need to reinstall.

\\//_

---

### Post by mztriz on 2005-09-22
[QUOTE=skoal]oops. yes, sir.  Just do this:

sudo passwd root

then, type in your regular user password first, then your root password twice...

Then, just type in:

su -

to login as root.

We'll get ya going, brother.  No need to reinstall.

\\//_[/QUOTE]


I reinstalled anyway lol ok now I'm about to try this.

ps. I'm a girl ;p

---

### Post by mztriz on 2005-09-22
[QUOTE=skoal]oops. yes, sir.  Just do this:

sudo passwd root

then, type in your regular user password first, then your root password twice...

Then, just type in:

su -

to login as root.

We'll get ya going, brother.  No need to reinstall.

\\//_[/QUOTE]
 
```
root@ubuntu:~# sudo gedit /ect/modules

(gedit:6748): Gtk-WARNING **: cannot open display:
```

---

### Post by skoal on 2005-09-22
oops. yes, mam, I mean.  Will get ya going, sister...

Shoot, I may be digging us both deeper into a sinkhole, here, but...you wouldn't happen to know vi would you? I'm so far removed from GUI reliability these days I don't even have a clue what else is out there for editors.  I haven't used Emacs in over 10 years (and don't have it installed), so I'd just be equally lost suggesting it to you.  Anyways, you get that "cannot open display" because you're using gedit (which is a GUI app and you're running X under a different user now, root).

Umm, lemme think here...

Try this, first (still as root):

nano /etc/modules

I haven't used nano in ages and almost deleted half my modules file while navigating around in vi style.  I _think_ you just use the arrows and delete key, then type ^W (for write, I think) and then answer yes...

I'm really having a hard time at this point trying to remember where we left off without re-reading 3 pages of this.  If this don't work, just 'pm' me and I step you through this over gAIM.  Too many things could be going on here (and we'll just fill up 5 pages worth before we reach a sol'n).  You can post back the sol'n here later for someone else to read if they stumble on this thread...

Let me know if 'nano' works or just 'pm' me...

\\//_

---

### Post by mztriz on 2005-09-22
[QUOTE=skoal]oops. yes, mam, I mean.  Will get ya going, sister...

Shoot, I may be digging us both deeper into a sinkhole, here, but...you wouldn't happen to know vi would you? I'm so far removed from GUI reliability these days I don't even have a clue what else is out there for editors.  I haven't used Emacs in over 10 years (and don't have it installed), so I'd just be equally lost suggesting it to you.  Anyways, you get that "cannot open display" because you're using gedit (which is a GUI app and you're running X under a different user now, root).

Umm, lemme think here...

Try this, first (still as root):

nano /etc/modules

I haven't used nano in ages and almost deleted half my modules file while navigating around in vi style.  I _think_ you just use the arrows and delete key, then type ^W (for write, I think) and then answer yes...

I'm really having a hard time at this point trying to remember where we left off without re-reading 3 pages of this.  If this don't work, just 'pm' me and I step you through this over gAIM.  Too many things could be going on here (and we'll just fill up 5 pages worth before we reach a sol'n).  You can post back the sol'n here later for someone else to read if they stumble on this thread...

Let me know if 'nano' works or just 'pm' me...

\\//_[/QUOTE]


Ok, I PMed you. Thanks  :)

---

### Post by mztriz on 2005-10-07
ok... lets restart... I reinstalled Ubuntu, and I have a snd-cs4236 sound card....and now.... what should I do?

---

### Post by mztriz on 2005-10-07
ok I got it to work sorta... I did this 
sudo modprobe snd-cs4236 then, alsamixer 

However, I tried to add it to /ect/modules using nano, and it still told me there was no directory.


 I can hear the speakers on but nothing else works. 

EX. if I put in a cd it opens the player (which it wouldn't do before, because it told me I had no sound) and I go to play a song but it doesnt work. The cd is recognized it even picks up the title and track listing from online. Once I hit play nothing happens. It says 

"Error Playing CD.
Reason: Could not open resouce for writing."

---

### Post by skoal on 2005-10-07
Mztriz, did I make a typo somewhere in my prior posts?

That should be: /**etc**/modules

Check the spelling you're using.  By the way, if you've succesfully 'modprobe'd the driver already, all you need to do is fire up alsamixer and turn up the various channels for sound.

\\//_

---

### Post by mztriz on 2005-10-07
Ah, that would have been my mistake. Sorry =\

I already turned the sound up though, and I'm still getting that error when I try to play anything.

---

### Post by mztriz on 2005-10-07
[QUOTE=mztriz]Ah, that would have been my mistake. Sorry =\

I already turned the sound up though, and I'm still getting that error when I try to play anything.[/QUOTE]

My mistake again... I just restarted and now everything works just fine.

Thank you so much for all of your help, and putting up with my crazyness. :D

---

### Post by skoal on 2005-10-07
[QUOTE=mztriz]Thank you so much for all of your help, and putting up with my crazyness. :D[/QUOTE]
What did mama always say, "crazy is as crazy does!".  I reread some of these posts, and even I actually completely overlooked your typo and went merrily along by offering and _incorrect_ reason for your problem!

If your sound is working now, that's great.  The only other issue I noticed here was that "Error Playing CD" problem, but you never mentioned which application that is.  Go to help > about in the menu for it.  Then, you can do a search in these forums for a similiar problem, or post back here.

\\//_

---

### Post by mztriz on 2005-10-07
[QUOTE=skoal]What did mama always say, "crazy is as crazy does!".  I reread some of these posts, and even I actually completely overlooked your typo and went merrily along by offering and _incorrect_ reason for your problem!

If your sound is working now, that's great.  The only other issue I noticed here was that "Error Playing CD" problem, but you never mentioned which application that is.  Go to help > about in the menu for it.  Then, you can do a search in these forums for a similiar problem, or post back here.

\\//_[/QUOTE]

It's fine now (= The error went away when I restarted

---

