---
title: "Autoinstall in 23.10 broken?"
date: 2024-02-06
forum: Installation &amp; Upgrades
---

### Post by Jaxilian on 2024-02-06
Hi all

I tried adding landscape installation in my autoinstall file with this reference [https://cloudinit.readthedocs.io/en/23.4.1/reference/modules.html](https://cloudinit.readthedocs.io/en/23.4.1/reference/modules.html). 

To be honest, the whole autoinstall seems very buggy or plain straight broken. I have it working without the landscape code, but it seems to skip ALL the settings completely and doesn't even install the landscape-client. I can add the PPA though.
The older installation style, preseed in 22.04 I got landscape to work nice so I have working settings to use.

Does anyone have this working? Please share some if you do.

Is Ubuntu 23.10 desktop excluded from Landscape is some way in regards of autoinstall? If so, that would be bad cause 23.10 is all I can train on before 24.04 LTS comes. I tried looking into [https://github.com/canonical/subiquity/blob/main/autoinstall-schema.json](https://github.com/canonical/subiquity/blob/main/autoinstall-schema.json) to try find some evidence of existance, but nothing

Why is it on [https://discourse.ubuntu.com/t/how-to-install-landscape-client/39093](https://discourse.ubuntu.com/t/how-to-install-landscape-client/39093) if it doesn't work?
the active-directory also doesn't work in the autoinstall.

---

