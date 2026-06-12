---
title: "Anyone Successfully Connect to a Wireless Network In Kubuntu Jaunty?"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-03-01
I can't seem to. My laptop is a Gateway m7315u and its wireless adapter doesn't need closed source drivers to work. (It even worked with Intrepid out of the box). 

For some reason, I cannot connect to my wireless router. I put in the password exactly the way it should be and triple checked the settings, but it asks for the password again and fails infinitely.

Is wireless working in Kubuntu at all? Has anyone had any luck?

---

### Post by PRGUY85 on 2009-03-01
Are you using the Network Plasmoid?

---

### Post by meborc on 2009-03-01
l use kubuntu with latest upgrades and wifi works fine. My card is using b43 driver.

---

### Post by garba on 2009-03-01
just tried the latest alpha release, it works here, btw long live the new connection plasmoid it looks very promising, knetworkmanager should be banned from this world

---

### Post by jlacroix on 2009-03-01
I'm using the Plasmoid, which I think is no better than knetworkmanager.

---

### Post by zenarcher on 2009-03-01
Works just fine here, as well, with an Atheros wireless chip.

Cheers,
zenarcher

---

### Post by jlacroix on 2009-03-01
Very weird, I wonder what my problem might be? I have Vista on a smaller partition and that connects fine with the same settings...

---

### Post by kayosiii on 2009-03-01
Working here using ralink chipset

---

### Post by firstc624 on 2009-03-01
as does here and here is what i am running:

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


Just in case

---

### Post by jepong on 2009-03-01
i was able to use wireless on my msi wind

---

### Post by jlacroix on 2009-03-01
I rebooted and tried again, still not working. All updates applied. Is there anything you guys recommend that I try?

---

### Post by caryb on 2009-03-02
> I rebooted and tried again, still not working. All updates applied. Is there anything you guys recommend that I try?

Mine won't work either! I am using 128bit Shared WEP key, is anyone else who's plasmoid is working using the same configuration:confused:


Cary

---

### Post by jlacroix on 2009-03-02
> **caryb said:**
> Mine won't work either! I am using 128bit Shared WEP key, is anyone else who's plasmoid is working using the same configuration:confused:


Cary

Thank you, I didn't even think about posting that. I'm using a 128-bit WEP key too.

---

### Post by Cernel Joson on 2009-03-02
Mine works fine, and I'm also using a 128-bit WEP. Intel 3945abg, by the way.

---

### Post by meborc on 2009-03-02
for some reason my wifi is now not working any more (unprotected network)

still the same b43

thanks guys for changing my luck :D

---

### Post by meborc on 2009-03-03
update... 

my Kubuntu jaunty is now connecting fine... i don't think it has anything to do with the updates as there has been no wifi related ones lately (afaik)

anyway, all is well once more :)

---

### Post by kgagu on 2009-03-03
I have unprotected network and it does not connect kubuntu 9.04 alpha5. Any help ?

---

### Post by caryb on 2009-03-03
I turned of the hide essid on my access point (router) & bingo my wireless fired up:) I found the hint on this forum.


Cary

---

### Post by LorneLReap on 2009-03-04
I really like the looks, new to Kubuntu-Ubuntu only a year of use but the Alphe is just a little to Buggy yet.
And Yes the Networking works but is buggy and intermitant...love the plasmid for network.
I am 75 feet away from wireless router but it can't stay connected and can't remember the Key, so back to 8.10 and update to KDE 8.2! Good work for an Alpha, But not so user friendly yet.

---

### Post by jwork123nl on 2009-03-04
Using alfa5, network plasmoid, i cannot connect to my network with hidden ssid but it works if I unhide the ssid in my linksys.
I use WPA security with preshared key (PSK).

This is a real bug in the plasmoid.
I think the OP has another problem though.

John

---

### Post by jwork123nl on 2009-03-04
And the bad news is that there is currently no development being done on the networkmanager plasmoid.
Last "real" commit is 2009-02-17

See here:
[http://lists.kde.org/?l=kde-commits&w=2&r=1&s=networkmanager&q=b](http://lists.kde.org/?l=kde-commits&w=2&r=1&s=networkmanager&q=b)

---

### Post by jlacroix on 2009-03-04
Should I report this bug, or is it out of our hands?

---

