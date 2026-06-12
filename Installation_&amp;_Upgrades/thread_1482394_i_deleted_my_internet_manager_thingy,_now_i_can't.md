---
title: "i deleted my internet manager thingy, now i can't"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by WOOHOOHOO on 2010-05-13
download anything (obviously). Can someone walk me through how to get it back online. I didn't have audio after upgrading and i ended up deleting the internet connection thing. i cant download from terminal/package manager etc. 

I tried rolling back but it still doesnt work.

Please help.

---

### Post by i.r.id10t on 2010-05-13
If you are on a wired connection, and if your ehternet device is eth0 then

sudo dhclient eth0 

should get you a dhcp address.  Change the eth0 to whatever your network device is.

If you are using wireless you'll need to use iwconfig to set your SSID, etc. before doing this.

---

### Post by Onesimus on 2010-05-13
If you mean the internet icon on the top panel.

You need to right click on panel, select 'Add to Panel', then add the 'Notification Area'

---

### Post by WOOHOOHOO on 2010-05-14
> **i.r.id10t said:**
> If you are on a wired connection, and if your ehternet device is eth0 then

sudo dhclient eth0 

should get you a dhcp address.  Change the eth0 to whatever your network device is.

If you are using wireless you'll need to use iwconfig to set your SSID, etc. before doing this.

Hi, thanks for the reply. 

I did the sudo dhclient eth0 part, it does have a dhcp numbers, one dhcpDISCOVER, one DHCPOFFER, one DHCPREQUEST and one DHCPPACK.Which one,and how do i change it? I dont have the internet icon in the panel to click on. ALso, when you say my network device, do you mean the type of modem?

Thanks.

---

### Post by mhgsys on 2010-05-14
after the sudo dhclient eth0 got the offered ip adres.
 do a 

```
 sudo apt-get install network-manager-gnome
```

---

### Post by WOOHOOHOO on 2010-05-14
yay! COol, internet is now working. DOwnloaded the gnome thing and installed that also. I guess when  i reload it will give me an icon,

Thanks guys, good work!
:guitar:

---

### Post by mhgsys on 2010-05-14
Well, Please try it out. 

And mark your thread as solved if it worked out for you 

(go to thread tools > mark this thread as solved)

---

