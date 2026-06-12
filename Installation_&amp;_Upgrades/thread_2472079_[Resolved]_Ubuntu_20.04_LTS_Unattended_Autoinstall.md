---
title: "[Resolved] Ubuntu 20.04 LTS Unattended Autoinstall Stuck at Interactive Dialog"
date: 2022-02-16
forum: Installation &amp; Upgrades
---

### Post by tacoeater on 2022-02-16
Hi there. We are attempting to build VirtualBox images automatically over AWS EC2 agent pool. So far I have successfully deployed the build stack locally with packer.io and autoinstall (subiquity) scheme, and the biggest challenge is to pull out build console log from the headless remote server. Therefore I started with serial console:

packer json manifest:
```

      "type": "virtualbox-iso",
      "boot_command": [
        "<enter><enter><f6><esc><wait> ",
        "autoinstall ds=nocloud-net;s=http://{{ .HTTPIP }}:{{ .HTTPPort }}/ ",
         "console=ttyS0,115200n8 DEBIAN_FRONTEND=noninteractive noshell",
        "<enter><wait>"
      ],
      "vboxmanage": [
        ["modifyvm", "{{.Name}}", "--memory", "1024"],
        ["modifyvm", "{{.Name}}", "--uart1", "0x3F8", "4"],
        ["modifyvm", "{{.Name}}", "--uartmode1", "file", "/tmp/{{.Name}}.log"]
      ],
...

```

user-data:
```

#cloud-config
autoinstall:
  version: 1
  locale: en_US.UTF-8
  keyboard:
      layout: en
      variant: us
  network:
    network:
      version: 2
      ethernets:
        ens32:
          dhcp4: true
          dhcp-identifier: mac
        enp0s3:
          dhcp4: true
          dhcp-identifier: mac
  reporting:
    builtin:
      type: none
  identity:
    hostname: ***
    password: ***
    username: ***
  ssh:
    install-server: true
    allow-pw: true

```

The build hangs, and when I looked into the build log dumped from VirtualBox, I got this message...
```

Ubuntu 20.04.3 LTS ubuntu-server ttyS0




connecting...



================================================================================
  Serial                                                              [ Help ]
================================================================================


  As the installer is running on a serial console, it has started in basic
  mode, using only the ASCII character set and black and white colours.

  If you are connecting from a terminal emulator such as gnome-terminal that
  supports unicode and rich colours you can switch to "rich mode" which uses
  unicode, colours and supports many languages.

  You can also connect to the installer over the network via SSH, which will
  allow use of rich mode.


                          [ Continue in rich mode  > ]
                          [ Continue in basic mode > ]
                          [ View SSH instructions    ]

```

Apparently there is no way for me to hit enter to a headless, (supposed to be) fully automated process. How may I bypass this dialog? Both boot args (DEBIAN_FRONTEND=noninteractive noshell) and the reporting section in user-data cannot get over this dialog. However this won't show up and interrupt my local build, so I'm confused why would this dialog pop out and block the build process on Amazon EC2 servers, was it because a vga adapter presents in my local environment?

---

### Post by tacoeater on 2022-02-16
Turns out for some reason, the http file server is not locating the correct path so that the installer cannot access user-data properly

---

