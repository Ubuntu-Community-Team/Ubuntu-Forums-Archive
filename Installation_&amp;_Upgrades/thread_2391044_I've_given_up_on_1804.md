---
title: "I've given up on 18:04"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by AmpersUK on 2018-05-05
... and reverted to 17.10. I'll try again in three months.

I see that Ubuntu is now only geared for the USA market as I tried to change the supplied Amazon app from American to the UK and cannot seem to be able to change it. I checked under settings and it says UK but when I try to buy anything it shows the price only in dollars.

What a shame that a company based in the UK does this. Or, am I missing something?

---

### Post by PaulW2U on 2018-05-05
> **AmpersUK said:**
> What a shame that a company based in the UK does this. Or, am I missing something?
I no longer use Amazon so hadn't come across this issue before.

At the foot of the Amazon front page you should see some buttons for language and country. Mine was set to USA - a quick change and I'm back at home seeing £ signs. :)

Possibly a bug that needs reporting as I was asked if the Amazon application could use my location settings.

Edit: An issue for some time - [Amazon webapp always going to amazon.com]("https://bugs.launchpad.net/ubuntu/+source/webapps-applications/+bug/1237999")

---

### Post by AmpersUK on 2018-05-05
Thanks, it seems to have been a problem since Ubuntu 13.04. Hopefully by 25.04 it will be fixed :-)

---

### Post by dino99 on 2018-05-05
There is no problem using amazon from a browser: simply select the good url location. But i suppose you are used to 'click' the Amazon icon proposed, which point to US by default; if you want that icon to point to UK, then simply edit the icon properties and adapt the linked url.

---

### Post by PaulW2U on 2018-05-05
> **AmpersUK said:**
> Thanks, it seems to have been a problem since Ubuntu 13.04. Hopefully by 25.04 it will be fixed :-)
A low priority bug as I would imagine most users would use a browser bookmark that links directly to their own country specific Amazon site.
> **dino99 said:**
> if you want that icon to point to UK, then simply edit the icon properties and adapt the linked url.
If you are prompted to allow the Amazon webapp to use your location settings then you would expect to be directed to the appropriate site for your location. Manual editing of system settings to make something work correctly or as expected is unacceptable in my opinion.

---

### Post by Skaperen on 2018-05-05
i use Amazon and Amazon AWS via a VPN service in another country.  when i connect to these web sites, they assume *i* am in the VPN provider's country.  e.g Amazon assumes country-of-customer == country-of-provider.  i can change it, but i have to do so on each visit.  as soon as i bought something via that account, that fixed it.  it is probably looking at currency of payment, now, which is another issue since people *can* use the currency of many other countries (i have, a few times).  what if my first purchase was not in my own country currency?

---

### Post by PaulW2U on 2018-05-06
I'm glad you posted Skaparen. I'm now using another installation of Ubuntu 18.04.

When starting the Amazon webapp I made sure that I allowed the app to read my location and I went directly to the amazon.co.uk website as I would expect. All prices shown in UK pounds.

So possibly still an issue in some Ubuntu releases as the bug report is still open but it does seem to work in 18.04 provided permission is granted for a user's location to be read. The default was for permission to be denied.

---

