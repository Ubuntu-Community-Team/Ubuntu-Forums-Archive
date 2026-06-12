---
title: "No splash during boot with edgy"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by KaosX on 2006-10-30
Finally got dapper upgraded to edgy as of 15 - 20 minutes ago, aside from the update wiping out the xserver and the i810 driver not being picked up (fixed all that manually)

the bootsplash never shows up, I just just a blinking cursor until gdm finally pops up, Id like to be able to see the splash, or even the boot messages rather than just a blinking cursor...anyone else have any issues with this or could suggest anything?

I was thinking it could be something in grub but im unsure and frustrated after my first battle getting X back up and running.

Any help is **deeply** appreciated, thank you very much.

---

### Post by xlulux on 2006-10-30
try this 

sudo gedit /boot/grub/menu.lst

the go down to the line that starts with kernel

for me it is 

kernel	/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash

make sure the line ends with splash. i left out some tabs and spacing due to size restrictions in this forum but just match it up with whatever is already there.

good luck

---

### Post by KaosX on 2006-10-30
Thanks for the suggestion, unfortunately the line for the default kernel im using already has ro quiet splash on the end of it, pretty weird.

---

### Post by KaosX on 2006-10-30
At least I feel like im making headway,

adding a VGA=773 to the end of the kernel line did get the usplash visible again, but it's hanging on boot..so Im going to trouble shoot that.

---

### Post by rcatman on 2006-10-31
I'm having the same issue. I have an LCD monitor. With the install of Dapper I had some resolution issues. It seemed Ubuntu wanted to use a higher resolution and/or refresh rate than what my LCD supported. 

On bootup, when the splash should be displayed my monitor goes blank with a box saying "Out of Range" in the middle of the screen. I'm assuming its because the setting for the splash either uses a resolution my monitor isnt handling or the refresh range is 'out of range'.

I searched the forums and found [this thread]("http://www.ubuntuforums.org/showthread.php?t=286993&highlight=out+of+range+boot").

I tried adding vga=785 to the end of the line in grub, but the computer freezes and goes no where. Hmm... its at most aesthetic for me to have the splash, but i'd like it to work :) maybe once?? hehe. What else can I do?

---

### Post by neildarlow on 2006-10-31
You might be missing the **usplash-theme-ubuntu** package. My dapper to edgy upgrade left it out.

---

### Post by dmrlook on 2008-01-04
Hello - anyone ever have any luck with this issue.  It described exactly what I am dealing with today with Ubuntu 7.10.  I just installed it a few days ago, and so far, so good, except this one issue.  My monitor always displays "Out of Range" and I know it is because the screen refresh rate during boot up (when the splash would be displayed) is too high.  Setting the vga parameter to one of many options made no difference.  However it appears that the VGA parameter is for resolution and not necessarily refresh rate.  So, I am still at a loss for how to fix this issue.  Any ideas would be greatly appreciated.

Thanks!

---

