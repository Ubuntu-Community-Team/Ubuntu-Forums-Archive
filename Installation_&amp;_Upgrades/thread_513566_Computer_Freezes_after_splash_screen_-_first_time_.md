---
title: "Computer Freezes after splash screen - first time booting"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by smartsalman on 2007-07-30
Hey,

My computer freezes after I try to boot ubuntu. This is the first time i'm booting it after the install. It installed perfectly and installed the boot loader then from the loader I select ubuntu (non recovery mode) and it starts, then goes to the splash screen, then splash screen dissapears and computer hangs up.

any help?

Thanks,
Salman

Using HP DV6115CA laptop,
AMD Turion 64 X2 TL-52
2GB RAM
100 GB HD
Nvidia GO 6150 128MB RAM

---

### Post by bogolisk on 2007-07-30
> **smartsalman said:**
> Hey,

My computer freezes after I try to boot ubuntu. This is the first time i'm booting it after the install. It installed perfectly and installed the boot loader then from the loader I select ubuntu (non recovery mode) and it starts, then goes to the splash screen, then splash screen dissapears and computer hangs up.

any help?

Thanks,
Salman

Using HP DV6115CA laptop,
AMD Turion 64 X2 TL-52
2GB RAM
100 GB HD
Nvidia GO 6150 128MB RAM

Which version of Ubuntu? I have a Nvidia 6150/ MCP51 board too, and it would take feisty (kernel 2.6.20) to boot with USB legacy enabled in the bios. Dapper and Edgy (kernel < 2.6.20) kernels would not boot with USB legacy enabled in the bios.

It's a bug in the ubuntu kernels because all versions of grml ([http://grml.org](http://grml.org))  i've tried have no problem booting my mobo with legacy usb enabled in the bios.

---

### Post by smartsalman on 2007-07-30
Its the latest one i JUST downloaded it like 5 hrs ago.

I did not understand a word u just said lol.. sorry :(. So what exactly do I do to boot it?

sorry bout that.

---

### Post by smartsalman on 2007-07-30
are there certain paramerters i should boot with?

---

### Post by smartsalman on 2007-07-30
Also i cannot find a legacy usb option in my bios (HP laptop)

---

### Post by bogolisk on 2007-07-30
> **bogolisk said:**
> Which version of Ubuntu? I have a Nvidia 6150/ MCP51 board too, and it would take feisty (kernel 2.6.20) to boot with USB legacy enabled in the bios. Dapper and Edgy (kernel < 2.6.20) kernels would not boot with USB legacy enabled in the bios.

It's a bug in the ubuntu kernels because all versions of grml ([http://grml.org](http://grml.org))  i've tried have no problem booting my mobo with legacy usb enabled in the bios.

[LIST]
[*]dapper : ubuntu 6.o6 LTS
[*]edgy: ubuntu 6.10
[*]feisty: ubuntu 7.10
[/LIST]

try to disable USB in the BIOS. Once Linux (sucessfully) booted, it can handle USB by itself. disconnect all usb devices (mouse, pointer, usb keys, external keyboard, etc)

and try to boot.

---

### Post by smartsalman on 2007-07-30
No option in BIOS about disabling and enabling USB :S

---

### Post by bogolisk on 2007-07-30
> **smartsalman said:**
> No option in BIOS about disabling and enabling USB :S

disconnect all usb devices: card reader, card, mouse, etc.

---

### Post by smartsalman on 2007-07-30
OK let me try that,

be back in 5 mins

---

### Post by smartsalman on 2007-07-30
nope :(

this is exactly what happens

I see the splash screen with the loading bar underneath. When it loads completely, the splash screen dissapears and on the screen "_" appears and flashes bout 5 times then screen goes blank and nothing happens

Again this is the first time linux is booting on my system. It installed perfectly but cannot boot now...

I have nothing pluged into my laptop but the charger

---

### Post by RandomGameR on 2007-07-30
I'm a bit of a noob myself so this might not be of any help but when your computer hits the flashing "_" can you try to hit ALT-F1.

If you have the same problem that I had then you'll see a text-based interface that will allow you to log-in using the username and password you supplied during installation.  You'll then want to go [here]("http://www.nvidia.com/content/drivers/drivers.asp") to find the script that will download or compile the appropriate drivers for your graphics card and 64 bit version.

Hope this helps.

---

### Post by smartsalman on 2007-07-30
o wait... i have the 32 bit version not the 64 bit...

will that be ok?

i'm running AMD Turion 64

---

### Post by RandomGameR on 2007-07-30
Yeah, I believe that you're fine in using the 32 bit version with a 64 bit processor.  The problem that I had seemed similar to yours and it was that my graphics card (An NVIDIA GO as well) needed updated drivers.  Nvidia's page there gives drivers for Linux x86, which is what I believe you'd need.

Are you able to login when you hit ALT-F2, though?

---

### Post by smartsalman on 2007-07-30
nope :(

i press the alt f2.. it goes to text mode for literally like 2 seconds then the screen goes blank..

any other way to enter the text mode and install the drivers?

---

### Post by merlinus on 2007-07-30
Maybe this will work:

Ctrl-Alt-F1 to get to prompt

sudo dpkg-reconfigure xserver-xorg

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:

startx

or reboot.

-merlin

---

### Post by smartsalman on 2007-07-30
It wont let me goto the prompt

it loads up stuff then hangs the computer... I cannot get to the command mode...

---

### Post by smartsalman on 2007-07-30
so pissed....

i think i am gonna install fedora or something now...

---

