---
title: "Partitioning?"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Jonas Wakefield on 2008-04-29
Ok I'm completely new to the whole Ubuntu thing but anyway... I installed Ubuntu 7.10 and couldn't get on the Internet because I needed a b43xxfwcutter or something to enable my Broadcom card. So when I go to install the newest version of Ubuntu 8.10, I want to have it to dual-boot and share my hard disk or drive, whatever its called...

But when I get to Step 4 of 7 of the installation with partition it  only alows me to use all my hard drive or disk (160GB) or manual.

Before I had the option to put 50% Vista and 50% Ubuntu.

How do I get that back, or what way do I partition to get Ubuntu and keep Vista without changing it.

Cheers

---

### Post by z0mbie on 2008-04-29
How was your previous partition setup?
Was it standard ext3 for / & swap? If its so then you can just install over (delete) your old Ubuntu by selecting ext3 and mounting it as / also selecting format partition ([COLOR="Red"]remember this will delete everything in the partitions[/COLOR]). NTFS partition is your Vista, don't touch it, make sure you don't select format on that partition. Then the rest of the installation should be smooth.

---

### Post by lemming465 on 2008-04-29
You need *manual* in this situation; don't panic; pretty much all you have to do is point at your root partition and use the drop down to say use it as root.

---

### Post by Jonas Wakefield on 2008-05-01
Thanks a lot z0mbie, got that running, but now I have to set up my Internet Connection. It picks up my router and its signal strength, but it wont connect. I put in my panel a Monitor Network applet and I don't what to set it at, some say I have to set my Network thing to WEP from WPA.

When I open that Monitor Network applet, I have the choice to choose my interface. It always stays at lo(loopback), and I think it should be at wlan0, but sure, any ideas. If you need anymore iformation ask...

Cheers

---

### Post by lemming465 on 2008-05-02
You don't have to downgrade your wireless from WPA to WEP; I'm using WPA2 with a laptop running Ubuntu 8.04 just fine.  Mine has a not very well supported Atheros chipset though, so it took some work to get it there, and I'm currently using ndiswrapper with a windows driver.  Maybe for 8.10 this fall I'll be able to go native.

Anyway, in your case it sounds like you have a broadcom chip, and there are a lot of reports of issues with the new b43 driver under hardy.  Run *sudo lscpi -vv* and copy down all the information about your wireless chip, and then spend a while spelunking in the wireless forum.  You aren't alone, and someone there probably has an answer for you already.

---

