---
title: "Complete mess after failed upgrade to 11.10"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by pssturges on 2011-10-26
Hi,

This morning I tried to upgrade my mythbuntu backend machine from 11.04 to 11.10. All the packages downloaded successfully but at some point during the installing upgrades stage, there was an error about not being able to install samba. I clicked ok and the upgrade continued until all the installation faze had completed when a similar error appeared and additionally stated the the upgrade could not be completed. It also stated that the machine may have been left in an unusable state.  Before I rebooted, I opened synaptic which said there was some dependency issues which I successfully fixed and applied within synaptic. During this samba installed. 

I then rebooted. Now grub appears and the machine startes to boot. The 'Ubuntu 11.10' splash screen appears for a little while then a message appears below it saying ' Waiting for network configuration'. A little while later the message changes to 'Waiting upto an additional 60 more seconds for network configuration'. 1 minute later another message briefly appears saying something along the lines of ' booting anyway'.  The screen goes black then doesn't progress any further. 

I can boot into a text console via recovery mode, but I have no network connectivity despite using that option. This machine had been set up with a static ip within the network manager applet and is hard wired to the router. I'm not sure if that has something to do with  my network issues now. 

I think if I can get network connectivity, I will have a chance of solving any other problems. 

Any on ideas on where I can go from here much appreciated

Edit: I have made some progress...After booting to a terminal via recovery mode, if I run 'startx' a proper xfce session starts and runs. It's not the usual mythbuntu style session but its functional. Only problem is, still no network. It does seem if I can get the network working, all will be good. 
Looking at this output:
```
phil@htpcserver:~/Desktop$ lspci | grep Eth
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
phil@htpcserver:~/Desktop$ ifconfig
phil@htpcserver:~/Desktop$ 

```
The NVIDIA controller is the on board nic which became faulty some time ago, so I replaced it with the Realtek in a pci slot. Interestingly ifconfig produces no output???

BTW 11.10 live cd works fine and ahs network connectivity.

---

