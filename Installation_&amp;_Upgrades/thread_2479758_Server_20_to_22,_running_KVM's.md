---
title: "Server 20 to 22, running KVM's"
date: 2022-10-05
forum: Installation &amp; Upgrades
---

### Post by thebearak on 2022-10-05
My set up is a Core i7 Quad core.  I mostly set this up for storage, so it is gigantic case with 2 RAID arrays in it.   One is a 2 x 4 TB (Raid0) and the other is/was a 8 x 2 TB (Raid5) and it boots from a 1TB SSD (non-raid).  The Raids are Software Raids (mdadm) are using the motherboard SATA ports.

I had this set up for a while running Ubuntu Server 20.xx for quite some time now and of course, everything was running smooth.    When it bugged me about upgrading to 22, I finally gave in and tried to do the upgrade using the "do-release-upgrade".  Well, for some reason, the upgrade decided to wipe one of the RAID disk in the 8x2 Raid and put the upgrade on there.  Booting back into the SSD (20) I was unable to rebuild the RAID 5, so I lost my data on the RAID 5.  Not a big deal as I have backups.

I then un-plugged all the drives except the SSD and did a clean install on the disk using 22.  Installed KVM, did most of the configuration.  Then plugged the drives back in.  Kept the 2x4GB Raid as is and it works fine.  Tried connecting up the 8 x 2 GB RAID and completely started from scratch with it.   After I got it all back up and configured, the 8x2TB was having issues, maybe a bad drive, but it would not tell me which drive.  It would just give a generic error for the whole Raid and then lock up the server.   Decided to just remove that RAID and break it down to individual disk using LVM.

Now, with that all configured, I can't get virt-manager to launch at all.   When trying from a remote computer, it will just act like I didn't type anything at all.

method from remote Ubuntu Desktop:

# ssh -X 10.10.10.5

login:  NAME
Pass:  PASS

server: $ virt-manager

then nothing.

Just for a check, typing "xclock" brings up the clock just fine.

I've tried reinstalling the virt-manager on the server.   No change.

---

