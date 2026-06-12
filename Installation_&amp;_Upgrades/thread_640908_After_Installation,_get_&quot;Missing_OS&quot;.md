---
title: "After Installation, get &quot;Missing OS&quot;"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by FunFred on 2007-12-14
Hi! Ok, well, I just attempted to install Ubuntu for the first time (outside of my CPU Diagnoistics class).

I burnt the Boot CD with no problems, and everything seems to boot correctly from the Live CD.

I then go through the installation process, and everything appears to work fine. No error messages or anything.

However, when I attempt to boot from the HDD, I get the message "Missing OS"

I am guessing that Ubuntu has successfully cleared my former partition (Windows, which I wanted to get rid of). However, it appears to not want to install Ubuntu.

So, what am I missing?  Any suggestions?

Thanks! I appreciate it!

---

### Post by volkswagner on 2007-12-14
Start by going into bios and making sure hardisk is first boot device.  If it is boot from the live cd and browse your file system partiion, check /boot and report back what is there.

---

### Post by FunFred on 2007-12-14
Ok. Well, I actually changed the boot order to make the HDD the first device. However, I still get the same message.

I am not really sure what you want to know about the /boot folder, so I am just listing the files:

abi-2.6.22-14-generic

config-2.6.22-14-generic

initrd.img-2.6.22-14-generic

initrd.img-2.6.22-14-generic.bak

memtest86+.bin

system.map-2.6.22-14-generic

vmlinuz-2.6.22-14-generic

Does that give you a clue? Any ideas?

Thanks for the help in advance!

---

### Post by diatribe on 2007-12-14
there should be a grub subfolder under boot, I am guessing that the menu.lst file contained within that folder is pointing to an incorrect partition, hence the missing os error.  check your menu.lst to make sure all parititons are entered correctly

---

### Post by FunFred on 2007-12-14
I know this may sound stupid, but I can't seem to find that subfolder. I have checked via GNOME and Terminal (I use Macs, so I am familiar with Terminal), and I simply can't find it. I also looked for menu.lst with the Tracker Search Tool, and it returned no results.

Please forgive me if that is really dumb! Thanks for your patience!

---

### Post by diatribe on 2007-12-14
you need to install a bootloader then, that would be grub

---

### Post by FunFred on 2007-12-14
Ok. Well, I tried everything I can think of.

I burnt a Grub ISO, but it kept failing when I tried to get it to install itself (Error 15: Can't Find File [something like that]). I then simply tried bring the Grub folder over to Ubuntu and running it from there (I found some instructions online), but that didn't work.

So where should I go from here?

Once again, thank you so much for your help and patience. I know that you don't have to spend your time doing this, and I really appreciate it.

---

### Post by FunFred on 2007-12-16
well, today I finally received the official Ubuntu CD (I had been using a downloaded ISO before). Sure enough, installing from this CD worked perfectly. Go figure.

Thanks for all of your help and patience! Is there some way I can the you points or something for your help?

---

### Post by cjm5229 on 2007-12-16
You probably burned your first CD at too fast a speed, you always need to burn your install CD at the slowest speed your burning software will let you. Glad to hear the Shipit CD's worked for you.:)

---

