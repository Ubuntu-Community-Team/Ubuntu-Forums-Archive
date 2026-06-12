---
title: "Upgrade From Kubuntu Feisty to Gutsy Beta incomplete"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by amsri on 2007-09-28
Hi

FIRST OF ALL I WOULD LIKE TO SAY THAT I AM TOTALLY NEW TO LINUX AND UBUNTU. I installed feisty on my Toshiba laptop about two months ago and was so happy with it that, in anticipation of getting more and better, I decided to upgrade to Kubuntu Gutsy 7.10 Beta released yesterday.

Some information:

I have a Toshiba Satellite Pro M70 with dual boot (XP Pro and Feisty 7.04) running before I went for Upgrade. I also have both the Gnome and KDE desktops and was switching frequently to know and enjoy different things new to me. In fact I first installed Edubuntu and then installed Kubuntu-desktop on top of it using synaptic.

I used adept manager to carry out the upgrade and followed the steps mentioned on [https://help.ubuntu.com/community/GutsyUpgrades#head-3cb12417f0af7f24d4a34f2ae4040bf791c42f52](https://help.ubuntu.com/community/GutsyUpgrades#head-3cb12417f0af7f24d4a34f2ae4040bf791c42f52)

The upgrade hung on "Modifying Softwares channels" as nothing happened for half an hour and I had to quit the upgrade.

Thereafter, I restarted the computer and restarted the upgrade using kdesu "adept_manager --version-upgrade"
It started this time and the tool fetched all the upgrade, unpacked it and started configuring the packages.

All went fine till configuring gmone-terminal-editor which failed to configure and I closed the window as prompted by the upgrade tool. The upgrade tool started configuring samba but was never able to do so. It was stuck on "Configuring Samba.." for an hour when I again decided to abort the upgrade.

Now I am nowhere and my system in the middle of nowhere. Grub boot menu now shows several gutsy KERNELS. I am able to boot into Kubuntu using the old Kernel ending with some....16. However, the newest Kernel ending with some .22 fails and I see some Kernel Panic message. When I boot into gutsy using old kernel I can see all the desktop environment but since the system is in the middle of nowhere several services are not available or don't start eg. my network connection (wireless). Tough I can see several new gutsy softwares like Dolphin.

Now my question is: what to do to get my system to a normal state (without wiping out every thing and re-installing). PLEASE HELP. Any answer, keeping in mind that I am a newbie, would be highly appreciated. I thing comes to my mind but I am not sure if it will work and that is: dpkg --configure -a

Thanks to all in advance.

---

### Post by Seisen on 2007-09-28
If you can boot into recovery mode and use the internet do that then enter these command in the terminal. If you can't boot into recovery mode and use the internet than boot into any one of the kernels that you can use the internet in. Also if if your not in recovery mode you need to add "sudo in front of these commands.

```
apt-get -f install
dpkg --configure -a
```

---

### Post by amsri on 2007-09-28
> **Seisen said:**
> If you can boot into recovery mode and use the internet do that then enter these command in the terminal. If you can't boot into recovery mode and use the internet than boot into any one of the kernels that you can use the internet in. Also if if your not in recovery mode you need to add "sudo in front of these commands.

```
apt-get -f install
dpkg --configure -a
```

Thanks you very much for the reply. I will try this today. One more thing (and sorry if this is a stupid question);How will I know in recovery mode that I Can use the internet--should I type these commands and see if it is working or there is any other way. Well the wireless internet is not working in graphical mode of Kernel 2.6.20-16. This was may main working kernel in feisty and I am able to boot this kernel in gutsy.

---

### Post by amsri on 2007-09-29
Hi 

The above solution almost solved the problem solved the problem but the following errors still exist what ever I do:
sudo apt-get update
sudo apt-get -f install
dpkg --configure -f
sudo apt-get upgrade
sudo apt-get dist-upgrade

any of the above in any order does not cure the error given below:

aanjaneya@aanjaneya-laptop:~$ sudo dpkg --configure -a
Setting up gnome-terminal-data (2.18.2-0ubuntu1) ...
/usr/share/gconf/schemas/gnome-terminal.schemas:14248: parser error : Premature end of data in tag long line 14248
         <long>Gyorsbillenty&#369; új lap nyitásához. Karakterláncként kife
                                                                            ^
/usr/share/gconf/schemas/gnome-terminal.schemas:14248: parser error : Premature end of data in tag locale line 14246
         <long>Gyorsbillenty&#369; új lap nyitásához. Karakterláncként kife
                                                                            ^
/usr/share/gconf/schemas/gnome-terminal.schemas:14248: parser error : Premature end of data in tag schema line 14085
         <long>Gyorsbillenty&#369; új lap nyitásához. Karakterláncként kife
                                                                            ^
/usr/share/gconf/schemas/gnome-terminal.schemas:14248: parser error : Premature end of data in tag schemalist line 2
         <long>Gyorsbillenty&#369; új lap nyitásához. Karakterláncként kife
                                                                            ^
/usr/share/gconf/schemas/gnome-terminal.schemas:14248: parser error : Premature end of data in tag gconfschemafile line 1
         <long>Gyorsbillenty&#369; új lap nyitásához. Karakterláncként kife
                                                                            ^
Failed to open `/usr/share/gconf/schemas/gnome-terminal.schemas': Input/output error
dpkg: error processing gnome-terminal-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on gnome-terminal-data (>= 2.18); however:
  Package gnome-terminal-data is not configured yet.
 gnome-terminal depends on gnome-terminal-data (<< 2.19); however:
  Package gnome-terminal-data is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of edubuntu-desktop:
 edubuntu-desktop depends on gnome-terminal; however:
  Package gnome-terminal is not configured yet.
dpkg: error processing edubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-terminal-data
 gnome-terminal
 edubuntu-desktop

---

### Post by Pumalite on 2007-09-29
[https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)

---

### Post by amsri on 2007-09-29
> **Pumalite said:**
> [https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)

Thanks for the post Pumalite. I tried the solution in the link but the problem still remains as it is.

---

### Post by Pumalite on 2007-09-29
[http://lists.alioth.debian.org/pipermail/pkg-gnome-maintainers/2005-October/019166.html](http://lists.alioth.debian.org/pipermail/pkg-gnome-maintainers/2005-October/019166.html)
[http://ubuntuforums.org/archive/index.php/t-347282.html](http://ubuntuforums.org/archive/index.php/t-347282.html)

(I'd tell you that I think upgrades are messy. I usually save data and do a clean install)

---

