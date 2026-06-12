---
title: "After update to Edgy wireless card stopped working"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by rboss on 2006-10-30
After I updated to Edgy, my wireless card (Prism 2.5 Wavelan) stopped working. (No such device).

Does anyone have similar problems? Any help?

---

### Post by koshari on 2006-10-30
in edgy i had to blacklist the following modules to get my prism pci adapter to load the orinco drivers , and then it was happy, 

```
blacklist prism2
blacklist prism2_pci
blacklist hostap_pci
blacklist hostap
```

simply add these entrys to your ```
/etc/modprobe.d/blacklist
``` file

---

### Post by rboss on 2006-10-30
Yes, that did it. Now it's working like a charm. Thank you!

---

### Post by svenaron on 2006-11-02
Works brilliantly for me on my ThinkPad T30 as well.
Thanks!

/Sven

---

### Post by syg00 on 2006-11-04
+1.
Mepis found it o.k. but has other issues - this is to get "her wot must be obeyed" onto Ubuntu.

Thanks.

---

### Post by Drain on 2006-11-18
Chalk up another small victory for your solution.  Thanks!

---

### Post by StFS on 2006-12-16
kudos! works for me over here too... and fixed my long lasting problem of not being able to use knetworkmanager too! so double kudos.

---

### Post by alm on 2007-01-15
Same problem here.
After updating to Edgy (having same problems) the wifi stoped working.
Then, after a clean Edgy install it DID WORK for a few minutes and then died.
The funny thing is that when I boot from the edgy installing CD it WORKS great.

I am starting to desperate !  ](*,) 


lspci:

00:00.0 Host bridge: ATI Technologies Inc R200 AGP Bridge [Mobility Radeon 7000 IGP] (rev 05)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 7000 IGP
02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
------------------------------------------

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

------------------------------------------
sudo iwlist ath0 scanning

ath0      Interface doesn't support scanning : Invalid argument

(when booting from the edgy Installing CD the scanning goes ok !)

---

### Post by koshari on 2007-01-29
> 02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

thats a different chipset and i dont think uses the same modules as the prism .

---

### Post by MalVeauX on 2007-02-05
Hello,

Well, I had just clean installed ubuntu 6.10 and used a guide here to make the broadcom wireless work, via ndiswrapper. All was working great. I went wireless and was free.

Then I let ubuntu update (something like 113 updates or files or something).

It froze a little after it downloaded and installed all that.
Then I rebooted and wireless was just gone.

My ndiswrapper is still functioning; my driver is still loaded, etc.
But my networking gives me an error just for clicking it:

SICIOFLAGGS: device not found..

Or something along those lines.
I have no idea how to fix this, or even begin.

Any suggestions on beginning even know where to start?

Very best,

---

### Post by gtemedtk1 on 2007-02-07
Has anyone tried madwifi drivers?  I have used it in SuSE 10.2 before and it worked great. I am planning on using it with my Ubuntu install on the same laptop. Will let you know how it works. I hope this helps.  :)

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

### Post by rustylix on 2007-03-19
It seems I am in the same boat with the Prism 2.5 as most of you.  The only difference is....  I know absolutely jack about linux, including what it takes to edit the blacklist file.  I have located it on my file system, but it is owned by the root user, and I am unable to edit its contents.  I imagine I need to log in as sudo using the terminal but have no idea how.  Can somebody please explain how I can add these four lines to the blacklist file?

Thanks
Rick

---

### Post by rustylix on 2007-03-19
50 google searches later and I now know enough to append four lines to the blacklist file albiet probably the hardest way possible.  If anyone else comes across this forum and knows as jack little about linux that I do, post a reply and I'll explain what I did.....

---

### Post by serpentsky on 2007-03-21
> **koshari said:**
> in edgy i had to blacklist the following modules to get my prism pci adapter to load the orinco drivers , and then it was happy, 

```
blacklist prism2
blacklist prism2_pci
blacklist hostap_pci
blacklist hostap
```

simply add these entrys to your ```
/etc/modprobe.d/blacklist
``` file

i had the same problems. (ibm t23, minipci prism) but with this entries it works fine :)
thx a lot!

---

### Post by badtzninja on 2007-03-28
I'm new to Ubuntu/Linux and don't know much about it. So any help in getting my wlan working would be greatly appreciated!

---

### Post by OzDad on 2007-10-20
> **koshari said:**
> in edgy i had to blacklist the following modules to get my prism pci adapter to load the orinco drivers , and then it was happy, 

```
blacklist prism2
blacklist prism2_pci
blacklist hostap_pci
blacklist hostap
```

simply add these entrys to your ```
/etc/modprobe.d/blacklist
``` file

Ellooo,
I installed ubuntu 7.10 onto my HP Pavillion DV6000 laptop, which was the only one that would remove the Vista OS.
My wireless internet connection was working until yesterday when i had 62 updates.
As it downloaded about the 14th or15th update everything stopped. I now have no internet and am getting the SIOCGIFFLAGS error too.

The entry's above from Koshari are to be added to the code. Where is the code found? Is it in Terminal?

Thanks,
Andy.

---

### Post by H-Radical on 2007-10-28
I tried the blacklist too, but it did nothing for me. I still get the same SIOCGIFFLAGS error.

cheers

---

### Post by ozPATT on 2007-10-31
hey there ozDad, did you check to make sure the wireless switch was on? ;) I would bet a lot of money that if you switch that on you will have your internet back ;)

---

### Post by OzDad on 2007-11-01
Thanks ozPATT, when i've got 135 beans under my belt, i may be half as good as you!

---

