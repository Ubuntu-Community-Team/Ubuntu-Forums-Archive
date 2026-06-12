---
title: "Wi-Fi and Bluetooth are disable after upgrading from 22.04 to 22.10"
date: 2022-10-22
forum: Installation &amp; Upgrades
---

### Post by josefranw on 2022-10-22
My wi-fi and bluetooth appeared as disable after upgrading my Xubuntu from 22.04 to 22.10, recently.

I can't seem to be able to enable this via the network manager, because no matter how many times I click on "enable wi-fi" it simply won't enable. No pop-out message would appear, or anything.

I did not switch off any physical button; neither did I press any key to disable wi-fi or bluetooth. It just appeared like that after the system reboot from the upgrade.

I am no expert so I was wondering if anyone could guide me through some steps to try to find a solution to this problem. Thanks.

---

### Post by #&amp;thj^% on 2022-10-22
To help gain viewer's here would you please include this:
```
rfkill list all
```
Please use code tags for your reply's screenshots are not a real good source for viewing terminal commands.
Thanks

---

### Post by josefranw on 2022-10-22
```
rfkill list all0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no



```

---

### Post by #&amp;thj^% on 2022-10-22
Is this is a VAIO laptop?

---

### Post by josefranw on 2022-10-22
> **1fallen said:**
> Is this is a VAIO laptop?

Yes, it is.

---

### Post by #&amp;thj^% on 2022-10-22
> **josefranw said:**
> Yes, it is.

Thought so ;)
please run these one at a time:
```
echo "blacklist iwlwifi" >> sudo /etc/modprobe.d/blacklist.conf.

echo "blacklist sony_laptop" >> sudo /etc/modprobe.d/blacklist.conf
```
Power off or a Cold boot will make the changes, and now any different?

---

### Post by josefranw on 2022-10-22
Still not working... :(

---

### Post by #&amp;thj^% on 2022-10-23
I see your running 22.10, which is pretty much running a beta or point release, they are known to be buggy. This is their best effort before porting it to a final point release to 22.04.(xx)
They also at times bring new features again as rc candidates.
Supported only for 9 months>>>22.04 is supported for 5 years from release date.
I'd go back to more stable and working system if it were me. :)

---

### Post by josefranw on 2022-10-25
Update: The Wi-Fi worked perfectly fine all day, yesterday after I had turned off the laptop and I had gone to sleep. Yesterday, I turned it back on and the wifi was working fine... But then, today when I turned it on again, it wasn't working anymore. I have rebooted it several times, and it continues to be disabled. 

I can't understand how or why it is disabled now but it worked fine yesterday and it was also disabled the days before yesterday. I did not change, update or remove anything.

---

### Post by josefranw on 2022-10-28
[COLOR=#232629][FONT=-apple-system]As of today, I turned on my laptop again and both Bluetooth and Wifi appear as enabled and are working. I fear that if I reboot it, it would again show as disabled and won't work. 

[/FONT][/COLOR]```
rfkill 
ID TYPE      DEVICE              SOFT      HARD  
0 wlan      sony-wifi      unblocked unblocked  
1 bluetooth sony-bluetooth unblocked unblocked  
2 bluetooth hci0           unblocked unblocked  
3 wlan      phy0           unblocked unblocked
```

---

### Post by josefranw on 2022-11-13
Fixed with[FONT=var(--theme-post-body-font-family)] echo "blacklist sony-laptop" | sudo tee /etc/modprobe.d/sony-laptop.conf then reboot.[/FONT]

---

