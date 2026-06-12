---
title: "No Dual Boot, how to fix?"
date: 2004-10-22
forum: Installation &amp; Upgrades
---

### Post by helwitch on 2004-10-22
I'm pretty much an utter noob to linux. I installed Ubuntu on my laptop (on it's own partition) and am never seeing a boot to windows option. I've checked with 3rd party software, the windows partition is still there and looks intact.
I assume I've got to edit the boot file to add a windows option. Does hitting esc when grub says hit esc for the menu, and then hitting E to edit commands before booting give me the file I need to add the windows option to?
If that is the right file, what (exactly, like step by step) do I add to the file that opens to make it give me the boot option? 
And if that's not the right file, then what is, and where is is, and what do I add to it? (I mentioned the utter noobishness, right?) Thanks.
Oh, the windows is windows XP pro SP-2. And I have another computer running XP, if I need to look at the boot.ini file on it to see what to add to the boot file on the laptop. And if there's already a FAQ on this I somehow missed, or if it's already been answered here and I failed to find it when I searched ( i searched for windows dual), just let me know where and I'll go read it.

---

### Post by FLeiXiuS on 2004-10-22
Read the FAQ: [http://wiki.ubuntulinux.org/FrequentlyAskedQuestions](http://wiki.ubuntulinux.org/FrequentlyAskedQuestions)

I believe this was answered there.  Good luck, if not please post again!

---

### Post by helwitch on 2004-10-22
[quote=FLeiXiuS]Read the FAQ: [http://wiki.ubuntulinux.org/FrequentlyAskedQuestions](http://wiki.ubuntulinux.org/FrequentlyAskedQuestions)

I believe this was answered there.  Good luck, if not please post again![/quote]
Well, that does tell me where I need to make the change. But it doesn't tell me what change I need to make, and I have no clue. I've never used linux before, never set up a dual boot before. I sort of know how one goes about setting up a dual boot in windows, but not in linux. the line from the windows boot.ini is
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
But the grub file doesn't have the entries listed like that, so I'm guessing it's phrased a different way for windows than it is for linux. So what I need to know is what the line I should add to the grub file to make it include windows in the boot options should say.

---

### Post by FLeiXiuS on 2004-10-23
Let me explain...

The windows boot.cfg is no where near simular to the /etc/grub/menu.lst.  Lets walk you through...

Open your Grub Menu List Config.

```

sudo gedit /etc/grub/menu.lst

```

Browse around until you find the line, 
```
Title Ubuntu
```

Above this, type:
```

title Windows
root (hd0,0)
makeactive
chainloader +1 

```

Change the hd0,0 to the partition/hard drive where windows is installed!  Save then, restart and test your boot loader.

---

### Post by helwitch on 2004-10-23
[QUOTE=FLeiXiuS]Change the hd0,0 to the partition/hard drive where windows is installed!  Save then, restart and test your boot loader.[/QUOTE]
Fabulous, that was exactly what I need. One one last question, windows is installed on the first parition on the only hard drive. So is it 0,0 ? (Yeah, I could do trial and error, and may well if I get bored before there's a reply, but I figured better to ask first. *grin*)

---

### Post by FLeiXiuS on 2004-10-23
Yes, 0,0 would be correct!  Your welcome!

Enjoy Ubuntu :lol:

---

### Post by helwitch on 2004-10-23
[QUOTE=FLeiXiuS]Yes, 0,0 would be correct!  Your welcome!
Enjoy Ubuntu :lol:[/QUOTE]
it was /boot/grub/menu.lst. And I had to use vi cos the GUI isn't working so I couldn't use gedit, and someone had given me specific instructions for using vi. ( [http://www.ubuntuforums.org/showthread.php?t=1534](http://www.ubuntuforums.org/showthread.php?t=1534) ). And I figured out find (to find where menu.lst was) all by myself (sorta, I have a nice lil commands cheat cheat and I read the info)! (And yes, I realize I sound like a 2 year old who managed to tie their shoes, quit picking on me :P )
AND I DID IT! *happy dances* I found the right file, and edited it, and got it to let me boot windows! I feel so good now. *smiles the smile of someone who FINALLY got SOMETHING to work right.*

---

### Post by mark on 2004-10-24
[QUOTE=helwitch]it was /boot/grub/menu.lst. And I had to use vi cos the GUI isn't working so I couldn't use gedit, and someone had given me specific instructions for using vi. ( [http://www.ubuntuforums.org/showthread.php?t=1534]("http://www.ubuntuforums.org/showthread.php?t=1534") ). And I figured out find (to find where menu.lst was) all by myself (sorta, I have a nice lil commands cheat cheat and I read the info)! (And yes, I realize I sound like a 2 year old who managed to tie their shoes, quit picking on me :P )
 AND I DID IT! *happy dances* I found the right file, and edited it, and got it to let me boot windows! I feel so good now. *smiles the smile of someone who FINALLY got SOMETHING to work right.*[/QUOTE]Enjot the feeling - you shoulda seen me the first time I got Linux to *boot*...;)

---

### Post by nyx on 2004-10-24
[QUOTE=mark]Enjot the feeling - you shoulda seen me the first time I got Linux to *boot*...;)[/QUOTE]
 Can this also be used in dual booting other linuxes?
As I have ubuntu and suse and hopefully will have another distro on, but don't have windows anymore.  (yay me!) 
they're on different partitions too.

---

### Post by zevoneer on 2004-10-25
Just hi-jacking this thread with another dual boot problem.

I have Fedora on partition HDA5, I have edited GRUB with the following taken from Fedora's own GRUB file:
title Fedora Core 2.6.5-1.358
	root (hd0,0)
	kernel /vmlinuz-2.6.5-1.358 ro root=LABEL=/ rhgb quiet
	initrd /initrd-2.6.5-1.358.img

However when I try to boot from the GRUB menu I get the following message:
Root (hd0,4)
Filesystem is ext2fs, partition type 0x83
Kernel /vmlinuz-2.6.5-1 .358 ro root=LABEL= /rhgb quiet
Error 15: File not found.

I've also used Chainloader +1 and got the same error, anyone know what I'm doing wrong?

---

### Post by FLeiXiuS on 2004-10-25
[QUOTE=nyx]Can this also be used in dual booting other linuxes?
As I have ubuntu and suse and hopefully will have another distro on, but don't have windows anymore.  (yay me!) 
they're on different partitions too.[/QUOTE]

Yes of course, it should be universal for all linux whom run grub.

[QUOTE=zevoneer]Just hi-jacking this thread with another dual boot problem.

I have Fedora on partition HDA5, I have edited GRUB with the following taken from Fedora's own GRUB file:
title Fedora Core 2.6.5-1.358
	root (hd0,0)
	kernel /vmlinuz-2.6.5-1.358 ro root=LABEL=/ rhgb quiet
	initrd /initrd-2.6.5-1.358.img

However when I try to boot from the GRUB menu I get the following message:
Root (hd0,4)
Filesystem is ext2fs, partition type 0x83
Kernel /vmlinuz-2.6.5-1 .358 ro root=LABEL= /rhgb quiet
Error 15: File not found.

I've also used Chainloader +1 and got the same error, anyone know what I'm doing wrong?[/QUOTE]

Perhaps the problem is fedora 8).  Hm, I would try makeactive before chainloader +1.

---

### Post by zevoneer on 2004-10-26
Thanks for the advice but none of that worked, in the end what did was adding
/boot at the kernel and initrd lines as below. 

title Fedora Core 2.6.5-1.358
root (hd0,4)
kernel /boot/vmlinuz-2.6.5-1.358 ro root=LABEL=/ rhgb quiet
initrd /boot/initrd-2.6.5-1.358.img

---

### Post by bubbamctavish on 2004-11-13
[QUOTE=FLeiXiuS]Let me explain...

The windows boot.cfg is no where near simular to the /etc/grub/menu.lst.  Lets walk you through...

Open your Grub Menu List Config.

```

sudo gedit /etc/grub/menu.lst

```

Browse around until you find the line, 
```
Title Ubuntu
```

Above this, type:
```

title Windows
root (hd0,0)
makeactive
chainloader +1 

```

Change the hd0,0 to the partition/hard drive where windows is installed!  Save then, restart and test your boot loader.[/QUOTE]
 Cheers.

I um made a similar post to that earlier today but didn't find this one earlier (must have used the wrong keywords. my apologies to the mods).

Anyways, I tried that and it works...to an extent. Now when I select that option I'm taken to the grub command prompt "grub> " with a slew of commands (root, fileconfig, color, etc.) But still no windows... is there some sort of command i'm missing or was there something done wrong during the linux/grub/partition installation? I've partitioned the windows 2k installation in the fat32 partition and ubuntu on the other (ext3 file system i think)

Any help would be appreciated. Thanks

athlon xp 2200+
512 mb ram

---

### Post by cbarnes on 2004-12-28
Just a small detail I noticed when trying to implement the great advice on this thread.  My grub stuff is not located in /etc/ so I kept being unable to modify the specified file.  My recent release of Ubuntu for AMD-64 had placed grub in /boot/grub.  Realizing this, I could then edit the files appropriately to get Windows back.  I am new to everything Unix/linux so wasted a fair amount of time before figuring this out.  I hope it will save someone else some time to look around for grub if they run into my same problem!

---

### Post by Randabis on 2004-12-28
[QUOTE=bubbamctavish]Cheers.

I um made a similar post to that earlier today but didn't find this one earlier (must have used the wrong keywords. my apologies to the mods).

Anyways, I tried that and it works...to an extent. Now when I select that option I'm taken to the grub command prompt "grub> " with a slew of commands (root, fileconfig, color, etc.) But still no windows... is there some sort of command i'm missing or was there something done wrong during the linux/grub/partition installation? I've partitioned the windows 2k installation in the fat32 partition and ubuntu on the other (ext3 file system i think)

Any help would be appreciated. Thanks

athlon xp 2200+
512 mb ram[/QUOTE]

Try this.

```
grub> find /boot/grub/menu.lst
```

It should find this file, if it doesn't, then you have a problem. Anyway, assuming it finds it, it should display something similar to this

```
hd(0,0)
```

Now, type

```
root (hd0,0)
```
Substitute (hd0,0) for whatever the results were in your find.

It should then display the filesystem type, and some other crap. After this, type

```
setup (hd0)
```

It should then spout off some stuff and then load your menu.lst that contains your boot choices.

---

### Post by luckyxxx on 2005-01-07
Hi, I know your all talking about grub but I have a similar problem with my lilo.  I am running Xandros and Ubuntu but  the ubuntu script is missing in my lilo.conf file.  I have been trying to write the script myself
image=/vmlinuz
        label=ubuntu
	vga=0xf04
	root=/dev/hda2
	read-only
 but have had only limited success.  I have been able to at least have lilo list ubuntu in the menu but it won't boot up.  I have tried inserting "initred=/boot/inetrd-2.6.8.1-3-386" and various renditions of this but nothing seems to work.  I have been at this now 2 day reading lots of mans and now I ask for help.  Hopefully one of you can be of help.  Do you know the proper Ubuntu script to use to edit my lilo.conf file?  Your help would be greatly appreciated.  I have tried my best but its just not good enough.

---

