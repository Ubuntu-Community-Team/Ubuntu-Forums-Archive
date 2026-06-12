---
title: "Ubuntu core headless setup"
date: 2023-11-30
forum: Installation &amp; Upgrades
---

### Post by aristotle4 on 2023-11-30
Is there any documentation on performing a headless setup?

Can I just modify cmdline.txt along with network-config to get a clean boot where I can ssh in? It seems I ned to provide my SSO credentials and I don't see how to do that on a headless setup.

---

### Post by ian-weisser on 2023-11-30
Ubuntu Core Server is designed for headless running only after setup is complete.

It is not designed for headless setup.
Setup includes decompressing and setting up the filesystem, downloading your SSH public key from a trusted source (SSO), and creating your account. And a couple reboots in there, too.

For users doing mass-installs or creating appliances, don't install each one. Create your own complete installed-system image (complete with your public SSH key), clone it, and use a script to individualize the machine_id.

The in-development Ubuntu Core Desktop won't have the SSO requirement, and will have a much more familiar install method. But it's not released yet. Still in the oven.

---

