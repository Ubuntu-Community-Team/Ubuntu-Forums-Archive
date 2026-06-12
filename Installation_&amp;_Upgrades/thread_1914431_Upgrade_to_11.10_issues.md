---
title: "Upgrade to 11.10 issues"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by MrJones on 2012-01-24
Hi,

I am an unexperienced Ubuntu user and I upgraded my 11.04 installation to 11.10 some time ago. Since then, the following things have been out of the order, and I can't figure out what is wrong.

1. Some sounds (login sound, sound you here when you change the volume) are not working anymore

2. It still runs kernel 2.6, eventhough kernel 3.0 was installed and I recently upgraded it. Grub only displays the old kernel, and I tried to change this with grub-customizer, but this doesn't change anything, eventhough I saved it.

I have an install with a seperate partition for the home folder. Could this have gone wrong while upgrading? How can I find out what's wrong and how to fix it?

Thanx!

---

### Post by raja.genupula on 2012-01-24
[http://askubuntu.com/questions/90009/no-startup-sound-in-ubuntu-11-10](http://askubuntu.com/questions/90009/no-startup-sound-in-ubuntu-11-10)

That above link is for your sound problem .

EDIT:(thinking some where). 

```
sudo update-grub 
``` output of that .

---

### Post by grahammechanical on 2012-01-24
First, can you tell us in more detail what you did to try to fix this?

Second, the log-in sound will be switched off by default in 12.04. It is thought that the log-in sound will be unnecessary because the intention is to have a fast boot up.

You can look in Startup Applications in the power cog menu to see if Gnome Login Sound is there and if it has a tick mark. It is there in my 12.04 alpha but without the tick mark.

As regards kernels and Grub Customizer all I can offer is to suggest (respectfully) that you did not do it right. I use Grub customizer a lot. And it works for me.

I have four versions of Ubuntu and the 12.04 alpha has had four or five kernel updates the last few weeks. Every time this happens I log into my 11.10 and run Grub Customizer. I uncheck the kernel that was being used and I then check the latest kernel and I save. And I am then using the latest 12.04 (3.20.0-10) kernel.

Are you dual booting? Have tried the Save to MBR option as well as Saving?

Regards

---

### Post by MrJones on 2012-01-24
Ok, the login sound problem is fixed, thanks!

Now, for the Grub problem: I saved it to the MBR (thanks for pointing that out to me) and that did change grub, but now it gives options to boot into kernels that I didn't specify in grub-customizer. I wanted to make it so it would only give me the option to boot into 3.0.15 and windows (yes, I run a dual-boot system), but it gives me options for older kernels up until 3.0.12, and this weird option to run a chainloader (don't know what that is). When I select the chainloader option however, I get error 11: Unrecognized string device. So then I checked the menu.lst file, and it gave the same options the new grub gives me now, but I don't see what's wrong in there. Any suggestions?

```
title        Ubuntu 11.10, kernel 3.0.0-12-generic
uuid        35de7d2e-3ed5-4314-a824-419bf5380266
kernel        /vmlinuz-3.0.0-12-generic root=UUID=11c57c3a-845a-4e79-a266-bb0c20139fed ro quiet splash 
initrd        /initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
uuid        35de7d2e-3ed5-4314-a824-419bf5380266
kernel        /vmlinuz-3.0.0-12-generic root=UUID=11c57c3a-845a-4e79-a266-bb0c20139fed ro  single
initrd        /initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, kernel 2.6.38-11-generic
uuid        35de7d2e-3ed5-4314-a824-419bf5380266
kernel        /vmlinuz-2.6.38-11-generic root=UUID=11c57c3a-845a-4e79-a266-bb0c20139fed ro quiet splash 
initrd        /initrd.img-2.6.38-11-generic

title        Ubuntu 11.10, kernel 2.6.38-11-generic (recovery mode)
uuid        35de7d2e-3ed5-4314-a824-419bf5380266
kernel        /vmlinuz-2.6.38-11-generic root=UUID=11c57c3a-845a-4e79-a266-bb0c20139fed ro  single
initrd        /initrd.img-2.6.38-11-generic

title        Ubuntu 11.10, kernel 2.6.38-10-generic
uuid        35de7d2e-3ed5-4314-a824-419bf5380266
kernel        /vmlinuz-2.6.38-10-generic root=UUID=11c57c3a-845a-4e79-a266-bb0c20139fed ro quiet splash 
initrd        /initrd.img-2.6.38-10-generic

title        Ubuntu 11.10, kernel 2.6.38-10-generic (recovery mode)
uuid        35de7d2e-3ed5-4314-a824-419bf5380266
kernel        /vmlinuz-2.6.38-10-generic root=UUID=11c57c3a-845a-4e79-a266-bb0c20139fed ro  single
initrd        /initrd.img-2.6.38-10-generic

title        Ubuntu 11.10, kernel 2.6.38-8-generic
uuid        35de7d2e-3ed5-4314-a824-419bf5380266
kernel        /vmlinuz-2.6.38-8-generic root=UUID=11c57c3a-845a-4e79-a266-bb0c20139fed ro quiet splash 
initrd        /initrd.img-2.6.38-8-generic

title        Ubuntu 11.10, kernel 2.6.38-8-generic (recovery mode)
uuid        35de7d2e-3ed5-4314-a824-419bf5380266
kernel        /vmlinuz-2.6.38-8-generic root=UUID=11c57c3a-845a-4e79-a266-bb0c20139fed ro  single
initrd        /initrd.img-2.6.38-8-generic

title        Chainload into GRUB 2
root        35de7d2e-3ed5-4314-a824-419bf5380266
kernel        /boot/grub/core.img

title        Ubuntu 11.10, memtest86+
uuid        35de7d2e-3ed5-4314-a824-419bf5380266
kernel        /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by raja.genupula on 2012-01-24
Actually In the new Grub , all the information will be in grub.cfg . Look for the entries in that . 

Regarding Grub customizer , again you have to open once and check it out.

---

### Post by MrJones on 2012-01-24
Ok, I checked again, and the grub-customizer says differently from the menu I get presented on boot. So this is the version of grub I have installed according to the Ubuntu software thingy: grub 0.97-29ubuntu64.

---

### Post by raja.genupula on 2012-01-25
So now boot menu ok ? Let me know 

& 

Right now do you have problem with Grub customizer ?

If yes reinstall it and try again .

---

### Post by MrJones on 2012-01-25
Actually, it's not ok. It still uses the information from menu.lst, which led me to install grub 1.99 manually. When I did that, I read about a program called mbchk and that you shouldn't use grub before running that, so I did, and it said there was no multiboot header.

And what's also really annoying, Windows has been lost from the boot menu, so I can't boot into that anymore, and I kinda need it. So I'm a bit at a loss here. Thinking about doing a fresh install...

---

### Post by raja.genupula on 2012-01-25
Hi I think we have many issues with your GRUB . I hope try to install boot-repair software . Install it and run it .you can get the link from GRUB Restore in my signature . 

Let me know what you got .All the best.

---

### Post by MrJones on 2012-01-25
Ok, I followed this: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

It told me to install Grub2 like this: sudo apt-get install grub-pc

And that worked! Now I can finally boot into windows again. Thanks for your help!

---

### Post by raja.genupula on 2012-01-25
yeah that's good news man ,so all issues are solved ?

---

### Post by MrJones on 2012-01-26
They are indeed :) Good to finally see the new Dash. Now just to find out how to mark this thread as solved...

---

