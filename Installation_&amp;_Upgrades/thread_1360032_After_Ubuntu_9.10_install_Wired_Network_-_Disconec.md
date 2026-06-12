---
title: "After Ubuntu 9.10 install: Wired Network - Disconected - you are now offline error"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by abcuser on 2009-12-20
Hi,
on my home computer were installed Windows XP and Ubuntu 9.04 as dual boot. Both system were working without any problem.

Today I have removed Ubuntu 9.04 and fresh installed Ubuntu 9.10 (I used manual partitioning and delete Ubuntu 9.04 partition and create new partition for Ubuntu 9.10). Installation finished successfully without any error. I rebooted computer in Ubuntu and network should be working out of the box (like in Ubuntu 9.04). But passing one minute after reboot I get error: "Wired Network - Disconnected - you are now offline."

I have checked network settings and default should be fine using DHCP server and no proxy.

I have rebooted PC and boot into Windows XP and there is no problem with network, I can successfully connect to Internet, so network is working fine.

PC uses "Intel PRO/100 VE Network Connection" network card.

Any idea what is wrong on my Ubuntu 9.10 network settings?

Regards

---

### Post by abcuser on 2009-12-29
Hi,
very strange... I haven't had time to solve this problem, so I have been only using Windows XP for more then a week. But today I turned on computer and forget to choose Windows from grub menu, so Ubuntu was started and network is working without any problem at all. This is very strange... Any idea what was wrong with network?
Regards

---

### Post by avtolle on 2009-12-29
No idea, but I had a very similar experience, which has not recurred in ~2 months.

---

### Post by abcuser on 2009-12-30
Hi,
today I have started up Windows XP (dual boot) and now I have the same problem in Windows. I get network error "Limited or no conectivety". I haven't change anything in Windows!

But now network is working fine in Ubuntu. Any idea what is happening? So I have dual boot but when network is working fine with Ubuntu, then network is not working in Windows XP and vice versa.

What could be wrong?
Regards

---

### Post by abcuser on 2010-01-02
Hi,
I have temporally solved the problem.
1. In Ubuntu I have checked my IP address ("sudo ifconfig" command).
2. Then I have rebooted into Windows XP.
3. I have checked IP address in Windows ("ipcofnig /all" command). Funny thing it has completely different IP address.
4. I have set Ubuntu's IP address in Windows XP network connection as static IP address (I know I have dynamic IP, so this would not work) pressed OK button and network connection is not working (as expected).
5. Then I have reentered network settings as "Obtain an IP address automatically" and pressed OK button. Now my network connection works fine in Windows.

It looks by executing this trick it triggered DHCP server to send me a new IP address. I have rechecked using "ipconfig /all" and now I have new IP address.

Just a note, before that I have used "ipconfig /renew", this command should convinced DHCP server to renew IP address, but I always got "DHCP server time expired" error.

According to [Windows XP Troubleshooting network connection problems](http://www.microsoft.com/windowsxp/using/networking/maintain/troubleshoot.mspx) I suspect that there is some kind of problem related to DHCP server of my ISP vendor. I don't know how DHCP server assigns **new** IP address, but I suspect that new IP address is not assigned, because most probably DHCP server is convinced that this is the same hardware system (it actually is there are just two operating systems on it), so there should be no need of changing IP address.

I have done the final test, I rebooted computer and started Ubuntu 9.10 and Ubuntu can't connect to internet - the same error as in title of this thread.

Is there any trick in Ubuntu to fool down DHCP server to assign me a new IP address?
Regards

---

### Post by glaverty on 2010-08-23
From a terminal windows, you could try:
sudo dhclient

That's a quick way of requesting a new IP from your router...

---

### Post by xaliqen on 2010-08-24
Are you using a router you installed, or is someone else controlling the DHCP server on your network?

If you have access to administrative functions on your router, I would check the setup there and look through the logs.

You might also consider changing your DNS servers if you frequently experience errors related to "partial connectivity."  The OpenDNS servers are a good option if you don't want to use the DNS servers provided by your ISP ([instructions here]("https://store.opendns.com/setup/operatingsystem/ubuntu")).

---

