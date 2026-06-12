---
title: "Disk time 100% Ubuntu 18.04.1 installation"
date: 2018-10-21
forum: Installation &amp; Upgrades
---

### Post by chrie2 on 2018-10-21
[FONT=inherit]As student I can use the VMware Workstation 14 for free.[/FONT]
[FONT=inherit]When I try to install ubuntu 18.04.1-desktop the disk time of my windows 10 host machine goes to 100% immediately the Ubuntu installation wizard start. When I fast enough I can only select the keyboard layout and than the VM hangs.[/FONT]
[FONT=inherit]The Process VMware Workstation VMX consume all of the disk time.[/FONT]
[FONT=inherit]I tried to change the disk settings that the vm does an instant full allocation.[/FONT]
[FONT=inherit]Other OS also the ubuntu 18.04 server edition install and work without problems.

[/FONT]


[COLOR=#666666][FONT=proxima-nova]Acer [COLOR=#222222][FONT=Roboto]Swift[/FONT][/COLOR][COLOR=#222222][FONT=Roboto] 3 SF315-52.[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#666666][FONT=proxima-nova][COLOR=#222222][FONT=Roboto]No other VMs are running.[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#666666][FONT=proxima-nova][COLOR=#222222][FONT=Roboto]I run in this problem also with the Ubuntu live option (test ubuntu) to try it only.

So far I get now answer from the VMware community thus I try it here.  [https://communities.vmware.com/message/2810092#2810092](https://communities.vmware.com/message/2810092#2810092)[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by mastablasta on 2018-10-23
you can try virtualbox instead. it is also free to use.

alternately install ubuntu server and then install the desktop on it.

```
sudo apt-get ubuntu-desktop
```

perhaps that would work. though if the issue is with WM or it's use of GPU (?! - used by desktop)  it could be why it is hanging.

---

