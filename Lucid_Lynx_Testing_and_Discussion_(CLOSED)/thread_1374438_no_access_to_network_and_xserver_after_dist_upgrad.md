---
title: "no access to network and xserver after dist upgrade"
date: 2010-01-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bluesscream on 2010-01-06
Last actualisation and reboot after installing repo's nvidia 173... destroyed access to xserver and network's manual configuration. I don't find a fitting config file. /etc/network/interfaces has only the default entry. Where will I find the ip4 settings for editing them manually?

---

### Post by maheshasolkar on 2010-01-06
I am having trouble with NetworkMansger/nm-applet since last night too. I am doubtful if it is related to nvidia modules though. My laptop has Intel video hardware.

Did you get any other updates along with nvidia ones?

---

### Post by cariboo on 2010-01-06
You can set static ip addresses using Network-Manager, just right click on the icon in the top panel then:

[list]
[*] Select edit Connections
[*] Select your network device
[*] Click Edit
[*] Click the IPv4 tab
[*] Select Manual from the Method dropdown
[*] Click Add to enter your ip address, netmask and gateway. Press Enter after after each address
[*] enter you DNS addresses
[*] Click Apply and enter your password
[*] Disable and Enable networking to make the changes take affect
[/list]

---

### Post by bluesscream on 2010-01-07
> click on the icon in the top panel
I would have done this if I'd come to a graphic display :-\" Lack of this was the reason of my question, and still I'd recommend an answer... I think further on it's /etc/network/interfaces and the update had deleted my entries - it's alpha :)

As I had not much to loose in lucid I just remembered old §$%$%&()/&% experiences and reinstalled. 
Further on some troubles with nvidia - after login I always have to run ```
sudo restart gdm
``` for getting proprietary driver - but a lot works fine

---

### Post by trulan on 2010-01-08
So far I think the only NVidia driver that is working properly in Lucid is the 190 series from sevenmachines ppa, unless they got the 190 or 195 series in the repos now.  The issue is with Xorg if I understand correctly.  And the drivers from the ppa didn't work with the rt kernel for me, so I haven't been doing much in Lucid lately.

---

### Post by cariboo on 2010-01-08
> **bluesscream said:**
> I would have done this if I'd come to a graphic display :-\" Lack of this was the reason of my question, and still I'd recommend an answer... I think further on it's /etc/network/interfaces and the update had deleted my entries - it's alpha :)

As I had not much to loose in lucid I just remembered old §$%$%&()/&% experiences and reinstalled. 
Further on some troubles with nvidia - after login I always have to run ```
sudo restart gdm
``` for getting proprietary driver - but a lot works fine

Network manager stores the settings in /etc/NetworkManager/system-connections/Auto eth0, you may be able to manually add your ip address. This is what the ipv4 section looks like on my system:

```
[ipv4]
method=manual
dns=64.59.168.13;
addresses1=192.168.1.215;24;192.168.1.1;
ignore-auto-routes=false
ignore-auto-dns=false
dhcp-send-hostname=false
never-default=false
```

---

### Post by VMC on 2010-01-08
Odd, as I have nothing in that folder. Its parent folder I have this:

```
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager/nm-system-settings.conf
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

My network connection is for a wired etho. I'm using a DSL modem.

---

### Post by bluesscream on 2010-01-08
Tx cariboo, > Network manager stores the settings in /etc/NetworkManager/system-connections/Auto eth0 there it is here too. Now I know where to look in next case of synchronous network and graphics disaster :)
But is /etc/network/interfaces obsolete? I don't see any advantage when polished ip connection programs like network manager or wicd save standard settings into their own places/conf.files.

---

### Post by bluesscream on 2010-01-08
Hi Trulan, you're right, but I still love the silence of my old passive cooled fx5200 which isn't accepted by the 190/195... group, I need legacy 173... drivers. 173.14.22 from Nvidia works smart in lucid alpha, 2.6.32.9-generic-pae as well as 2.6.31-9-rt, but the settings get lost. After restart I have to log in in low graphics mode, then run sudo restart gdm and fit the resolution in Nvidia's gui. Everytime I choose an alternative kernel I must reinstall the Nvidia driver.  ```
sudo sh NVIDIA-Linux-xxx-xxxxxxxxx-pkg1.run -a -K --kernel-name=$OTHER KERNEL
``` doesn't help even if I sucessfully compiled after setting paths for the fitting headers manually.
I hope this will be fixed in some days, so we can start our audio tests to harden ubuntustudio for lucid ;)

---

### Post by nanog on 2010-01-08
nvidia 185 works fine, for me.

---

### Post by cariboo on 2010-01-08
nm

---

### Post by zika on 2010-01-09
> **bluesscream said:**
> Tx cariboo,  there it is here too. Now I know where to look in next case of synchronous network and graphics disaster :)
But is /etc/network/interfaces obsolete? I don't see any advantage when polished ip connection programs like network manager or wicd save standard settings into their own places/conf.files.No it is not. Whatever interface You enable in /etc/network/interfaces NM will not touch. It will complain about it but that is still an option. You can configure NM to accept the fact that it is not responsible for any interface and complaint will stop. I see NM, now, not as polished gadget but as a tool. For quite some time I used to disable it because it caused more trouble that it brought but, now, it grew into useful tool.
**Update:** I shouldn't have praised NM so much. Yesterday it was making my networking living in hell. It is uninstalled now! I thought my HW went wrong (no cable left unchecked, ebooted several times, changed DNS tens of times, complained to my son for his torrenting) but **NO**, it was NW from daily trunk. Back to /etc/network/interfaces...

---

