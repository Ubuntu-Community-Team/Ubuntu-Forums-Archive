---
title: "How can I script the setup of disposable virtual guests?"
date: 2019-05-27
forum: Installation &amp; Upgrades
---

### Post by pbwolf on 2019-05-27
I'm using Ubuntu 18.04 because it is LTS.  I would like to automate the setup of a virtual guest with a desktop, a web browser (all patched and up-to-date), and an auto-login user account that should change its password on first login.

virt-builder looks very promising, but I ran into problems.  First, I tried to make an Ubuntu guest image (Sad to say, the latest Ubuntu it offers is 18.04):

```
sudo virt-builder ubuntu-18.04 -o ubuntu-18.04 --network --size 21G --smp 4 --install 'gnome-shell' --install 'ubuntu-gnome-desktop'
```

But it emitted a ton of error messages, ending with these:

```
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch/usb-modeswitch_2.5.2+repack0-2ubuntu1_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-legacy_1.19.6-1ubuntu4_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
virt-builder: error: 
        export DEBIAN_FRONTEND=noninteractive
        apt_opts='-q -y -o Dpkg::Options::=--force-confnew'
        apt-get $apt_opts update
        apt-get $apt_opts install 'gnome-shell'
      : command exited with an error
```

I fetched some of the failed deb URLs with curl all right, so virt-builder is having a more exotic kind of trouble. Well, I don't especially require Ubuntu in the guest, so next I tried to make a Fedora 30 guest image:

```
sudo virt-builder fedora-30 -o fedora-30 --network --size 21G --smp 4 --append-line /etc/dnf/dnf.conf:zchunk=False --install '@Fedora Workstation' --install '@KDE (K Desktop Environment)'
```

But there was trouble of a different nature:

```
Failed to synchronize cache for repo 'fedora-modular'
Error: Failed to synchronize cache for repo 'fedora-modular'
virt-builder: error: dnf -y install '@Fedora Workstation': command exited
```

Finally, I tried Fedora 29, with the same outcome as Fedora 30.

How do folks automate the installation of a virtual guest of Ubuntu 18.04?

---

### Post by TheFu on 2019-05-28
I don't make disposable desktops, but perhaps these search terms will help:

Ubuntu OEM Install [https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
vagrant [https://www.vagrantup.com/intro/getting-started/provisioning.html](https://www.vagrantup.com/intro/getting-started/provisioning.html)
virt-install [https://manpages.ubuntu.com/manpages/bionic/man1/virt-install.1.html](https://manpages.ubuntu.com/manpages/bionic/man1/virt-install.1.html)
ansible [https://www.ansible.com/use-cases/provisioning](https://www.ansible.com/use-cases/provisioning) / puppet / chef / CFengine / .... 

I might need a fresh desktop for some temporary need once every 6 months, so virt-manager is fine.
If I needed to have 25+ created and destroyed daily, I'd probably setup an LVM LV with an Ubuntu OEM Install, then clone that LV as needed for new VMs, have a tiny script that had virsh using a template and sed for the VM definition and startup with an email sending the connection information to the requester and some DB somewhere for my records.
If any customization was needed, I'd probably use Ansible.

---

