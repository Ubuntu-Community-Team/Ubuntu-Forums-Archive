---
title: "What are devices managed or devices unmanaged (NetworkManager)"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-10-12
[user confused]

Hi all, 
 With the recent NetworkManager issue , I have been confused by the terms 'managed' and 'unmanaged' as being thrown about in whatever bug or stuff one says. 

Can somebody clarify what the terms means? Also should they be 'unmanaged or managed connections' or should they be called as 'unmanaged or managed connections' (What is proper terminology? )

Thirdly, if somebody can give some concrete examples of 'managed and unmanaged connections/devices ' would be great. 

Lastly, specific case-scenario ' Wired connections from ethernet chipset/card to router' would it be 'managed or unmanaged connection/device' ?

The router/modem does all the authentication stuff with the ISP and stuff. 

 [user still confused]

---

### Post by iponeverything on 2008-10-12
This may have changed recently, so someone please correct me if I am wrong:

If you configure a device -- wired or wireless through the /etc/network/interfaces file (there are some GUI's for managing this file too) the Network Manager will no longer try manage it for you. Otherwise it will, using its own framework. The drawback to this that I have seen, is that I have to login to the desktop before my it will configure my interfaces..

With regard to NM:

Managed:  Store all information regarding IP configuration and states, configure/de-configure the interface when required.

UnManaged: Ignore the interface and allow other mechanisms manage state changes.

---

### Post by tact on 2008-10-12
As iponeverything mentions -  in regards to networkmanager, the terms "managed" and "unmanaged" just refer to whether networkmanager is managing (or not managing) a particular network adapter.

Also seconding iponeverything - if you manually configure (or use any commandline or GUI tool to configure) a network adapter you remove it from networkmanager's control and so that device is "unmanaged" as far as networkmanager is concerned.

Regarding the need to manually set up a network interface if it is needed to be up when no user is logged in - a difference with the latest networkmanager, v0.7 which is in the current intrepid ibex betas - it allows one to set network devices as "system" network devices.  No more need to do thi smanually any more.   The new networkmanager also allows more than one active network adapter to be up at once.

---

### Post by ShirishAg75 on 2008-10-12
right, but it still has bugs, right now using a workaround for the issue I'm having at [lpbug]279262[/lpbug]

---

