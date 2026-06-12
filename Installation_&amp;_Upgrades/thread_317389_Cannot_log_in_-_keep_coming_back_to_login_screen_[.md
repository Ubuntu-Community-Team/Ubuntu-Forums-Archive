---
title: "Cannot log in - keep coming back to login screen [Resolved]"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by Abecedaria on 2006-12-12
I just installed xubuntu dapper on a very old laptop (P2 150, 80MB RAM, Neomagic video) and am having the problem were I login at the main screen, the screen disappears (as if it's starting to login) and then it goes right back to the login screen. I've tried to ctrl-alt-F1 and login at the command line which works fine so I know my account is active. I tried reconfiguring the x-server with the VESA driver and reconfiguring GDM according to tseliot's instructions with no improvement. 

Are there any log files I can look at that might give me some clues? Any other ideas for what might be wrong? 

I've installed from this same xubuntu CD on this same laptop before in the past and it worked fine. 

Cheers,

abc

---

### Post by malcolm1234 on 2006-12-12
I have the same problem. As a temporary workaround I've set a short timed login to keep re-logging me back in. After 2-3 attempts it stabilises.

I had no problems under Dapper but when I upgraded to Edgy it started. I've now reinstalled Edgy but still have the same problem.

My machine is fairly up to date (Sempron 3400+, 1GB RAM, 250GB HDD, Radeon X550).

Does anyone have a solution, or a way of investigating?

My first guess is that either the new init system is loading things at funny times which is causing them to tread on each other, or one of my drivers is misbehaving (although it does eventually stabilise so I suspect init for now).

---

### Post by Abecedaria on 2006-12-14
> **Abecedaria said:**
> I just installed xubuntu dapper on a very old laptop (P2 150, 80MB RAM, Neomagic video) and am having the problem were I login at the main screen, the screen disappears (as if it's starting to login) and then it goes right back to the login screen. 

Problem solved. My disk was full. I should remember that a typical cause of log-in failure is not being able to write to your home folder. This is either because of permissions or a full disk. 

Live and learn. 

abc

---

### Post by malcolm1234 on 2006-12-15
> **Abecedaria said:**
> Problem solved. My disk was full. I should remember that a typical cause of log-in failure is not being able to write to your home folder. This is either because of permissions or a full disk. 


Sadly, that doesn't sound like the same problem I'm having - my home partition has plenty of space and I can get in after a few tries. Ho hum.

---

