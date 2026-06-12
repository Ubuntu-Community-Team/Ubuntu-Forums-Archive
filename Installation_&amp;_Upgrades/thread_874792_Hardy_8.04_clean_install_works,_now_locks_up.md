---
title: "Hardy 8.04 clean install works, now locks up"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by boomcat on 2008-07-30
I did a successful clean install of Hardy, with all updates, yesterday. I used a small monitor in the spare bedroom with a resolution of 1024x768.

Today I moved the computer into its final position with a big Dell P990 monitor. When I booted it up, it was in 640x480. I looked at System/Preferences/Screen Resolution and the only resolution available was 640x480.

This computer uses the onboard Intel video output. And the P990 monitor works at 1024x768 and higher: it's on a KVM switch with a Windows 2K computer and works fine.

So I tried a couple of fixes here on the Forum (Envy and another one that I can't remember) and the last thing I saw on the screen was "all users must log-off for the new settings to take effect". So I restarted the computer and now it boots to an amber screen with a HUGE Ubuntu logo in the lower right corner and then locks up! This is true of all of the maintenance-boot modes, too: they all end up with this.

All I did was switch monitors! What can I do to fix this?

---

### Post by nbayiha on 2008-07-30
What's the video card ? Nvidia or Ati or Intel ?

---

### Post by boomcat on 2008-07-30
It is the standard onboard Intel graphics adapter with the, according to the Ubuntu Hardware Manager, "82G965 Integrated Graphics Controller".

I just moved the computer off of the Dell Monitor with the KVM switch and back to the Princeton monitor, and it boots fine! Could it be the KVM switch?! That seems impossible!

---

### Post by jmirick on 2008-07-30
Physical KVM, or an electronic one?

---

### Post by boomcat on 2008-07-30
It's an electronic KVM switch: double-tap "Scroll Lock" key to switch computers.

---

### Post by boomcat on 2008-08-05
I'm still struggling with this. 

I have found that "xrandr -s 1280x1024" works wonders!

The "System/Preferences/Screen Resolution" tool reads the current screen resolution, but won't set it: instead it sets the whole screen to one big, gigantic flashing pixel!

And the other Terminal command, oh, what is it? "sudo displayconfig-dtk" or something, that doesn't work either.

So I'm still working on it.

When I boot, the display comes up blue-colored and with the three menu selections completely out of scan on the left. In the extreme upper left corner I can see the Firefox icon. I have moved an icon for Terminal to the middle of the upper panel, so I can enter "sudo xrandr -s 1280x1024" as soon as I log on. After that, I'm golden until I have to log in again. 

I wish I knew where Hardy stores the startup resolution!

---

