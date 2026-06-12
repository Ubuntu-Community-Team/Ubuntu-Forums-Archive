---
title: "Proper way to install Docker"
date: 2024-08-23
forum: Installation &amp; Upgrades
---

### Post by John Nagle on 2024-08-23
I need to install Docker on Ubuntu 22.04 LTS to run Open Drone Map, which has dropped support for their "snap" release.

The Ubuntu Store will install Docker, but the Docker it installs (Docker version 24.0.4) needs the Docker daemon. That apparently isn't installed, or isn't running.

I tried to start it, using 

    sudo systemctl start docker

But that got "Unit docker.service not found"

Does the Ubuntu Store version work? Or should that just be removed, and the complicated instructions on the Docker web site followed?

---

### Post by Tadaen_Sylvermane on 2024-08-23
```
sudo snap install docker
```

Haven't had much of an issue with it yet although you need to manually create a docker group and put your user into it, that or su into root. Otherwise it works perfectly

---

### Post by John Nagle on 2024-08-23
Right, the default docker is privileged. Bleah.

I really want to run the docker system with no privileges, but that looks complicated.

---

### Post by Tadaen_Sylvermane on 2024-10-23
Old thread. Look into podman.

---

