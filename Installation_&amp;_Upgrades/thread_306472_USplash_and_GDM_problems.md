---
title: "USplash and GDM problems"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by deejross on 2006-11-25
First of all, I'm a novice linux user, I guess. I know enough to get myself into trouble...that's about the best way to describe my experience. Now, in the Windows world, I can show Bill a thing or two, but here in the land of Linux I'm a lost puppy dog. So I really appreciate your help ;) 

I just upgraded to Edgy from Dapper using the official method and I'm having problems. Well, first, I couldn't get my monitor's native resolution (1920x1200) until I upgraded to Edgy, so I'm happy that works, but I'm not happy about what I have to do every time I boot.

When rebooting after the upgrade, I noticed there was no splash screen. Just a minute of black screen, which REALLY makes me nervous. So I went through the forums and ended up adding vga=791 to the grub config file. Well, now I see the splash screen, but it appears in the lower-right corner of my screen, so I only see the letters "Ubu". Then on the lower-left side is the rest of it, "ntu". Weird, right?

Also, after I did that, X wouldn't start. I read the error output, but it didn't make much sense to me. It said something about not being able to find the RADEON device at PCI:1:0:1 (i think those were the numbers), and that it couldn't do MergeFB. Well, lucky me, I was researching something earlier and I remembered MergeFB referring to a better way to framebuffer if you have two monitors or something like that. So I ran dpkg-reconfigure xserver-xorg and went through the whole thing until it asked me if I wanted to use a frame buffer. I said No.

Now when I reboot, instead of X crashing, it flashes my screen, then sends it to power save mode, then keeps doing it until I hit Ctrl+Alt+Backspace. After that, GDM loads up perfectly to my native resolution. But it's so weird because I have to do that every time I reboot or it just keeps looping through turning the monitor on and off.

Just for the record, the frame buffer thingy was on in Dapper and seemed to work fine until I made that change to the grub file, then it all went up in flames. Does anyone have any ideas as to how I can fix this? Again, thanks for your help.

---

### Post by spd106 on 2006-11-25
I had a similar issue with Usplash after the upgrade from dapper and solved it by changing the **/etc/usplash.conf** file to the correct resolution.
Then regenerating the the initrd referenced in grub at boot **sudo update-initramfs -u**.

I'm not sure about the gdm issue, I have an nVidia card.

---

### Post by deejross on 2006-11-25
When I went to change the resolution in the file, I noticed it had it setup for 1920x1440 resolution, which my monitor doesn't even support. I changed the yres down to native 1200, but that didn't fly, so I set it all to 1024x768 and now it seems to work fine. I've also rebooted twice and both times went straight into GDM without having to restart X. So somehow, usplash was screwing X up.

But is there a way to run usplash at 1920x1200, or is 1024x768 the max?

Thanks for your help spd106 :D

---

### Post by spd106 on 2006-11-25
[quote=deejross]But is there a way to run usplash at 1920x1200, or is 1024x768 the max?[/quote]
 
After upgrading my usplash.conf was set to 1600x1200 before I changed it, so you could try that. It might need to be specific dimensions due to scaling, I'm not sure.

My monitors both max out at 1024x768 and I don't have anything bigger around, so I'm sorry that I can't help any further.

---

### Post by Dougle on 2007-08-02
Tryed 1600x1200 on my 1920x1200 monitor.. not pretty, much the same result as these guys report. looks like 1024x768 is the maximum.

---

