---
title: "HDMI (Intel X4500HD) and surround sound"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ormandj on 2009-09-27
Hi,

I have a Shuttle XPC with an Intel X4500HD. Out of the box, HDMI video is working perfectly, and amazingly enough, HDMI audio is too - except one minor detail - I cannot seem to do AC3/DTS/etc pass-through.

I used to do this when running Arch by using mplayer/vlc and telling them to use the specific alsa device (0,3 in my case) and output pass-through, but I think in Karmic something is attached to this device preventing that from working. This is my HTPC so this is a rather pressing issue.

How do I enable AC3/DTS/etc pass-through over HDMI in Karmic (Gnome)?

David

---

### Post by jaakan on 2009-09-28
looking at this page, HDMI audio is not listed 

[http://www.intel.com/products/desktop/motherboards/DG45ID/DG45ID-overview.htm](http://www.intel.com/products/desktop/motherboards/DG45ID/DG45ID-overview.htm) - Intel® G45 Express Chipset 

I know that doesn't support dts ma / dd ma.. etc...
some do a S/PDIF pass-through to hdmi but for pcm/low-end dd/ low-end dts only I don't see that listed.

the new AMD gfx 5xxx cards have full on board high-end audio support via hdmi.

---

### Post by ormandj on 2009-09-28
> **jaakan said:**
> looking at this page, HDMI audio is not listed 

[http://www.intel.com/products/desktop/motherboards/DG45ID/DG45ID-overview.htm](http://www.intel.com/products/desktop/motherboards/DG45ID/DG45ID-overview.htm) - Intel® G45 Express Chipset 

I know that doesn't support dts ma / dd ma.. etc...
some do a S/PDIF pass-through to hdmi but for pcm/low-end dd/ low-end dts only I don't see that listed.

the new AMD gfx 5xxx cards have full on board high-end audio support via hdmi.

Did you even read my post?

1) HDMI Audio IS working, out of the box, on Karmic. I just don't have pass-through of AC3 and so forth.
2) I am looking for information concerning getting AC3/etc pass-through working - as I *had* it working on this exact same hardware, using Linux, but on another distribution. Both mplayer and vlc were able to feed my receiver AC3/etc. The issue lies with some combination of Pulse/ALSA/so forth on this version of Ubuntu - and I was asking if anybody had any experience with this and knew how to get it working.

I appreciate your input, but please read what you are responding to before you respond to it. My hardware does function as expected, using Linux. I just need help making it work properly for pass-through with Ubuntu 9.10. In essence, I just want to be able to have surround sound when watching my movie library.

Thanks,
David

---

### Post by jaakan on 2009-09-29
Sorry, I miss read the first line.

---

### Post by ormandj on 2009-09-30
> **jaakan said:**
> Sorry, I miss read the first line.

No problem! I still haven't found a solution, but I'll try to respond here if I do.

---

