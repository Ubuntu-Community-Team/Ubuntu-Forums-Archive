---
title: "Grub Problems"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by darkan9el on 2008-02-14
Hi all, I've just installed Ubuntu Gutsy Gibbon (7.10 x86) on my PC. Oh by the way I'm a Linux (Ubuntu) newbie so take it slow, and no rough stuff lol! 

I have a SATA Hard drive and a PATA Hard drive.

SATA is setup with:
[LIST]
[*]XP Pro SP3 on dev/sda1
[*]Unbuntu on dev/sda2
[*]Swap on dev/sda3
[/LIST]

PATA is setup as
[LIST]
[*]Data on dev/hda1
[/LIST]

I have rebooted and I get the grub screen come up but the lists are wrong. I click on the Ubuntu links and I get an error because its pointing to the wrong place. I thought I had a problem booting to windows but that was sorted; fortunately, by another error.

the problem is Ubuntu is actually on (hd0,1) not (hd1,1) so; as I understand it, and please feel free to correct me if I'm wrong lol! all the links with regard to ubuntu can be sorted with a simple change to (hd0,1)

The Vista and XP links can also be sorted with a bit of a change, Vista can be removed because I don't have Vista! but the Vista link will actually boot my XP up, if I click the XP link I get a NTDLR missing error, which I should because it's pointing to the wrong place, so changing the XP link to (hd0,0) should fix that problem... yes? then I can just remove the Vista link.

So how do I do that if I can't get into Unbuntu and I can't edit from the live CD as it says I'm not the owner. I'm missing something here but me brain just ain't firing on all cylinders today. #-o

Any advice or help is very welcome,  

**My Menu.lst file**

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f70bf098-724a-4a0d-898b-0b700cc93314 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f70bf098-724a-4a0d-898b-0b700cc93314 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by EXCiD3 on 2008-02-14
This can be confusing at first but it is actually quite simple. Grub counts drives and partitions starting at 0...everything else typically counts drives starting at 1 or 'a'.

/dev/sda1 = hd 0,0 in grub
/dev/sda2 = hd 0,1


You can mount your ubuntu installation in the livecd and edit grub from there. 

```
sudo mkdir /mnt/ubuntu
sudo mout -t ext3 /dev/sda2 /mnt/ubuntu
df -h
```
Type these in terminal and it should mount your ubuntu installation to the /mnt/ubuntu folder. You can then browse and modify the contents of your menu.lst.

---

### Post by darkan9el on 2008-02-14
Hi, many thanks for the explanation, and the howto.

I have just sorted it myself, more by sheer luck than skill, but I am typing this from my newly installed and updated Ubuntu, I did the bit to mkdir and mount, but not quite the same as you have typed, nevertheless, I have printed your info off just in case I forget. 
Fortunately It allowed me to edit the menu.lst file and I was right in my assumptions; much to my surprise :) and I booted into Ubuntu with a big smile on my face.

To be honest I didn't quite know what I was doing nor understood the whys and hows, but i'll get up to speed with the lingo soon enough. Up to yet I really like it, just got to play around now.

Once again many thanks for the reply, I don't doubt I'll be back with more questions once I've messed it up lol!

---

### Post by EXCiD3 on 2008-02-14
Haha, im glad you got it working. I reinstalled ubuntu at least 35 times in the first several months trying new things and not having the slightest idea on how to fix it. It takes a while to learn but it just takes time.

---

### Post by darkan9el on 2008-02-14
lol! Ubuntu has already bitch slapped me, I rebooted after the updates and the menu.lst seems to have reverted back to the old settings, :-({|=  I'm in windows at the mo but I'm going back in guys I maybe a while,  but I will be back. [-o<

Seriously though I'm going to use EXCiD3 info to get myself back into Ubuntu, at least it gives me a chance to try it out and its all about the learning.

Going for the Compiz fusion thang next hehe! to the max!!\\:D/


Well I think Ubuntu is playing games with me because I went to change the menu.lst file and this time it allowed me to boot to Linux and I'm posting from it now. Crazy!

---

