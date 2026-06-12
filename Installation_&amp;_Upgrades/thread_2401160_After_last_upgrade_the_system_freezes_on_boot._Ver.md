---
title: "After last upgrade the system freezes on boot. Version 18.04 LTS"
date: 2018-09-14
forum: Installation &amp; Upgrades
---

### Post by lluis-turro on 2018-09-14
When booting the screen stays blank, no messages and no HD activity.

If I reboot, enter the BIOS and use *Boot options* to select the EFI partition, the system boots slower but normal.

BIOS Secure Boot is enabled

The dpkg.log for last upgrade is:

```

2018-09-13 10:58:33 startup archives unpack
2018-09-13 10:58:33 upgrade shim:amd64 13-0ubuntu2 15+1533136590.3beb971-0ubuntu1
2018-09-13 10:58:33 status half-configured shim:amd64 13-0ubuntu2
2018-09-13 10:58:33 status unpacked shim:amd64 13-0ubuntu2
2018-09-13 10:58:33 status half-installed shim:amd64 13-0ubuntu2
2018-09-13 10:58:33 status half-installed shim:amd64 13-0ubuntu2
2018-09-13 10:58:33 status unpacked shim:amd64 15+1533136590.3beb971-0ubuntu1
2018-09-13 10:58:33 status unpacked shim:amd64 15+1533136590.3beb971-0ubuntu1
2018-09-13 10:58:33 upgrade shim-signed:amd64 1.34.9.2+13-0ubuntu2 1.37~18.04.1+15+1533136590.3beb971-0ubuntu1
2018-09-13 10:58:33 status half-configured shim-signed:amd64 1.34.9.2+13-0ubuntu2
2018-09-13 10:58:33 status unpacked shim-signed:amd64 1.34.9.2+13-0ubuntu2
2018-09-13 10:58:33 status half-installed shim-signed:amd64 1.34.9.2+13-0ubuntu2
2018-09-13 10:58:33 status half-installed shim-signed:amd64 1.34.9.2+13-0ubuntu2
2018-09-13 10:58:34 status unpacked shim-signed:amd64 1.37~18.04.1+15+1533136590.3beb971-0ubuntu1
2018-09-13 10:58:34 status unpacked shim-signed:amd64 1.37~18.04.1+15+1533136590.3beb971-0ubuntu1
2018-09-13 10:58:34 startup packages configure
2018-09-13 10:58:34 configure shim:amd64 15+1533136590.3beb971-0ubuntu1 <none>
2018-09-13 10:58:34 status unpacked shim:amd64 15+1533136590.3beb971-0ubuntu1
2018-09-13 10:58:34 status half-configured shim:amd64 15+1533136590.3beb971-0ubuntu1
2018-09-13 10:58:34 status installed shim:amd64 15+1533136590.3beb971-0ubuntu1
2018-09-13 10:58:34 configure shim-signed:amd64 1.37~18.04.1+15+1533136590.3beb971-0ubuntu1 <none>
2018-09-13 10:58:34 status unpacked shim-signed:amd64 1.37~18.04.1+15+1533136590.3beb971-0ubuntu1
2018-09-13 10:58:34 status half-configured shim-signed:amd64 1.37~18.04.1+15+1533136590.3beb971-0ubuntu1
2018-09-13 10:58:35 status installed shim-signed:amd64 1.37~18.04.1+15+1533136590.3beb971-0ubuntu1

```

---

