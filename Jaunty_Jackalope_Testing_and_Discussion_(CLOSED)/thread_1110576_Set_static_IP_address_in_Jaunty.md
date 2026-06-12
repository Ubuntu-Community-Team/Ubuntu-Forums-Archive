---
title: "Set static IP address in Jaunty?"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by SoftwareExplorer on 2009-03-29
So this is one of the things that made me stick with the LTS Hardy instead of going to intrepid. I'm currently trying to figure out how you can set a static ip with GUI (Network Manager most likely). Is there a way to do this? I can do it in windows (after reading instructions), but can't seem to figure it out on Linux. TIA

---

### Post by e-rebus on 2009-03-29
> **SoftwareExplorer said:**
> So this is one of the things that made me stick with the LTS Hardy instead of going to intrepid. I'm currently trying to figure out how you can set a static ip with GUI (Network Manager most likely). Is there a way to do this? I can do it in windows (after reading instructions), but can't seem to figure it out on Linux. TIA

Actually, setting up static IP in Intrepid is quite easy, don't know about Jaunty, but I would imagine it's the same. If you right click on the Network Manager applet and select Edit Connections..., then select Wired tab (if you are setting a static IP for wired connection) and select Add. Give a name to this connection and click on IPv4 Settings, select Manual under Method drop down and punch in your IP, netmask, gateway, dns, etc. and you are done. Works fine here.

---

### Post by novafluxx on 2009-03-30
Yes its that easy, as he described. Thanks for the information!

---

### Post by vishalrao on 2009-03-30
i've added the manual entry in network manager (kubuntu) but it shows "never used" and its still getting an IP from DHCP not the specified static one...even after reboot... last time (with intrepid) i remember i had to edit /etc/network/interfaces and uninstall network manager to get it to be static...

---

### Post by e-rebus on 2009-03-30
> **vishalrao said:**
> i've added the manual entry in network manager (kubuntu) but it shows "never used" and its still getting an IP from DHCP not the specified static one...even after reboot... last time (with intrepid) i remember i had to edit /etc/network/interfaces and uninstall network manager to get it to be static...

Can it be that you still had the default DHCP configuration used even when you've added your static configuration? I currently have two configurations set up, one with static IP for work and one with DHCP for home. And I choose one depending on where I am. NM defaults to the static IP config whenever I plug in an ethernet cable, so if I am at home I have to click on the applet and choose the "home" config manually.

---

### Post by SoftwareExplorer on 2009-03-30
> Originally Posted by **e-rebus**
Actually, setting up static IP in Intrepid is quite easy, don't know about Jaunty, but I would imagine it's the same. If you right click on the Network Manager applet and select Edit Connections..., then select Wired tab (if you are setting a static IP for wired connection) and select Add. Give a name to this connection and click on IPv4 Settings, select Manual under Method drop down and punch in your IP, netmask, gateway, dns, etc. and you are done. Works fine here.

Thanks for the encouragement. I apparently needed to get the DNS addresses from my isp. It's working now.

I vaguely remember having troubles with static ip when intrepid came out-- maybe it was updated, or, I might have not been persistent enough.

---

### Post by e-rebus on 2009-03-30
> **SoftwareExplorer said:**
> Thanks for the encouragement. I apparently needed to get the DNS addresses from my isp. It's working now.

I vaguely remember having troubles with static ip when intrepid came out-- maybe it was updated, or, I might have not been persistent enough.

Cool, glad it worked out for you!

---

