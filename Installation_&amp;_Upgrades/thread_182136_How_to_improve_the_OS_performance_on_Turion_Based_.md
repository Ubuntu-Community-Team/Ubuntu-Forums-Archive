---
title: "How to improve the OS performance on Turion Based laptops"
date: 2006-05-25
forum: Installation &amp; Upgrades
---

### Post by sreeharsha on 2006-05-25
Hi There,

I tried to installed Ubuntu Dapper (both 32 bit & 64 bit) on my AMD Turion based laptop (HP nx6125). It took almost 6 hrs to complete the installation and also the when it loads the Gnome it takes atleast 5 min to come up and if i select any options on the Gnome panel it takes like ages to open up. it took almost 6 minutes for firefox browser to come up. My question is how do i improve the OS preformance on my laptop. is there any specific patch or tunning parameters for turion based laptops to improve the performance ?

Thanks
Sree

---

### Post by colo on 2006-05-25
THis CLEARLY is not normal. Please check if other distributions show the same problems (recommendations: [http://slax.linux-live.org/](http://slax.linux-live.org/) or [http://www.knoppix.net/](http://www.knoppix.net/) ) and report back once you know.

---

### Post by andram on 2006-05-30
It is important to add "noapic" at the boot line for this machine. Did you try this?

---

### Post by Zdravko on 2006-05-30
What makes this option "noapic" exactly?

---

### Post by sreeharsha on 2006-05-31
No i have not tired this option. let me try this and let you all know

---

### Post by sreeharsha on 2006-05-31
[QUOTE=andram]It is important to add "noapic" at the boot line for this machine. Did you try this?[/QUOTE]

Thanks Andram ... it worked like charm.. adding this line was like a booster.. it boots up faster and all the application comes up faster... 

It would be grt if you could explain in detail what excatly "noapic" do and why do we require to add this line for AMD based desktops or laptops ?

Regds
Sree

---

