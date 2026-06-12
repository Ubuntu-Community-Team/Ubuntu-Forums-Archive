---
title: "Question about &quot;Which services should be restarted dialog?&quot;"
date: 2023-08-25
forum: Installation &amp; Upgrades
---

### Post by daveheadrick on 2023-08-25
This is my first-ever post here. The answer to my question probably exists but I couldn't find it.

I just installed Ubuntu 22.04.2 followed by doing a "sudo apt update" and a "sudo apt upgrade". I then got a dialog which says "Which services should be restarted?" which lists 12 possible services that could be restarted with 7 services checked by default.

So that I don't have to research this, can I just click "OK", which will restart the 7 services checked by default?  Or maybe I should check the checkbox of all 12 services and restart them all?

Is there some downside to restarting a service that doesn't really need to be restarted?  

I presume this dialog is a one-time thing associated with "sudo apt update" followed by "sudo apt upgrade", and I'll never see this dialog again.  If that's the case, I'm inclined to restart all 12 services, and just be done with it.

Please let me know if it's more complicated than this.  Thanks.

---

### Post by #&amp;thj^% on 2023-08-25
> **daveheadrick said:**
> This is my first-ever post here. The answer to my question probably exists but I couldn't find it.

I presume this dialog is a one-time thing associated with "sudo apt update" followed by "sudo apt upgrade", and I'll never see this dialog again.  If that's the case, I'm inclined to restart all 12 services, and just be done with it.

Please let me know if it's more complicated than this.  Thanks.
I set mine to restart by default as well, but it's no substitution for a restart. (New Session with the updated services)
No you will see it when a service has had a update and needs the restart to implement the change.
Or even  a re-start for all changes.

---

### Post by daveheadrick on 2023-08-25
Thanks for your reply but I couldn't tell what you're recommending.  Again, I just installed Ubuntu 22.04.2 followed by doing a "sudo apt update" and a "sudo apt upgrade" followed by a Ubuntu-generated dialog which says "Which services should be restarted?"  Should I restart the 7 (of 12) services that are checked by default or should I make sure all 12 services are checked, and then restart them all ?

Thanks again.

---

