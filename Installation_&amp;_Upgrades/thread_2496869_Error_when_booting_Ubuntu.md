---
title: "Error when booting Ubuntu"
date: 2024-04-15
forum: Installation &amp; Upgrades
---

### Post by mirek-kulda on 2024-04-15
Hi,

I want to install/try Ubuntu 24.04 (or any older  version of Ubuntu). I am  using an HP Spectre x360 14-eu0000nc. An error occurs when booting (after typing Try ubuntu or Install safe graphics). Is there smth I can do about it? 

Thanks!

```
usb 4-1: Product: Mass Storage Device
usb 4-1: Manufacturer: JetFlash
usb 4-1: SerialNumber: 3E6F9AB3HXXXXXXX
i2c_hid i2c-ELAN0732:00: [E4:5E4-9DB9-A0A4D34F6226]: i2c_hid_get_input: incomplete report (63/64)
input:  ELAN0732:00 04F3:22E1 Touchpad as  /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN0732:00/0018:04F3:22E1.0001/input/input7
input:  ELAN0732:00 04F3:22E1 Touchpad as  /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN0732:00/0018:04F3:22E1.0001/input/input8
input:  ELAN0732:00 04F3:22E1 Touchpad as  /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN0732:00/0018:04F3:22E1.0001/input/input9
input:  ELAN0732:00 04F3:22E1 Touchpad as  /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN0732:00/0018:04F3:22E1.0001/input/input10
input:  ELAN0732:00 04F3:22E1 Touchpad as  /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN0732:00/0018:04F3:22E1.0001/input/input11
input:  ELAN0732:00 04F3:22E1 Keyboard as  /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN0732:00/0018:04F3:22E1.0001/input/input12
input:  ELAN0732:00 04F3:22E1 Mouse as  /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN0732:00/0018:04F3:22E1.0001/input/input13
input:  ELAN0732:00 04F3:22E1 Mouse as  /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN0732:00/0018:04F3:22E1.0001/input/input14
input:  ELAN0732:00 04F3:22E1 Mouse as  /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN0732:00/0018:04F3:22E1.0001/input/input16
input:  ELAN0732:00 04F3:22E1 Mouse as  /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN0732:00/0018:04F3:22E1.0001/input/input17
hid-generic 0018:04F3:22E1.0002: input,hidraw1: I2C HID v1.00 Keyboard [ELAN0732:00 04F3:22E1] on i2c-ELAN0732:00
hid-generic 0018:04F3:22E1.0002: input,hidraw2: I2C HID v1.00 Device [ELAN0732:00 04F3:22E1] on i2c-ELAN0732:00
hid-generic 001F:8087:0AC2.0004: hidraw3: SENSOR_HUB_HID v2.00 Device [hid-ishtp 8087:0AC2] on 
hid-generic 001F:8087:0AC2.0005: hidraw4: SENSOR_HUB_HID v2.00 Device [hid-ishtp 8087:0AC2] on 
hid-generic 001F:8087:0AC2.0006: hidraw5: SENSOR_HUB_HID v2.00 Device [hid-ishtp 8087:0AC2] on 
hid-generic 001F:8087:0AC2.0007: hidraw6: SENSOR_HUB_HID v2.00 Device [hid-ishtp 8087:0AC2] on 
hid-generic 001F:8087:0AC2.0008: hidraw7: SENSOR_HUB_HID v2.00 Device [hid-ishtp 8087:0AC2] on 
hid-sensor-hub 001F:8087:0AC2.0003: hidraw2: SENSOR_HUB_HID v2.00 Device [hid-ishtp 8087:0AC2] on 
hid-sensor-hub 001F:8087:0AC2.0004: hidraw3: SENSOR_HUB_HID v2.00 Device [hid-ishtp 8087:0AC2] on 
hid-sensor-hub 001F:8087:0AC2.0005: hidraw4: SENSOR_HUB_HID v2.00 Device [hid-ishtp 8087:0AC2] on 
hid-sensor-hub 001F:8087:0AC2.0006: hidraw5: SENSOR_HUB_HID v2.00 Device [hid-ishtp 8087:0AC2] on 
hid-sensor-hub 001F:8087:0AC2.0007: hidraw6: SENSOR_HUB_HID v2.00 Device [hid-ishtp 8087:0AC2] on 
hid-sensor-hub 001F:8087:0AC2.0008: hidraw7: SENSOR_HUB_HID v2.00 Device [hid-ishtp 8087:0AC2] on 
raiddisk: avx2x4 gen() 6805 MiB/s
raiddisk: avx2x2 gen() 6805 MiB/s
raiddisk: avx2x1 gen() 6805 MiB/s
raiddisk: using algorithm avx2x2_gen() 6805 MiB/s
raiddisk: using algorithm avx2x4_gen() 8005 MiB/s
raiddisk: using avx2 recovery algorithm
raiddisk: automatically using best checksumming function avx
async_tx: api initialized (async)
stdin: Invalid argument
stdin: Invalid argument
stdin: Invalid argument
stdin: Invalid argument
stdin: Invalid argument
stdin: Invalid argument
```

---

### Post by ActionParsnip on 2024-04-15
[https://askubuntu.com/questions/1393957/stdin-invalid-argument](https://askubuntu.com/questions/1393957/stdin-invalid-argument)

Do you have a USB storage attached? If so, try booting without it (if possible)

---

### Post by mirek-kulda on 2024-04-16
I tried just about everything. Boot from USB, boot from disk with ubuntu installed, boot from CD, change ubuntu boot settings, disconnect and connect usb, connect usb drive via usb2 hub. I had practically everything disabled in the bios at one point.

---

### Post by mirek-kulda on 2024-04-18
I think this is an incompatible hardwere, also the Debian installer freezes on "Looking for hardware". Ubuntu won't run on this laptop yet...

---

