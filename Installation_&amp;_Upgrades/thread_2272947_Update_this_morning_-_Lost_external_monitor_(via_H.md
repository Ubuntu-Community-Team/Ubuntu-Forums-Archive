---
title: "Update this morning - Lost external monitor (via HDMI)"
date: 2015-04-09
forum: Installation &amp; Upgrades
---

### Post by joseph57 on 2015-04-09
I logged in this morning and my OS told me there were software updates available. I ran the updates and rebooted and lost my external monitor. I am running Ubuntu 14 on an HP Probook 4545s with Xubuntu desktop. I dug through a bunch of threads and the basics of what I found were I had to figure out what package caused the loss and revert back to the older version - I have no idea how to do this. Any advice / help how to get my monitor back??

I ran  tail -n25 /var/log/apt/history.log    and got:
                                                     Start-Date: 2015-04-09  11:30:54            
            Commandline: aptdaemon role='role-commit-packages' sender=':1.156'            
            Install: linux-image-3.16.0-34-generic:amd64 (3.16.0-34.45~14.04.1), linux-headers-3.16.0-34:amd64 (3.16.0-34.45~14.04.1), linux-headers-3.16.0-34-generic:amd64 (3.16.0-34.45~14.04.1), linux-image-extra-3.16.0-34-generic:amd64 (3.16.0-34.45~14.04.1)            
                        Upgrade: libsystemd-login0:amd64 (204-5ubuntu20.10, 204-5ubuntu20.11), systemd-services:amd64 (204-5ubuntu20.10, 204-5ubuntu20.11), linux-image-generic-lts-utopic:amd64 (3.16.0.33.26, 3.16.0.34.27), libsystemd-daemon0:amd64 (204-5ubuntu20.10, 204-5ubuntu20.11), libgudev-1.0-0:amd64 (204-5ubuntu20.10, 204-5ubuntu20.11), libpolkit-agent-1-0:amd64 (0.105-4ubuntu2, 0.105-4ubuntu2.14.04.1), libpam-systemd:amd64 (204-5ubuntu20.10, 204-5ubuntu20.11), udev:amd64 (204-5ubuntu20.10, 204-5ubuntu20.11), policykit-1:amd64 (0.105-4ubuntu2, 0.105-4ubuntu2.14.04.1), gir1.2-gudev-1.0:amd64 (204-5ubuntu20.10, 204-5ubuntu20.11), libudev1:amd64 (204-5ubuntu20.10, 204-5ubuntu20.11), libpolkit-backend-1-0:amd64 (0.105-4ubuntu2, 0.105-4ubuntu2.14.04.1), libpolkit-gobject-1-0:amd64 (0.105-4ubuntu2, 0.105-4ubuntu2.14.04.1), linux-generic-lts-utopic:amd64 (3.16.0.33.26, 3.16.0.34.27), linux-libc-dev:amd64 (3.13.0-48.80, 3.13.0-49.81), libtasn1-6:amd64 (3.4-3ubuntu0.1, 3.4-3ubuntu0.2), linux-headers-generic-lts-utopic:amd64 (3.16.0.33.26, 3.16.0.34.27)            
            End-Date: 2015-04-09  11:33:12

---

### Post by joseph57 on 2015-04-09
I just realized that I lost my wallpaper as well - not sure if that matters.

---

