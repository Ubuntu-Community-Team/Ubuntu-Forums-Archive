---
title: "nvidia - montior detection wrong - force correct resolution"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by surfer on 2012-04-25
i have a samsung syncmaster sa850 that has a resolution of 2560x1440. my graphics card is an nvidia quadro nvs 295. the output of the card is DisplayPort.

when i connect the monitor directly via the DisplayPort out of the card to the DisplayPort in of the monitor, everything works fine.

now i also have a KVM switch (CubiQ CS1644) that is capable of that resolution. its inputs and outputs are DVI-D. i use an active DisplayPort-DVI-D converter (and DVI-D cables) to connect the KVM switch. as this setting has already worked with the maximum resolution, i'm sure all the components are ok.

but usually the setting does not work; i get a resolution of 1280x1440 (which is doubly annoying as it is scaled...).

i downloaded the EDID information when the monitor was connected to the DisplayPort (and running at full resolution), generated a Monitor section for xorg.conf and added a Screen section there. but to no avail; nvidia-settings does not offer any of the 16:9 resolutions i entered there.

what can i do? thanks in advance!

---

