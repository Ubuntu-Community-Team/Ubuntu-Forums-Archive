---
title: "Switching to 9.10 loses internet"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MrDead on 2009-10-13
I recently upgrade to karmic from jaunty (9.04-9.10) and unfortunately my wireless now does not work. The wireless card itself is working, but whenever I try to connect to a network (which I know works) it tries to connect but it keeps asking over and over again for the WEP key for the network. Each time I enter it in it just sits for a little while then asks for it again. I tried manually erasing then refilling the wireless profiles, but it still asks for the key. I am sure I have the right key, but for some reason it's not accepting it on either connection. If necessary I can post any command ouputs you may want, but I doubt this has anything to do with anything that complicated.

---

### Post by lidex on 2009-10-13
If it worked before, I'd suggest rolling back your wireless driver. Karmic is still in beta.

---

### Post by MrDead on 2009-10-13
I'm pretty sure the hardware/driver is working fine and it took me a while to get it working before. This same thing happened in 9.04, and I'm not quite sure what I did to fix it, if I did anything. 
Thanks for the suggestion, but does anyone have any other ideas?

---

### Post by MrDead on 2009-10-14
I think the problem lies in the software or some interaction the software is having with administrative permissions, so is there any way to manually connect to a network, or ensure that administrative permissions are present?

---

### Post by RobtA on 2009-10-14
Try this: Open Terminal, and attempt to launch the network manager program.

nm-connection-editor

If it fails, and complains that some file is missing, or some folder cannot be opened, then you may be able to repair the problem manually. That happened to me: 9.10 was working fine on wireless until some update had an "oops," and I repaired it by creating a dummy file or folder according to Terminal's complaint. The "oops" went away at the next update, so not many folks saw it.

---

### Post by MrDead on 2009-10-22
I tried what you suggested, and it did come up with an error, but it doesn't seem to relate to what my problem is.

I typed in nm-connection-editor, the editor window came up, but the terminal output gave me this :```
**nm-connection-editor:4342:Warning**:nm_connection_list_new:failed to load VPN plugins: couldn't read VPN .Name files directory /etc/networkManager/VPN
```
I'm not quite sure what this means, but I don't really care about VPN connections, and whenever I connect the system monitor registers some network activity, but then it asks for the network WEP key again and again.

---

### Post by pstickar on 2009-10-25
I get the same error message (VPN plugin, about which I _do_ care), but I do not get any questions for the network WEP key, so I would say they are independent problems.

Mine is a fresh install (9.10, 64 bits) on a hp2530p laptop, sporting an Intel Link 5100 AGN network card.

Two minutes after: got rid of that error message by installing package network-manager-vpnc. I do not think it will solve your problem, though.

---

### Post by lidex on 2009-10-25
Its' probably network-manager. May be a fix in the pipeline. Try enabling all updates in software sources (including proposed and backports). Then in terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
Reboot

Next try re-installing NM
Reboot

---

### Post by MrDead on 2009-10-27
Thanks alot for the advice, but unfortunately I can only connect to the internet via wireless (I'm dual booting w/ windows 7 RC and the internet works fine (kinda)). So, is there any way to download the requisite update files without connecting to the internet while on Ubuntu, like downloading the files then transferring them to the ubuntu partition?

---

