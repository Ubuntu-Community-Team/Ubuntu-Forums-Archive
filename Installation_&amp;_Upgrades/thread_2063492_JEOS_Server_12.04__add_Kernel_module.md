---
title: "JEOS Server 12.04 / add Kernel module"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by esa007 on 2012-09-27
Hello,

in have installed an Ubuntu Server  12.04 x64 ( server -kvm ) on top of that machine i add the packeg   "Virtual Machine Host" to use it as an hypervisor.

For the vm i use JEOS server 12.04 x64 ( vm2 )

Over an USB-Device i receive date and this should be vissibel on the vm2.

I configured the USB-Pathtrough vom server to vm and this works fine.

vm2:
```

  root@vm2:/# lsusb
  Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 001 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
  root@vm2:/# 
  root@vm2:/# usb-devices
  ....
  T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
  D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
  P:  Vendor=0403 ProdID=6001 Rev=06.00
  S:  Manufacturer=FTDI
  S:  Product=FT232R USB UART
  S:  SerialNumber=A4VPKI9K
  C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=250mA
  I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
  

```but there is nod device driver on the vm2 (JEOS)   Driver=(none)

when i switch the USB-Device to the server-kvm there is a device driver attached:
Driver=ftdi_sio
```

 
  T:  Bus=01 Lev=03 Prnt=03 Port=02 Cnt=03 Dev#=  6 Spd=12  MxCh= 0
  D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
  P:  Vendor=0403 ProdID=6001 Rev=06.00
  S:  Manufacturer=FTDI
  S:  Product=FT232R USB UART
  S:  SerialNumber=A1VPKIAV
  C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=250mA
  I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=ftdi_sio
  

```On the server there is a kernel module installed:
```

  # lsmod
  ...
  ftdi_sio               40715  2
  usbserial              47077  5 ftdi_sio
  ...
  

```
on JEOS ( vm2 ) it looks different:
```

 root@vm2:/# lsmod
  Module                  Size  Used by
  psmouse                97362  0
  serio_raw              13211  0
  virtio_balloon         13108  0
  lp                     17799  0
  parport                46562  1 lp
  floppy                 70365  0
  root@vm2:/#
  root@vm2:/#
   
  root@vm2:/# modprobe ftdi_sio
  FATAL: Module ftdi_sio not found.
   
  root@vm2:/# modprobe usbserial
  [FONT=&quot]FATAL: Module usbserial not found.[/FONT]

```

So i can passtrough the USB-Device but i can not use it on JEOS because of the missing kernel modules.
Is it possible to download the missing modules and install it to JEOS
or do i have to install a full server-version on my vm...

some ideas....??

---

