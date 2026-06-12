---
title: "blank screen durring 12.04 server insallation"
date: 2013-04-02
forum: Installation &amp; Upgrades
---

### Post by jjgist on 2013-04-02
I am trying to install ubuntu server using a cd on an old dell optiplex 760. the computer has a core 2 duo processor and im using the integrated graphics and networking. the computer loads the disk and i make it to the install options screen. when i selec install ubuntu server i get a black screen and nothing apears to be happening. I have tried selecting nomodeset but i have the same problem. when i select acpi=off or nolapic the instalion screen apears and i am asked to select a language but my keyboard is disabled so i am not able to go any further. does anybody know what my problem is any help would be appreciated.

p.s. 
I have tried installing both the 32 and 64 bit versions.

---

### Post by jjgist on 2013-04-03
update:
i updated the bios and i no longer have the blank screen issue but my keyboard is still deativated after i select the install ubuntu option.does anyone know what might cause this.

---

### Post by Bashing-om on 2013-04-03
jjgist; Hi !

The keyboard and mouse are handled by BIOS until the operating system is loaded. In my BIOS I have options as to what keyboard and mouse I have attached and my options have to be compatible. I am using the old ps2 keyboard and mouse.
I will advise to look around in bios and play with some of the options ( be prepared to reset to defaults, both in BIOS and as well how to reset back to defaults in the event you are not able to boot into the BIOS settings).
[INDENT=2]
just my thoughts

[/INDENT]

---

### Post by jjgist on 2013-04-03
As far as i can tell the only bios options i have are to activate or deactivate the usb controller. I am using a usb keyboard by the way. i dont have any older keyboards lying around. am i just stuck at this point

---

### Post by Bashing-om on 2013-04-03
jjgist; Ain't stuck, just scrambling for options !

How 'bout hunting up documentation for your version of BIOS (google is our friend). Re-reading your post(s) again. Seems I have jumped to conclusions as I see it now, keyboard works up until ubuntu is loading ( bios has at this time handed over control, and ubuntu does not handle it ?? I expect during the install stage the the hardware installed is probed and the kernel makes the adjustment, Makes me wonder what BIOS is telling the kernel.

After installation; ->/etc/X11/Xorg.conf
That is where XServer looks first for a Xorg configuration file. After it looks there, then it looks in the /usr/share/X11/xorg.conf.d directory...-> but on the desktop this has been largely depreciated // Do not know if or why a server would depend on this config file.

However:
XServer is just not the "basic" graphics layer... It's also how the keyboard, mouse, touchpad, gamecontroller, etc. interact in that layer... the /usr/share/X11/xorg.conf.d directory usually just contains files for those interactive pointing devices.

That directory also may contain custom files for a particular GPU, saying this is the how this GPU should be defined... But those would be files that the user defined and put in there him/herself.

With all that said ---  and I have not messed with a server in several years- try this:
The installer runs on VT1, if you switch the console 2 (alt+f2) and hit enter, lands you in a busy box shell (minimal) from which one may take some matters into your own hands. (alt+f1) returns you to the install console. The biggy here is that console 4 contains a running , though non-interactive-- logfile of the installation ! (alt+f4)

So What I propose is to wipe out your current work, and install a new, watching console 4 for what is going on, why the kernel is not picking up the keyboard.

I hope that this is the way the server install still works ![INDENT=2]
think'n with my fingers and pass'n it on

[/INDENT]

---

### Post by jjgist on 2013-04-03
im not sure how to get those alternate consoles. i lose the keyboard immediatly after i press install ubuntu server. i see the screen where i would select language and time zone but i have no input so i cant move forward. I have found other people with this problem on the internet and the solution is usually to use another keyboard. i use this keyboard with 12.04 desktop often but i didnt use if for the install so maybe its a compadability issue. i can press esc and get to the terminal boot menu but i think that will bring me to the same place as the graphical menu.

---

### Post by Bashing-om on 2013-04-03
jjgist;

