---
title: "Trying to update new install of Ubu20. Prompt to Reboot in mid-Update. Can't"
date: 2023-09-27
forum: Installation &amp; Upgrades
---

### Post by Mugsy323 on 2023-09-27
I'm trying to install Ubuntu 20.04.

After installing, it prompts me to update everything to the latest versions.

I get as far as the update for "dbus" when the update window (displaying progress window) suddenly stops with the message "Please reboot at first opportunity" (not an exact quote.) But the update does not continue (I've tried waiting several times, after reinstalling several times.)

So I try rebooting but I can't because Ubu thinks "Update" is still running (even if I close the window.) I can't run anything either (Terminal won't open. Browser won't launch.)

I have no idea how to get Ubuntu to complete an update after a fresh install. Suggestions?

[IMG]https://i.postimg.cc/x8zjQRy3/ubu-cant-reboot.jpg[/IMG]
(Clicking "Authenticate" just brings up same window over & over again.)

---

### Post by TheFu on 2023-09-27
Is the hardware newer than April 2022?
Does the "Try Ubuntu" mode work?  If it does, but the install isn't working, it could be BIOS, Storage hardware or some other hardware in the way.  Please run and post the output from **inxi -Fxxz**. You'll need to install that package while in the "Try Ubuntu" mode.

Which exact release of 20.04 are you trying to install?  The current release would be 20.04.6.  20.04.1-20.04.5 aren't supported.

What is your experience level? Can't really tell based on posts or join date here.

---

