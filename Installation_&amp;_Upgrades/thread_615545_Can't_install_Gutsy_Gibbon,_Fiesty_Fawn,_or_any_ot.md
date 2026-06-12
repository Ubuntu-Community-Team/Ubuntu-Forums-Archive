---
title: "Can't install Gutsy Gibbon, Fiesty Fawn, or any other release of Ubuntu on HP DV9000z"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by sterilehighfive on 2007-11-17
I've been trying for a few weeks now, searched google, and searched the forums. I'm a total newbie to the world of linux so I don't know whats what, so I thank you for any help in advance.

Whenever I try to install, the install log gives me the bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed. After I get that error a few times, the install just halts at a blank screen and does nothing after that.

Right now the HP is running windows xp
2 gb of ram
AMD Turion 64 x2 TL-64 processor at about 2.2ghz
NVidia GeForce Go6150

If you need any more information, let me know

---

### Post by Ekeluo on 2007-11-17
Try starting in safe graphics mode. Also try a different CD or flavour (kubuntu). Or alternately, dive in with a alternate CD.

---

### Post by dannns on 2007-11-17
Or try this: (applies to a DV6000Z)
When you are booting the Live CD, press F6 and add **noapic** to the kernel options. If that doesn't work you can try **noapic nolapic**.

---

### Post by sterilehighfive on 2007-11-17
So i added noapic but now it tells me to insert a driver cd, how do i do that?

---

### Post by dannns on 2007-11-18
I'm not sure what you are referring to, you press F6, add noapic, and press enter to continue booting. The only CD needed is the Ubuntu Live CD.

---

