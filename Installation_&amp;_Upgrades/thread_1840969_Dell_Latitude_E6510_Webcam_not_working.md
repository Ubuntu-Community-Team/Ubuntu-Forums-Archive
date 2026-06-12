---
title: "Dell Latitude E6510 Webcam not working"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by rajtendulkar on 2011-09-08
Dear Forum,

I am not able to figure out how to make webcam work on my Ubuntu 11.04.
I am not sure if there is any hardware problem.

I have Dell Latitude E6510 machine.

Here is the lsusb output - 

```

$ lsusb
Bus 002 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 003: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```here is the output of webcam command from terminal
```

$ webcam
reading config file: /home/rajtendulkar/.webcamrc
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no grabber device available

```can anyone please tell me how can I turn on the webcam?

Thank You,
Raj

---

