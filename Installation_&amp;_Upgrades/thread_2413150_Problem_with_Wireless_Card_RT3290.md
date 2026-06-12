---
title: "Problem with Wireless Card RT3290"
date: 2019-02-21
forum: Installation &amp; Upgrades
---

### Post by aefkaa on 2019-02-21
Hello, I have got problem with Wireless card RT3290. I have laptop ASUS X550LC with card RT3290 and I can't connect with internet. 

I know that problem is: 
```
0: phy0: Wireless LAN
    Soft blocked: no
   [COLOR=#ff0000]** Hard blocked: yes**[/COLOR]

```

My combine keys Fn+F2 don't working. 
Set default settings in BIOS also don't working. 

In blacklist.conf I don't have f.e. rt2800pci 

*lspci -vnn | grep Network* :
```
03:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]

```

[I]iwconfig :
[/I]```
wlp3s0f0  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:off
          
enp2s0f1  no wireless extensions.

lo        no wireless extensions.

```[I]

Thanks for your time :)
[/I]

---

