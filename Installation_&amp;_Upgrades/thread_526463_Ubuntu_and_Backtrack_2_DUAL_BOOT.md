---
title: "Ubuntu and Backtrack 2 DUAL BOOT"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by HuXu on 2007-08-15
Alright so i am trying to have Ubuntu and Backtrack 2 dual boot... i have successfully installed backtrack to the 2nd partition on my drive. this is what my drive looks like

[ Ubuntu ][ BackTrack ][ NTFS (no OS) ][ swap ] 

ubuntu boots fine, i am new to doing dual boot but i have editted the menu.lst to the best of my knowledge and when i click the option of booting to Backtrack it gives me "error 17 Cannot Mount selected partition"
here is what i have in my menu.lst


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1d633f9f-883c-4b39-9c97-dc54bdaaf744 ro quiet splash acpi=off noacpi
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		BackTrack 2
root		(hd0,1)
kernel		/boot/vmlinuz root=UUID=1d633f9f-883c-4b39-9c97-dc54bdaaf744 ro quiet splash acpi=off noacpi
initrd		/boot/splash

---

### Post by w116tjb on 2007-11-01
> 
title BackTrack

root (hd0,1)

kernel /boot/vmlinuz ro root=/dev/sda2

boot 


Try using that in your menu.lst.

I posted about this a few days ago, you can check out the thread here if you'd like.
[http://ubuntuforums.org/showthread.php?t=596869]("http://ubuntuforums.org/showthread.php?t=596869")

---

