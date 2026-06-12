---
title: "Device Is Unmanaged"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Mr Fredrick on 2008-10-06
Hi All,

The Intrepid Network Manager continually reports that my wired connection *device is unmanaged* (the wireless connections are OK).

Strangely enough both the Update Manager and Synaptics are able to download data over the connection but FireFox can't connect.

I have installed the latest kernel and all the most recent updates. I have also uninstalled and reinstalled the Network Manager several times but to no avail.

Does anybody have any suggestions,

Thanks,

Mr Fred.

---

### Post by ktp on 2008-10-06
Make sure firefox is not in "work offline" mode...File/Work Offline.

If it is, then it might be that NM is reporting not connection and Firefox puts itself in the Work Offline mode.  If this is the case, then you can disable it in firefox by going to about:config and setting toolkit.networkmanager.disable to true.

---

### Post by Mr Fredrick on 2008-10-06
Thanks ktp, I will try that but just one more silly question:

Exactly where is about:config

---

### Post by ktp on 2008-10-06
type that in the address bar...just like a url.

---

### Post by Mr Fredrick on 2008-10-06
Found *about:config*.

Thanks again!

---

### Post by Mr Fredrick on 2008-10-07
> **ktp said:**
> Make sure firefox is not in "work offline" mode...File/Work Offline.

If it is, then it might be that NM is reporting not connection and Firefox puts itself in the Work Offline mode.  If this is the case, then you can disable it in firefox by going to about:config and setting toolkit.networkmanager.disable to true.

Thanks ktp. It worked - and I am now posting this message from Intrepid instead of having to go back to XP all the time as previously (I have a dual boot machine) and that's a big step forward.

However, it still leave the problem of why the Network Manager isn't working as expected.

---

### Post by ktp on 2008-10-07
Great...I don't know if this why it is not working, but there are some issues with the new NM and things are improving.  Information in this bug might help:

[https://bugs.launchpad.net/network-manager/+bug/256054](https://bugs.launchpad.net/network-manager/+bug/256054)

---

### Post by skroops on 2008-10-07
I had this same problem, I had to edit */etc/NetworkManager/nm-system-settings.conf* and changed the line under *[ifupdown]* to [I]managed=true

[/I]edit: possibly unrelated, but after doing that, I found that my boot was hanging up on "Configuring Network Devices".  So I edit /etc/network/interfaces and commented out all the lines that deal with my ethernet.  This fixed my slow boot and my wired connection still works.  in fact it plays alot nicer with nm-applet now.

---

