---
title: "Xenial Installation is ignoring kickstart file configurations during install"
date: 2019-05-28
forum: Installation &amp; Upgrades
---

### Post by maretodoric on 2019-05-28
Hello everyone.

I have rather specific and weird issue when trying to install Ubuntu using virt-install tool with kickstart file. Basically, i will create a VM like this:

```
virt-install --connect=qemu+ssh://hypervisor/system \
--name=testytest \
--hvm \
--graphics vnc \
--disk path=/dev/mapper/testytest,bus=virtio,cache=none \
--vcpus 1 \
--ram=2048 \
--location=http://rs.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/installer-amd64 \
--extra-args "net.ifnames=0 biosdevname=0 ksdevice=eth1 ks=http://kickstart.local.server/ks/testytest.cfg" \
--network bridge=br6,model=virtio \
--network bridge=br7,model=virtio \
--boot hd,cdrom,menu=on \
--os-type=linux \
--os-variant=ubuntuquantal \
--metadata description="LinuxTim test" \
--noreboot
```

Kickstart file, at least header is like this:
```
#########################################
##   Ubuntu kickstart script - za VPS  ##
#########################################

install
url --url="http://rs.archive.ubuntu.com/ubuntu/"
ntext
keyboard --vckeymap=us --xlayouts='us'
lang en_US.UTF-8
poweroff

network --device=eth0 --bootproto=static --ip=10.8.0.11 --netmask=255.255.0.0 --hostname=testytest --nameserver 10.0.0.1,10.0.0.2 --gateway=10.8.0.65
network --bootproto=dhcp --device=eth1

```

So it should do this:
I set two NICs for VPS, br6 which is isolated network (and should be represented as eth0 because of append tags), therefore 10.8.x.x IP address
And br7 (which should be eth1) which is NATted network where we have DHCP server and it's allowed to go online. To fetch kickstart script and install ubuntu from sources.

But this happens:
I issue script to install VPS, it will download initrd and kernel and transfer it to KVM Hypervisor. Installation will boot, it will obtain an IP address from DHCP and will download the kickstart file
But there we have issue, even though in kickstart i have defined eth0 for an IP address and eth1 for DHCP, somehow, don't know how, installer sets eth1 with an IP address that eth0 should use, and eth0 has nothing.

I see this because i receive an error during installation that "Bad archive mirror" and when i go to shell, i issue "ip addr" and see that eth1 have IP address when it shouldn't.

If i would to issue dhclient eth1, it will obtain an IP back from DHCP and i can continue without issues.
Does anyone know why would this happen and how can i prevent it ?

Beside that, i have another issue with kickstart being completely ignored

I have following partitions set in kickstart like this

```
bootloader --location=mbr
zerombr yes
clearpart --all --initlabel
part swap --size 2048 --ondisk vda
part / --fstype ext4 --grow --asprimary --ondisk vda


```

So it should create first partition as swap with 2048MB space and another one with full space.
So not only will it pause installation at that point and ask me to perform changes to drive partitions, which are already specified, but what happens is it will want to create first partition as primary and 5th partition as SWAP with only 1GB. Why? :/

Any help would be appreciated.

Full kickstart file if needed is this

```
#########################################
##   Ubuntu kickstart script - za VPS  ##
#########################################

install
# Uncommentuj cdrom i commentuj url ako se reinstalira
# URL se koristi za automatizaciju instalacije novog VPS-a
#cdrom
url --url="http://rs.archive.ubuntu.com/ubuntu/"
ntext
keyboard --vckeymap=us --xlayouts='us'
lang en_US.UTF-8
poweroff

network --device=eth0 --bootproto=static --ip=10.8.0.11 --netmask=255.255.0.0 --hostname=testytest --nameserver 10.0.0.1,10.0.0.2 --gateway=10.8.0.65
network --bootproto=dhcp --device=eth1

user --disabled
rootpw --iscrypted $6$4LO0JFXop7vuq6IC$LV2wWsP2P5T3daqA1757ddEgsorrEfkOhM25z4avcrV3mI21CMmuiryi4CdOeGZaJsky44081fJjycDWlezOG.

firstboot --disabled
firewall --disabled
selinux --disabled
authconfig --enableshadow --passalgo=sha512
timezone Europe/Belgrade --utc

bootloader --location=mbr
zerombr yes
clearpart --all --initlabel
part swap --size 2048 --ondisk vda
part / --fstype ext4 --grow --asprimary --ondisk vda

skipx

%packages
ubuntu-cloudimage-keyring
ubuntu-core-launcher
ubuntu-keyring
ubuntu-minimal
ubuntu-release-upgrader-core
ubuntu-server
ubuntu-standard
bash-completion
openssh-server
vim
mc
net-tools
screen
curl
wget
nagios-plugins
snmp
snmpd

```

Just to add!
After installation, IP address that was in kickstart set for eth0, definitely stays in eth1 like during installation, and --nameserver directive is ignored, DNS servers are not listed.

---

### Post by maretodoric on 2019-06-05
So.. Noone has any ideas regarding this?

---

