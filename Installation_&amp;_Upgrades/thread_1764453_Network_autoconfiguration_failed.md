---
title: "Network autoconfiguration failed"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by entropy51 on 2011-05-21
Hi Everyone,

I recently purchased a Dell Vostro v130 which came with Win 7 pre-loaded.  I've been using it for a few weeks with no problems, but now I'd like to install ubuntu studio.

I made it through the the partitioning part but now I'm getting a networking error: "Network autoconfiguration failed. Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly."

I've been using the wireless connection in win 7 without any problem so I don't know why I'm having a problem now.

Does anyone have any thoughts?  

Thanks for your help.

---

### Post by ajgreeny on 2011-05-21
Is your router not set up to use DHCP in windows?  If it is it should also work for you in ubuntu.

Does the live CD/USB give you a wireless connection?

What wireless adapter are you using?

---

### Post by entropy51 on 2011-05-21
Please bear with me since I'm a relative novice.

My understanding is that in n Win 7, DHCP is enabled if within my TCP/IPv4 properties "obtain IP address automatically" and "obtain DNS server address automatically" are selected.  In my case they are and I have no issues connecting to the internet.

My wireless adapter is Dell Wireless 1702 802.11b/g/n

What do you mean by "Does the live CD/USB give you a wireless connection?"?  

thanks for your help.

---

### Post by entropy51 on 2011-05-21
Is it possible the installation is trying to use a wired connection instead of a wireless?  Should it matter?

---

### Post by ajgreeny on 2011-05-22
If you are connected with a cable remove it and see if it helps.

I have no idea about the dell wireless adapters, or what chipsets they  use, but you can find that info with ```
sudo lshw -C network
```  in terminal.

---

### Post by entropy51 on 2011-05-22
The cable is not plugged in and I haven't finished the install yet so I am unable to use the terminal.

---

### Post by entropy51 on 2011-05-22
So just out of curiosity, I disabled my wired connection within the bios and then booted back into Win 7 to see if the wireless was still working (it was working).

Next, I started the install again and this time I get the error "no network interfaces detected".  Now I am convinced that Ubuntu is not recognizing my wireless adapter.  Any ideas on how to get it to recognize it?

---

### Post by cchhrriiss121212 on 2011-05-22
Studio does not have wireless enabled, this is by design as it interferes with audio processes for some users. 

If you need wireless, it is best to go with regular Ubuntu and then add whatever studio packages you like via synaptic or software centre. Or carry on installing Studio with a wired connection present, then install gnome network manager to add wireless functionality.

---

### Post by entropy51 on 2011-05-22
Whoa...that totally makes sense.  On my desktop, I have studio installed and guess what, wireless doesn't work there either.  

do you know of any tutorials on how to install the gnome network manager?

Thanks for the help!

---

### Post by cchhrriiss121212 on 2011-05-22
Plug in to a wired connection and get it from synaptic. See here for more detail:
[https://help.ubuntu.com/community/UbuntuStudioNetworkSetup](https://help.ubuntu.com/community/UbuntuStudioNetworkSetup)

---

### Post by entropy51 on 2011-05-22
I'll check it out.  Thanks for your help!

---

