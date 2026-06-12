---
title: "MSI Wind Camera on Karmic"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by luis.nando on 2009-10-05
Community,

i have upgraded from jaunty to karmic beta on my msi wind u100, after that my built in camera stopped working. When i run lsusb i found:
```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 018: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I tested it with Skype and Cheese, both programs tells the same: no camera found!


What could be happening here? Any ideas?

Thanks in advance

---

### Post by kelpdip on 2009-10-06
I'm curious too but am not running the beta.

Go to Preferences --> Multimedia Systems Selector --> Video
What is shown in the input 'device' dropdown other than 'default'?
What happens when you click 'test'?

There is a webcam hotkey, it is fn+f6 on the u110. Try pressing this and clicking 'test'.

My u110 camera doesn't seem to show on lsusb for me either but it works fine in 8.10.

---

### Post by luis.nando on 2009-10-07
Also,

i did the last upgrade of kernel, and not only the camera don't work, but also my SD and USB ports...

i guess i'll wait for new development...

---

### Post by Zorael on 2009-10-08
This is either hardware failure, or part of a larger issue. I have an Advent 4211 which is a MSI Wind U100 rebrand with the same camera.

What seems to happen is that if the camera is active during boot, **or** whenever activating it, the kernel stops being able to manage that usb hub. Meaning, the system doesn't react at all when connecting new usb devices. (they don't even power up)

```
[  108.080149] usb 1-5: new high speed USB device using ehci_hcd and address 4                                    
[  108.256555] usb 1-5: configuration #1 chosen from 1 choice                                                     
[  108.301840] Linux video capture interface: v2.00                                                               
[  108.316404] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)                                         
[  108.334164] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input9            
[  108.334319] usbcore: registered new interface driver uvcvideo                                                  
[  108.334332] USB Video Class driver (v0.1.0)                                                                    
[  108.436914] ehci_hcd 0000:00:1d.7: force halt; handhake f8042024 00004000 00000000 -> -110                     
[  109.756735] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756749] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756759] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756768] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756776] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756782] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?                                    
[  109.756792] hub 1-0:1.0: cannot disable port 6 (err = -108)                                                    
[  109.756803] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756812] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756821] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756829] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756837] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756845] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?                                    
[  109.756856] hub 1-0:1.0: cannot disable port 6 (err = -108)                                                    
[  109.756867] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756876] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756884] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756892] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756902] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756909] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?                                    
[  109.756919] hub 1-0:1.0: cannot disable port 6 (err = -108)                                                    
[  109.756928] hub 1-0:1.0: cannot reset port 6 (err = -108)                                                      
[  109.756937] hub 1-0:1.0: cannot reset port 6 (err = -108)
[  109.756947] hub 1-0:1.0: cannot reset port 6 (err = -108)
[  109.756956] hub 1-0:1.0: cannot reset port 6 (err = -108)
[  109.756965] hub 1-0:1.0: cannot reset port 6 (err = -108)
[  109.756972] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  109.756983] hub 1-0:1.0: cannot disable port 6 (err = -108)
[  109.756994] hub 1-0:1.0: cannot disable port 6 (err = -108)
[  109.757365] hub 1-0:1.0: hub_port_status failed (err = -108)
```
Do a 'dmesg | grep -i usb' to see if you've gotten those messages, too.

1-5 is the camera and 1-6 is the card reader.

It works fine in Windows. BUT, when I tried it on a Jaunty live usb it didn't work there either. So either the usb or camera driver in Karmic changed some setting in the camera hardware itself, or it's (partial) hardware failure that the kernel can't cope with.

---

### Post by Zorael on 2009-10-08
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352)

So at least we're not alone, yay.

---

