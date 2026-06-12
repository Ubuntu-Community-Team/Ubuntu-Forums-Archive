---
title: "Possible fix for nVidia low graphics bug :) Something to check"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by JamesB7 on 2008-05-17
Hey all,

I hadn't used Linux in six months, so today I thought to myself, "Hey, why don't I try Linux again, this will be FUN :KS." Turns out the upgrade broke everything for me. Good job having your act together guys.

Anyhow, here's the deal. The new nVidia drivers won't work if your kernel is the old version. How could that happen, you say? Here is how. I use GRUB to triple boot Kubuntu 32-bit (for compiling eeeevil closed source apps), Ubuntu 64-bit (what I've just got working and am using now), and Windows XP (because it's better).

Now, having installed Kubuntu 32-bit *after* Ubuntu 64-bit, upgrading Ubuntu 64-bit meant that it was using Kubuntu's boot loader and menu.lst. As a result, when Ubuntu 64-bit upgraded, while it updated its own menu.lst, it did not update the one I was booting from.

You should add a check for this in the installer, and if it identifies the bootloader as GRUB, figure out where GRUB is actually reading menu.lst from. Clearly when I installed Kubuntu 32-bit it figured that out, since it copied menu.lst over. Why didn't it reference the original and use that? Who knows, I bet all you incompetent tech "wizards" can tell me, or maybe I should "implement it myself since it's open source!" hah, but there you have it, something to check if you aren't able to get your driver working.

James

---

### Post by cac67 on 2008-05-17
> **JamesB7 said:**
> I bet all you incompetent tech "wizards" can tell me, or maybe I should "implement it myself since it's open source!" hah, but there you have it, something to check if you aren't able to get your driver working.

James

Wow, are you this condescending to everyone, or just anonymously on the internet?

---

### Post by JamesB7 on 2008-05-17
Not at all, just towards the Linux community. My issue is that, here's something that could work really well, and does at the low level, but my experience throughout the years is there are always a billion really OBVIOUS things that make it painful to use. Things that would get caught if there was any evidence ANYONE at all paid attention to usability, or even detail.

Let me give you some great examples. Know that "low graphics mode"? Clearly nobody ever actually tested it.

It puts you at 800x600, or is it 640x480. Either way, you can't see the OK button of 9/10ths of the windows. Anyone who doesn't know how to use Tab (that is, MOST people) or hit Maximize is doomed. Oops.

Here's another. I was running at 1280x1024 before this "upgrade". Once I did get it working, and booted, it started me at the low graphics resolution I ended up at because of the install problems. Unfortunately something didn't get the memo because it only showed me the top left quarter of the login screen. Missing? The login part. Nice wallpaper though. Nothing to click on. Somebody must have forgotten to center it. Oops. I got through by entering a login and password, but come on.

Hmm. Konqueror. If you hit the middle mouse button to close a Tab it says 'Malformed URL error'. WTF.

If these were obscure it'd be one thing. Surely the developer of the 'low graphics mode' would have noticed that. Surely the developer of Konqueror would have noticed that. Etc. There are worse aspects of Linux, like centralized package repositories, which really are symptomatic of a totally broken approach to software, but I won't go there.

On the plus side Terminal Server Client now lets you map your local drives, and my sound card finally works. So it's not all bad. At least modern distros adhere to Fitt's Law *old Mandrake distros, terrrrible on that*...

---