### Post by #&amp;thj^% on 2022-10-05
might not hurt to see the .xml file as well:
```
<domain type="kvm">
  <name>ubuntu22.04</name>
  <uuid>61380d5c-acd6-4bbb-98ee-f9435a1a2d0d</uuid>
  <metadata>
    <libosinfo:libosinfo xmlns:libosinfo="http://libosinfo.org/xmlns/libvirt/domain/1.0">
      <libosinfo:os id="http://ubuntu.com/ubuntu/22.04"/>
    </libosinfo:libosinfo>
  </metadata>
  <memory unit="KiB">4194304</memory>
  <currentMemory unit="KiB">4194304</currentMemory>
  <vcpu placement="static">4</vcpu>
  <os>
    <type arch="x86_64" machine="pc-q35-7.1">hvm</type>
    <boot dev="hd"/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <vmport state="off"/>
  </features>
  <cpu mode="host-passthrough" check="none" migratable="on"/>
  <clock offset="utc">
    <timer name="rtc" tickpolicy="catchup"/>
    <timer name="pit" tickpolicy="delay"/>
    <timer name="hpet" present="no"/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <pm>
    <suspend-to-mem enabled="no"/>
    <suspend-to-disk enabled="no"/>
  </pm>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type="file" device="disk">
      <driver name="qemu" type="qcow2" discard="unmap"/>
      <source file="/var/lib/libvirt/images/ubuntu22.04.qcow2"/>
      <target dev="vda" bus="virtio"/>
      <address type="pci" domain="0x0000" bus="0x04" slot="0x00" function="0x0"/>
    </disk>
    <disk type="file" device="cdrom">
      <driver name="qemu" type="raw"/>
      <target dev="sda" bus="sata"/>
      <readonly/>
      <address type="drive" controller="0" bus="0" target="0" unit="0"/>
    </disk>
    <controller type="usb" index="0" model="qemu-xhci" ports="15">
      <address type="pci" domain="0x0000" bus="0x02" slot="0x00" function="0x0"/>
    </controller>
    <controller type="pci" index="0" model="pcie-root"/>
    <controller type="pci" index="1" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="1" port="0x10"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x0" multifunction="on"/>
    </controller>
    <controller type="pci" index="2" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="2" port="0x11"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x1"/>
    </controller>
    <controller type="pci" index="3" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="3" port="0x12"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x2"/>
    </controller>
    <controller type="pci" index="4" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="4" port="0x13"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x3"/>
    </controller>
    <controller type="pci" index="5" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="5" port="0x14"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x4"/>
    </controller>
    <controller type="pci" index="6" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="6" port="0x15"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x5"/>
    </controller>
    <controller type="pci" index="7" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="7" port="0x16"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x6"/>
    </controller>
    <controller type="pci" index="8" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="8" port="0x17"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x7"/>
    </controller>
    <controller type="pci" index="9" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="9" port="0x18"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x0" multifunction="on"/>
    </controller>
    <controller type="pci" index="10" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="10" port="0x19"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x1"/>
    </controller>
    <controller type="pci" index="11" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="11" port="0x1a"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x2"/>
    </controller>
    <controller type="pci" index="12" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="12" port="0x1b"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x3"/>
    </controller>
    <controller type="pci" index="13" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="13" port="0x1c"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x4"/>
    </controller>
    <controller type="pci" index="14" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="14" port="0x1d"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x5"/>
    </controller>
    <controller type="sata" index="0">
      <address type="pci" domain="0x0000" bus="0x00" slot="0x1f" function="0x2"/>
    </controller>
    <controller type="virtio-serial" index="0">
      <address type="pci" domain="0x0000" bus="0x03" slot="0x00" function="0x0"/>
    </controller>
    <interface type="direct">
      <mac address="52:54:00:0b:a0:40"/>
      <source dev="eno1" mode="bridge"/>
      <model type="virtio"/>
      <address type="pci" domain="0x0000" bus="0x01" slot="0x00" function="0x0"/>
    </interface>
    <serial type="pty">
      <target type="isa-serial" port="0">
        <model name="isa-serial"/>
      </target>
    </serial>
    <console type="pty">
      <target type="serial" port="0"/>
    </console>
    <channel type="unix">
      <target type="virtio" name="org.qemu.guest_agent.0"/>
      <address type="virtio-serial" controller="0" bus="0" port="1"/>
    </channel>
    <channel type="spicevmc">
      <target type="virtio" name="com.redhat.spice.0"/>
      <address type="virtio-serial" controller="0" bus="0" port="2"/>
    </channel>
    <input type="tablet" bus="usb">
      <address type="usb" bus="0" port="1"/>
    </input>
    <input type="mouse" bus="ps2"/>
    <input type="keyboard" bus="ps2"/>
    <graphics type="spice" autoport="yes">
      <listen type="address"/>
      <image compression="off"/>
    </graphics>
    <sound model="ich9">
      <address type="pci" domain="0x0000" bus="0x00" slot="0x1b" function="0x0"/>
    </sound>
    <audio id="1" type="spice"/>
    <video>
      <model type="qxl" ram="65536" vram="65536" vgamem="16384" heads="1" primary="yes"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x0"/>
    </video>
    <redirdev bus="usb" type="spicevmc">
      <address type="usb" bus="0" port="2"/>
    </redirdev>
    <redirdev bus="usb" type="spicevmc">
      <address type="usb" bus="0" port="3"/>
    </redirdev>
    <memballoon model="virtio">
      <address type="pci" domain="0x0000" bus="0x05" slot="0x00" function="0x0"/>
    </memballoon>
    <rng model="virtio">
      <backend model="random">/dev/urandom</backend>
      <address type="pci" domain="0x0000" bus="0x06" slot="0x00" function="0x0"/>
    </rng>
  </devices>
</domain>

```
I set this one up to play with, so of course don't copy mine. (Just a friendly warning if not known already)

---

### Post by thebearak on 2022-10-05
Thanks, something I noticed was that gnome-sessions was having a lot of errors.   I killed the process (GDM3) and the virt-manager started working again.  Must be some configuration issue with the display manager.   I'll explore that a bit more.

---

