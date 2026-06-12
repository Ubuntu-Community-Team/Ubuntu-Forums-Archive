---
title: "switching Ubuntu installation from DSL to dialup"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2008-04-23
My sister can not get DSL or any other type of high speed access at her location.

If I take her computer to my house where I have DSL and install Ubuntu/Gutsy on it and install all of the updates and all of the applications that she will need (so that I don't have to do all of that on her dialup connection, which would take hours upon hours, if not days to do on dialup), will there be any problems involved in then taking the computer to her house and hooking it up and configuring her dialup connection ?

Will the fact that the computer has been previously configured on my DSL modem thru the ethernet port, etc. cause any problems when I switch the computer over to her dialup, i.e. will be computer O/S still be **looking for the DSL connection** and thus have problems connecting to the internet thru her dialup connection ?  Is this doable ?

Is there anyone out there that has first hand experience at doing this ?

Thanks.

---

### Post by dstew on 2008-04-23
I don't have first-hand experience, but you should be able to configure it to use the dial-up modem. You can disable the ethernet interface in the Network window. Maybe there will already be an un-configured modem interface there. If not, you will need to configure the modem interface using the command line. But, once it is configured, it is just like any other network interface to the system. It won't look for the ethernet interface if it is disabled.

---

