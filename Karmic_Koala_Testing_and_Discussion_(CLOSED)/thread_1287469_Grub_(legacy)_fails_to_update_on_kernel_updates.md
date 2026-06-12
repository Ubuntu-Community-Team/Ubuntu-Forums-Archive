---
title: "Grub (legacy) fails to update on kernel updates"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by awam66 on 2009-10-10
Hello, I have been having a bit of bother with Grub after a clean install of Karmic Beta. During the install from the CD grub failed to install with an error. I have Dell C521 desktop amd athlon 64bit processor 1g ram and internal Hard Drive 180gb with an external usb 80gb drive. Jauntu is on the internal drive and Karmic beta on the usb drive. The syestem is set to boot from the usb drive. 
To cut a long story short eventually I managed to get Grub legacy working on Karmic but not Grub2. Now in the recent upgrades of the kernel to 2.6.31-12 and 2.6.31-13 the upgrade failed to update the menu.lst in grub and I have to do a manual update-grub.
I should report this as a bug but should I try to update to Grub2 first to see what happens?
TIA

---

### Post by VMC on 2009-10-10
What does the error say? Also go [here]("https://wiki.ubuntu.com/Grub2#GRUB 2 Testing") for help in installing grub2.

---

### Post by awam66 on 2009-10-10
> **VMC said:**
> What does the error say? Also go [here]("https://wiki.ubuntu.com/Grub2#GRUB 2 Testing") for help in installing grub2.

Soory I can't remember the exact error as it was 10 days ago, but if I remember right it just said failed to install.
I have had gub 2 but it ails to find the internal harddrive and I had to mess abot with bootorder if I want to go to my Jaunty installation which of course is my default. The update should nevertheless still pdate grub legacy surely?

---

### Post by ranch hand on 2009-10-10
It does not sound like grub-legacy is working right either.

I think that I would start by reinstalling grub-common and see if that helps.

---

### Post by awam66 on 2009-10-10
> **ranch hand said:**
> It does not sound like grub-legacy is working right either.

I think that I would start by reinstalling grub-common and see if that helps.

Yes I might try that when I get back to that computer (laptop at the mo).
The thing is when watching the updates in the terminal there is no mention of updating grub when the kernal updates. 
Will be tomorrow now as just going out for a meal.

---

### Post by ranch hand on 2009-10-10
Grub-legacy asks if you want to leave the current version or the maintainers version of /boot/grub/menu.lst when updating kernals.

Grub2 runs update-grub.

You should, by the way, be able to directly edit the /boot/grub/menu.lst by running;
```

gksudo gedit /boot/grub/menu.lst

```
and just change the kernal number and boot to the new kernal.

It could be that you did not get the message as to version and you may find both kernals in there.  In that case you can remove the old kernal or just hash it out incase you want it later or change the default entry (this is up toward the top of the page and is just a number, starting with 0, for the entry you want to boot from).

---

### Post by awam66 on 2009-10-11
> **ranch hand said:**
> Grub-legacy asks if you want to leave the current version or the maintainers version of /boot/grub/menu.lst when updating kernals.

Grub2 runs update-grub.

You should, by the way, be able to directly edit the /boot/grub/menu.lst by running;
```

gksudo gedit /boot/grub/menu.lst

```
and just change the kernal number and boot to the new kernal.

It could be that you did not get the message as to version and you may find both kernals in there.  In that case you can remove the old kernal or just hash it out incase you want it later or change the default entry (this is up toward the top of the page and is just a number, starting with 0, for the entry you want to boot from).

Yes I'm fully conversant with all you say above but as I said there was no attempt in the update to update grub at all. This is my main point.
However I have now managed to install grub2 which was the main problem with the beta install and it is now working. We will see  what happens at the next kernel update.
Thanks to all who replied

---

