---
title: "Getting rid of &quot;persistent&quot; boot"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by Lord_Vacuity on 2007-03-02
I was running Dapper LiveDVD on my Xp laptop. I didn't have a partition available on the HD so I was using an external HD connected via USB. On that external HD I had that Persistent folder to save my settings for when I ran the LiveDVD, Casper-RW I think it is.  Anyway, I liked Ubuntu so I decided to install for a dual boot configuration. I made a 8.45 GB partition etc. and installed it. Runs great and I just upgraded to Edgy. 

My problem is that when it boots it still asks for that Casper-Rw from the external HD which I assumed I would no longer need, besides that HD has crapped out on me anyway so even if I wanted to connect it it isn't any good. So I can still boot but I have to do a Control D, in the middle of the bootup to get around that. My question is, what do I need to do to make it stop looking for that file on the external HD? I am thinking it is some parameter I have to change in Grub but I don't have the foggiest what that change would be. I was thinking that I should be looking for something about "persistent" and just delete that line but I don't see it in there.

Any help would be appreciated, thanks.

---

### Post by wavesound on 2007-03-03
Hi
Can you post your /boot/grub/menu.lst  (no i)so we can see whats on there.

You may find you can comment out ( # ) the stuff pointing to your old drive.

Here is mine:

*******************************************
title		Ubuntu, kernel 2.6.15-28-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot
********************************************
To stop the last on showing I would:

#title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdc1 ro single
#initrd		/boot/initrd.img-2.6.15-27-386
#boot

This means you can go back and 'uncoment' the lines to make them work again.
:) 
Cheers
Bob

---

### Post by Lord_Vacuity on 2007-03-04
Actually, I just noticed that since i upgraded to Edgy, I've seem to have lost a bunch of my permissions. I have checked my permission properties and it shows me having Admin level permissions but still I can't write to any folder beyond /user/ and even there, I can only drag down level and not across or up. So I am guessing I will just have to clean reinstall Edgy straight off an install disk. This time I know not to be using a persistent parameter when I boot it.

---

