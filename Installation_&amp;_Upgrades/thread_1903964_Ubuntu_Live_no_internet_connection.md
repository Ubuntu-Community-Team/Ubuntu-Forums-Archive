---
title: "Ubuntu Live no internet connection"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by marel on 2012-01-03
I've booted USB with Ubuntu and started Ubuntu Live however there's no internet connection. I am suspecting that the problem might be that I've changed my MAC address on Windows and that it gets reset every time I load Ubuntu. What should I do then ? Register actual MAC address with ISP or change it in Ubuntu again ?

---

### Post by efflandt on 2012-01-03
Are you directly connected to a cable modem?  If so, you may need to either totally power down the modem for a few minutes if it does not have a reset button, or clone the MAC address that was previously used.  For any other type of connection MAC address should not really matter, as long as it has a non-zero MAC that does not conflict with something else.  I have never changed a MAC, but it looks like **ifconfig** may be able to do that.

Are you sure that the proper or best module is being used for your network device? The following should give some info about your network device and module it is using now:

```
sudo lspci -v
```

---

### Post by ottosykora on 2012-01-04
I know they are specific hacker tools to 'change MAC' for a moment just to bypass some MAC filtering in a network.

But for generic users MAC can not be changed at all, it is fixed burned into the network adapter and it does not change if you switch between windows and linux. If it does, you hardware is definitely broken and has to be disposed of.

There is  no way your MAC can change by resetting the power of any part of your network. The MAC is assigned to the manufacturer of network devices and only he can insert it during the production into the chipset.

And the manufacturer has to ensure, that no MAC exists twice at any time.

---

