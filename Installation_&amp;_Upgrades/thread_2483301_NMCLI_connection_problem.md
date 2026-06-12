---
title: "NMCLI connection problem"
date: 2023-01-25
forum: Installation &amp; Upgrades
---

### Post by greg-hains on 2023-01-25
Good afternoon.

I have need to have an Ubuntu system (20.04) to VPN into a client site, and copy files to a Windows share on that site, then disconnect, but I have a problem...
I know the actual VPN links works OK at the destination as I have it currently running in a Windows-to-Windows environment, but the source/originating box has been changed to Ubuntu. 

I have followed several guides and created a VPN entry with NMCLI (which went OK), however, when I run it:   
    [COLOR=#008000]nmcli c up vpnname[/COLOR]
The error received is:  
   [COLOR=#a52a2a] Error: Connection activation failed: Could not find source connection.[/COLOR]

If I read it right, it appears that the eth0 interface is not managed by nmcli (as shown by "nmcli device status"), so I need to change it so the response is "full" not "none".

I cannot find much information on how to troubleshoot this error. Is somebody able to give me a hint please?

I know there is no short answer to this whole topic as I have seen it in many similar posts, but if I can have eth0 managed by Network Manager I'll be a little further along. :)

 Any pointers are appreciated. 

Cheers,
Greg

---

