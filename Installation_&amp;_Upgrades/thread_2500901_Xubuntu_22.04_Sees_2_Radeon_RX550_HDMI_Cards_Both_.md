---
title: "Xubuntu 22.04 Sees 2 Radeon RX550 HDMI Cards Both As HDMI 4, 20.04 Does Not"
date: 2024-09-15
forum: Installation &amp; Upgrades
---

### Post by Lasakro on 2024-09-15
With Xubuntu 20.04 & Ubuntu Studio 20.04 my 2 Radeon RX550 cards are seen by PulseAudio as HDMI 4 and HDMI 5. Works as expected.

After a fresh install of Xubuntu 22.04 both cards are seen as HDMI 4. pavucontrol does give me two controls both as HDMI 4 and controls fine. HDMI 2, 3 & 5 are reported as unplugged.

Looking at alsamixer it shows both cards with different address and uses different IRQ's, image attached.

The road block I'm running into is with 22.04 and PulseAudio upgraded to PipeWire In RaySession it only shows only one HDMI card as HDMI 4. Therefore I'm only able to wire one HDMI output.

I'm using Xubuntu on an alternate SSD as a test platform before upgrading my Ubuntu Studio main OS from 20 to 22.

Any thoughts as a solution to get the cards as seen as 2 separate HDMI numbers like 20 does?

---

