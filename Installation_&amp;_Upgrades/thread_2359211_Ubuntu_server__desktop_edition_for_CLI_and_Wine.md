---
title: "Ubuntu server / desktop edition for CLI and Wine"
date: 2017-04-21
forum: Installation &amp; Upgrades
---

### Post by psking on 2017-04-21
Hi,

I have been a user of Ubuntu server for around 6 years.  My servers are built only for CLI access only - I never really had a need for a GUI, however a few years back I recall having dependency issue when trying to install Wine in order to install a Windows package I wanted to run in batch mode, again from the command line interface.

I need to build just such a server now and am wondering what the best option would be.  If I went for Ubuntu desktop could I select all of the options I currently have in my server installations?  I would continue to use CLI almost exclusively, but I was thinking that, as well as being easier to install Wine on, it might actually be easier to administer via the GUI.

Any recommendations would be much appreciated.

Thanks,

Phil

---

### Post by TheFu on 2017-04-22
I'd go the other way - install the server, then add only the GUI tools you need.  
99% of admin via the CLI **is** easier, BTW.  It doesn't change every few years in huge ways.

But, yes, you can install a desktop (don't use Unity for a remote desktop, use LXDE or XFCE4 or Mate) if you want all that bloat.  

I think you will need to setup a remote desktop - use x2go - to make **winecfg** easier to run to configure the WINEPREFIX and odd things each different Windows program demands.  x2go works over ssh (requires ssh actually). No extra ports or any other port security efforts needed than you are already doing for ssh.  x2go works easiest with lxde.  Of course, if you know exactly what you need for the WINE programs and don't need the WINE GUI at all, then you don't need any client-gui stuff at all.

---

### Post by psking on 2017-04-22
Thanks TheFu,

I'm kind've glad you said that, I am happier with the server version.  I think if I install it then immediately try and install Wine before I get using the server in anger, at least I have the option of starting again if it all goes pear-shaped!

Thanks for the advice on x2go, will certainly check that out.  I think I will need a WINE GUI because the software I need to use is primarily a Windows GUI-based package but it does have the ability to be run in batch mode from the command line.

Better get the server ordered now!

Thanks for the advice.

Phil

---

### Post by TheFu on 2017-04-22
> **psking said:**
>  Better get the server ordered now!

I'd just spin up a VM and do everything in there. If I outgrew what the physical host can handle for a VM, then I'd probably just buy a larger VM server, but my current "physical servers" are all 5+ yrs old, so a replacement wouldn't be too expensive AND would easily support 200 containers or 20 VMs.

---

### Post by psking on 2017-04-22
Will do as a VM, probably on an old VMware ESXI host as proof of concept.

Phil

---

