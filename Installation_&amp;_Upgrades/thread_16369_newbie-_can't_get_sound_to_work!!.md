---
title: "newbie- can't get sound to work!!"
date: 2005-02-21
forum: Installation &amp; Upgrades
---

### Post by herbert on 2005-02-21
Hi Guys and Gals!!
I'm new to this linux stuff but I am pretty expert with windows!!

Ok, Install went great after a few hiccups but I'm finally at the desktop. I am pretty impressed at how far linux-unbuntu  has come. I had a great Install experience, expecting the install to be pretty hairy but it was as easy as win98 or win XP.  \\:D/  \\:D/ 

Ok, here is my problem I get the following error messages at startup.
Starting Hotplug Subsystem

modprobe: Fatal: error Inserting pciehp(/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permitted

modprobe: Fatal: error Inserting shpchp(/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permitted

Are these messages related to the failure of the sound card to work?

The sound card is detected as a cirrus logic crystal CS4281 PCI audio

I have Mixer support but no sound under any conditions. (CD apps, midiplayer etc.)

Do I need a different sound card ?

The motherboard is an Apollo MVP3/ Pro 133x 
CPU AMD K6-2 533 mhz
128 MB RAM
60 GB Maxtor drive

Where do I go from here? Thanks in advance!!

---

### Post by CyrilleMortreux on 2005-02-21
[QUOTE=herbert]
Ok, here is my problem I get the following error messages at startup.
Starting Hotplug Subsystem

modprobe: Fatal: error Inserting pciehp(/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permitted

modprobe: Fatal: error Inserting shpchp(/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permitted
[/QUOTE]

This is for PCI Hot plug devices. Your motherboard seems not to be concerned, and the boot system tells you that there is no way to use these modules because you have no such devices. 

That's all, and nothing to do with your soundcard. You 'll have to "blacklisted" these modules but I just can't remember where...

For that, I use "modconf" a very usefull Debian tool you may not find in the Ubuntu repository, but in Debian (Testing / Unstable) /main


> 
The sound card is detected as a cirrus logic crystal CS4281 PCI audio

I have Mixer support but no sound under any conditions. (CD apps, midiplayer etc.)

Do I need a different sound card ?


You should maybe try that as user in a xterm :

"alsamixer"

Use M to unmute 

"alsactl store" to register your values

And try.

---

### Post by herbert on 2005-02-21
okay

> That's all, and nothing to do with your soundcard. You 'll have to **"blacklisted"** these modules but I just can't remember where...

For that, I use **"modconf"** a very usefull Debian tool you may not find in the Ubuntu repository, but in Debian (Testing / Unstable) /main

what!! I don't speak linux yet please rephrase!! :-)  :-)

---

### Post by kassetra on 2005-02-21
[QUOTE=herbert]okay
 what!! I don't speak linux yet please rephrase!! :-)  :-)[/QUOTE]
 
 First of all, hi and welcome to ubuntu!
 Second, here is a great "[starter guide]("http://ubuntuguide.org/")" :)
 Third, here is how to [stop those trivial error messages]("http://ubuntuguide.org/#modprobefatalerror") at bootup.
 
 Also, did you get your sound working?

---

### Post by piedamaro on 2005-02-21
[QUOTE=herbert]I am pretty expert with windows!![/QUOTE]
This isn't always an advantage :D

---

### Post by cliff58 on 2005-02-21
[QUOTE=piedamaro]This isn't always an advantage :D[/QUOTE]

I second that emotion  :grin:

---

### Post by herbert on 2005-02-21
[QUOTE=kassetra]First of all, hi and welcome to ubuntu!
 Second, here is a great "[starter guide]("http://ubuntuguide.org/")" :)
 Third, here is how to [stop those trivial error messages]("http://ubuntuguide.org/#modprobefatalerror") at bootup.
 
 Also, did you get your sound working?[/QUOTE]

thanks for the tips. I do need the starter guide

No I don't have it working yet, still trying!

Actually this is my second experience with linux. Years ago I tried it with not a lot of success. I didn't have any linux compatible hardware so I gave up after about 2  months of failures. I tried the old distros recently on some spare hardware and I got it going to my surprize. I then stumble upon ubuntu and it renewed the fires to learn the system.

---

### Post by herbert on 2005-02-21
[QUOTE=piedamaro]This isn't always an advantage [/QUOTE]

[QUOTE=cliff58]I second that emotion  :grin:[/QUOTE]

The biggest hurdle so far is that I am reading the older posts and I have to guess what is trying to be communicated.

Examples, I know what a partition or MBR is but I am not sure yet about dual boot issues (I haven't needed to actually do it yet). I know my way around the dos command line but I don't know the equivalent commands yet in linux.

---

### Post by herbert on 2005-02-21
[QUOTE=CyrilleMortreux] You should maybe try that as user in a xterm :

"alsamixer"

Use M to unmute 

"alsactl store" to register your values

And try.[/QUOTE]

output from above: 

*alsactl: save_state:1088: cannot open /var/lib/alsa/asound.state for writing*

---

### Post by starfarer on 2005-02-22
I nearly had the same problem. CD player and music player doesn't produce any sound although slider is moving(ie playing). I downloaded xine and Xmms and suddenly i got the sound  :grin: .I have Turtle Beach Santa Cruz sound card and volume panel shows 2 bars 1) CS4297 and 2) CS46XX (right soundcard  for me btw).  I followed the guide for installation [http://ubuntuguide.org/#add-onapplications](http://ubuntuguide.org/#add-onapplications) for Xine and Xmms and also multimedia codecs.

Still CD player/music player  is not producing sound though but i can't complain as Xine is playing my MP3's and cd player.At least i can hear MUSIC!

---

### Post by herbert on 2005-02-22
[QUOTE=starfarer]I nearly had the same problem. CD player and music player doesn't produce any sound although slider is moving(ie playing). I downloaded xine and Xmms and suddenly i got the sound  :grin: .I have Turtle Beach Santa Cruz sound card and volume panel shows 2 bars 1) CS4297 and 2) CS46XX (right soundcard  for me btw).  I followed the guide for installation [http://ubuntuguide.org/#add-onapplications](http://ubuntuguide.org/#add-onapplications) for Xine and Xmms and also multimedia codecs.

Still CD player/music player  is not producing sound though but i can't complain as Xine is playing my MP3's and cd player. At least i can hear MUSIC![/QUOTE]

Thanks Starfarer
I tried all of the above, still no sound, nice graphics though!

---

### Post by herbert on 2005-02-22
> First of all, hi and welcome to ubuntu!
Second, here is a great "starter guide"
Third, here is how to stop those trivial error messages at bootup.

Also, did you get your sound working?

Thanks kassetra
That was exactly what I needed. 3 problems down, 1 to go, (That stupid sound card.)

---

### Post by leifew on 2005-02-23
I have the same problem during booting as herbert:
Starting Hotplug Subsystem

modprobe: Fatal: error Inserting pciehp(/lib/modules/2.6.8.1-4-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permitted

modprobe: Fatal: error Inserting shpchp(/lib/modules/2.6.8.1-4-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permitte

kassetra's tip how to stop those trivial error messages at bootup didn't work. I still get the same message when booting.

Maybe it doesn't work because my laptop is rather old and BIOS might not support ACPI ?
Excerpt from dmesg:

ACPI disabled because your bios is from 1999 and too old
You can enable it with acpi=force
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
Local APIC disabled by BIOS -- reenabling.
Could not enable APIC!

Don't use to much time on that, 'cause I'll install Ubuntu on a newer PC later on. I'm just curious why it didn't work.

Best,
leifew

---

### Post by herbert on 2005-02-23
[QUOTE=leifew]
Maybe it doesn't work because my laptop is rather old and BIOS might not support ACPI ?
Excerpt from dmesg:

ACPI disabled because your bios is from 1999 and too old
You can enable it with acpi=force
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
Local APIC disabled by BIOS -- reenabling.
Could not enable APIC!

Don't use to much time on that, 'cause I'll install Ubuntu on a newer PC later on. I'm just curious why it didn't work.

Best,
leifew[/QUOTE]

I am curious too the date of my bios is 3/21/2000 and is an award bios v4.60 pga but I did get ACPI to work(The system would not automatically power down until the ACPI began working) and the "trivial" error messages did stop. The only problems I'm getting which may be BIOS related is the system hangs on boot from cd-rom when no CD-ROM is present in the drive. Switching back to boot from C first allows ubuntu to load. (System does boot from CD when a bootable CD is in the drive.)

I am thinking about reflashing the BIOS to see if that would help. I'd hate to lose a test bed if flashing the BIOS makes things worst so it will be a last resort.

Also I have been getting a message on booting that says :

boot:
uncompressing linux...  Ok booting the kernel.
PCI:  0000:00:07.3: Class 604 doesn't match header type 00 ignoring class

then the system boots normally. Could this be part of the no sound problem?

Thanks guys!

---

### Post by Tyche on 2005-02-23
[QUOTE=herbert]output from above: 

*alsactl: save_state:1088: cannot open /var/lib/alsa/asound.state for writing*[/QUOTE]


Open a terminal (regular will do) and type:

sudo alsamixer M

and hit <ENTER>
you will be asked for your password

Arrow keys (left and right) to the various columns you want to unmute and type M for each one, then use the up arrow key to raise the volume.

when you are finished, type:

alsactl store

and hit <ENTER>

This works.  I just used it.  Now, if you'll excuse me, I'll turn down the volume on my speakers and search for a cure for shell shock.

8-)

---

### Post by herbert on 2005-02-24
Thanks guys

I got it to work! Thanks to all that posted help!

What worked!! I think a combination of all the things I did  that were recommended in the unofficial starter guide to ubuntu. (xine, xmms, multimedia codecs, repositories) 

I think it had been working since I got the mixer app to load. It turns out that I had to set every thing at max before I got any sound out. it seems I am getting a lot of hum and noise from the cpu when I move the mouse or the screen saver kicks end.

But hey, I've got sound!! CD Player was the first app to produce sound. Now that I got it working I will try loading ubuntu again and seeing what was actually the least I had to do to get sound.

Thanks again :smile:  :smile:

---

### Post by piedamaro on 2005-02-28
[QUOTE=herbert]Thanks guys

I got it to work! Thanks to all that posted help!

What worked!! I think a combination of all the things I did  that were recommended in the unofficial starter guide to ubuntu. (xine, xmms, multimedia codecs, repositories) 

I think it had been working since I got the mixer app to load. It turns out that I had to set every thing at max before I got any sound out. it seems I am getting a lot of hum and noise from the cpu when I move the mouse or the screen saver kicks end.

But hey, I've got sound!! CD Player was the first app to produce sound. Now that I got it working I will try loading ubuntu again and seeing what was actually the least I had to do to get sound.

Thanks again :smile:  :smile:[/QUOTE]
 IIRC when adio drivers are loaded, the mixer is muted, but just set it one time and you should be ok.
Hum is a common problem with integrated soundcards, especially with integrated vgas which usually use some hacks on the agp to obtain better performance. Tipically you hear noise when you move the mouse, resize windows etc.
There should be some tips on the subject at [www.alsa-project.org](www.alsa-project.org) and linux-sound.org/

---

