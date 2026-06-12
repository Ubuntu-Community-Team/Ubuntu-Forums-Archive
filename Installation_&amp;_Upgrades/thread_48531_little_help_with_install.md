---
title: "little help with install"
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by downtheciv on 2005-07-12
hey all 
looks like i will be spending a bit of time here this site looks fantasitc! 
i have a question about installing ubuntu 5.04 and whether or not it is possible to install on a hard drive without a cd boot up recognition in the bios. 
i havent tried the wiki suggestion of installing via the boot in windows as i have formatted the hd. should i try installing windows and then installing ubuntu in the way suggested in the installation with non removable media wiki ???

i have tried installing ubuntu onto a hd on my machine and transfering to another machine i would like to get ubuntu runnning on, and i get this error.

Uncompressing linux... ok, booting kernel
ACPI: unable to locate RSDP audit (1121353201.695.0): initialized /bin/sh: error while loading shared libraries: libc. 50.6: cannot open shared object directory
Kernel panic. not synching: VFS: Unable to mount root fs on unknown.block (0,0)

all help and hints appreciated

---

### Post by C.B. on 2005-07-13
This is not a very graceful nor technical solution, but as you said "all help and hints appreciated . . ."  	:-\"

You might try loading the Ubuntu installation file "Intel x86 install CD" to a bootable hard drive, stick the HD in the machine instead of a CD, install to a second clean HD. When the installation is finished, wipe the first (install) HD and use it for extra storage space.

Like I say, none too elegant. But who knows, it might just work.

Hopefully someone will have a better solution.

Good luck.

    Charles.

---

### Post by downtheciv on 2005-07-13
hey now thats not a bad idea at all
are suggesting coping the (whole) install cd to a hard drive? or perhaps a certian installation file of the cd? 

if so, do you think a cut and paste copy in a certian os, say i dunno winblows? to the booting hard drive, then a change over to the recipient machine would do the job. 
pending on success a then full installation into a dummy/slave hard drive? 

you are going to have to explain it to me in pre school stages, i dropped knoppix for ubuntu in the hope it would be easier to understand

i think i have the gist of it though two hd's on with a copy of the install cd on it, the master, booting up, yeah???

---

### Post by downtheciv on 2005-07-13
hmm tried it no luck im afraid, i might try messing roung with the master/slave combo and booting flags, but for now i just got a message basically saying non readable media or something like that.
why is i can install windows in a hard drive transfer the hd to another machine and it still boots, granted its badly however it still boot, yet linux wont when i try the same procedure? ](*,)

---

### Post by C.B. on 2005-07-14
Sorry that didn't help. Can't answer your question re windows either.

Re "master/slave combo and booting flags." Yes, if you can get BIOS to recognize the Ubuntu install HD as Prim Master it should boot it, right? What sort of BIOS/error messages, if any, do you get?

Did you download the "Intel x86 install CD" installation file? Maybe it just won't work the same on a HD instead of a CD. In any case, it's also a good idea to run the MD5 checksum utility on the file once you've downloaded it to make sure it's error free. Go to [www.ubuntulinux.org/wiki/BurningIsoHowto](www.ubuntulinux.org/wiki/BurningIsoHowto) . There you will find something on MD5. I had to download a couple of times before I got a good (i.e., bootable) file package.

Not sure what else to suggest. Sometimes sheer persistance and bit of luck (educated guess?) does the trick. :-?

---

### Post by downtheciv on 2005-07-14
i didnt download any iso's i got a cd shipped over from switzerland i think, took ages but was worth it, so i have a genuine linux ubuntu disc, i will try another hd boot hmmm
i have the install hd partitioned the problem may lie there

---

### Post by downtheciv on 2005-07-15
i think i may have a problem because of the way i have installed it onto hd i do not believe it is an iso, what would be the best way to say the disc image to iso????? then i will try booting up from the hd install cd iso.

---

### Post by C.B. on 2005-07-16
You may want to look at "Install GNU/Linux without any CD, floppy, USB-key, nor any other removable media" at [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html) . I think this applies to your situation. It looks a bit complex, but the info is Ubuntu specific. Just take it slowly and work thru it one step at a time. What I find sometimes helps is to edit the instructions so you have only the info needed, each step in order, and print it out to have in front of you in case something goes wrong.

---

### Post by downtheciv on 2005-07-17
hey C.B apprecitate your help here
am getting a prompt during the loadlin asking for the name of the kernel image file. 
i got the file from the ubuntu archive, just typing the command loadlin linux.bin brings the prompt up i guess the question is what is the kernel image file name??
any ideas? am just about there

---

### Post by C.B. on 2005-07-18
At this point I have to admit that I am fairly new to all of this too. . . . just one step ahead of you in that I've had Ubuntu Linux running for a few weeks now. I had some troubles getting started (using an older system) and so learned a few things the hard way. I understand the difficulties of needing to work around the limitations of hardware at hand,  so I've been trying to come up with suggestions that might work for you. But you're treading new ground here as far as my own experience goes and I don't want to give bad advice just trying to be helpful. I've been hoping that someone more knowledgeable would jump in on this thread and give some guidence, but you may have to figure out the final step or two on your own. As you say, you're almost there. Sorry to say that about the only thing I can offer at this point is "Don't give up!"

---

### Post by wvslkr on 2005-07-18
If I am understanding correctly, you can't set your bios to boot from cdrom.  I am assuming you do have a cdrom available for  the machine.  If that is the case you may want to try this: [https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto).  Much easier than what you are trying to do.

GL. Hope that helps. :)

---

