---
title: "No sound detected with ubuntu"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by kelean on 2005-03-20
I cannot get any sound except the beep.  I have asked for help before with not much help.  I am running hoary 5.04 with the 2.6.10.5-686 kernel.  I have a cs-42xx sound card.  I have looked at so many different posts im getting mixxed up and confused.    If there is any other info needed please let me know.

  lspci returns this:
kevin@Kelean:~ $ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0e.0 Communication controller: Conexant HCF 56k Data/Fax/Voice Modem (Worldwide) (rev 08)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

Im not sure where to go from here.

---

### Post by ubuntu-geek on 2005-03-20
Check out my post here.. You are probably one of the many stuck in this sound hell :)

[http://ubuntuforums.org/showpost.php?p=100610&postcount=7](http://ubuntuforums.org/showpost.php?p=100610&postcount=7)

---

### Post by kelean on 2005-03-20
[QUOTE=ubuntu-geek]Check out my post here.. You are probably one of the many stuck in this sound hell :)

[http://ubuntuforums.org/showpost.php?p=100610&postcount=7](http://ubuntuforums.org/showpost.php?p=100610&postcount=7)[/QUOTE]
 I have tried what you suggested but when I get to the line

sudo ./configure --with-cards=emu10k1 --with-sequencer=yes

Here is the output

kevin@Kelean:/usr/src/alsa-driver-1.0.8 $ sudo ./configure --with-cards=snd-cs4232
--with-sequencer=yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

The only thing I changed was to put in my card

Any suggestions?

---

### Post by kelean on 2005-03-23
[QUOTE=kelean]I have tried what you suggested but when I get to the line

sudo ./configure --with-cards=emu10k1 --with-sequencer=yes

Here is the output

kevin@Kelean:/usr/src/alsa-driver-1.0.8 $ sudo ./configure --with-cards=snd-cs4232
--with-sequencer=yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

The only thing I changed was to put in my card

Any suggestions?[/QUOTE]
 I SURRENDER UBUNTU WINS!!!!!!!!
BACK TO YOPER I GO WHERE EVERYTHING WORKS WITH MY SYSTEM.

---

### Post by ubuntu-geek on 2005-03-23
Ubuntu doesnt come with compilers by default they need to be installed.

sudo apt-get install build-essential

That will give you the proper tools to build programs.

---

### Post by reshimo on 2005-04-17
Ubuntu-geek,

I have a SB Audigy LS and it is recognized in lspci. I am following a combination of instructions from [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+LS.&chip=SB0310%2C+P17&module=ca0106](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+LS.&chip=SB0310%2C+P17&module=ca0106)
and your post, but I am getting stymied...

I have installed the compilers and all works well until I run configuration using:

sudo ./configure --with-cards=ca0106 --with-sequencer=yes

I receive the following output:

checking for which soundcards to compile driver for... configure: error: Unsupported soundcard ca0106

Any ideas?

Thanks in advance,
reshimo

---

### Post by mikerm19 on 2005-10-13
Sorry to bring back an old thread, but I am having the same problem as above. When I get to the configure step I get the unsupported sound card error, any ideas?

```

checking for which soundcards to compile driver for... configure: error: Unsupported soundcard ca0106

```

In the --help it lists that exact one.

---

### Post by ryen on 2005-10-25
I had the same problem on debian sarge. Not sure why this fixed it, but by installing the kernel headers (apt-get install kernel-headers-2.4.xx..) seemed to have done the trick. Goodluck!

---

### Post by JLChafardet on 2005-12-13
it seems that this will never be worked out.

im stuck at the same issue.

i only get 2.1 audio, 2 front speakers and the bass. the rest is muted.

have tried EVERYTHING that has been said here, no luck.

i think the only thing left to try is kernel recompiling which was something i didnt wanted to mess with.

---

