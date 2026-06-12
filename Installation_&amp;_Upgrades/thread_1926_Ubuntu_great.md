---
title: "Ubuntu great"
date: 2004-10-24
forum: Installation &amp; Upgrades
---

### Post by jcscar on 2004-10-24
I have managed to get Ubuntu running great, with a few setbacks mentioned in other post, However I managed to kill my windows installation do to my own clumsyness in the install. Now I want to partition my drive to allow room for me to install windows again because I have a few programs that will only run under windows that I need to run.  However I want to use Ubuntu 90% of the time.  I really don't want to have to reinstall Ubuntu now that I have a lot of stuff working that wasn't to begin with. 

 Is there some partitioning tool for Linux I can download?

 Is there a certain way I should go about installing Windows XP on the same drive?

---

### Post by FLeiXiuS on 2004-10-24
I'm a huge fan of 
```
cfdisk
```

Give it a shot..enter it into a term.

---

### Post by im_ka on 2004-10-24
what are those windows apps you can't replace with linux ones? maybe we can help ;)

---

### Post by jcscar on 2004-10-24
I am very familiar with Photoshop. I manipulate pictures professionally.  Several games I have like Starcraft, Broodwar, and other Blizzard products. 

I am looking for a gui partioning program

---

### Post by rolf on 2004-10-24
Windows really shines in gaming, I can't argue with that.

---

### Post by im_ka on 2004-10-24
i haven't really used photoshop, but i think the gimp is quite a replacement.

games: download cedega (windows emulator made for gaming) normally, you'd have to pay for it...  but pm me to get it :D
it should work without problems for almost all games. please don't ask me how to set it up, i don't play myself (i just "put my hands" on cedega so i can pass it on). do some [http://www.google.com/linux](http://www.google.com/linux) search on it. or ask here on the forum, i'm sure there are users around using cedega (formerly known as winex).

gui partitioning: qtparted

---

### Post by jdong on 2004-10-24
[QUOTE=jcscar]
I am looking for a gui partioning program[/QUOTE]

QTParted is a Partition Magic clone, capable of safely resizing many FS'es, like NTFS, FATxx, most Linux filesystems, etc. It also functions as a GUI partitioner.


It's in Ubuntu universe and is installable via APT/Synaptic!

---

### Post by jdong on 2004-10-24
[QUOTE=im_ka]
games: download cedega (windows emulator made for gaming) normally, you'd have to pay for it...  but get it here: [http://www.unet.univie.ac.at/~a0201073/files/cedega.tar.gz](http://www.unet.univie.ac.at/~a0201073/files/cedega.tar.gz) :D
it should work without problems for almost all games. please don't ask me how to set it up, i don't play myself (i just "put my hands" on cedega so i can pass it on). do some [http://www.google.com/linux](http://www.google.com/linux) search on it. or ask here on the forum, i'm sure there are users around using cedega (formerly known as winex).
[/QUOTE]
umm, just out of curiousity, is it legal to redistribute cedega? Is it a gpl-governed program like that?

---

### Post by im_ka on 2004-10-24
[QUOTE=jdong]umm, just out of curiousity, is it legal to redistribute cedega? Is it a gpl-governed program like that?[/QUOTE]

afaik, it's allowed to build it from cvs for free
let's keep it this way ;)

---

### Post by jcscar on 2004-10-24
[QUOTE=jdong]QTParted is a Partition Magic clone, capable of safely resizing many FS'es, like NTFS, FATxx, most Linux filesystems, etc. It also functions as a GUI partitioner.


It's in Ubuntu universe and is installable via APT/Synaptic![/QUOTE]
 APT/Synaptic
Ok, I know about Synaptic Package Manager but I couldn't find QTParted.
Or is APT/Synaptic not the SYnaptic Package Manager that comes with Ubuntu?

---

### Post by Rancoras on 2004-10-24
He or she meant apt OR synaptic.  Make sure you have universe enabled in order to find it.  Check out the howto in the howto and faq section of this site for details on how to enable universe.

---

### Post by jdong on 2004-10-24
[QUOTE=jcscar]APT/Synaptic
Ok, I know about Synaptic Package Manager but I couldn't find QTParted.
Or is APT/Synaptic not the SYnaptic Package Manager that comes with Ubuntu?[/QUOTE]

Sorry, I meant either apt or synaptic. Synaptic (in the background) translates your selections into commands fed to apt (Advanced Package Tool). For example, installing qtparted is accomplished by the command **apt-get install qtparted**.

---

### Post by jmings on 2004-10-24
[QUOTE=Rancoras]He or she meant apt OR synaptic.  Make sure you have universe enabled in order to find it.  Check out the howto in the howto and faq section of this site for details on how to enable universe.[/QUOTE]
 Or at the main site 

[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-09-30.5359349801/view?searchterm=universe](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-09-30.5359349801/view?searchterm=universe)

---

### Post by Seti on 2004-10-25
using QTparted is quite easy. If you use  a liveCD(mepis or knoppix) you may find that you need to reboot after you delete each partition before you can delete the next one.(at least that is what I have found).
You can then use it to make an NTFS for windows, and a SWAP and an EXT3 for Ubuntu. Grub takes care of the rest.

---

### Post by Lord_ZealoN on 2004-10-31
I untar the cedega file but not works

WHat i may be for cedega works?

---

