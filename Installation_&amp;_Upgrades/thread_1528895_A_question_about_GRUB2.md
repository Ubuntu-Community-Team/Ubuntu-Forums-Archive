---
title: "A question about GRUB2"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by thelugnut on 2010-07-11
I have installed on my hard disk, Windows XP Pro, Ubuntu 10.04, Ubuntu 9.04, and a partition containing my data.
The present setup uses GRUB2 and works very well.
I want to remove the 9.04, and install another 10.04. 
But, since I have already set up the GRUB2 menu nice and pretty, I would like to continue to use it, rather than going through the whole procedure again.
This was easily accomplished with GRUB legacy, but I don't know about GRUB2. 
```
find /boot/grub/stage1
boot (hd0,x)
setup (hd0)
quit
```
Is The procedure the same? If different, how so?

---

### Post by tommcd on 2010-07-11
> **thelugnut said:**
> I have installed on my hard disk, Windows XP Pro, Ubuntu 10.04, Ubuntu 9.04, and a partition containing my data.
The present setup uses GRUB2 and works very well.
I want to remove the 9.04, and install another 10.04. 
But, since I have already set up the GRUB2 menu nice and pretty, I would like to continue to use it, rather than going through the whole procedure again.

Just install the new 10.04, and when you get to the part to install grub, choose "advanced options" (or whatever it says exactly) and choose to install the new 10.04 grub2 to the new Ubuntu 10.04's root directory.
Then boot into the old Ubuntu 10.04 and simply run:
```
sudo update-grub
```
... and it should pick up your new-er Ubuntu 10.04 and include it in your grub2 boot options when you boot your "old" Ubutu 10.04.

Just out of curiosity ... Why do you want 2 versions of Ubuntu 10.04??? Do you want the extra install of 10.04 for learning or experimenting?? If so, then this is a good idea if you want to play around without destroying your main fail safe system.

See these tutorials on grub2 for further reading:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by alexshr on 2010-07-11
You can preserve the old grub settings and still update your system from 9.04 to 10.04. All you need is keep backup of your grub settings.

Once you fully update the system from 9.04 to 10.04. The system will replace the grub settings. Now to change your grub settings back to the older one. First update the grub settings by issuing command "sudo update-grub". You will get a message similar to one below.
```

Found background image: grub.png
Found linux image: /boot/vmlinuz-2.6.35-6-generic
Found initrd image: /boot/initrd.img-2.6.35-6-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

Now, keep the menu entries intact and make your changes.

with best regards,
samundra

---

### Post by thelugnut on 2010-07-11
tommcd & alexshr, Thanks for the quick replies. 
To answer you question, my wife uses the computer as well. I want to have her on a separate partition, because I like to play and experiment which sometimes leads to evil and disastrous results. I can always take the time to fix it, but if she wants to do something, her system is always there for her. Those of you that are married will understand this, I think. I use the fat-32 partition to hold the data for the same basic reasoning.

---

### Post by tommcd on 2010-07-12
> **thelugnut said:**
> ... my wife uses the computer as well. I want to have her on a separate partition, because I like to play and experiment which sometimes leads to evil and disastrous results. 
Well, if my experiences anything like yours, you will most definitely want her on a separate partition! Or better yet, put her on a separate computer altogether! ...  And make sure that computer is in a different room from your computer! ;) 
In any case, doing what I suggested in my last post should work.

---

### Post by thelugnut on 2010-07-13
Silly old me...of course it worked very well. I just forgot to write that in. Again, many thanks!
As for your suggestion of a different computer, I plan on doing that very thing as soon as I receive my refund check, which I was told is,"in the mail".

---

### Post by libssd on 2010-07-13
Please delete.

---

