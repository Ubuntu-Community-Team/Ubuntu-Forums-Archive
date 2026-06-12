---
title: "How I solved my 11.10 upgrade hassles (grub, lightdm, classicmenu, wifi)"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by jago25_98 on 2011-10-18
I was careful with checking config files on upgrade. Only a few were replaced and I checked each one manually. 

 On reboot grub2 had no menu, just a prompt. No idea why! Failbeans! 

A recovery CD with chroot wasn't working for me because I couldn't remember how to mount /dev/ with --bind 
So with a lot of searching I did: 
```
root (hd0,8)
linux /boot/vmlinuxzMykernel root=/dev/sda8
boot

```
On login lightdm didn't accept my password so I did 
*ctrl+alt+F1*
logged in 
*/etc/init.d/lightdm stop*
*dpkg-reconfigure lightdm* & selected gdm (even though I already did this on upgrade)

Then to help the unity hassle I did
```
apt-get install classicmen-indicator
```

I then found *NetworkManager* was telling me `Wireless is disabled` but I knew that was BS because I hate NetworkManager and it was showing the card names greyed out, yet I couldn't select the option to enable WiFi. 
So I used *wicd*

By now I was up and running. I notice the unity dash has no right click edit. Hard to say how to customise it. 

Then before doing: 
```
#update-grub2
```
I removed and *customised /etc/grub.d/* all except os_prober

Conclusion: This sort of thing has happened on the last 4x I've upgraded so I conclude that *do-release-upgrade* is alpha, and recommend wiping it all to upgrade unless you want to mess it up and learn some stuff gentoo style along the way in getting it going.


update:

Had to switch to kernel v3 supplied with oneric but Virtualbox and it's kernel module works :-) I notice Grub has about 8 entries all the same for linux, and only one for Windows...
GDM didn't work on reboot. Switched to lightDM. Found the reason it was booting me back to login without any verbose feedback as to why was because 3D was enabled. I found I could select 2D and login. This was then confirmed with 
```

$glxinfo  |grep dir

```

Hope this helps someone

---

