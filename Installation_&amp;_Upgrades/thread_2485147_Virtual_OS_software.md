---
title: "Virtual OS software"
date: 2023-03-21
forum: Installation &amp; Upgrades
---

### Post by skywalker007 on 2023-03-21
[FONT=arial]I am trying to install KVM to be able to run virtual machines on the laptop.
The laptop did pass the checks that it can support it. So I stated installing it, installation went well and there was no problem and came to the following point. First they said I need to ENABLE and then START using the commands:
[/FONT][FONT=arial][$ sudo systemctl enable --now libvirtd]
[$ sudo systemctl start libvirtd]

This went fine with no errors, finally they said that I have to confirm it is running

[$ sudo systemctl status libvirtd]

But just get back a error reading : Unit libvirt.service could not be found.

On my own desktop KVM is visable but when I try to open it I just get a error reading "unable to connect to libvirt quemu:///system Verify that the 'libvirt' daemon is running.

I am running 22.10 but I suppose KVM should still work.

-- Just want to ask the following as well. They said I should check to make sure my laptop can support virtual maschines and make sure the answer is not 0 by using [ [/FONT]egrep -c &#8216;(svm|vmx)&#8217; /proc/cpuinfo [FONT=arial]]. What does it mean if mine comes back 4

Thanks
Johan
[/FONT]

---

### Post by ActionParsnip on 2023-03-21
[https://ubuntu.com/blog/kvm-hyphervisor](https://ubuntu.com/blog/kvm-hyphervisor)

Does that help?

---

### Post by Dennis N on 2023-03-21
> ENABLE and then START using the commands:
[$ sudo systemctl enable --now libvirtd]
[$ sudo systemctl start libvirtd]

You need to enable the libvirtd.service, not libvirtd.

```
sudo systemctl enable libvirtd.service.
sudo systemctl start libvirtd.service
```

also add your user to the libvirt group
```
sudo usermod -G libvirt -a put-username-here
```

Restart to get all this working.

---

### Post by skywalker007 on 2023-03-21
Hi

Thanks, how do I uninstall the KVM application that is currently installed, as I suppose I need to start from the beginning to install an new one

---

### Post by skywalker007 on 2023-03-21
Hi Dennis

I did try it and unfortunately the error was the same.

---

### Post by Dennis N on 2023-03-21
I don't think you would need to reinstall anything if you have already installed the needed packages.

---

### Post by Dennis N on 2023-03-21
What packages did you install?

---

### Post by Dennis N on 2023-03-21
One other thing: You may need to enable virtualization in the BIOS or UEFI settings.

---

### Post by skywalker007 on 2023-03-21
I am trying to find KVM between all the installed applications but cannot find a application called KVM. Is it placed as a different name?

---

### Post by skywalker007 on 2023-03-21
Or possibly give me the command line to uninstall it. Because when I use [https://ubuntu.com/blog/kvm-hyphervisor](https://ubuntu.com/blog/kvm-hyphervisor) and go from that code, I also get a error. Could that be that there is one unsuccessful installation and I just want to try it from the beginning basically.

---

### Post by MAFoElffen on 2023-03-21
@et-all, take a breath... On mine:
```

mafoelffen@Mikes-B460M:~$ systemctl status libvirtd
&#9679; libvirtd.service - Virtualization daemon
     Loaded: loaded (/lib/systemd/system/libvirtd.service; enabled; vendor pres>
     Active: active (running) since Wed 2023-03-08 22:02:30 PST; 1 week 5 days >
TriggeredBy: &#9679; libvirtd.socket
             &#9679; libvirtd-ro.socket
             &#9679; libvirtd-admin.socket
       Docs: man:libvirtd(8)
             https://libvirt.org
   Main PID: 3508 (libvirtd)
      Tasks: 27 (limit: 32768)
     Memory: 49.6M
     CGroup: /system.slice/libvirtd.service
             &#9500;&#9472;3508 /usr/sbin/libvirtd
             &#9500;&#9472;3691 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/defa>
             &#9500;&#9472;3692 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/defa>
             &#9500;&#9472;3720 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/Isol>
             &#9500;&#9472;3758 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/Isol>
             &#9492;&#9472;3759 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/Isol>

Mar 21 09:39:41 Mikes-B460M dnsmasq-dhcp[3691]: DHCPREQUEST(virbr0) 192.168.122>
Mar 21 09:39:41 Mikes-B460M dnsmasq-dhcp[3691]: DHCPACK(virbr0) 192.168.122.185>
Mar 21 10:06:33 Mikes-B460M dnsmasq-dhcp[3691]: DHCPREQUEST(virbr0) 192.168.122>
Mar 21 10:06:33 Mikes-B460M dnsmasq-dhcp[3691]: DHCPACK(virbr0) 192.168.122.185>

```

Please do this and post the output of, within code tags:
```

sudo apt list --installed qemu-kvm libvirt-daemon-system virtinst libvirt-clients bridge-utils network-manager

```

---

### Post by Dennis N on 2023-03-21
_One more thing:_
check the groups your user belongs to: You need to belong to two groups to work with virt-manager: libvirt and kvm. Use this command:
```
dmn@Sydney:~$ groups
dmn adm cdrom sudo dip plugdev lpadmin sambashare **kvm libvirt**

```
I only mentioned libvirt in the previous post.
I looked back at my command history going way back, and I also used a different command than previously given to add myself to these groups:
```
sudo adduser dmn libvirt
sudo adduser dmn kvm  

```
I think the inability to connect may be due to lack of permissions. Being in the right group should fix that.

_Additional information:_
I checked my logs and found the reference to installing QEMU/KVM on Ubuntu 20.04 on Apr 30, 2021. I noted that I had trouble finding a definitive list of packages to install. Several guides were consulted, and all had different lists! My log entry says I installed the following, but some could be dependencies of others and did not need to be explicitly installed. I'm not sure which. 

qemu-kvm
libvirt-clients
libvirt-daemon-system
virtinst
virt-manager
libvirt-daemon
virt-viewer
libspice-server1
then add yourself the the libvirt and kvm groups

---

### Post by TheFu on 2023-03-21
> **skywalker007 said:**
>  
-- Just want to ask the following as well. They said I should check to make sure my laptop can support virtual maschines and make sure the answer is not 0 by using **[ egrep -c ‘(svm|vmx)’ /proc/cpuinfo ]**. What does it mean if mine comes back 4

It means you have 4 cores and they are all ready to use VT-x or AMDv hardware extensions for virtualization hardware support.  I.e., your bios is set fine.

Just came across this yesterday: [https://linuxhint.com/install-kvm-ubuntu-22-04/](https://linuxhint.com/install-kvm-ubuntu-22-04/) 
Seems reasonable, though I didn't follow it.  I've been using KVM/QEMU + libvirt + virt-manager for almost 15 yrs now.

Please stick with normal fonts here.

Did you post the actual error in the thread?  I didn't see it.

---

### Post by Dennis N on 2023-03-22
You indicate that you have "solved" this installation problem by adding the "solved" tag to your title. What was your solution? Did anything in the thread help you?

---

