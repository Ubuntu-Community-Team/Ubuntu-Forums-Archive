---
title: "Help! Samba is driving me nuts!"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GARoss on 2009-04-17
Out of nowhere I'm having printer sharing issues. A few days ago it worked fine.
Standard file sharing is working great between 3 computers, all are Ubuntu 9.04 fully updated. But, with a shared printer problem arose yesterday & is consistent on the 2 computers that share via the network with the computer that has the printer plugged into it. An error, ***tree connect failed (NT_STATUS_ACCESS_DENIED)***. A password prompt popped up. Why now? Never set one up; never had to before.
So, I deleted the printer & tried to reconnect. ***tree connect failed (NT_STATUS_ACCESS_DENIED)*** again. Did a search & found a solution that said to delete a word in smb.conf, change "valid users" to "users". I did, no help.
Deleted & tried again. Same thing. 
Shut down & booted up & this time when I try to reconnect I can't even find a printer on the network! The only way to print is to print from the computer with printer plugged into it. That's it.
Is there a known bug?
How can I check to find out what's wrong?
Thanks.

---

### Post by t-o-c on 2009-04-17
The system with the printer plugged into it - check that it's printer is being shared, and there are no passwords or user restrictions applied to printing.

public = yes in the samba config on that machine might help.

---

### Post by GARoss on 2009-04-18
> **t-o-c said:**
> The system with the printer plugged into it - check that it's printer is being shared, and there are no passwords or user restrictions applied to printing.

public = yes in the samba config on that machine might help.
Thanks.
Today it's back to [I][B]tree connect failed (NT_STATUS_ACCESS_DENIED)
[/B][/I] again after I reinstalled samba, smbclient & anything associated with sharing. I did this on ALL computers. At least it's showing the printer.:-({|=
I changed "valid users" to "users" in smb.conf & here's
# public shares, not just authenticated ones usershare allow guests = yes

I'm lost on this. Is there another way to share printers on a network other than Samba?
George

---

