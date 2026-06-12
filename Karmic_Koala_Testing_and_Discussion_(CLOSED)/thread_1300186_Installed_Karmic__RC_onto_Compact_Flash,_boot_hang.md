---
title: "Installed Karmic  RC onto Compact Flash, boot hangs."
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by knave on 2009-10-24
Hi all,

I have a lovely little Toshiba Portege R100, the harddrive of which has been replaced by a compact flash card in an adapter.  The installation of Karmic went smoothly, however when I start the R100 up, the Toshiba logo splash shows, and then nothing but a blinking cursor in the top left corner.  This is BEFORE anything else starts or shows.  I mention this specifically because I have seen a lot of talk about this cursor business showing after the word GRUB shows...this does not happen with my card.  I believe this is an error to do with the adapter, but I'm sure how to check this short of buying another one.

Why am I convinced it's the adapter?  Two reasons.  Firstly, I have successfully installed from the exact same .iso on the laptop's original HDD and it works like a charm.  Secondly, when I boot from said HDD and inspect the CF card in gparted (using a PCMCIA adapter), it shows up as you might expect - as a partition with ubuntu installed on it.

Getting to the point, my questions are two:

1.  Does anybody know why this might be happening specifically with the CF card?

2.  If not, is there anything I can do to get a log or some sort of output to indicate where/when/why it's happening?

I have read that it may be that the adapter does not support UDMA, but I also read that this is only an issue if installing Windows.

Please ask if you need clarification of anything, I'm writing this between inbound calls on a tired Sunday morning at work :-) (New Zealand time).

Thanks team

---

### Post by knave on 2009-10-24
Wow this section moves fast, hope it's not too early/rude to bump :-)

[and thanks to the mod who moved this :-)]

---

### Post by knave on 2009-10-27
And now I haven't been able to sell the card on :-(

Has anybody experienced anything similar to this issue?

Thanks

---

### Post by ronacc on 2009-10-27
have you sucessfully booted anything from the cf card adapter ? I'm not sure that it will be recognised until the kernel loads ( unless as with the eeepc it is in the bios ) .

---

### Post by sgosnell on 2009-10-28
Does the CF card show up in the BIOS?  If so, it should boot.  

It's not unusual to get a bad install onto a flash drive, so you might try reinstalling Ubuntu onto it.

---

### Post by knave on 2009-10-28
No, I booted the laptop from a pcmcia adapter to install from another flash card.  I might try a different adapter or would this not be worthwhile?

---

### Post by knave on 2009-10-28
> **sgosnell said:**
> Does the CF card show up in the BIOS?  If so, it should boot.  

It's not unusual to get a bad install onto a flash drive, so you might try reinstalling Ubuntu onto it.


Sorry my last reply was to the chap above :-)

The card does not show in the bios when i try to select the boot order - it says "No HDD" (I think)

---

### Post by sgosnell on 2009-10-28
Well, if it doesn't appear in the BIOS, you can't boot from it, AFAIK.  The BIOS has to recognize a drive in order to boot.  If the adapter requires a driver, that may be the problem, because the driver is loaded by the OS.  USB drives are normally seen by BIOS, but that's because the motherboard has the USB adapter, and the BIOS knows about that.

---

### Post by knave on 2009-10-28
Sweet bix, thanks man.

I will throw down some coin for another adapter of a slightly different flavour and if that bombs then I'll move on!

---

