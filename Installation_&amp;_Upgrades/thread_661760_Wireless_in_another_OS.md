---
title: "Wireless in another OS"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by burning_man13 on 2008-01-08
I know this is a Ubuntu forum... but I'm having a very hard time with my wireless in OpenSuse 10.3, and the forums there are junk... I've had a post there for over a week, and haven't had one response... I'm dual booting OpenSuse and Ubuntu (90% of the drive is Gutsy)... I cannot connect to my wireless in OpenSuse, but I can in Gutsy, when I plug my computer in through ethernet the internet works just fine... My wireless card is an Intell PRO/Wireless 100 VE wireless card, I'm wondering if it is a driver problem, I don't believe it is, because the card is recognized... So if anybody here is versed in Suse, any help would be appreciated... I won't be offended if people in a Ubuntu forum can't completely help me, as long as I can get a start (the people in Suse can't give me that)... once again, all thanks in advance...

---

### Post by Steve1961 on 2008-01-08
I thought Intel PRO/Wireless 100 VE was a wired network card - might be worth double checking this by issuing the following command:

lspci -v

Anyway, this link might help you out:

[http://en.opensuse.org/HCL/Network_Adapters_%28Wireless%29](http://en.opensuse.org/HCL/Network_Adapters_%28Wireless%29)

I notice that there's a bug in the 3945ABG variant of the intel wireless support in suse 10.3, but if this is your card there also seems to be a fix (update) on the page as well

---

### Post by burning_man13 on 2008-01-08
You might be right there... I'll have to look on my Ubuntu to see what my wireless card is... I could have swore that was it... but that repository list was good news... I'm pretty sure I can find my driver there... thanks for the start at least... if not... I'll prolly be back here, due to the fact that I can't find any help on Suseforums (not to rip on them, I really like the OS, but the help isn't the greatest)...

---

### Post by Steve1961 on 2008-01-08
Best of luck :)

---

