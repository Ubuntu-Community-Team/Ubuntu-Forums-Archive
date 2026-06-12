---
title: "Problems with RTL8169/8110 after installation of Lucid Lynx"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by f4ils0me on 2010-04-11
Hello everyone,
iam new to this forum. Never had any problems with stable ubuntu releases, but now i got curious and updated to Lucid Lynx.

Everythink went nicely, BUT now i startup my Windows 7 (64bit) and my onboard lan tells me there is no cable connected. Well there is. I am using onboard lan with cable in ubuntu just fine.

I see that this is more a Windows kind of problem, but is there any chance this could be related?
The thing is, i reinstalled Windows just to check (the standard windows approach). It still sais that i unplugged my cable... :(

Anyone encounterd this problem?

I use the following mainboard:

MSI P965 Neo
Intel® P965 + Intel® ICH8 Chipset
Onboard Lan: Realtek® RTL8110SC (Windows states: RTL8169/8110)

Maybe there is a way to reset some onchip settings of the onboard lan?

Happy for every hint i can get!

Sorry my english for this is not my native language...

---

### Post by null_pointer_us on 2010-04-11
You could try resetting the BIOS.

This is usually done via the Clear CMOS jumper, as follows:

1. Power down.
2. Unplug the power cable (the one outside the case).
3. Wait 5-10 seconds.
4. Move the Clear CMOS jumper to its other position.
5. Move it back to its original position.
6. Reconnect power cable and power up.
7. Change the BIOS settings as needed to restore your config.

Occasionally, it's a little button instead of a jumper.

(It helps to write down BIOS settings before resetting them.)

If the system is custom built, be aware there's a small chance [with some older motherboards and "high performance" memory (e.g. > 800 mhz)] have trouble starting at standard speed and voltage.

---

### Post by f4ils0me on 2010-04-11
> **null_pointer_us said:**
> You could try resetting the BIOS.

You really think this could be necessary?
I did not make any changes to my BIOS configuration... And there are only a few options according to onboard lan. (Like disable it)

If i do decide to do this, wouldn't it be sufficient to reset bios from bios setup menu itself?

But thx for the hint anyways...

---

### Post by null_pointer_us on 2010-04-11
Yeah, you could try loading the defaults first.

Or try just disabling NIC, reboot, and re-enable NIC.

Sometimes leaving the computer unplugged for 10 seconds will fix some issues.

Motherboards these days come with really buggy BIOS code that just won't properly reset some things when one would expect (e.g. cold boot, warm boot, resume, reset).

---

### Post by f4ils0me on 2010-04-12
> **null_pointer_us said:**
> 
Or try just disabling NIC, reboot, and re-enable NIC.


Well disalbing NIC does not do the trick.
I dont get why Ubuntu still has normal lan connection while on windows its sais cable is unplugged all the time.
On the other hand the connection led (indicating a connected cable) is green all the time even if i unplug the cable...

I'll tryout the other hint now...

---

### Post by kahping on 2010-04-12
> **f4ils0me said:**
> Well disalbing NIC does not do the trick

Just curious. Did you disable NIC in BIOS or Windows?

---

### Post by Irihapeti on 2010-04-12
I've had similar problems with the same ethernet chip. Something in the 2.6.32 kernel causes the MAC address to be changed and the interface becomes eth1 instead of eth0.

To reset it, turn the computer off at the wall, or remove the battery (not the BIOS battery) if it's a laptop. Leave it for a minute or two, then turn it on again.

---

### Post by f4ils0me on 2010-04-14
> **Irihapeti said:**
> I've had similar problems with the same ethernet chip. Something in the 2.6.32 kernel causes the MAC address to be changed and the interface becomes eth1 instead of eth0.

To reset it, turn the computer off at the wall, or remove the battery (not the BIOS battery) if it's a laptop. Leave it for a minute or two, then turn it on again.

Thanks for the tip!
It worked!
\\:D/\\:D/

---

### Post by CRSharff on 2010-04-24
Had the exact same problem, found this thread after a quick goodle search. Didn't really think that my linux install could affect my Windows install but thank you for the information! Hopefully this works, gonna go unplug right now.

---

