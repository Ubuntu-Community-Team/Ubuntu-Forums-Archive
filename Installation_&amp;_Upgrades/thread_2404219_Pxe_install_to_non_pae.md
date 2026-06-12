---
title: "Pxe install to non pae"
date: 2018-10-21
forum: Installation &amp; Upgrades
---

### Post by atux on 2018-10-21
Hi. I am trying to install ubuntu 18 server in an Alix 2d13(pcengines) by making usenof a pxe. The thing is that when the client boots, it geta an IP and it finds the image to boot from. Then i am getting the following error:
[I][B]
This kernel requires the following features not present on the CPU:
pae
Unable to boot - please use a kernel appropriate for your CPU.[/B][/I]

Once the system boots, gets IP and finds the image, i cannot see anything on the screen (through serial). The only thing shown is the aforementioned error.
The PXE server is in dnsmasq
Any idea how to overcome this problem please?

---

