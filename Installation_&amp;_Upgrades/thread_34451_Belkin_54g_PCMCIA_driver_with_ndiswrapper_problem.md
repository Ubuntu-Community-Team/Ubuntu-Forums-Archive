---
title: "Belkin 54g PCMCIA driver with ndiswrapper problem"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by oilz on 2005-05-14
Hi,

I just purchased the Belkin 54g Wi-Fi Router and PCMICA card.
My router is running on an XP box with no problems.

But gettting the PCMCIA wi-fi card driver to be installed on my notebook running Ubuntu (Hoary) is not easy at best.

Since there are no drivers for this PCMCIA card under linux (I think), I believe my only option is to user the Windows driver with ndiswrapper.

Currently when booting Ubuntu, all lights on the PCMCIA card are off.

lspci displays the following details on the PCMCIA wi-fi card:
Network controller: Broadcom Corpoartion BCM4306 802.11b/g Wireless LAN Controller (rev 03)


After getting the drivers from the CDROM (bcmwl5.inf and bcmwl5.sys) and installing the driver with ndiswrapper:
sudo ndiswrapper -i /home/peter/bcmwl5.inf

And checking to see if it's installed ok:
sudo ndiswrapper -l

I get the following output:
Installed ndis drivers:
bcmwl5   invalid driver!


This is where I'm stuck big time with ndiswrapper!

Can anyone please help, as I'd really love to get wi-fi working for Ubuntu.

Thanks

---

### Post by oilz on 2005-05-15
Hi all,

After many hours, I found the problem with the driver.

There is another driver on the CD called bcmwl5a.inf.
This seems to install ok.

Now to get Wi-Fi up and running.

---