I too have seen post where the only solution has been to use a ps2 keyboard///If you can still locate one, that would be the quickest way to troubleshoot out of this. I must conclude that some BIOS' just do not support USB // Sure is funny though that the keyboard functions up until the operating system should take over. Something is not getting passed OR not getting picked up.
Question to me, what is going on before Xorg is loaded into the operating system ?

Right now I am stuck, I just can not think of a way to either see what is happening nor do I know of a way to invoke any kernel parameters without a functional keyboard.....-> recompile from source is rather drastic !

I'll do some more pondering, perhaps in the meantime another will chime in with advise .[INDENT=3]
still learning even after all these years
[/INDENT]

---

### Post by MAFoElffen on 2013-04-04
+1 with Bashing-om on the keyboard. 

His 1st post was confused with a desktop edition... Ubuntu Server does not use X11 at all, unless the user installs it. 

The Server install iso is Linux kernel and so it the installed system. So the keyboard is BIOS to Grub2. Grub2 has kb and basic USB drivers.. Note that LILO doesn't recognized USB keyboards... Then hands off to kernel (kb drivers there also). Then if there are graphics layers, as in a desktop edition, then there are additional keyboard drivers in X11. 

After installing Server edition on hundreds of server's... I can confirm that "some" server boards don't like a USB keyboard on the install disk. ...and not all BIOS'es will pick up a USB keyboard in post. USB support on the motherboards has layers... So you have more of a chance on picking up USB keyboard through one of the USB root hub ports than through the second layer or an extension...Those root ports are normally on the back of the motherboard, near the keyboard/mouse PS2 ports. Usually ports on the front of a PC are on a higher layer or on an extension. But those same ports do pick up when the kernel boots through the HID drivers. 

I have 2 server boards here that are opposite and would only POST with a USB keyboard, but those are oddballs and not the norm. A ASUS and a Dell 960 server. Funny thing is I have 2 Dell 960 Servers and the other is fine/normal. But with both those 960's, the USB keyboard is not recognized in enough time to be able to get into BIOS Settings using a USB keyboard, so it doesn't recognize them early enough on those...

I have access to both PS2 and USB keyboards here, but I "do" a lot of dev testing. Traditionally, you are going to have more of a chance for success with a PS2 keyboard during POST and the early boot process. I get keyboards (both usb or ps2) for about $10 each at a Recycler. I also have USB/PS2 adapters for my USB mice and keyboards. They plug into the mouse/keyboard PS2 ports of the motherboard and the USB mouse or keyboard plug into them.

---

### Post by jjgist on 2013-04-04
this computer doesn&#8217;t even have a PS/2 port. It does have a parallel port that I can set to ps2 from the bios if I can find a keyboard and and an adaptor I might give that a try. iv never used a parallel port before so im not sure it will work. So far iv tried every usb port on the front and back of the machine. is there nothing that can be done to make it recognise the usb.

---

### Post by Bashing-om on 2013-04-04
@ MAFoElffen; Thank you once again, I appreciate the instruction. That helps much to alleviate my confusion. Filed and placed !

@         jjgist; Well, Maybe nor stuck, just between a rock and a hard place. Looks like there is no getting around the fact, going to have to come up with a keyboard/arrangement compatible with your BIOS.

Please let us know in this thread how it goes.[INDENT=2]
my best regards


[/INDENT]

---

### Post by steeldriver on 2013-04-04
I guess it may be that acpi=off is killing your USB peripherals - it's a bit of a longshot but you could try boot option 'i915.modeset=0' (which is specific to older Intel graphics) instead of 'nomodeset' (which I *think* is for nvidia) and dropping the 'acpi=off'

You *may* need to edit the boot line directly as I'm not sure that 'i915.modeset=0' is offered in the F6 menu

[http://askubuntu.com/questions/136593/how-can-i-fix-broken-i915-drivers-for-intel-gpus](http://askubuntu.com/questions/136593/how-can-i-fix-broken-i915-drivers-for-intel-gpus)

---

