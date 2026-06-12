---
title: "Brasero Intrepid Ibex"
date: 2008-07-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wlake on 2008-07-17
When I try to use Brasero to burn an iso image, the burn icon is grayed out. It seems to realize there is a recordable DVD disk in the drive but the burn option is not available. Anyone else with this problem.
Also, I have the Nvidia 177 driver loaded, and it seems to be working. I had to copy over an old xorg.conf to get it to work. However, it does not show up under the Systm>Administration>Hardware Drivers. I do get the nvidia logo when I start up.

---

### Post by BackwardsDown on 2008-07-17
About the nvidia-driver, there is a discussion going about removing the nvidia drivers from the restricted-driver-manager. I don't know why they want this or what they want to do with it.

---

### Post by Gina on 2008-07-17
As I understand it, the driver doesn't show in the Hardware Drivers list because it doesn't require separate firmware installed - everything needed is installed when you install the driver.

---

### Post by olskar on 2008-07-17
Do you get a message in brasero telling you something about you are missing plugins and can therefore not burn? That is a known problem and will be fixed (Is already fixed in Svn I think)

---

### Post by wlake on 2008-07-17
Thanks for all the replies. In reference to the Brasero problem, no, I do not get any error message. It is just if I click on the burn iso icon and add the iso file to be burned. The burn icon which starts the process stays grayed out.
Regards,
wlake

---

### Post by Seventh Reign on 2008-07-18
Are you trying to burn to a Dual-Layer DVD?  As far as I know Brasero does not support Dual-Layer DVD's.  Atleast it didnt the last time I used it.  If this is the case, you are better off installing K3B.

---

### Post by steeleyuk on 2008-07-19
It does support dual layer now.

---

### Post by olskar on 2008-07-19
I keep getting those messages about missing plugins in 0.8 :/

---

### Post by Seventh Reign on 2008-07-19
Still sounds like an incompatible media problem.  Some CDs/DVDs just wont work in certain drives.  

It would help alot if you could tell us what DVD Burner and Blank Media you are using.

---

### Post by olskar on 2008-07-19
> **Seventh Reign said:**
> Still sounds like an incompatible media problem.  Some CDs/DVDs just wont work in certain drives.  

It would help alot if you could tell us what DVD Burner and Blank Media you are using.

It is a usual 4,7 GB DVD-RW I am using in a HL-DT-STDVDRRW GSA-H20L . The strange part is that I can burn it perfectly in K3B and therefore I assume its a bug in Brasero

---

### Post by Seventh Reign on 2008-07-19
1. What brand of Blank Media?
2. Try burning another disc perhaps?  (Another brand/normal cd)

Brasero is nice for a quick burn every once in a while, but there's no doubt k3b blows it away.  Would be nice if they'd develop a TRUE gnome equivalent.  Gnomebaker isnt it.

Someone start working on G3b?

---

### Post by Seventh Reign on 2008-07-19
It seems that DVD Burner you have is prone to problems like this.  There are posts about it all over the place in google.

---

