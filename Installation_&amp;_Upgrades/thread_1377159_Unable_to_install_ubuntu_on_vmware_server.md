---
title: "Unable to install ubuntu on vmware server"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by kushal154 on 2010-01-10
Hi 

I have downloaded vmware server 1.0.10 and ubuntu 9.10. Installed vmware server on my windows xp and created the disk space for Ubuntu. Now when i am running the virtual machine using the above downloaded iso image, I get the installation window. I selected 'Install Ubuntu' option and hit Enter. But after this nothing is happening. It's just giving me black window.

Here's the log:

Jan 10 09:54:11: vmx| Log for VMware Server pid=1708 version=1.0.10 build=build-203137 option=Release
----
----
Jan 10 09:54:12: vmx| VUI: A new VMControl client connected.
Jan 10 09:54:12: vcpu-0| PShare: enabled 1, scanRate 32, checkRate 16
Jan 10 09:54:12: vcpu-0| guestCpuFeatures = 0x9871fe03
Jan 10 09:54:12: vcpu-0| Init modules.
Jan 10 09:54:12: vcpu-0| CPU reset: hard
Jan 10 09:54:12: vmx| VNET: Notification enabled for Ethernet0
Jan 10 09:54:12: vcpu-0| INTELRDMSR(0x8b) = 0x00000a0700000000
Jan 10 09:54:12: vcpu-0| INTELRDMSR(0x17) = 0x001c000098f48a25
Jan 10 09:54:12: vmx| IPC version negotiation version: VMX returning 2.1 to servercontrol
Jan 10 09:54:12: vmx| IPC vmcontrol-temp version: VMX returning 11.4 to servercontrol that tried 11.4
Jan 10 09:54:12: vcpu-0| sz=3108832
Jan 10 09:54:12: vcpu-0| vmm32 initialized: Releasebuild-203137. cflags: 0x08000002.01c41400.00000150
Jan 10 09:54:12: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0x0) and 0xec000000(0x0)
Jan 10 09:54:12: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Jan 10 09:54:12: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Jan 10 09:54:12: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Jan 10 09:54:12: vcpu-0| SVGA: Registering IOSpace at 0x1060 (0x0)
Jan 10 09:54:12: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Jan 10 09:54:12: mks| Ignoring update request in VGA_Expose (mode change pending).
Jan 10 09:54:14: vcpu-0| DISKUTIL: scsi0:0 : geometry=1044/255/63
Jan 10 09:54:15: vcpu-0| BIOS-UUID is 56 4d 32 03 67 5e 0d 8b-93 c0 e8 0c 7c c2 5d fc
Jan 10 09:54:15: vcpu-0| DISKUTIL: scsi0:0 : toolsVersion = 0
Jan 10 09:54:15: vcpu-0| DISKUTIL: Offline toolsVersion = 0
Jan 10 09:54:15: mks| VNCENCODE 1 encoding mode change: (720x400x24depth,32bpp)
Jan 10 09:54:17: mks| VNCENCODE 1 encoding mode change: (640x480x16depth,16bpp)
Jan 10 09:54:26: vcpu-0| Unknown int 10h func 0x0000
Jan 10 09:54:26: mks| SOCKET 1 new update req with non-empty pending: logical error on server/client?
Jan 10 09:54:26: mks| HostOps hideCursor before defineCursor!
Jan 10 09:54:26: mks| VNCENCODE 1 encoding mode change: (720x400x24depth,32bpp)
Jan 10 09:54:26: vcpu-0| X86Fault_Warning: vmcore/vmm32/bt/btpriv.c:1353: cs:eip=0x60:0xc0127073 fault=13
Jan 10 09:56:30: mks| MKS set guest selection request with invalid state 2
Jan 10 10:04:02: mks| MKS set guest selection request with invalid state 2
Jan 10 10:04:12: vmx| TOOLS setting the tools version to '0'
Jan 10 10:16:46: mks| MKS set guest selection request with invalid state 2

Really appreciate some help.

Thanks.

---

### Post by SecretCode on 2010-01-11
Nothing concrete, just ... have you clicked in the window and moved the mouse? The vm may have gone to power-saving screen-blanking.

And ... have you considered VirtualBox?

---

### Post by kushal154 on 2010-01-12
It worked with vmware just after I sent this post. I also tried with virtualbox and it worked like a charm. Thanks for the advice.

---