### Post by MAFoElffen on 2022-10-06
Ensure the status of the "lib-virtd" daemon is enabled and running
```

mafoelffen@ubuntu:~$ sudo systemctl status libvirtd
[sudo] password for mafoelffen: 
&#9679; libvirtd.service - Virtualization daemon
     Loaded: loaded (/lib/systemd/system/libvirtd.service; enabled; vendo>
     Active: active (running) since Thu 2022-09-29 16:13:16 PDT; 6 days a>
TriggeredBy: &#9679; libvirtd-admin.socket
             &#9679; libvirtd-ro.socket
             &#9679; libvirtd.socket
       Docs: man:libvirtd(8)
             https://libvirt.org
   Main PID: 1127 (libvirtd)
      Tasks: 21 (limit: 32768)
     Memory: 13.4M
        CPU: 12min 220ms
     CGroup: /system.slice/libvirtd.service
             &#9500;&#9472;1127 /usr/sbin/libvirtd
             &#9500;&#9472;1321 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmas>
             &#9492;&#9472;1322 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmas>

Oct 02 10:03:54 ubuntu dnsmasq[1321]: reading /etc/resolv.conf
Oct 02 10:03:54 ubuntu dnsmasq[1321]: using nameserver 127.0.0.53#53
Oct 02 11:57:51 ubuntu dnsmasq[1321]: reading /etc/resolv.conf
Oct 02 11:57:51 ubuntu dnsmasq[1321]: using nameserver 127.0.0.53#53
Oct 02 11:57:51 ubuntu dnsmasq[1321]: reading /etc/resolv.conf
Oct 02 11:57:51 ubuntu dnsmasq[1321]: using nameserver 127.0.0.53#53
Oct 02 11:57:57 ubuntu dnsmasq[1321]: reading /etc/resolv.conf
Oct 02 11:57:57 ubuntu dnsmasq[1321]: using nameserver 127.0.0.53#53
Oct 02 11:57:57 ubuntu dnsmasq[1321]: reading /etc/resolv.conf
Oct 02 11:57:57 ubuntu dnsmasq[1321]: using nameserver 127.0.0.53#53
lines 8-27/27 (END)

```
And that your userid is part of the 'kvm' and 'libvirt' groups:
```

mafoelffen@ubuntu:~$ groups
mafoelffen sudo [COLOR=#ff0000]kvm libvirt[/COLOR] libvirt-qemu

```
Enabling the daemon, and assigning a user to those two groups are two required steps needs after just installing kvm/qemu...

---

### Post by thebearak on 2022-10-13
It all checked out and status was okay.  I put a different desktop environment on it (plain old X) and it works fast and just fine.   Some sort of conflict with Gnome, which might be solved "automatically" if Gnome is installed before qemu.

I was having some other compatibility issues with version 22 and software I was running.  Had to revert back to 20.x

---

### Post by MAFoElffen on 2022-10-14
Hmmmmm. I tested and and ran Ubuntu 22.04 and KVM/QEMU 6.x since the start in DEV. "6.0" was released back in August of last year. It runs great.

I would suspect it is more an issue of the X forwarding. Instead, why are you not using Network Manager Locally, and doing the Qemu:/// connection remotely through Network-Manager? That is what I and most people do... (???)

---

### Post by TheFu on 2022-10-14
> **MAFoElffen said:**
>  doing the Qemu:/// connection remotely through Network-Manager? That is what I and most people do... (???)

This is how I do it ----- well, ssh+qemu --- but the same. Though I to run virt-manager remotely from time to time, but not on 22.04.  I removed the ability for MOTD and apt nagging on all my systems long ago.  I see only the "Last login:" line, nothing else.

I did an upgrade (fresh OS install + restore of backup settings, data, and packages) of a KVM system from 18.04 to 20.04 last month. All the old VMs are running perfect, but new VMs refuse to start.  I haven't researched it to know the cause, but suspect it is that libvirt defaults were changed to expect UEFI, which I don't use in VMs.

---

### Post by MAFoElffen on 2022-10-16
I suspect it was the OP trying to do X-Forwarding over a default install of Ubuntu, and the default setting is set to use Wayland instead of Xorg....

---

